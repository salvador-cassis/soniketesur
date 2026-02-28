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
# No build required - open index.html directly in browser
# Or serve locally:
python3 -m http.server 8000
# Then open http://localhost:8000
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

### Design System

**Color Palette** (CSS custom properties in `:root`):
| Variable | Value | Usage |
|----------|-------|-------|
| `--bg` | `#0b0b0b` | Page background (dark) |
| `--bg-light` | `#141414` | Card/section backgrounds |
| `--text` | `#f0f0f0` | Primary text |
| `--text-muted` | `#888` | Secondary text |
| `--accent` | `#d4a012` | Gold accent (brand color) |
| `--accent-dim` | `#a67c00` | Hover state for accent |
| `--border` | `#222` | Subtle borders |

**Typography**:
- Display/Titles: `Syne` (Google Fonts) — bold, geometric
- Body: `Inter` (Google Fonts) — clean, readable
- Font sizes use `clamp()` for responsive scaling

**Spacing** (CSS custom properties):
- `--space-xs`: 12-20px
- `--space-sm`: 24-40px
- `--space-md`: 48-80px
- `--space-lg`: 80-140px

---

### HTML Conventions

1. **Language**: Always `lang="es"` for Spanish
2. **Semantic elements**: Use `<section>`, `<nav>`, `<header>`, `<footer>`, `<main>`
3. **Section IDs**: Use descriptive IDs for navigation anchors (`#about`, `#services`, `#portfolio`, etc.)
4. **Classes**: BEM-lite naming (e.g., `.service-card`, `.service-card__title`)
5. **Accessibility**:
   - All images require `alt` text
   - Form inputs require `<label>` elements
   - Use semantic heading hierarchy (h1 → h2 → h3)

---

### CSS Guidelines

1. **Organization**: All CSS in `<style>` tag in `<head>` (no external CSS file)
2. **Variables**: Define all colors, spacing, fonts in `:root`
3. **Mobile-first**: Write base styles, add `@media (min-width: 768px)` for desktop
4. **Animations**:
   - Use CSS transitions (0.3s ease) for hover states
   - Use `@keyframes` for scroll-triggered animations (`.fade-in` class)
5. **Reset**: Include basic reset:
   ```css
   *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
   ```

---

### JavaScript Guidelines

1. **Placement**: All JS in `<script>` at end of `<body>`
2. **No dependencies**: Vanilla JavaScript only
3. **Patterns used**:
   - `document.getElementById()` for element selection
   - `addEventListener()` for event handling
   - `IntersectionObserver` for scroll animations
4. **Features**:
   - Navigation scroll effect (add `.scrolled` class on scroll)
   - Fade-in animations on scroll (`.fade-in` → `.visible`)

---

### Naming Conventions

| Element | Convention | Example |
|---------|------------|---------|
| Classes | lowercase, hyphenated | `.hero-content`, `.service-card` |
| IDs | lowercase, hyphenated | `#nav`, `#contact` |
| CSS Variables | lowercase, hyphenated | `--accent`, `--bg-light` |
| Section IDs | lowercase, descriptive | `#portfolio`, `#process` |

---

### Error Handling

- **HTML**: Ensure all tags are properly closed
- **Forms**: Include `required` attribute on mandatory inputs
- **Links**: Use `target="_blank" rel="noopener"` for external links
- **Images**: Always include `alt` attribute for accessibility

---

## Brand Guidelines (Reference)

From the brand document:

- **Positioning**: "Narrativa primero. Técnica al servicio del relato."
- **Market**: Animation teams with public funding, independent narrative cinema
- **Value**: Sound design, music, Foley, editing, mixing, technical deliverables
- **Visual Identity**: Dark theme (black dominant), white secondary, gold accent (#d4a012)
- **Isotype**: Half 8-pointed star (white), geometric and minimal

---

## Common Tasks

### Updating Portfolio Images
Find `.portfolio-item` elements and replace `src` in `<img>` tags:
```html
<div class="portfolio-item">
  <img src="path/to/image.jpg" alt="Project description">
  ...
</div>
```

### Modifying Services
Edit content within `.service-card` elements in `#services` section.

### Adding New Sections
1. Add `<section id="new-section">` with appropriate content
2. Add link in `<nav>` → `.nav-links`
3. Add corresponding CSS if needed

### Changing Colors
Modify CSS custom properties in `:root` at top of `<style>`:
```css
:root {
  --accent: #newcolor;
  --accent-dim: #newcolordark;
}
```

---

## Deployment Notes

- GitHub Pages serves from `main` branch root
- Custom domain: `soniketesur.com` (configured in CNAME)
- Changes push to `main` auto-deploy within ~1-2 minutes
