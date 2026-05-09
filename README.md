# 🔗 Personal Linktree — boyvalentyas-stack.github.io

A personal link-in-bio page serving as a centralized professional hub. Displays work experience, tech stack, skills, and all external profile links in a single URL. Designed with a dark terminal aesthetic and an animated matrix background.

🌐 **Live site:** [boyvalentyas-stack.github.io](https://boyvalentyas-stack.github.io)

---

## Table of Contents

- [Project Overview](#project-overview)
- [Project Structure](#project-structure)
- [Technology Stack](#technology-stack)
- [Design System](#design-system)
- [UI Components](#ui-components)
- [JavaScript Modules](#javascript-modules)
- [Data Reference](#data-reference)
- [SEO & Metadata](#seo--metadata)
- [Deployment Guide](#deployment-guide)
- [Maintenance Guide](#maintenance-guide)
- [Known Limitations](#known-limitations)
- [Changelog](#changelog)

---

## Project Overview

This project is a personal **link-in-bio page** — commonly referred to as a "Linktree" — designed to serve as the single URL shared across all professional profiles. Built entirely with plain HTML, CSS, and Vanilla JavaScript. No framework, no build tool, no backend, no database.

Beyond aggregating links, the page functions as a lightweight professional profile displaying:

- Current professional identity and open-to-work status
- Chronological work experience (5 entries)
- Technology stack (12 tools)
- Professional skills (10 competencies)
- 8 external links (GitHub, LinkedIn, 3 portfolios, Instagram, WhatsApp, Email)

---

## Project Structure

```
boyvalentyas-stack.github.io/
│
├── index.html          ← Single application file (HTML + CSS + JS)
├── main-favicon.ico    ← Browser tab icon
└── README.md           ← This file
```

All styles and scripts are embedded directly inside `index.html`. There are no external CSS files, no JavaScript modules, and no dependency manifests beyond Google Fonts.

---

## Technology Stack

| Layer | Technology | Notes |
|---|---|---|
| Markup | HTML5 | Single file, semantic elements (`<main>`, `<header>`, `<nav>`, `<footer>`) |
| Styling | CSS3 | Embedded `<style>` block; CSS custom properties for design tokens |
| Scripting | Vanilla JavaScript | Embedded `<script>` block; Canvas API + IntersectionObserver |
| Rendering | HTML Canvas API | Matrix rain background animation |
| Fonts | Google Fonts | JetBrains Mono + Space Grotesk; loaded with `preconnect` |
| Favicon | `.ico` | `main-favicon.ico` |
| Hosting | GitHub Pages | Free static hosting; auto-deploys on push to `main` |
| Version Control | Git / GitHub | Managed via GitHub web interface |

---

## Design System

All design tokens are defined in `:root` CSS custom properties.

### Color Palette

| Variable | Value | Usage |
|---|---|---|
| `--bg` | `#080C0A` | Page background |
| `--bg2` | `#0D1210` | Secondary background |
| `--bg3` | `#111A16` | Tertiary background |
| `--surface` | `rgba(255,255,255,0.03)` | Card and link button backgrounds |
| `--border` | `rgba(255,255,255,0.07)` | Default borders |
| `--border-hi` | `rgba(29,200,130,0.35)` | Highlighted borders (hover, active) |
| `--green` | `#1DC882` | Primary accent — avatar border, status dot, badges, arrows |
| `--green-dim` | `#0F6E48` | Secondary accent — link numbers, section labels |
| `--green-glow` | `rgba(29,200,130,0.12)` | Hover background glow on links |
| `--text` | `#E8F0EC` | Primary text |
| `--text-mid` | `#8AA898` | Secondary text — bio, subtitles |
| `--text-dim` | `#4A6458` | Tertiary text — periods, dimmed labels |

### Typography

| Variable | Font | Usage |
|---|---|---|
| `--mono` | JetBrains Mono | Name, section labels, link numbers, tags, open badge |
| `--sans` | Space Grotesk | Bio, link labels, subtitles, general body text |

### Border Radius

| Variable | Value |
|---|---|
| `--radius` | `6px` |

---

## UI Components

All components are contained within `<main class="page">`, a centered column with `max-width: 660px`.

### Header

Displays the owner's profile photo, name with blinking cursor, title badge, bio, and open-to-work status badge.

- **Avatar** — `88×88px` circular image sourced from `https://github.com/boyvalentyas-stack.png`. Updates automatically when the GitHub profile photo changes — no manual file change required.
- **Spinning border** — CSS `conic-gradient` animated with `@keyframes spinBorder` (6s loop) around the avatar.
- **Status dot** — `14×14px` green circle with a pulsing ring (`@keyframes pulse`) positioned at bottom-right of the avatar. Indicates open-to-work status.
- **Blinking cursor** — `_` character appended to the name, animated with `@keyframes blink` (1s step-end loop).
- **Title badge** — pill-shaped element with `▸` prefix displaying "QA & Solution Engineer".
- **Open badge** — inline element with a pulsing green dot, text "Open to work · Let's connect".

### Divider

Full-width `1px` horizontal line using `--border` color, with a `40px` accent segment in `--green-dim` centered via `::after`. Used between all major sections.

### Experience Section

Five `.exp-card` elements in a `.exp-list` flex column. Each card uses a two-column CSS grid:

| Element | Class | Grid position |
|---|---|---|
| Job title | `.exp-title` | Column 1, Row 1 |
| Company | `.exp-company` | Column 1, Row 2 |
| Date range | `.exp-period` | Column 2, Rows 1–2 (vertically centered, right-aligned) |

On mobile (`≤ 480px`), the grid collapses to single column with the period moving to Row 3, left-aligned.

Hover state: `--border-hi` border color + `--green-glow` background + `2px` left accent bar via `::before`.

### Tags (Tech Stacks & Skills)

`.tags` flex container with `flex-wrap: wrap` and `8px` gap. Each `.tag` is a `<span>` with monospace font, `--border` border, and `--surface` background. Hover state transitions color to `--green` and border to `--border-hi`.

### Link Buttons

Eight `.link-btn` anchor elements in a `.links` flex column. Each contains:

| Element | Class | Content |
|---|---|---|
| Number | `.link-num` | `01` through `08` in `--green-dim` |
| Icon | `.link-icon` | Unicode symbol |
| Label + subtitle | `.link-label` + `.link-sub` | Link name + descriptor |
| Arrow | `.link-arrow` | `→` in `--green-dim` |

Hover state: `translateX(3px)` slide + left gradient glow overlay via `::after` + arrow color shifts to `--green` and translates `3px` right.

One link (Portfolio #1 — Citra Art Frame) has the `.highlight` class applied, giving it a persistent highlighted border and green label.

### Footer

Single centered line in monospace: `// built with HTML & CSS · hosted on GitHub Pages · powered by Claude.AI`, with hyperlinks on "GitHub Pages" and "Claude.AI".

---

## JavaScript Modules

### Matrix Background Animation

Uses the HTML Canvas API and `requestAnimationFrame`.

**Character set:** `'01アイウエオカキクケコタチツテトナニヌネノ'` — binary digits and 19 Japanese katakana characters.

**Column width:** `18px`. Column count is `Math.floor(canvas.width / 18)`.

**Color logic:** Every 7th column renders at `rgba(29,200,130,0.55)` (brighter). All other columns render at `rgba(15,110,72,0.35)` (dimmer). This creates visual depth variation across the rain.

**Drop reset:** When a drop reaches the canvas bottom, it has a `2.2%` chance per frame (`Math.random() > 0.978`) of resetting to row 0. This staggers cascade timing naturally.

**Tab visibility:** The animation pauses automatically when the browser tab is hidden (`document.visibilitychange` → `document.hidden`). This prevents unnecessary CPU usage in background tabs.

**Canvas resize:** On `window.resize`, the canvas dimensions are updated and all drops reset to row 1.

### Stagger Reveal Animation

Uses `IntersectionObserver` with `threshold: 0.1`.

On each `.stagger` element observed:
1. An `animationDelay` is set programmatically: `0.05 + (index × 0.05)` seconds.
2. When the element enters the viewport, the `visible` class is added, triggering `@keyframes fadeUp`.
3. `observer.unobserve(e.target)` is called immediately — the observer stops watching once revealed, preventing memory leaks.

---

## Data Reference

### Work Experience

| # | Title | Company | Period |
|---|---|---|---|
| 1 | Solution Engineer | BFI Finance Indonesia | Dec 2024 – Feb 2026 |
| 2 | Associate Solution Engineer | BFI Finance Indonesia | Jan 2024 – Nov 2024 |
| 3 | Associate QA Engineer | BFI Finance Indonesia | Apr 2023 – Dec 2023 |
| 4 | Test Engineer | AbiShar Technologies · Placed at BFI Finance | Aug 2021 – Apr 2023 |
| 5 | IT QA Automation | FUSI Solusi Integrasi · Placed at KSEI | Feb 2020 – Jul 2021 |

### Tech Stacks (12 items)

`JIRA` · `Confluence` · `Google Workspace` · `Microsoft Office` · `Draw.io` · `Postman` · `Katalon` · `JavaScript` · `Python` · `PostgreSQL` · `Claude.AI` · `Zoom`

### Skills (10 items)

`Test Strategy` · `Manual Testing` · `Automation Testing` · `API Testing` · `Requirement Gathering` · `System Architecture Design` · `System Integration` · `Project Management` · `Vendor Management` · `Data Analysis`

### Link Directory

| # | Label | URL | Opens |
|---|---|---|---|
| 01 | GitHub | https://github.com/boyvalentyas-stack/ | New tab |
| 02 | LinkedIn | https://www.linkedin.com/in/boy-valentyas-indra-gunara-86a9ba181/ | New tab |
| 03 | Portfolio #1 — Citra Art Frame | https://boyvalentyas-stack.github.io/citra-art-frame/ | New tab |
| 04 | Portfolio #2 — Free CV Maker | https://boyvalentyas-stack.github.io/cv-generator/ | New tab |
| 05 | Portfolio #3 — Snack Shop [DEMO] | https://boyvalentyas-stack.github.io/snack-shop/ | New tab |
| 06 | Instagram | https://www.instagram.com/aceblanc.toujo/ | New tab |
| 07 | WhatsApp | https://wa.me/6289636306541 | New tab |
| 08 | Email | mailto:dev.boyvalentyas@email.com | New tab |

---

## SEO & Metadata

| Tag | Value |
|---|---|
| `<title>` | Boy Valentyas Indra G. — QA & Solution Engineer |
| `<meta name="description">` | Boy Valentyas Indra G. — Quality Assurance & Solution Engineer based in Jakarta, Indonesia. 5+ years experience in QA, BA, PM, and System Integration. |
| `<meta name="author">` | Boy Valentyas Indra G. |
| `<html lang>` | `en` (static; dynamically updated by `setLang()` if i18n is added) |
| `og:title` | Boy Valentyas Indra G. — QA & Solution Engineer |
| `og:description` | Quality Assurance & Solution Engineer based in Jakarta. Open to work. Let's connect. |
| `og:url` | https://boyvalentyas-stack.github.io |
| `og:type` | website |
| Favicon | `main-favicon.ico` |

---

## Deployment Guide

Hosted on **GitHub Pages** from the `main` branch root. No build step required.

### Prerequisites
- GitHub account
- Repository named exactly `boyvalentyas-stack.github.io`
- GitHub Pages enabled: **Settings → Pages → Source: Deploy from branch → main → / (root)**

### Deploying a Change (via GitHub web interface)
1. Navigate to the repository on GitHub.
2. Click `index.html` → click the pencil icon (Edit).
3. Make changes.
4. Click **Commit changes**.
5. Wait 1–3 minutes. Monitor status under the **Actions** tab — green ✅ means live.
6. Verify at `https://boyvalentyas-stack.github.io`.

---

## Maintenance Guide

### Update Profile Photo
Change the GitHub profile photo under **github.com → Settings → Edit profile photo**. The avatar on the page updates automatically — no file changes needed.

### Add a New Link

In the `<!-- LINKS -->` section, add a new `<a>` element following the existing pattern:

```html
<a class="link-btn stagger" href="https://your-url.com" target="_blank" rel="noopener noreferrer" title="Describe the link">
  <span class="link-num">09</span>
  <span class="link-icon">◆</span>
  <span class="link-label">Label Text<span class="link-sub">subtitle here</span></span>
  <span class="link-arrow">→</span>
</a>
```

Increment the `.link-num` value to the next sequential number.

### Add a New Experience Entry

In the `<!-- EXPERIENCE -->` section, insert a new `.exp-card` at the **top** of `.exp-list` (most recent first):

```html
<div class="exp-card stagger">
  <span class="exp-title">Your Job Title</span>
  <span class="exp-company">Company Name</span>
  <span class="exp-period">Mon YYYY – Mon YYYY</span>
</div>
```

### Add or Remove a Tag

In either the Tech Stacks or Skills section, add or remove a `<span class="tag">` element:

```html
<span class="tag">New Skill Name</span>
```

### Update Open-to-Work Status

To remove the open-to-work indicator, delete or hide the `.status-dot` div and the `.open-badge` span in the header.

---

## Known Limitations

| Limitation | Detail |
|---|---|
| Portfolio links #4 and #5 | `cv-generator` and `snack-shop` link to subpath URLs that return 404 until those repositories are created and GitHub Pages is enabled on each. |
| No `<meta name="robots">` | The page has no explicit robots directive. Defaults to `index, follow` in most crawlers, but not explicitly declared. |
| No `<link rel="canonical">` | Canonical URL not declared. Low risk for a single-page site, but recommended for completeness. |
| Profile photo depends on GitHub CDN | The avatar is loaded from `github.com`. If GitHub's CDN is unavailable, the avatar will not render. |
| Animation runs despite `paused` flag | When `paused = true`, `requestAnimationFrame(draw)` is still called each frame (it returns early). A more efficient approach would call `cancelAnimationFrame(animId)` when pausing and restart on visibility restore. |
| No `<link rel="preconnect">` for Google Fonts | Font loading does not use `preconnect`, which delays first render slightly on cold loads. |

---

## Changelog

| Version | Date | Changes |
|---|---|---|
| 2.0 | May 2026 | Full redesign: dark terminal aesthetic, JetBrains Mono + Space Grotesk fonts, spinning avatar border, pulsing status dot, stagger reveal animation, `requestAnimationFrame` matrix with tab-visibility pause, `IntersectionObserver` with `unobserve`, Open Graph tags, meta description, corrected all typos (Python, PostgreSQL, System Architecture Design), `title` attributes on all links, proper `alt` text on avatar. |
| 1.0 | Apr 2026 | Initial release: matrix animation, experience/skills/links layout, profile photo from GitHub. |
