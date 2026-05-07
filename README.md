# Project Documentation
## Personal Linktree — boyvalentyas-stack.github.io

**Author:** Boy Valentyas Indra G.  
**Document Version:** 1.0  
**Last Updated:** May 2026  
**Project Type:** Static Web Application  
**Hosting:** GitHub Pages  
**Live URL:** https://boyvalentyas-stack.github.io

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Project Structure](#2-project-structure)
3. [Technology Stack](#3-technology-stack)
4. [File Reference](#4-file-reference)
   - 4.1 [index.html](#41-indexhtml)
   - 4.2 [README.md](#42-readmemd)
5. [UI Components](#5-ui-components)
   - 5.1 [Avatar](#51-avatar)
   - 5.2 [Identity Block](#52-identity-block)
   - 5.3 [Status Badge](#53-status-badge)
   - 5.4 [Experience Section](#54-experience-section)
   - 5.5 [Tech Stacks Section](#55-tech-stacks-section)
   - 5.6 [Skills Section](#56-skills-section)
   - 5.7 [Links Section](#57-links-section)
   - 5.8 [Footer](#58-footer)
6. [Styling Reference](#6-styling-reference)
   - 6.1 [Color Palette](#61-color-palette)
   - 6.2 [Typography](#62-typography)
   - 6.3 [Layout](#63-layout)
   - 6.4 [Animations](#64-animations)
7. [JavaScript: Matrix Animation](#7-javascript-matrix-animation)
8. [Data Reference](#8-data-reference)
   - 8.1 [Work Experience Entries](#81-work-experience-entries)
   - 8.2 [Tech Stack Items](#82-tech-stack-items)
   - 8.3 [Skill Items](#83-skill-items)
   - 8.4 [Link Directory](#84-link-directory)
9. [Deployment Guide](#9-deployment-guide)
10. [Maintenance Guide](#10-maintenance-guide)
    - 10.1 [How to Add a New Link](#101-how-to-add-a-new-link)
    - 10.2 [How to Add a New Experience Entry](#102-how-to-add-a-new-experience-entry)
    - 10.3 [How to Add or Remove a Skill or Tech Stack Badge](#103-how-to-add-or-remove-a-skill-or-tech-stack-badge)
    - 10.4 [How to Update the Profile Photo](#104-how-to-update-the-profile-photo)
    - 10.5 [How to Update the Status Text](#105-how-to-update-the-status-text)
11. [Known Limitations](#11-known-limitations)
12. [Changelog](#12-changelog)

---

## 1. Project Overview

This project is a personal **link-in-bio page** — commonly referred to as a "Linktree" — designed to serve as a centralized hub for professional and social media presence. It is intended to be shared as a single URL, from which visitors can navigate to the owner's GitHub profile, LinkedIn, portfolio projects, Instagram, WhatsApp, and email contact.

Beyond its link-aggregation function, the page acts as a lightweight professional profile, displaying:

- Current professional title and bio
- Chronological work experience
- Technical tools and technology stack
- Professional skills and competencies
- Open-to-work status

The page is built entirely with plain HTML and CSS, with one JavaScript block responsible solely for the animated background. It requires no framework, no build tool, no backend, and no database. It is hosted for free on GitHub Pages.

---

## 2. Project Structure

```
boyvalentyas-stack.github.io/         ← Repository root
│
├── index.html                         ← Main and only page of the application
├── main-favicon.ico                   ← Browser tab icon
└── README.md                          ← Repository description for GitHub
```

There are no subdirectories, no external CSS files, no JavaScript modules, and no dependency manifests. All styles and scripts are embedded directly inside `index.html`.

---

## 3. Technology Stack

| Layer | Technology | Notes |
|---|---|---|
| Markup | HTML5 | Single file, no templating engine |
| Styling | CSS3 (inline `<style>`) | No framework, no preprocessor |
| Scripting | Vanilla JavaScript (inline `<script>`) | Used exclusively for the matrix animation |
| Rendering | HTML Canvas API | Powers the animated background |
| Font | `monospace` (system default) | No external font loaded |
| Favicon | `.ico` format | Referenced as `main-favicon.ico` |
| Hosting | GitHub Pages | Free static hosting via GitHub |
| Version Control | Git | Managed via GitHub web interface |

---

## 4. File Reference

### 4.1 index.html

This is the sole application file. It contains three logical sections:

**`<head>`** — Document metadata, viewport configuration, favicon reference, and all embedded CSS styles.

**`<body>`** — Two direct children:
  - `<canvas id="matrix">` — The full-viewport animated background layer.
  - `<div class="wrap">` — The main content container, rendered on top of the canvas.

**`<script>`** (at bottom of body) — JavaScript for the matrix rain animation, including canvas sizing, character rendering, and the animation loop.

**Encoding:** UTF-8  
**Viewport:** Responsive (`width=device-width, initial-scale=1.0`)  
**Language:** Not explicitly declared (no `lang` attribute on `<html>`)

---

### 4.2 README.md

The README is the public-facing description of the repository as it appears on GitHub. It documents:

- Project purpose (personal link-in-bio page)
- Live site URL
- A placeholder for a screenshot (currently commented out)
- Technologies used
- Key learning outcomes documented by the author

The README does not contain any configuration values or technical specifications beyond what is listed above.

---

## 5. UI Components

All components are contained within `<div class="wrap">`, which is a centered column with a maximum width of `420px`.

### 5.1 Avatar

```html
<div class="avatar">
  <img src="https://github.com/boyvalentyas-stack.png" alt="avatar" />
</div>
```

The avatar is a circular image container (`80×80px`, `border-radius: 50%`) with a `2px solid` border in the primary green color. The image source points to the owner's GitHub profile photo via the public GitHub avatar URL pattern (`github.com/{username}.png`). This means the profile photo updates automatically whenever the GitHub profile photo is changed — no manual update to `index.html` is needed.

---

### 5.2 Identity Block

```html
<h1>Boy Valentyas Indra G.<span class="cursor">_</span></h1>
<p class="bio">> Quality Assurance Engineer with Experience as BA PM SA when assigned as Solution Engineer</p>
```

The `<h1>` displays the owner's full name followed by a blinking underscore cursor (`_`) using a CSS keyframe animation. The `.bio` paragraph uses a terminal-style `>` prefix and displays the professional title and role summary in the primary green color.

---

### 5.3 Status Badge

```html
<p class="status open">Let's connect if you want to talk about technology, efficiency, or building scalable digital solutions.</p>
```

The `.status` element has two possible states, controlled by the presence of the `.open` class:

| Class | Behavior |
|---|---|
| `.status.open` | Displays text in green; prepends `[ ` and appends ` — open to work ]` via CSS `::before` and `::after` pseudo-elements |
| `.status` (without `.open`) | No pseudo-elements, default muted color |

Currently the `.open` class is applied, indicating the owner is open to work.

> **Note:** The `::before` and `::after` content is defined in CSS as `"[ "` and `" — open to work ]"` respectively. The paragraph's own text content is the body of the message displayed between those brackets.

---

### 5.4 Experience Section

Introduced by a section label comment `// experience`, this section renders a vertical stack of `.card` elements, each representing one role in reverse chronological order.

Each `.card` contains three elements:

| Element | Class | Purpose |
|---|---|---|
| `<p>` | `.exp-title` | Job title |
| `<p>` | `.exp-company` | Employer name |
| `<p>` | `.exp-period` | Employment date range |

There are currently **5 experience entries** in the page. See Section 8.1 for the full data.

---

### 5.5 Tech Stacks Section

Introduced by the section label `// tech stacks`, this section renders a flex-wrapped collection of `.skill` badge elements inside a `.skills` container.

Each badge is a `<span class="skill">` with the tool or technology name as its text content. Badges wrap automatically based on the container width. There are currently **12 tech stack items**. See Section 8.2 for the full list.

---

### 5.6 Skills Section

Introduced by the section label `// skills`, this section follows the same structure as the Tech Stacks section — a `.skills` flex container with `.skill` span badges. There are currently **10 skill items**. See Section 8.3 for the full list.

---

### 5.7 Links Section

Introduced by the section label `// find me on`, this section renders a vertical stack of `<a>` anchor elements, each representing one external destination.

Each link follows this internal structure:

```html
<a href="{URL}" target="_blank" rel="noopener noreferrer">
  <span class="prefix">{number}.</span> {Label} <span class="arrow">-></span>
</a>
```

All links open in a new browser tab (`target="_blank"`). The `rel="noopener noreferrer"` attribute is applied on all links as a security best practice. There are currently **8 links**. See Section 8.4 for the full directory.

---

### 5.8 Footer

```html
<p class="footer">// built with html & hosted on github pages powered by Claude.AI</p>
```

A single line of centered, low-contrast text at the bottom of the content column. Uses terminal-style `//` comment prefix. No interactive elements.

---

## 6. Styling Reference

All styles are defined in a single `<style>` block in the `<head>`. There are no external stylesheets, no CSS variables, and no media queries.

### 6.1 Color Palette

| Role | Value | Used On |
|---|---|---|
| Page background | `#0d0d0d` | `body` background |
| Content overlay background | `rgba(0,0,0,0.5)` | `.card`, `a` link background |
| Primary green | `#1D9E75` | Avatar border, `.bio`, `.exp-company`, link border |
| Secondary green | `#5DCAA5` | `.skill` text color, link text color |
| Dark green | `#0F6E56` | `.prefix`, `.arrow`, `.section-label`, `.skill` border |
| Dark green badge bg | `rgba(15,110,86,0.15)` | `.skill` background |
| Card border | `#1a1a1a` | `.card` border, `<hr>` border |
| Primary text | `#e0e0e0` | `h1`, `.exp-title` |
| Muted text | `#444` | `.exp-period` |
| Footer text | `#333` | `.footer` |

---

### 6.2 Typography

| Element | Font | Size | Weight | Color |
|---|---|---|---|---|
| All body text | `monospace` (system) | — | Normal | Varies |
| `h1` name | monospace | `18px` | Default | `#e0e0e0` |
| `.bio` | monospace | `13px` | Normal | `#1D9E75` |
| `.status` | monospace | `12px` | Normal | `#1D9E75` (when `.open`) |
| `.section-label` | monospace | `11px` | Normal | `#0F6E56` |
| `.exp-title` | monospace | `13px` | `500` | `#e0e0e0` |
| `.exp-company` | monospace | `12px` | Normal | `#1D9E75` |
| `.exp-period` | monospace | `11px` | Normal | `#444` |
| `.skill` | monospace | `11px` | Normal | `#5DCAA5` |
| `a` link | monospace | `14px` | Normal | `#5DCAA5` |
| `.footer` | monospace | `11px` | Normal | `#333` |

---

### 6.3 Layout

The page uses a simple vertical centering layout:

- `body`: `display: flex`, `justify-content: center`, `padding: 3rem 1rem`
- `.wrap`: `max-width: 420px`, `width: 100%`, `position: relative`, `z-index: 2`
- `canvas`: `position: fixed`, `z-index: 0` — stays behind all content
- `.skills`: `display: flex`, `flex-wrap: wrap`, `gap: 8px`

The `z-index` layering model:

| Layer | z-index | Element |
|---|---|---|
| Background animation | `0` | `canvas#matrix` |
| Content | `2` | `.wrap` |

---

### 6.4 Animations

**Blinking cursor** — defined via `@keyframes blink`:

```css
@keyframes blink {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0; }
}
```

Applied to `.cursor` with `animation: blink 1s infinite`. Creates a 1-second blinking cycle on the `_` character appended to the owner's name.

**Link hover state** — no animation, instant:
```css
a:hover { background: rgba(29,158,117,0.12); }
```

---

## 7. JavaScript: Matrix Animation

The matrix animation is the only JavaScript on the page. It runs as a continuous loop, rendering falling characters on the `<canvas>` element behind the content.

### How It Works

**1. Canvas sizing:**
```javascript
function resize() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
}
resize();
window.addEventListener('resize', resize);
```
The canvas is resized to match the full browser window on load and whenever the window is resized.

**2. Column calculation:**
```javascript
const cols = () => Math.floor(canvas.width / 16);
```
The canvas is divided into columns 16px wide. Each column has one falling character at a time.

**3. Drop tracking:**
```javascript
let drops = Array(cols()).fill(1);
window.addEventListener('resize', () => { drops = Array(cols()).fill(1); });
```
An array tracks the current vertical position (in row units) of the falling character in each column. On resize, all drops reset to the top.

**4. Character set:**
```javascript
const chars = '01アイウエオカキクケコサシスセソタチツテト';
```
The character pool consists of binary digits (`0`, `1`) and 19 Japanese katakana characters.

**5. Draw loop:**
```javascript
function draw() {
  ctx.fillStyle = 'rgba(13,13,13,0.05)';
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  ctx.font = '13px monospace';
  drops.forEach((y, i) => {
    const char = chars[Math.floor(Math.random() * chars.length)];
    ctx.fillStyle = i % 5 === 0 ? '#5DCAA5' : '#0F6E56';
    ctx.fillText(char, i * 16, y * 16);
    if (y * 16 > canvas.height && Math.random() > 0.975) drops[i] = 0;
    drops[i]++;
  });
}
setInterval(draw, 50);
```

Each frame (every 50ms = 20fps):
- A semi-transparent dark rectangle is drawn over the entire canvas. This creates the fade trail effect — older characters gradually disappear rather than vanishing instantly.
- Each column renders one random character at its current drop position.
- Every 5th column (`i % 5 === 0`) renders in the lighter green (`#5DCAA5`). All other columns use the darker green (`#0F6E56`). This creates a subtle highlight variation.
- When a drop reaches the bottom of the canvas, it has a 2.5% chance per frame of resetting to the top, creating varied cascade timing across columns.

**Performance note:** The animation runs at a fixed 50ms interval (`setInterval`). It does not use `requestAnimationFrame` and therefore runs regardless of tab visibility.

---

## 8. Data Reference

### 8.1 Work Experience Entries

Listed in the order they appear in the page (reverse chronological):

| # | Title | Company | Period |
|---|---|---|---|
| 1 | Solution Engineer | BFI Finance Indonesia | Dec 2024 — Feb 2026 |
| 2 | Associate Solution Engineer | BFI Finance Indonesia | Jan 2024 — Nov 2024 |
| 3 | Associate QA Engineer | BFI Finance Indonesia | Apr 2023 — Dec 2023 |
| 4 | Test Engineer | AbiShar Technologies Indonesia - Placed on BFI Finance | Aug 2021 — Apr 2023 |
| 5 | IT QA Automation | FUSI Solusi Integrasi - Placed on KSEI | Feb 2020 — Jul 2021 |

---

### 8.2 Tech Stack Items

12 items, in order of appearance:

`JIRA` · `Confluence` · `Google Workspace` · `Microsoft Office` · `Zoom` · `Draw.io` · `Postman` · `Katalon` · `Claude.AI` · `Javascript` · `Phyton` · `PostgreSQL`

---

### 8.3 Skill Items

10 items, in order of appearance:

`Test Strategy` · `Manual Testing` · `Automation Testing` · `API Testing` · `Requirement Gathering` · `System Architecture Design` · `System Integration` · `Project Management` · `Vendor Management` · `Data Analysis`

---

### 8.4 Link Directory

8 links, in order of appearance:

| # | Label | Destination URL | Opens |
|---|---|---|---|
| 01 | GitHub | https://github.com/boyvalentyas-stack/ | New tab |
| 02 | LinkedIn | https://www.linkedin.com/in/boy-valentyas-indra-gunara-86a9ba181/ | New tab |
| 03 | Portfolio #1 - Family Business | https://boyvalentyas-stack.github.io/citra-art-frame/ | New tab |
| 04 | Portfolio #2 - Free CV Maker | https://boyvalentyas-stack.github.io/cv-generator/ | New tab |
| 05 | Portfolio #3 - [DEMO] Snack Shop | https://boyvalentyas-stack.github.io/snack-shop/ | New tab |
| 06 | Instagram | https://www.instagram.com/aceblanc.toujo/ | New tab |
| 07 | WhatsApp | https://wa.me/6289636306541 | New tab |
| 08 | Email me | mailto:dev.boyvalentyas@email.com | New tab |

---

## 9. Deployment Guide

This project is hosted on **GitHub Pages** using the default branch deployment method. No CI/CD pipeline, no build step, and no server configuration is required.

### Prerequisites
- A GitHub account
- A repository named exactly `{username}.github.io` (in this case, `boyvalentyas-stack.github.io`)
- GitHub Pages enabled on the repository

### Enabling GitHub Pages
1. Navigate to the repository on GitHub.
2. Click **Settings**.
3. In the left sidebar, click **Pages**.
4. Under **Source**, select **Deploy from a branch**.
5. Set the branch to `main` and the folder to `/ (root)`.
6. Click **Save**.

### Deploying a Change
Since this project uses the GitHub web interface (no local Git installation required):

1. Navigate to the repository on GitHub.
2. Click on the file to edit (e.g., `index.html`).
3. Click the **pencil icon** (Edit this file).
4. Make the desired changes.
5. Scroll down and click **Commit changes**.
6. Wait approximately 1–3 minutes for GitHub Pages to rebuild.
7. Verify the change at `https://boyvalentyas-stack.github.io`.

**Deployment status** can be checked under the **Actions** tab of the repository. A green checkmark indicates the deployment completed successfully. An orange circle indicates it is still building.

---

## 10. Maintenance Guide

### 10.1 How to Add a New Link

Locate the `<!-- Links -->` section in `index.html`. Add a new `<a>` element following the existing pattern, incrementing the prefix number:

```html
<a href="https://your-new-url.com" target="_blank" rel="noopener noreferrer">
  <span class="prefix">09.</span> Label Text <span class="arrow">-></span>
</a>
```

Replace `09.` with the next sequential number, `https://your-new-url.com` with the destination URL, and `Label Text` with the display name.

---

### 10.2 How to Add a New Experience Entry

Locate the `<!-- Experience -->` section in `index.html`. Add a new `.card` block. For the most recent role, insert it at the **top** of the list (immediately after the section label):

```html
<div class="card">
  <p class="exp-title">Your Job Title</p>
  <p class="exp-company">Your Company Name</p>
  <p class="exp-period">Month YYYY — Month YYYY</p>
</div>
```

Use `present` instead of an end month/year if the role is current.

---

### 10.3 How to Add or Remove a Skill or Tech Stack Badge

Locate either the `<!-- Tech Stacks -->` or `<!-- Skills -->` section. To **add** a badge, insert a new `<span>`:

```html
<span class="skill">New Tool Name</span>
```

To **remove** a badge, delete the corresponding `<span class="skill">...</span>` line.

---

### 10.4 How to Update the Profile Photo

The profile photo is sourced automatically from the GitHub profile:

```html
<img src="https://github.com/boyvalentyas-stack.png" alt="avatar" />
```

To update the photo, simply update the **GitHub profile picture** on GitHub (`Settings → Edit profile photo`). The change will reflect on the Linktree page automatically within a few minutes — no changes to `index.html` are required.

---

### 10.5 How to Update the Status Text

Locate the `.status` paragraph in `index.html`:

```html
<p class="status open">Your status message here.</p>
```

Replace the text content with the new message. The `[ ... — open to work ]` wrapper is added automatically by CSS and does not need to be typed manually.

To **remove** the open-to-work indicator, remove the `open` class:

```html
<p class="status">Your status message here.</p>
```

---

## 11. Known Limitations

| Limitation | Detail |
|---|---|
| No responsive breakpoints | The page has no CSS media queries. On very small screens (below ~360px wide), some elements may appear cramped. The `.wrap` container does use `width: 100%` with `padding: 3rem 1rem` which provides basic adaptability, but no explicit mobile layout adjustments are defined. |
| No `lang` attribute | The `<html>` element does not declare a `lang` attribute. This may affect screen readers and SEO. |
| Animation runs on hidden tabs | The matrix animation uses `setInterval` rather than `requestAnimationFrame`. It continues consuming CPU when the browser tab is not in focus. |
| No offline support | There is no service worker or caching strategy. The page is not available offline. |
| Profile photo depends on GitHub | The avatar image is loaded from `github.com`. If GitHub's CDN is unavailable, the avatar will not display. |
| Two potential typos in content | "Phyton" (Python) and "Architechture" (Architecture) in the skill badges — see Sections 8.2 and 8.3. |
| Portfolio links #4 and #5 | `cv-generator` and `snack-shop` portfolio links point to subpath URLs (`boyvalentyas-stack.github.io/cv-generator/` and `boyvalentyas-stack.github.io/snack-shop/`). These will return 404 until the corresponding repositories are created and GitHub Pages is enabled on each. |

---

## 12. Changelog

| Version | Date | Changes |
|---|---|---|
| 1.0 | May 2026 | Initial documentation created. Covers all components, styles, JavaScript, data, deployment, and maintenance procedures as sourced from the current `index.html` and `README.md`. |

---

*This document was produced by reviewing the source files `index.html` and `README.md` of the `boyvalentyas-stack.github.io` repository. All data points, URLs, color values, and code references are derived directly from those files.*
