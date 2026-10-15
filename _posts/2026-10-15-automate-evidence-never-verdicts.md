---
layout: post
title: "Automate the evidence, never the verdict"
date: 2026-10-15
tags: [Cui, AI Tools, LLM, Research Tools, Design]
giscus_comments: true
author: Arnold
toc:
    sidebar: right
---

*Design notes from building Cui, a research tool that argues with you, and the rule that ended up shaping almost every other decision in it.*

Most AI writing and research tools fail the same way: they agree with you. Ask whether your idea is good and you get a paragraph of encouragement. That's sycophancy, and by now everyone knows about it.

The obvious fix is to flip the sign and make the model critical: let it score your idea, flag the weak claims, tell you what to drop. That fails too, just more quietly. A model that grades your ideas doesn't remove the bias. It replaces your judgment with its own, and its own is mostly the consensus of its training data. In research that's a real problem, because good taste is often anti-consensus. The idea everyone thinks is dead is sometimes exactly the one worth working on.

So Cui runs on one rule:

> **Automate evidence-gathering. Never automate verdicts.**

*Evidence* is anything that brings facts to the surface: finding supporting papers, finding contradicting ones, digging up counterexamples, noticing that a new claim collides with something you said three months ago. A machine can do all of that, and it should do it aggressively.

A *verdict* is the decision itself: this claim lives or dies, here's why, this is or isn't worth my time. In Cui, only the human produces a verdict. The model can attack. It can't rule. In the current code that's literal: no machine path writes a verdict, not even as a suggestion. A verdict is a user action, and it won't go through without a written reason.

Stated like that, the rule sounds obvious. What I didn't expect was how many other design questions it settles once you take it seriously. The rest of this post is about those consequences. Some are enforced in today's code, some were prototyped in an earlier version and archived when I redesigned it, and one my own product still breaks. There's a table at the end saying which is which.

## 1. The attacker may read your history. The judge may not.

Cui keeps the full record of every claim you put through review: challenges, answers, verdicts. The natural next step is to use that history, so challenges get sharper over time and sound more like the objections *you* would raise.

An earlier prototype of Cui (June–July 2026) did this with a **precedent prior**: the challenge generator was given the causes of death of claims you had killed before. If your ideas kept dying because the sample couldn't carry the conclusion, the next challenge was more likely to come in from that angle.

The verdict side never sees any of it. That's not a shortcut in the implementation; it falls straight out of the rule. A sharper question is still evidence-gathering. A ruling that "judges the way you did last time" is a verdict, and it's automated.

Once you draw the line there, two failure modes show up as mirror images of each other:

- **Precedent conviction:** "You killed something like this before, so this one is probably dead too." The system manufactures consistency instead of looking for truth, and your taste hardens into inertia.
- **Precedent amnesty:** the reverse. "Claims like this survived before, so go easy on this one." It's the same substitution in the other direction: a fact about the past quietly becomes a conclusion about the present.

That's why the precedent prior took only **kills**; survivals were excluded by construction. This connects to another rule in Cui: **survived is not a truth certificate.** A surviving claim held up against the evidence and arguments of that round, nothing more, and the UI says so ("held up this round; not a certificate of truth"). If you feed survivals back in as "this kind of idea is fine", the challenger learns to read "made it through once" as "safe", and the system loses the one property it exists for, which is being adversarial.

## 2. Pick precedents by how they died, not what they were about

When a new claim comes in, which past kills are relevant to it? The intuitive answer is topic similarity: retrieve old claims that share words with the new one.

That turns out to be exactly wrong. The most useful precedents are the ones that **recur across topics**. Suppose you've killed claims about RLHF, retrieval and data curation, all because the evaluation couldn't separate the effect from a confound. That isn't about any of those topics. It's a habit of your method, and it's the pattern most worth putting in front of you. A word-overlap prefilter (no shared terms, discard) throws away precisely those precedents, and the precedent prior degrades into a weaker copy of duplicate detection.

That prototype got half of this right: it deliberately skipped the topic filter and just took your most recent kills. The full rule is to select by **cause of death and attack surface**. That part isn't built yet.

## 3. A verdict is not a boolean

For a kill to be useful later, it has to record how the claim died. In Cui a verdict is either *survived* or one of four causes of death:

- **Refuted:** it's wrong. A duplicate of an idea you already killed counts here too.
- **Not worth it:** it's right, but it isn't worth doing. This is the strongest signal of personal taste the system ever gets.
- **Boundary:** the original wording died, but the way it died draws a boundary, and a narrower version may still stand. Often the most valuable corpse in the record: what's worth remembering is "you narrowed it to X", not "you rejected it".
- **Circumstantial:** you can't defend it today, you're missing material, or now isn't the time. This is the only non-terminal cause, and it **requires a revival condition**: what would have to be true for the claim to be worth reopening. The event itself is rejected without one.

That last requirement does more work than it looks like. "I'll come back to it later" is the most comfortable lie in research. If you can't name a revival condition, the claim didn't die of circumstance. It died because you don't think it's worth doing, and the structure makes you say so.

## 4. Evidence has to be honest about "nothing"

If machines do the evidence-gathering, the evidence has to be trustworthy, and the most common way it fails is overclaiming. A retrieval system that always finds *something* supporting your claim is just sycophancy with citations.

Every paper Cui checks against a claim gets one of four labels:

- **supports**
- **contradicts**: the paper addresses the claim and weakens it.
- **silent**: the paper doesn't speak to this claim.
- **cannot assess**: the system couldn't tell.

**"Nothing found" is a first-class result, not a failure.** And it's kept apart from "couldn't tell": when the model's output fails to parse, the candidate is recorded as *cannot assess*, never as *silent*. A failure never gets dressed up as a finding.

There's a deterministic hook on the other side as well. When you confirm that a paper contradicts your claim, a challenge goes onto the board automatically, in the same commit, built from a fixed template with no LLM call. The system makes sure confirmed counter-evidence gets raised. It doesn't decide what that evidence means.

## 5. The quieter failure: ghost-writing

Sycophancy is easy to spot once you look for it: the model is flattering you, and you can tell.

**Ghost-writing** is worse, because you can't tell. It happens when the system helps turn a half-formed idea into a claim: an itch like "X and Y feel related, but I can't say how". The output is good. You nod and sign off. Now your record of "claims I came up with and defended" is really a record of claims the system steered you toward, and any personalization built on that history is learning the system, not you.

The line I settled on:

- A **static template** (assertion, scope, what would count as a counterexample) is fine. It's identical for every idea. It defines what a claim *is*, not what *this* claim should say.
- A **scaffold the model builds live for this particular itch** is ghost-writing, because it's already making decisions about your idea.

So while an idea is still forming, the system should ask and offer nothing: no candidate wording, not even a single phrase.

Here's where my own product falls short. Cui's free-form claim path follows the rule: a blank text box and three fixed questions. But the guided literature mode, added later, opens by having the model draft three to five candidate hypotheses for your question. They're never copied into your claim, and the prompt calls them candidates rather than conclusions, but they're exactly the kind of live, idea-specific scaffold described above. Writing this post is how I noticed; it's tracked in [#22](https://github.com/arnold117/Cui/issues/22).

The same reasoning decides when precedents should be allowed in. A claim that already exists and is under attack gets them, because that's evidence. A claim that's still forming doesn't, because that's shaping, and it pushes new ideas back into old grooves, including your own. A claim being judged doesn't either, because that's a verdict.

## 6. Why bother: your history is the asset

All of this matters because of what Cui is meant to become. The long-term bet is that your review history (every killed hypothesis, every narrowing, every "not worth it") is a private asset that compounds into a personal **Lens**: something that picks up how *you* read literature and defend claims, and brings that back the next time you think.

That only works if the history is actually yours. So the rule for the Lens is that it reads only trajectories that went through the review gate. The Lens itself isn't in the current code. What is there is the groundwork it depends on: every claim's history is an append-only event stream, and ideas you park for later sit in a separate sealed store, so half-formed thoughts can't leak into it. And if the system had written your verdicts or your claims, the Lens would just be learning from itself.

## If you're building an AI tool that judges things

None of this is specific to research. Code review bots, grading assistants and screening tools all have the same shape: a model that could gather evidence, and a temptation to let it rule. What I'd take away:

1. **Separate evidence from verdict in the data model, not just in the prompt.** A verdict should only ever come from a human, or sit as a pending suggestion until a human confirms it.
2. **Let the attacker read history. Never let the judge.**
3. **Never feed "passed" back in as "good".**
4. **Make "nothing found" a real output**, and keep it separate from errors.
5. **Watch for ghost-writing.** If users agree with everything your tool helps them produce, check whose ideas those are. That includes your own tool.

## What's built and what isn't

| Idea | Status |
| --- | --- |
| No machine-written verdicts; a verdict needs a written reason | In the current code |
| Four causes of death; *circumstantial* requires a revival condition | In the current code |
| *silent* and *cannot assess* as separate results; a failed parse is never recorded as *silent* | In the current code |
| A confirmed contradiction raises a challenge from a fixed template, with no LLM | In the current code |
| "Survived is not a truth certificate" in the UI copy | In the current code |
| Precedent prior fed only by kills, with no topic prefilter | Prototyped June–July 2026; archived in the redesign |
| Selecting precedents by cause of death | Design rule; not built |
| No ghost-writing | Free-form claim path: yes. Guided literature mode: not yet |
| Lens | Not in the current code (an early read-out was prototyped and archived); parked ideas already live in a separate sealed store |

## About Cui

Cui (淬, "to quench", as in tempering steel) is an open-source research environment. You start from a question, explore the literature, write your own claims, put them through adversarial review rounds, confirm the evidence, and come out with a map of the field and a list of gaps. Cui (formerly LitScribe, my literature-review engine) has been in development since January 2026; the current version is a redesign started in June.

It's early: a solo project, with the UI in the middle of a redesign and rough edges everywhere. But the core loop works. The domain vocabulary behind this post (in Chinese) is in [`CONTEXT.md`](https://github.com/arnold117/Cui/blob/main/CONTEXT.md).

Repo: [github.com/arnold117/Cui](https://github.com/arnold117/Cui) (MIT). Issues and arguments are welcome. It was built to be argued with.
