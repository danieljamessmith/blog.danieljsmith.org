# Blog Resurrection Plan

> Resurrecting the Quarto blog and integrating it into the danieljsmith.org subdomain structure.
> 
> **Decision**: Keep ALL posts (no curation). Add "Legacy" category to old posts.
> **Theme**: Amber/Orange (warm, creative, writing-focused)
> **Deployment**: GitHub Pages with custom domain (blog.danieljsmith.org)

---

## Progress

- [x] **Phase 1**: Get blog running locally (Quarto 1.8.27 installed, preview working)
- [x] **Phase 2**: Post curation decision (keeping all posts)
- [x] **Phase 3**: Update configuration
- [x] **Phase 4**: Amber theme styling
- [x] **Phase 5**: Write resurrection post
- [x] **Phase 6**: Quick wins agent pass
- [x] **Phase 7**: Landing page integration
- [x] **Phase 8**: Deployment

---

## Phase 3: Update Configuration

Update `_quarto.yml`:

| Setting | Current | New |
|---------|---------|-----|
| `site-url` | `danieljamessmith.github.io/portfolio/` | `https://blog.danieljsmith.org` |
| `title` | `"Blog"` | `"blog.danieljsmith.org"` |
| Navbar | LinkedIn, GitHub Repo, About | `← Main Site`, About, GitHub |

### Navbar changes

Add link back to hub (following tuition/resources pattern):

```yaml
navbar:
  left:
    - text: "← Main Site"
      href: https://danieljsmith.org
  right:
    - about.qmd
    - icon: github
      href: https://github.com/danieljamessmith
```

### About page updates

Update `about.qmd`:
- Refresh bio text
- Update LinkedIn link (check current: `linkedin.com/in/danieljames-smith/`)
- Update GitHub link (check current: `github.com/danieljamessmith`)

---

## Phase 4: Amber Theme Styling

### Color palette

- **Primary**: Amber `#f59e0b`, `#d97706`
- **Background light**: Warm white/cream
- **Background dark**: Slate with amber accents
- **Code blocks**: Keep purple border `#413764` or shift to amber

### Files to edit

1. **`custom.scss`** - Add SCSS variables:

```scss
/*-- scss:defaults --*/

// Amber primary colors
$primary: #f59e0b;
$secondary: #d97706;
$link-color: #b45309;

// Light theme
$body-bg: #fffbf5;
$body-color: #1f2937;

// Code blocks
$code-block-border-left: #f59e0b;
```

2. **`styles.css`** - Typography and accent tweaks

3. **`_quarto.yml`** - Update theme config:

```yaml
format:
  html:
    theme:
      light: [flatly, custom.scss]
      dark: [darkly, custom.scss]
    css: styles.css
```

---

## Phase 5: Resurrection Post

Create `posts/resurrection/index.qmd`:

```yaml
---
title: "The Blog Returns"
author: "Daniel J Smith"
date: "2026-01-28"
categories: [Announcement]
description: "This blog has been resurrected and is now part of the danieljsmith.org site family."
---
```

Content (you write):
- Brief announcement that blog is back
- Part of new danieljsmith.org site family
- Note about legacy posts from 2023-2024

---

## Phase 6: Quick Wins Agent Pass

- [ ] Add `Legacy` category to all existing posts (19 posts)
- [ ] Check notebooks for outdated patterns
- [ ] Ensure consistent frontmatter across posts
- [ ] Remove any dead/broken links
- [ ] Clean up `docs/` folder (will be regenerated)

---

## Phase 7: Landing Page Integration

Add blog card to `danieljsmith.org/src/pages/index.astro`:

```javascript
{
  title: 'Blog',
  description: 'Technical writing on mathematics, machine learning, and data science projects.',
  href: 'https://blog.danieljsmith.org',
  subdomain: 'blog.danieljsmith.org',
  theme: 'amber',
}
```

Add amber theme styling to match existing green/blue patterns:

```javascript
// In the card component
site.theme === 'amber' && "shadow-lg shadow-amber-500/10 hover:shadow-amber-500/20",
site.theme === 'amber' && "bg-gradient-to-br from-amber-50 via-amber-100/80 to-orange-100",
site.theme === 'amber' && "bg-gradient-to-br from-amber-400 to-orange-400",
// ... etc for all theme conditionals
```

---

## Phase 8: Deployment

1. **Create CNAME file** at `public/CNAME` (or root, depending on Quarto config):
   ```
   blog.danieljsmith.org
   ```

2. **Update `.gitignore`** - Current:
   ```
   /.quarto/
   ```
   Keep as-is (docs/ should be committed for GitHub Pages)

3. **Build final site**:
   ```bash
   quarto render
   ```

4. **Verify GitHub Pages settings**:
   - Source: Deploy from branch
   - Branch: main (or master)
   - Folder: /docs

5. **Push to GitHub**

---

## File Reference

### Files to modify

| File | Changes |
|------|---------|
| `_quarto.yml` | site-url, title, navbar |
| `custom.scss` | Amber color variables |
| `styles.css` | Typography tweaks |
| `about.qmd` | Updated bio and links |

### Files to create

| File | Purpose |
|------|---------|
| `posts/resurrection/index.qmd` | Announcement post |
| `public/CNAME` | Custom domain for GitHub Pages |

### Existing posts (all being kept)

| Prefix | Count | Topic |
|--------|-------|-------|
| bte | 4 | Boltzmann Transport Equation (undergrad research) |
| eh | 5 | Emmanuel House charity projects |
| ng | 3 | Neural networks from scratch |
| k | 2 | Kaggle/ML competitions |
| ste | 1 | STEP exam solution (tuition relevant) |
| yt | 4 | YouTube tutorial-inspired projects |

---

## Commands Reference

```bash
# Preview locally
quarto preview

# Full render
quarto render

# Check Quarto version
quarto --version
```

---

## Related Sites

- **Landing**: [danieljsmith.org](https://danieljsmith.org) - Astro + Tailwind
- **Tuition**: [tuition.danieljsmith.org](https://tuition.danieljsmith.org) - Emerald/green theme
- **Resources**: [resources.danieljsmith.org](https://resources.danieljsmith.org) - Slate/indigo theme
- **Blog**: [blog.danieljsmith.org](https://blog.danieljsmith.org) - Amber/orange theme (this site)
