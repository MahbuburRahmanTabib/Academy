# StoryFrame Academy — Website Design Documentation

> A complete breakdown of every design and technical decision made in building the StoryFrame Academy landing page. Written for developers, designers, or anyone who wants to understand, modify, or rebuild this site.

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Design Philosophy](#2-design-philosophy)
3. [File Structure](#3-file-structure)
4. [Color System](#4-color-system)
5. [Typography](#5-typography)
6. [Layout Architecture](#6-layout-architecture)
7. [Components — Section by Section](#7-components--section-by-section)
8. [Animations & Motion](#8-animations--motion)
9. [Interactive Elements](#9-interactive-elements)
10. [CSS Architecture](#10-css-architecture)
11. [JavaScript Logic](#11-javascript-logic)
12. [Responsive Design](#12-responsive-design)
13. [Brand Integration](#13-brand-integration)
14. [How to Customize](#14-how-to-customize)
15. [Going Live — Checklist](#15-going-live--checklist)

---

## 1. Project Overview

**What it is:** A single-page marketing website (landing page) for StoryFrame Academy — a video editing course teaching DaVinci Resolve from scratch.

**Goal of the page:** Convert visitors into enrolled students. Every section, every design decision, every line of copy is built to move someone from "curious" to "enrolled."

**Technology stack:**
- Pure HTML5 — no frameworks, no build tools
- Pure CSS3 — no preprocessors, no libraries
- Vanilla JavaScript — no dependencies
- Google Fonts — loaded via CDN for typography
- Single `.html` file — everything lives in one place

**Why a single file?**
For a landing page at this stage, a single file is the fastest to deploy, easiest to hand off, and requires zero server configuration. Paste it into any hosting service and it works instantly.

---

## 2. Design Philosophy

Before writing a single line of code, a clear aesthetic direction was committed to. The wrong approach is to start building and figure out the look later. The right approach is to decide the soul of the design first.

### The Direction: Dark Cinematic Editorial

The reference points were **A24 Films** (the production company behind Midsommar, Hereditary, Everything Everywhere All At Once) and **MasterClass** (the premium online education platform). Both share a quality: they feel like art, not products.

The goal was a website that feels like a **film studio that happens to teach** — not a course platform that happens to look nice.

### The One Unforgettable Thing

Every great design has one thing people remember. For this site it is: **the constellation mark that animates to life on page load.** Nodes appear one by one, lines draw themselves, and it feels like the brand is being born in front of you. That moment sets the entire tone.

### Principles Applied

| Principle | How it shows up |
|---|---|
| Dark = premium | Deep void black backgrounds, never pure #000000 |
| Jade = life | The one color accent that signals creativity and energy |
| Asymmetry = editorial | Headlines break the grid, sections breathe unevenly |
| Restraint = luxury | Not everything has an animation. Silence is design. |
| Typography does the heavy lifting | The fonts carry personality so layout can stay clean |

---

## 3. File Structure

The entire website is one file: `storyframe-academy-website.html`

Inside that file, the structure is:

```
<head>
  ├── Meta tags
  ├── Google Fonts import
  └── <style> — all CSS (organized by section)

<body>
  ├── Custom cursor elements
  ├── <nav> — fixed navigation bar
  ├── <section class="hero"> — full-screen hero
  ├── <div class="stats-bar"> — four key stats
  ├── <section class="learn"> — 6 skill cards
  ├── <section class="curriculum"> — module list
  ├── <section class="who"> — audience cards
  ├── <section class="get-section"> — inclusions
  ├── <section class="instructor"> — bio section
  ├── <section class="pricing"> — price card + CTA
  ├── <footer> — logo + links + copyright
  └── <script> — all JavaScript
```

---

## 4. Color System

All colors are stored as CSS custom properties (variables) on the `:root` selector. This means changing a color anywhere on the site requires changing it in exactly one place.

```css
:root {
  --void:   #050D0B;   /* Primary background — deepest dark */
  --abyss:  #091814;   /* Card backgrounds, alternate sections */
  --sea:    #0F2E27;   /* Hover states, secondary surfaces */
  --jade:   #3ECFB2;   /* THE accent — icon, highlights, CTA */
  --jade-dk:#0E9E86;   /* Darker jade for light backgrounds */
  --frost:  #E8F8F5;   /* Primary text color */
  --mist:   rgba(232,248,245,0.5);   /* Secondary text */
  --dim:    rgba(232,248,245,0.25);  /* Tertiary text, descriptions */
  --line:   rgba(62,207,178,0.12);   /* Borders, dividers */
}
```

### Why these colors work together

**Void (#050D0B)** is not pure black. It has a green undertone — `R:5, G:13, B:11`. The green tint makes it feel warmer and connects it to the jade accent. Pure black (`#000000`) would feel cold and disconnected from the brand.

**Jade (#3ECFB2)** is used sparingly and intentionally. It appears on: the constellation mark, "Frame" in the wordmark, CTA buttons, hover states, accent lines, and module tags. It never appears on large background areas. This scarcity makes it feel valuable.

**Frost (#E8F8F5)** is not pure white. It has a slight blue-green tint — matching the overall cool palette. Pure white against the dark background would create harsh contrast that feels cold rather than cinematic.

**The opacity system** (`--mist` at 50%, `--dim` at 25%) creates a clear information hierarchy without introducing new colors. The eye naturally reads full-opacity text first, then mist, then dim — matching headline → subheadline → body copy.

---

## 5. Typography

Three typefaces are used. Each has a specific role and never crosses into another's territory.

### Font 1 — Cormorant (Display / Headline)

```
font-family: 'Cormorant', serif
```

**Loaded from:** Google Fonts
`https://fonts.googleapis.com/css2?family=Cormorant:ital,wght@0,300;0,400;0,700;1,300;1,700`

**Used for:** All headlines, the wordmark, price numbers, section titles, module titles, card titles

**Why Cormorant:** It is a high-contrast serif based on the Garamond tradition. The difference between its thin and thick strokes is dramatic — which creates natural elegance at large sizes. It has an italic variant that feels genuinely expressive rather than just slanted. At 148px it feels cinematic. At 28px it still feels refined.

**Weight usage:**
- `font-weight: 700` (Bold) — "Story" in wordmark, main headlines
- `font-weight: 300` (Light) — "Frame" in wordmark, subheadlines
- `font-style: italic` — used on accent words within headlines to create rhythm and emphasis

**The contrast trick in the wordmark:**
```
Story   → Bold + Italic  (active, alive, moving)
Frame   → Light + Upright (structured, controlled, stable)
```
This contrast is intentional. Story is dynamic. Frame is the container. Together they are the brand.

---

### Font 2 — Space Mono (Labels / UI / Technical)

```
font-family: 'Space Mono', monospace
```

**Loaded from:** Google Fonts
`https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700`

**Used for:** "LABS" in wordmark, navigation links, section tags, stat labels, module meta, price period, footer links, button text, guarantee text

**Why Space Mono:** It is a monospace typeface with a technical, precise character. Against Cormorant's classical elegance, it creates contrast that says: this company is both artistic AND systematic. It is always used in uppercase with wide letter-spacing — never in sentence case.

**Letter-spacing values used:**
- Navigation links: `letter-spacing: 3px`
- Section tags: `letter-spacing: 5px`
- "LABS": `letter-spacing: 7px`
- Footer labels: `letter-spacing: 2px`

The wider the spacing, the more secondary/ambient the text feels.

---

### Font 3 — DM Sans (Body / Descriptions)

```
font-family: 'DM Sans', sans-serif
```

**Loaded from:** Google Fonts
`https://fonts.googleapis.com/css2?family=DM+Sans:wght@300;400;500`

**Used for:** All body copy, descriptions, paragraph text, the `<body>` default

**Why DM Sans:** Clean, neutral, humanist sans-serif. It does not compete with Cormorant or Space Mono. It simply communicates clearly at reading sizes. The `font-weight: 300` (Light) is set as the body default — which feels slightly more refined than regular weight for a premium brand.

---

## 6. Layout Architecture

### The Grid Philosophy

This site does not use a CSS grid framework. All layout is done with native CSS Grid and Flexbox where appropriate.

**Section padding** is consistent across all sections:
```css
section { padding: 120px 60px; }
```
`120px` vertical breathing room makes the page feel expensive. Cramped spacing feels cheap. On mobile this reduces to `80px 24px`.

### Alternating Backgrounds

Sections alternate between `--void` and `--abyss` to create visual rhythm without adding any graphic elements:

```
Hero          → --void
Stats bar     → --abyss
Learn         → --void
Curriculum    → --abyss
Who           → --void
Get section   → --abyss
Instructor    → --abyss
Pricing       → --void
Footer        → --void
```

This creates a breathing pattern. The eye gets a rest between sections naturally.

### The 2-Column Curriculum Layout

```css
.curriculum-layout {
  display: grid;
  grid-template-columns: 1fr 1.4fr;
  gap: 80px;
}
```

The `1fr / 1.4fr` ratio (roughly 42% / 58%) is intentionally asymmetric. Equal columns (50/50) feel static and corporate. The slight imbalance creates tension and movement — the wider column draws the eye first, then the left column provides context.

---

## 7. Components — Section by Section

### Navigation

**Position:** `fixed` — stays at top of viewport on scroll

**Background treatment:**
```css
background: linear-gradient(to bottom, rgba(5,13,11,.95), transparent);
backdrop-filter: blur(12px);
```
The gradient fades from near-opaque at top to transparent at bottom — so the nav floats over content without a hard edge. `backdrop-filter: blur(12px)` creates a frosted glass effect on the content beneath it.

**Three zones:** Logo (left) · Links (center) · CTA button (right)

The CTA button (`Enroll Now`) is the only element with a filled background in the nav. This makes it the single visual priority — the eye lands on it immediately.

---

### Hero Section

**Layout:** `min-height: 100vh` with `justify-content: flex-end` — content sits at the bottom of the viewport, not centered. This creates a more cinematic composition — like a film title card.

**The background constellation:** Positioned `absolute` at `top: 50%; right: 8%` — it sits behind the text at very low opacity. It is decorative but reinforces the brand mark in a subtle way.

**The headline structure:**
```html
Edit like          ← Bold, full opacity
you have           ← Italic, jade color (the emphasis)
something to say.  ← Light weight, 45% opacity (the resolution)
```
Three lines, three weights, three opacities. The eye reads bold first, then italic (different color), then light. This is a reading sequence, not just a headline.

**The `clamp()` function for responsive type:**
```css
font-size: clamp(64px, 9vw, 148px);
```
`clamp(min, preferred, max)` — the font scales fluidly with the viewport. On a phone it is 64px. On a 4K monitor it caps at 148px. No media queries needed for headline sizing.

---

### Stats Bar

Four numbers in a grid. The numbers use Cormorant Italic Bold — the same treatment as pricing — because both are about quantities that feel impressive.

The `∞` symbol for "Lifetime Access" is a deliberate emotional choice. It converts a feature ("no expiry date") into a feeling ("infinite possibility").

---

### Learn Cards (What You'll Learn)

**Grid:** `grid-template-columns: 1fr 1fr` — two columns, three rows of cards.

**The hover state:**
```css
.learn-card:hover {
  background: var(--sea);
  border-bottom: 2px solid var(--jade);
}
.learn-card::before {
  /* Top edge gradient line — appears on hover */
  background: linear-gradient(to right, transparent, var(--jade), transparent);
  opacity: 0; → opacity: 0.5 on hover;
}
```
On hover, the card gains: a teal bottom border, a subtle teal gradient along the top edge, and a slightly lighter background. Three simultaneous changes that feel cohesive.

---

### Curriculum Module List

Each module row uses a left border that appears on hover:
```css
.module {
  border-left: 2px solid transparent;
  transition: border-color .25s, background .25s;
}
.module:hover {
  border-left-color: var(--jade);
}
```
This is a classic editorial hover treatment — a colored tab appears on the left edge. Simple, clean, unmistakably intentional.

The module tags (Foundation / Core / Advanced / Bonus / Final) are borderline elements — just a 1px border, no fill:
```css
border: 1px solid var(--line);
color: var(--jade);
opacity: .7;
```

---

### Pricing Section

**The top edge accent line:**
```css
.price-card::before {
  content: '';
  position: absolute;
  top: -1px; left: 20%; right: 20%;
  height: 2px;
  background: linear-gradient(to right, transparent, var(--jade), transparent);
}
```
A 2px jade line fades in from both sides along the top of the card. It is subtle but creates the impression that this card is illuminated — glowing from within. This draws the eye to the card.

**The background glow:**
```css
.pricing-glow {
  background: radial-gradient(ellipse, rgba(62,207,178,.05) 0%, transparent 70%);
}
```
A barely-visible radial glow centered behind the pricing card. At 5% opacity it is below conscious perception but adds depth to the section.

**The guarantee line:**
```css
.pricing-guarantee::before,
.pricing-guarantee::after {
  content: '';
  width: 20px; height: 1px;
  background: var(--dim);
}
```
Short rules on either side of the guarantee text create an ornamental frame — turning a legal disclaimer into a typographic moment.

---

### CTA Button — Animated Fill

```css
.btn-primary {
  position: relative;
  overflow: hidden;
}
.btn-primary::after {
  content: '';
  position: absolute; inset: 0;
  background: var(--frost);
  transform: translateX(-101%);
  transition: transform .3s cubic-bezier(.16, 1, .3, 1);
}
.btn-primary:hover::after {
  transform: translateX(0);
}
.btn-primary span {
  position: relative; z-index: 1;
}
```

On hover, a white fill slides in from the left. The text (`<span>`) sits above it on `z-index: 1` so it remains visible throughout the transition. The `cubic-bezier(.16, 1, .3, 1)` easing is a spring curve — it starts slow and ends with a slight overshoot, which feels physical rather than mechanical.

---

## 8. Animations & Motion

### Page Load Sequence

Elements animate in with staggered delays using `animation-delay`. The sequence is:

```
0.2s  → Eyebrow tag (first to appear — establishes context)
0.35s → Hero headline (the statement)
0.5s  → Description paragraph
0.65s → CTA buttons (last — after attention is primed)
0.8s  → Constellation glow
1.2s  → Scroll indicator
```

The total load animation completes in about 1.5 seconds — long enough to feel intentional, short enough not to feel slow.

**The animation itself:**
```css
@keyframes riseUp {
  from { opacity: 0; transform: translateY(24px); }
  to   { opacity: 1; transform: translateY(0); }
}
```
Elements rise 24px as they fade in. This is a physical motion — as if the content is settling into place.

---

### Scroll Reveal

All sections below the hero use an `IntersectionObserver` — elements only animate when they enter the viewport:

```javascript
const obs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('visible');
      obs.unobserve(e.target); // Only animate once
    }
  });
}, { threshold: 0.12 });
```

`threshold: 0.12` means the animation triggers when 12% of the element is visible. This is low enough that it feels immediate when scrolling but doesn't trigger too early.

Cards within the same section have staggered delays via utility classes:
```css
.reveal-d1 { transition-delay: .1s; }
.reveal-d2 { transition-delay: .2s; }
.reveal-d3 { transition-delay: .3s; }
.reveal-d4 { transition-delay: .4s; }
```

---

### Constellation Animation

The hero constellation animates on `window.load` — after all resources are ready:

```javascript
nodes.forEach((n, i) =>
  setTimeout(() => { n.style.opacity = ...; }, i * 180)
);
lines.forEach((l, i) =>
  setTimeout(() => { l.style.opacity = ...; }, 600 + i * 120)
);
```

Nodes appear first (180ms apart), then lines draw in after a 600ms pause (120ms apart). This sequence mimics how a constellation is identified — you see the stars first, then the pattern reveals itself.

---

### Scroll Line Animation

```css
@keyframes scrollDrop {
  0%   { transform: scaleY(0); transform-origin: top; }
  50%  { transform: scaleY(1); transform-origin: top; }
  51%  { transform-origin: bottom; }
  100% { transform: scaleY(0); transform-origin: bottom; }
}
```

The scroll indicator line grows down from the top, then shrinks upward from the bottom — creating the impression of liquid dripping. The `transform-origin` switch at 51% is the trick that makes this work cleanly.

---

### Background Glow Pulse

```css
@keyframes glowPulse {
  0%, 100% { transform: scale(1); opacity: 1; }
  50%       { transform: scale(1.15); opacity: .6; }
}
```

The hero background glow slowly expands and contracts over 8 seconds. At full opacity it is only 7% visible (`rgba(62,207,178,.07)`). The animation is ambient — below conscious awareness but creates a sense of the page being alive.

---

## 9. Interactive Elements

### Custom Cursor

The default browser cursor is hidden (`cursor: none` on `body`) and replaced with two custom elements:

```html
<div class="cursor"></div>        <!-- Small jade dot -->
<div class="cursor-ring"></div>   <!-- Larger ring that follows with lag -->
```

**The dot** follows the mouse exactly (updated on `mousemove`).

**The ring** follows with a 12% lerp (linear interpolation) — it chases the dot smoothly:
```javascript
rx += (mx - rx) * .12;
ry += (my - ry) * .12;
```
This lag creates the impression of weight — the ring has physical momentum.

**On hover over interactive elements:** The dot scales up 2.5x and the ring expands to 56px — indicating that clicking is available without changing to the default pointer cursor.

---

## 10. CSS Architecture

### Organization

CSS is written in document order — styled from top of page to bottom. Sections within the `<style>` tag are separated by comment banners:

```css
/* ══════════════════════════════
   SECTION NAME
══════════════════════════════ */
```

This makes the CSS scannable without a preprocessor or external tools.

### Specificity Rules

- No IDs are used for styling (only for JavaScript targeting)
- Class selectors only — specificity stays flat and predictable
- No `!important` used anywhere
- Component styles are scoped to their parent class

### The `::before` / `::after` Pattern

Decorative elements are consistently implemented as pseudo-elements rather than extra HTML elements. Examples: the top-edge glow on the price card, the section tag leading line, the guarantee flanking lines. This keeps the HTML semantic and clean.

---

## 11. JavaScript Logic

Three pieces of JavaScript, all in a single `<script>` tag at the bottom of `<body>`.

### 1. Custom Cursor (lines ~1–20)

```javascript
document.addEventListener('mousemove', e => {
  mx = e.clientX; my = e.clientY;
  cursor.style.left = mx + 'px';
  cursor.style.top  = my + 'px';
});

function animRing() {
  rx += (mx - rx) * .12;
  ry += (my - ry) * .12;
  ring.style.left = rx + 'px';
  ring.style.top  = ry + 'px';
  requestAnimationFrame(animRing);
}
animRing();
```

The ring runs in a `requestAnimationFrame` loop — updating 60 times per second — which is why the lag feels smooth rather than choppy.

### 2. Scroll Reveal (lines ~21–32)

Uses `IntersectionObserver` API — modern, performant, no scroll event listeners. Runs once per element then disconnects (`obs.unobserve`).

### 3. Constellation Animation (lines ~33–45)

Runs on `window.load` (not `DOMContentLoaded`) to ensure all fonts are loaded before animation starts. Uses `setTimeout` chains rather than CSS animations for precise sequential control over each individual SVG element.

---

## 12. Responsive Design

Two breakpoints used:

```css
@media (max-width: 900px) { /* Tablet */ }
@media (max-width: 768px) { /* Mobile */ }
```

**What changes on mobile:**

| Element | Desktop | Mobile |
|---|---|---|
| Nav links | Visible | Hidden |
| Hero padding | 0 60px 80px | 0 24px 60px |
| Section padding | 120px 60px | 80px 24px |
| Learn grid | 2 columns | 1 column |
| Curriculum layout | 2 columns | 1 column |
| Who grid | 3 columns | 1 column |
| Get grid | 3 columns | 1 column |
| Stats bar | 4 columns | 2 columns |

The headline font uses `clamp()` so it never needs a media query — it scales fluidly between all viewport sizes.

---

## 13. Brand Integration

Every brand element from the StoryFrame Labs identity system is represented:

| Brand Element | Implementation |
|---|---|
| Constellation mark | SVG drawn by hand in code — same node positions, same line weights, same opacity values |
| Cormorant typeface | Primary display font throughout |
| Space Mono | Labels, navigation, technical text |
| Story / Frame contrast | Bold italic vs light upright in every wordmark instance |
| Jade (#3ECFB2) | Accent color on all interactive and highlight elements |
| Frost (#E8F8F5) | Primary text — same hex as brand system |
| Void (#050D0B) | Primary background — same hex as brand system |
| Parent company reference | Footer reads "A StoryFrame Labs Company" |

---

## 14. How to Customize

### Change the course price
Search for `$149` and replace with your price. Update the `<sup>$</sup>` and number separately if needed.

### Add your name and photo
In the instructor section, replace the placeholder `<div class="instructor-placeholder">SF</div>` with an `<img>` tag:
```html
<img src="your-photo.jpg" alt="Your Name"
  style="width:100%;height:100%;object-fit:cover;position:absolute;inset:0;">
```
Update `badge-name` and `badge-role` with your real name and title.

### Link the enroll buttons
All `href="#"` values on enroll buttons should be replaced with your payment link:
```html
<a href="https://your-payment-link.com" class="btn-enroll">
```

### Change the course stats
The four stats in the stats bar are hardcoded. Update the `.stat-num` values to match your actual course:
```html
<div class="stat-num">12+</div>  ← Hours of content
<div class="stat-num">40+</div>  ← Lessons
```

### Update module details
Each `.module` block contains a title and meta line. Update these to match your real curriculum, lesson counts, and time estimates.

### Add Google Analytics or tracking
Add your tracking script just before `</head>`:
```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
```

### Change the guarantee text
Find `.pricing-guarantee` and update the copy:
```html
<div class="pricing-guarantee">Your guarantee message here</div>
```

---

## 15. Going Live — Checklist

Before publishing, complete every item on this list:

**Content**
- [ ] Replace `$149` with actual price
- [ ] Add real instructor name and photo
- [ ] Update all lesson counts and hours to match actual course
- [ ] Link all "Enroll Now" buttons to payment platform
- [ ] Write real instructor bio (replace placeholder paragraphs)
- [ ] Set actual page `<title>` tag with your full course name
- [ ] Add `<meta name="description">` for SEO

**Technical**
- [ ] Add favicon (`<link rel="icon" href="favicon.ico">`)
- [ ] Add Open Graph tags for social sharing previews
- [ ] Add Google Analytics or Plausible tracking
- [ ] Test on mobile (real device, not just browser resize)
- [ ] Test all internal anchor links (`#curriculum`, `#pricing`, etc.)
- [ ] Check all external links open correctly

**Brand**
- [ ] Confirm logo colors match brand system exactly
- [ ] Confirm font loading (requires internet connection for Google Fonts)
- [ ] Add your real social media links to footer

**Legal**
- [ ] Link real Privacy Policy page
- [ ] Link real Terms of Service page
- [ ] Ensure refund policy matches guarantee copy

---

## Notes on the SVG Constellation

The constellation mark in this website is drawn entirely in inline SVG — no image files, no external assets. This means it scales perfectly at any resolution, loads instantly, and can be animated with JavaScript.

The node positions used consistently across all instances:

```
Top node (start):  cx="48" cy="12"
Right upper:       cx="80" cy="32"
Right lower:       cx="72" cy="68"
Bottom left:       cx="28" cy="78"
Left:              cx="14" cy="44"
Hub (jade, large): cx="40" cy="46"  ← This is StoryFrame Labs itself
Minor:             cx="62" cy="48"
```

The hub node is always the largest and always jade. Every other node connects back to it — representing the parent company at the center of all ventures.

---

*Documentation written for StoryFrame Labs · StoryFrame Academy · 2025*
*Every design decision in this document was made intentionally. Nothing is accidental.*
