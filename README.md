# Personal Portfolio Website

A clean, modern personal website built with vanilla HTML, CSS, and JavaScript. Perfect for showcasing your work as a software engineer, content creator, or any professional.

## Features

- **Zero Build Process**: Pure HTML, CSS, and JavaScript - no frameworks or build steps required
- **Easy Content Management**: Just edit Markdown files and JSON manifests
- **Dynamic Content Loading**: Articles and projects load dynamically from JSON files
- **Markdown Rendering**: Built-in support for rendering Markdown articles with zero-md
- **Responsive Design**: Mobile-first design using TailwindCSS
- **SEO Friendly**: Semantic HTML structure for better search engine optimization
- **Fast Loading**: Optimized for performance with minimal dependencies

## Project Structure

```
website/
├── index.html              # Home page
├── projects.html           # Projects listing page
├── articles.html           # Articles listing page
├── reader.html            # Dynamic Markdown reader
├── resume.html            # Resume page
├── data/
│   └── content.json       # Content manifest
├── content/
│   ├── articles/          # Markdown articles
│   ├── projects/          # Project content
│   └── excalidraw/        # Excalidraw diagrams
├── assets/
│   ├── images/            # Images and graphics
│   └── documents/         # PDFs and documents
└── README.md
```

## Getting Started

### 1. Clone or Download

```bash
git clone <your-repo-url>
cd website
```

### 2. Customize Content

Edit the `data/content.json` file to add your projects and articles:

```json
{
  "projects": [
    {
      "id": 1,
      "title": "Your Project Name",
      "description": "Project description",
      "technologies": ["JavaScript", "React", "Node.js"],
      "featured": true,
      "demoUrl": "https://your-demo.com",
      "githubUrl": "https://github.com/yourusername/project",
      "image": "assets/images/project.png",
      "date": "2024-01-15"
    }
  ],
  "articles": [
    {
      "id": 1,
      "title": "Your Article Title",
      "excerpt": "Article excerpt",
      "slug": "article-slug",
      "date": "2024-01-15",
      "readTime": 5,
      "tags": ["JavaScript", "Tutorial"],
      "featured": true,
      "file": "content/articles/article-slug.md"
    }
  ]
}
```

### 3. Add Your Content

- **Articles**: Create Markdown files in `content/articles/`
- **Images**: Add images to `assets/images/`
- **Documents**: Add PDFs to `assets/documents/`
- **Profile Photo**: Replace the placeholder in `index.html`

### 4. Update Personal Information

Edit the following files to customize your information:

- `index.html` - Update the About Me section
- `resume.html` - Update your resume content
- `data/content.json` - Update contact information and social links

### 5. Test Locally

Open `index.html` in your browser or use a local server:

```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx serve .

# Using PHP
php -S localhost:8000
```

## Content Management

### Adding New Articles

1. Create a new Markdown file in `content/articles/`
2. Add the article entry to `data/content.json`
3. The article will automatically appear on the articles page

### Adding New Projects

1. Add project entry to `data/content.json`
2. Optionally add project images to `assets/images/`
3. The project will appear on the projects page

### Excalidraw Integration

To embed Excalidraw diagrams in your articles:

1. Export your Excalidraw diagram as PNG or SVG
2. Save it in `content/excalidraw/`
3. Reference it in your Markdown:

```markdown
![My Diagram](../excalidraw/my-diagram.png)
```

## Customization

### Styling

The website uses TailwindCSS for styling. You can customize the appearance by:

1. Modifying the Tailwind classes in HTML files
2. Adding custom CSS in the `<style>` sections
3. Changing the color scheme by updating Tailwind classes

### Adding New Pages

1. Create a new HTML file
2. Copy the navigation structure from existing pages
3. Add the page to the navigation menu
4. Update the mobile menu as well

### Modifying the Layout

The layout is built with CSS Grid and Flexbox. Key layout classes:

- `max-w-6xl mx-auto` - Centers content with max width
- `grid md:grid-cols-2 lg:grid-cols-3` - Responsive grid layout
- `flex flex-col sm:flex-row` - Responsive flex layout

## Deployment

### GitHub Pages

1. Push your code to a GitHub repository
2. Go to repository Settings > Pages
3. Select "Deploy from a branch" and choose "main"
4. Your site will be available at `https://yourusername.github.io/repository-name`

### Netlify

1. Connect your GitHub repository to Netlify
2. Set build command to empty (no build needed)
3. Set publish directory to root
4. Deploy automatically on every push

### Vercel

1. Import your GitHub repository to Vercel
2. No build configuration needed
3. Deploy automatically

### Custom Domain

1. Add a `CNAME` file with your domain name
2. Configure DNS settings to point to your hosting provider
3. Update the domain in your hosting provider's settings

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Performance

The website is optimized for performance:

- Minimal JavaScript (only for dynamic content loading)
- CDN-hosted CSS and fonts
- Optimized images (add your own optimized images)
- No build process means faster development

## Contributing

Feel free to fork this project and customize it for your needs. If you create improvements, consider submitting a pull request.

## License

This project is open source and available under the [MIT License](LICENSE).

## Support

If you have questions or need help customizing the website:

1. Check the documentation in this README
2. Look at the example content in `data/content.json`
3. Examine the HTML structure in the existing pages
4. Open an issue in the repository

## Changelog

### Version 1.0.0
- Initial release
- Home page with About Me, Projects, Articles, Resume sections
- Dynamic content loading from JSON
- Markdown article rendering
- Responsive design with TailwindCSS
- Mobile-friendly navigation

---

**Happy coding!** 🚀

*This website template is designed to be simple, fast, and easy to maintain. Perfect for developers who want to focus on content rather than complex build processes.*
