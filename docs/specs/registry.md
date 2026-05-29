# Feature Registry — alexandra-energy

Source of truth for what this site currently ships. Mutable — describes current state, not history.

### landing-page (`/`)

- **Route:** `/` → `src/pages/index.astro` (wraps `src/layouts/Layout.astro`)
- **Purpose:** Single-page Hebrew RTL marketing site for Alexandra's energetic-wash / energy-healing practice.
- **Triggers / activation:** Served as the site index; static build.
- **Surface:** Sections — nav, hero, philosophy quote, "what is energetic wash" (3 cards), about (real photo + bio + badges), services (3 cards, middle featured, with prices), how-it-works (3 steps), testimonials (3), trust stats (4), FAQ accordion (5), contact form, footer. Client JS: nav scroll state, mobile hamburger menu, FAQ accordion.
- **Dependencies:** Astro, Tailwind (Vite plugin), `@astrojs/sitemap`. Heebo font via Google Fonts. Alexandra's photo at `public/alexandra.jpg`. No backend — contact form posts to `#` (placeholder).
- **RTL/SEO:** `<html lang="he" dir="rtl">`, logical CSS properties throughout, full OG/Twitter meta + `he_IL` locale, canonical link, `robots: index, follow`, sitemap at `/sitemap-index.xml`, `site: https://alexandra-energy.pages.dev`.
- **Key scenarios:** Build passes 0 errors; `dist/index.html` contains `lang="he"`, `dir="rtl"`, Heebo, the photo; sitemap generated.
- **Status:** `active`
- **Last updated:** `2026-05-29`
