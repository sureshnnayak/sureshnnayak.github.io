# Deployment Guide

This guide will help you deploy your personal portfolio website to various hosting platforms.

## Quick Start

Your website is ready to deploy! It's built with vanilla HTML, CSS, and JavaScript, so it can be deployed to any static hosting service.

## Deployment Options

### 1. GitHub Pages (Recommended)

**Pros:** Free, easy setup, automatic deployments from Git
**Cons:** Public repository required for free tier

#### Steps:

1. **Create a GitHub repository:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/yourusername/your-repo-name.git
   git push -u origin main
   ```

2. **Enable GitHub Pages:**
   - Go to your repository on GitHub
   - Click "Settings" tab
   - Scroll down to "Pages" section
   - Select "Deploy from a branch"
   - Choose "main" branch and "/ (root)" folder
   - Click "Save"

3. **Your site will be available at:**
   `https://yourusername.github.io/your-repo-name`

### 2. Netlify (Recommended)

**Pros:** Free tier, easy custom domain, form handling, serverless functions
**Cons:** None for basic usage

#### Steps:

1. **Deploy via Git:**
   - Go to [netlify.com](https://netlify.com)
   - Click "New site from Git"
   - Connect your GitHub account
   - Select your repository
   - Build settings:
     - Build command: (leave empty)
     - Publish directory: `.` (root)
   - Click "Deploy site"

2. **Deploy via Drag & Drop:**
   - Zip your website folder
   - Go to [netlify.com](https://netlify.com)
   - Drag and drop your zip file
   - Your site will be deployed instantly

3. **Custom domain (optional):**
   - Go to Site settings > Domain management
   - Add your custom domain
   - Update DNS records as instructed

### 3. Vercel

**Pros:** Fast global CDN, easy deployment, great for developers
**Cons:** Limited free tier for personal projects

#### Steps:

1. **Install Vercel CLI:**
   ```bash
   npm i -g vercel
   ```

2. **Deploy:**
   ```bash
   cd your-website-folder
   vercel
   ```

3. **Follow the prompts:**
   - Link to existing project or create new
   - Choose your framework (select "Other")
   - Deploy

### 4. Surge.sh

**Pros:** Simple, fast, command-line deployment
**Cons:** Basic features only

#### Steps:

1. **Install Surge:**
   ```bash
   npm install -g surge
   ```

2. **Deploy:**
   ```bash
   cd your-website-folder
   surge
   ```

3. **Follow prompts:**
   - Choose domain name
   - Deploy

## Custom Domain Setup

### 1. Buy a Domain
- Popular registrars: Namecheap, GoDaddy, Google Domains
- Choose a memorable name related to your brand

### 2. Configure DNS
- Add a CNAME record pointing to your hosting provider
- For Netlify: `your-site-name.netlify.app`
- For GitHub Pages: `yourusername.github.io`

### 3. Update Hosting Settings
- Add your custom domain in hosting provider settings
- Enable SSL certificate (usually automatic)

## Pre-Deployment Checklist

- [ ] Test all pages locally
- [ ] Check all links work
- [ ] Verify images load correctly
- [ ] Test responsive design on mobile
- [ ] Update contact information
- [ ] Add real social media links
- [ ] Replace placeholder content
- [ ] Test resume download
- [ ] Verify article reader functionality

## Post-Deployment Tasks

1. **SEO Optimization:**
   - Add meta descriptions to each page
   - Create a sitemap.xml
   - Submit to Google Search Console

2. **Analytics:**
   - Add Google Analytics
   - Set up Google Search Console
   - Monitor site performance

3. **Content Updates:**
   - Add new articles regularly
   - Update project portfolio
   - Keep resume current

## Maintenance

### Adding New Content

1. **New Article:**
   - Create `.md` file in `content/articles/`
   - Add entry to `data/content.json`
   - Commit and push changes

2. **New Project:**
   - Add entry to `data/content.json`
   - Add project images to `assets/images/`
   - Commit and push changes

3. **Update Resume:**
   - Replace `assets/documents/resume.pdf`
   - Update resume content in `resume.html`
   - Commit and push changes

### Regular Updates

- **Monthly:** Review and update content
- **Quarterly:** Check all links and functionality
- **Annually:** Review design and consider updates

## Troubleshooting

### Common Issues

1. **Images not loading:**
   - Check file paths are correct
   - Ensure images are in the right folder
   - Verify file permissions

2. **Articles not displaying:**
   - Check `data/content.json` syntax
   - Verify markdown files exist
   - Check browser console for errors

3. **Mobile responsiveness issues:**
   - Test on actual devices
   - Check TailwindCSS classes
   - Verify viewport meta tag

### Getting Help

- Check browser developer console for errors
- Validate HTML at [validator.w3.org](https://validator.w3.org)
- Test on multiple browsers
- Check hosting provider documentation

## Performance Optimization

### Image Optimization
- Use WebP format when possible
- Compress images before uploading
- Use appropriate image sizes

### Code Optimization
- Minify CSS and JavaScript (if not using CDN)
- Enable gzip compression
- Use CDN for external libraries

### Caching
- Set appropriate cache headers
- Use browser caching for static assets
- Consider using a CDN

## Security Considerations

- Keep dependencies updated
- Use HTTPS everywhere
- Set security headers
- Regular security audits
- Backup your content regularly

---

## Quick Commands

```bash
# Test locally
python3 -m http.server 8000
# or
npx serve .

# Deploy to Netlify
netlify deploy --prod

# Deploy to Vercel
vercel --prod

# Deploy to Surge
surge
```

Your website is now ready for deployment! Choose the option that best fits your needs and get your portfolio online.
