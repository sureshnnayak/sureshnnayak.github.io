# Article Visibility Control

This document explains how to control which articles are published and visible on your website.

## How It Works

Each article in `data/content.json` now has a `published` field that controls visibility:

- `"published": true` - Article is visible on the website
- `"published": false` - Article is hidden from the website
- No `published` field - Article is visible (default behavior)

## Current Article Status

| Article | Status | Visibility |
|---------|--------|------------|
| ShelfHelp: AI-Assisted Shopping | `published: true` | ✅ Visible |
| ArcOS systemd Migration | `published: true` | ✅ Visible |
| AI/ML Networking with NVIDIA Spectrum-3 | `published: true` | ✅ Visible |
| Broadcom Tomahawk 5 Platform Bring-up | `published: false` | ❌ Hidden |
| Automating Firmware Upgrades in ArcOS | `published: true` | ✅ Visible |

## How to Change Article Visibility

### To Hide an Article:
1. Open `data/content.json`
2. Find the article you want to hide
3. Change `"published": true` to `"published": false`
4. Save the file
5. Commit and push changes

### To Show a Hidden Article:
1. Open `data/content.json`
2. Find the article you want to show
3. Change `"published": false` to `"published": true`
4. Save the file
5. Commit and push changes

### To Add a New Article:
1. Add the article to `data/content.json`
2. Set `"published": true` to make it visible
3. Set `"published": false` to keep it hidden initially
4. Save the file
5. Commit and push changes

## Example

```json
{
  "id": 6,
  "title": "My New Article",
  "excerpt": "This is a new article...",
  "slug": "my-new-article",
  "date": "2025-01-20",
  "readTime": 5,
  "tags": ["New", "Article"],
  "featured": false,
  "published": false,  // ← This controls visibility
  "file": "content/articles/my-new-article.md"
}
```

## Where This Affects Visibility

The `published` field controls visibility in:

1. **Articles Page** (`/articles.html`) - Only published articles are shown
2. **Home Page** (`/index.html`) - Only published articles appear in "Latest Articles" section
3. **Search Results** - Only published articles are searchable
4. **Tag Filtering** - Only published articles are included in tag-based filtering

## Benefits

- **Draft Management**: Keep articles as drafts while working on them
- **Selective Publishing**: Choose which articles to showcase
- **Content Strategy**: Control your public content without deleting articles
- **Easy Toggle**: Quickly show/hide articles as needed

## Notes

- Hidden articles are still in the repository and can be made visible anytime
- The article files themselves are not affected, only their visibility
- This system works with both featured and non-featured articles
- Changes take effect immediately after pushing to GitHub Pages
