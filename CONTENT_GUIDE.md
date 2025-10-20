# Content Management Guide

This guide explains how to easily maintain and update your portfolio website content.

## Overview

Your website is designed for easy maintenance - just edit Markdown files and JSON manifests. No build process required!

## File Structure

```
website/
├── index.html              # Home page
├── projects.html           # Projects listing
├── articles.html           # Articles listing
├── reader.html            # Dynamic article reader
├── resume.html            # Resume page
├── data/
│   └── content.json       # Main content manifest
├── content/
│   ├── articles/          # Markdown articles
│   ├── projects/          # Project content (optional)
│   └── excalidraw/        # Excalidraw diagrams
├── assets/
│   ├── images/            # Images and graphics
│   └── documents/         # PDFs and documents
└── README.md
```

## Adding New Articles

### 1. Create Markdown File

Create a new `.md` file in `content/articles/`:

```markdown
# Your Article Title

Brief description of your article.

## Introduction

Your article content here...

## Conclusion

Wrap up your thoughts...
```

### 2. Update Content Manifest

Add your article to `data/content.json`:

```json
{
  "articles": [
    {
      "id": 6,
      "title": "Your Article Title",
      "excerpt": "Brief description of your article.",
      "slug": "your-article-slug",
      "date": "2024-01-20",
      "readTime": 5,
      "tags": ["JavaScript", "Tutorial"],
      "featured": false,
      "file": "content/articles/your-article-slug.md"
    }
  ]
}
```

### 3. Article Properties

- **id**: Unique number (increment from last article)
- **title**: Article title (displayed on cards)
- **excerpt**: Short description (displayed on cards)
- **slug**: URL-friendly version of title
- **date**: Publication date (YYYY-MM-DD format)
- **readTime**: Estimated reading time in minutes
- **tags**: Array of relevant tags
- **featured**: Boolean (true for homepage display)
- **file**: Path to markdown file

## Adding New Projects

### 1. Update Content Manifest

Add your project to `data/content.json`:

```json
{
  "projects": [
    {
      "id": 5,
      "title": "Your Project Name",
      "description": "Brief project description.",
      "technologies": ["JavaScript", "React", "Node.js"],
      "featured": true,
      "demoUrl": "https://your-demo.com",
      "githubUrl": "https://github.com/yourusername/project",
      "image": "assets/images/your-project.png",
      "date": "2024-01-20"
    }
  ]
}
```

### 2. Add Project Image

Save your project image as `assets/images/your-project.png` (or .jpg, .svg).

### 3. Project Properties

- **id**: Unique number
- **title**: Project name
- **description**: Brief description
- **technologies**: Array of tech stack
- **featured**: Boolean (true for homepage)
- **demoUrl**: Live demo URL
- **githubUrl**: Source code URL
- **image**: Path to project image
- **date**: Project completion date

## Updating Resume

### 1. Replace PDF

Replace `assets/documents/resume.pdf` with your updated resume.

### 2. Update HTML Content

Edit the resume content in `resume.html` to match your PDF.

## Adding Excalidraw Diagrams

### 1. Export from Excalidraw

- Create your diagram in Excalidraw
- Export as PNG or SVG
- Save to `content/excalidraw/`

### 2. Reference in Articles

In your markdown articles:

```markdown
![My Diagram](../excalidraw/my-diagram.png)
```

## Image Management

### Supported Formats
- PNG (recommended for photos)
- JPG (for photos)
- SVG (for icons and graphics)
- WebP (modern format, good compression)

### Image Optimization Tips
- Keep file sizes under 500KB
- Use appropriate dimensions
- Compress images before uploading
- Use descriptive filenames

## Content Best Practices

### Articles
- Write clear, engaging titles
- Use descriptive excerpts
- Add relevant tags
- Include code examples when helpful
- Use proper markdown formatting

### Projects
- Write compelling descriptions
- List all relevant technologies
- Provide working demo links
- Use high-quality screenshots
- Keep descriptions concise

### SEO Optimization
- Use descriptive page titles
- Add meta descriptions
- Use alt text for images
- Create meaningful URLs
- Write quality content

## Quick Updates

### Change Homepage Content
Edit the About Me section in `index.html`:

```html
<p class="text-lg text-gray-600 mb-6">
    Your updated bio here...
</p>
```

### Update Contact Information
Update contact details in `resume.html` and footer sections.

### Change Social Links
Update social media URLs in all HTML files' footer sections.

## Troubleshooting

### Article Not Showing
- Check `data/content.json` syntax
- Verify markdown file exists
- Check browser console for errors

### Image Not Loading
- Verify file path is correct
- Check file exists in assets folder
- Ensure proper file permissions

### Styling Issues
- Check TailwindCSS classes
- Verify responsive design
- Test on different screen sizes

## Automation Ideas

### Content Templates
Create templates for common content types:

```markdown
# Article Template

# {{title}}

{{excerpt}}

## Introduction

## Main Content

## Conclusion
```

### Batch Updates
Use find/replace to update multiple files:
- Update social links across all pages
- Change color scheme
- Update contact information

### Content Validation
Create a simple script to validate `content.json`:
- Check for required fields
- Validate file paths
- Ensure unique IDs

## Maintenance Schedule

### Weekly
- Check for broken links
- Review new content ideas
- Update project status

### Monthly
- Add new articles
- Update project portfolio
- Review and optimize images

### Quarterly
- Major content review
- Design updates
- Performance optimization

---

## Quick Reference

### Common Tasks

**Add Article:**
1. Create `.md` file in `content/articles/`
2. Add entry to `data/content.json`
3. Deploy changes

**Add Project:**
1. Add entry to `data/content.json`
2. Add image to `assets/images/`
3. Deploy changes

**Update Resume:**
1. Replace `assets/documents/resume.pdf`
2. Update `resume.html` content
3. Deploy changes

**Change Social Links:**
1. Update footer sections in all HTML files
2. Deploy changes

Your website is designed to be easy to maintain - just edit the content files and deploy!
