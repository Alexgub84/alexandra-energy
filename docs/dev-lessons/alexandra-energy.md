# Dev Lessons — alexandra-energy

Append-only. Newest entries at the bottom.

### [Decision] RTL via logical CSS properties, not physical

**Date:** 2026-05-29
**Context:** Rebuilt the landing page from English LTR to Hebrew RTL. Original CSS used physical directions (`left`, `right`, `padding-left`, `border-left`, `text-align: left`).
**Decision:** Converted every directional rule to logical properties — `inset-inline`, `inset-inline-start/end`, `border-inline-start`, `border-block-start/end`, `padding-inline`, `text-align: start`. Chose this over hardcoding RTL physical values (e.g. swapping every `left` to `right`) because logical properties stay correct if direction ever changes and read self-documenting.
**Reason:** With `dir="rtl"` on `<html>`, logical properties auto-mirror; physical ones would need manual flipping and silently break on any LTR fallback.
**Reuse tip:** For any RTL site, set `dir="rtl"` once and use logical CSS everywhere. Grep the built HTML for `left`/`right`/`text-align: left` to catch leftovers.

### [Bug] Scoped `<style>` cannot style `<body>`/`<html>` after extracting Layout

**Date:** 2026-05-29
**Problem:** Moving `<html>`/`<body>` into `Layout.astro` means a page-level Astro `<style>` block (scoped by default) no longer matches `body`/`html` — those elements live in the layout component, so base rules like `direction`, `font-family`, background silently don't apply.
**Solution:** Used `<style is:global>` in `index.astro` for the page's full stylesheet so `html`/`body`/`*` selectors apply across the layout boundary.
**Prevention:** When base/reset rules target `html`/`body`/`*` but those tags live in a layout, mark the style block `is:global` (or move base rules into `global.css`).

### [Decision] Heebo replaces serif/italic English fonts

**Date:** 2026-05-29
**Context:** Original design leaned on Cormorant Garamond italics and Raleway — none have proper Hebrew glyphs, and browser-synthesized italics on Hebrew look broken.
**Decision:** Dropped all `@fontsource` English fonts, loaded Heebo (300–800) from Google Fonts in `Layout.astro`, and removed every `font-style: italic`.
**Reason:** Heebo is a clean Hebrew sans with full weight range; synthetic italics on Hebrew are a known eyesore.
**Reuse tip:** For Hebrew sites pick a native Hebrew family and avoid italics entirely — use weight, not slant, for emphasis.
