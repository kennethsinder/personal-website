# CLAUDE.md

## Project Overview

Static HTML personal portfolio website for Kenneth Sinder, deployed at [ksinder.com](https://ksinder.com) via GitHub Pages.

## Tech Stack

- **HTML5** — single-page site in `index.html` (~30KB)
- **Tailwind CSS** — via CDN (`cdn.tailwindcss.com`), utility-first styling
- **Alpine.js** — lightweight reactivity for tabs, accordions, dark mode
- **Lucide Icons** — SVG icon library via CDN
- **Google Fonts** — Inter (body) and JetBrains Mono (code)

No build system, no package manager, no bundler. Everything is served as static files.

## File Structure

```
├── index.html      # Entire website (single file)
├── styles.css      # Legacy CSS (mostly unused, Open Sans)
├── favicon.png     # Site favicon
├── me.png          # Profile photo
├── resume.pdf      # Downloadable resume
├── CNAME           # Custom domain config (ksinder.com)
├── logos/          # Company logos for experience section
│   ├── canarie.png
│   ├── hootsuite.png
│   ├── linkedin.png
│   ├── notion.png
│   ├── stripe.png
│   ├── tangam.png
│   ├── waterloo.png
│   └── wish.png
└── README.md
```

## Development

### Local preview

Open `index.html` directly in a browser. No dev server required.

Alternatively, use any static file server:
```bash
python3 -m http.server 8000
# or
npx serve .
```

### Key conventions

- **All site content lives in `index.html`** — HTML structure, Tailwind config, inline `<style>`, and Alpine.js logic are all in this single file.
- **Tailwind config** is defined inline in a `<script>` tag: dark mode uses class strategy, custom fonts are extended.
- **Dark mode** uses Tailwind's `dark:` prefix with `class` strategy. Toggle state persists via `localStorage`.
- **Tabs** (About, Resume, Links) are controlled by Alpine.js `x-data` on the parent container.
- **Experience sections** use expandable accordions with Alpine.js `x-show` and CSS transitions.
- **No JavaScript build step** — all JS is inline or loaded via CDN `<script>` tags.

### Styling

- Primary approach: Tailwind utility classes directly on HTML elements
- Color scheme: indigo/purple accents on neutral gray backgrounds
- Dark mode: `gray-950` background, light text
- Custom CSS (in `<style>` tag): animations, transitions, gradient profile ring, hover effects, print styles
- `styles.css` is a legacy file and largely unused

## Deployment

- **Hosting**: GitHub Pages (static, from default branch)
- **Custom domain**: `ksinder.com` (configured via `CNAME` file)
- **No CI/CD pipeline** — push to default branch triggers automatic GitHub Pages deployment
- **No build step** — files are served as-is

## Testing

No automated tests. Verify changes by opening `index.html` in a browser and checking:
- Light and dark mode appearance
- Tab switching (About / Resume / Links)
- Accordion expand/collapse in Resume tab
- Responsive layout on mobile viewports
- Social/external links work correctly

## Common Tasks

### Update work experience
Edit the Resume tab section in `index.html`. Each job is an accordion item with Alpine.js `x-show` toggle. Follow the existing pattern for consistency.

### Add a new social link
Add to both the hero section (icon links) and the Links tab.

### Change color theme
Modify Tailwind classes throughout `index.html`. Accent colors use `indigo-*` and `purple-*` utilities.

### Update profile info
Edit the hero section (name, title, photo) and About tab content in `index.html`.
