# Arnold Zhou's Academic Website

[![Deployment Status](https://github.com/arnold117/arnold117.github.io/workflows/deploy/badge.svg)](https://github.com/arnold117/arnold117.github.io/actions)

Personal academic website of Arnold Zhou (周亚诺), showcasing research in ML for Digital Phenotyping, Wearable Sensing, and Light & Health.

🌐 **Live Site**: [https://arnold117.github.io](https://arnold117.github.io)

## About

This website is built using the [al-folio](https://github.com/alshedivat/al-folio) Jekyll theme, which is designed specifically for academics, researchers, and students. It provides a clean, responsive design with features optimized for presenting academic content.

## Features

- **Research Projects**: Showcase of current and past research work
- **Blog**: Technical blog posts and research updates
- **Publications**: (Coming soon) Auto-generated from BibTeX
- **CV**: Online curriculum vitae
- **Light/Dark Mode**: Theme switcher for comfortable viewing
- **Responsive Design**: Optimized for all devices

## Tech Stack

- **Jekyll**: Static site generator
- **al-folio Theme**: Academic website template
- **GitHub Pages**: Hosting
- **Liquid**: Templating language
- **Sass**: CSS preprocessing

## Local Development

To run this site locally:

```bash
# Install dependencies
bundle install

# Serve locally
bundle exec jekyll serve

# Visit http://localhost:4000
```

## Content Structure

```
├── _pages/          # Main pages (about, CV, etc.)
├── _posts/          # Blog posts
├── _projects/       # Research projects
├── _news/           # News and announcements
├── _bibliography/   # Publications (BibTeX)
├── assets/          # Images, CSS, JS
└── _config.yml      # Site configuration
```

## Customization

Key configuration is in `_config.yml`. See [CUSTOMIZE.md](CUSTOMIZE.md) for detailed instructions.

## Credits

- Theme: [al-folio](https://github.com/alshedivat/al-folio) by Maruan Al-Shedivat
- Hosted on [GitHub Pages](https://pages.github.com/)

## License

The theme is available as open source under the terms of the [MIT License](LICENSE).

The content (blog posts, projects, etc.) is © Arnold Zhou.

---

Last updated: January 2025
