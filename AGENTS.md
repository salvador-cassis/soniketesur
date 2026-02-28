# AGENTS.md - Sonikete Sur Website

## Project Overview

Sonikete Sur is a static HTML website for a professional sound design business. It's a single-page portfolio with embedded CSS and JavaScript, designed to showcase sound design services for animation and independent film.

**Repository**: https://github.com/salvador-cassis/soniketesur  
**Website**: https://soniketesur.com (GitHub Pages)

**Key Files**:
- `index.html` — Complete single-page website with embedded `<style>` and `<script>`
- `CNAME` — Domain configuration (soniketesur.com)

---

## Build & Development Commands

This is a **static HTML project** with no build tools, frameworks, or dependencies.

### Development
```bash
# Serve locally (recommended for testing)
python3 -m http.server 8000
# Then open http://localhost:8000

# Or open index.html directly in browser (file://)
```

### Testing & Validation
```bash
# No automated tests - manual browser testing required
# Test in: Chrome, Firefox, Safari, mobile browsers

# HTML validation - use W3C validator or browser devtools
# CSS validation - browser devtools no errors
# JavaScript - browser console no errors
```

### Linting
```bash
# No linting configured - validate HTML/CSS/JS manually
# Use browser devtools for debugging
```

### Deployment
```bash
# Push to GitHub - GitHub Pages auto-deploys from main branch
git add .
git commit -m "Update website"
git push origin main
```

---

## Code Style Guidelines

### General Principles

1. **Single file structure**: All code in `index.html` - CSS in `<style>`, JS in `<script>`
2. **No external dependencies**: Vanilla HTML, CSS, JavaScript only
3. **Language**: Spanish (`lang="es"`) for all content

---

### HTML Conventions

```html
<!-- Use semantic elements -->
<header>, <nav>, <main>, <section>, <footer>

<!-- Required attributes -->
lang="es"
alt for all <img>
required for mandatory form inputs

<!-- External links -->
target="_blank" rel="noopener"

<!-- Classes: BEM-lite -->
.service-card
.service-card__title
.service-card__description
```

**Section IDs**: Use descriptive lowercase IDs for navigation
- `#hero`, `#about`, `#services`, `#portfolio`, `#process`, `#contact`

---

### CSS Guidelines

**Organization**:
- All CSS in `<style>` tag in `<head>`
- Define variables in `:root` first
- Mobile-first: base styles, then `@media (min-width: 768px)`

**Variables** (defined in `:root`):
```css
--bg: #0b0b0b;         /* Page background */
--bg-light: #141414;   /* Cards/sections */
--text: #f0f0f0;       /* Primary text */
--text-muted: #888;    /* Secondary text */
--accent: #d4a012;     /* Gold accent */
--accent-dim: #a67c00;/* Hover state */
--border:        /* Borders #222; */

--space-xs: 12px;
--space-sm: 24px;
--space-md: 48px;
--space-lg: 80px;
```

**Typography**:
- Display/Titles: `Syne` (Google Fonts)
- Body: `Inter` (Google Fonts)
- Use `clamp()` for responsive font sizes

**Reset** (include at top of CSS):
```css
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
```

**Animations**:
- Transitions: `0.3s ease` for hover states
- Scroll animations: `.fade-in` class with `@keyframes`

---

### JavaScript Guidelines

**Placement**: `<script>` at end of `<body>`

**Patterns**:
```javascript
// Selection
document.getElementById('element-id');
document.querySelector('.class-name');

// Events
element.addEventListener('click', handler);

// Animations
IntersectionObserver for scroll-triggered effects

// State
.classList.add('scrolled');
.classList.toggle('visible');
```

**Avoid**:
- External libraries/frameworks
- Complex build tools
- Async/await unless necessary

---

### Naming Conventions

| Element | Convention | Example |
|---------|------------|---------|
| Classes | lowercase, hyphenated | `.hero-content` |
| IDs | lowercase, hyphenated | `#nav` |
| CSS Variables | lowercase, hyphenated | `--accent` |
| Section IDs | lowercase, descriptive | `#portfolio` |

---

### Error Handling

- **HTML**: Validate all tags properly closed
- **Forms**: Include `required` on mandatory inputs, `type="email"` for email fields
- **Links**: `target="_blank" rel="noopener"` for external links
- **Images**: Always include `alt` attribute
- **JavaScript**: Wrap in try/catch for potentially failing code

---

### Accessibility Checklist

- [ ] All images have descriptive `alt` text
- [ ] Form inputs have associated `<label>` elements
- [ ] Semantic heading hierarchy (h1 → h2 → h3)
- [ ] Color contrast meets WCAG AA standards
- [ ] Focus states visible for keyboard navigation
- [ ] `lang="es"` on `<html>` element

---

## Common Tasks

### Updating Portfolio Images
```html
<div class="portfolio-item">
  <img src="path/to/image.jpg" alt="Project description">
  <div class="portfolio-item__info">...</div>
</div>
```

### Modifying Services
Edit `.service-card` elements in `#services` section.

### Adding New Sections
1. Add `<section id="new-section">`
2. Add link in `.nav-links`
3. Add CSS if needed

### Changing Colors
```css
:root {
  --accent: #newcolor;
  --accent-dim: #newcolordark;
}
```

---

## Brand Guidelines

- **Positioning**: "Narrativa primero. Técnica al servicio del relato."
- **Market**: Animation teams with public funding, independent narrative cinema
- **Services**: Sound design, music, Foley, editing, mixing, technical deliverables
- **Visual**: Dark theme (#0b0b0b), white text (#f0f0f0), gold accent (#d4a012)
- **Isotype**: Half 8-pointed star (white), geometric and minimal

---

## Deployment Notes

- GitHub Pages serves from `main` branch root
- Custom domain: `soniketesur.com` (configured in CNAME)
- Auto-deploy: ~1-2 minutes after push to main

---

## What NOT To Do

- Do not add external CSS/JS files
- Do not add build tools (webpack, vite, etc.)
- Do not add JavaScript frameworks
- Do not change the language from Spanish
- Do not remove accessibility attributes
- Do not add analytics/tracking without approval
