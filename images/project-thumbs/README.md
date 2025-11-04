# Project Thumbnail Images

This folder contains thumbnail images for project cards.

## Required Images

Please add the following images to this folder:

1. **light-exposure.jpg** (for AI-Driven Light Exposure Classification project)
   - Recommended size: 600×400px or 16:9 aspect ratio
   - Suggested content: Wearable sensor, light spectrum visualization, or heatmap

2. **primekg.jpg** (for PrimeKG-RGCN Link Prediction project)
   - Recommended size: 600×400px or 16:9 aspect ratio
   - Suggested content: Knowledge graph visualization or network diagram

## Image Guidelines

- **Format:** JPG or PNG
- **Size:** Keep under 500KB for web performance
- **Aspect Ratio:** 16:9 or 1:1 for consistency
- **Resolution:** At least 600px wide for retina displays
- **Fallback:** If images are missing, cards will display without thumbnails

## Adding New Projects

When adding a new project, create a thumbnail and reference it in the project's front matter:

```yaml
thumb: /images/project-thumbs/your-project-name.jpg
```

---

**Temporary Note:** Until real images are added, you can:
- Use placeholder services (e.g., https://via.placeholder.com/600x400)
- Remove the `thumb:` field from project front matter to hide the image area
- Create simple graphics using tools like Canva or Figma
