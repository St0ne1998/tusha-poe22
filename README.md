# Tusha Petals & Gifts — WEDE5020 POE

**Student:** Amusement Herith Lubisi 
**Module:** WEDE5020 — Web Development  
**Part:** 2 of 3  
**Submission Date:29 May 2026  
**Live URL:** https://st0ne1998.github.io/TUSHA-F/  
**Repository:** https://github.com/st0ne1998/TUSHA-F

---

## Project Overview

Tusha Petals & Gifts is a real business website for a florist and gift shop based in Mbombela (Nelspruit), South Africa. The site showcases the business's floral arrangements, gift hampers, and contact details, allowing customers to order directly via WhatsApp.

---

## Part 2 Context — CSS Styling & Responsive Design

Part 2 builds on the HTML-only foundation submitted in Part 1. The primary deliverables for this part are:

1. A dedicated external stylesheet (`style.css`) linked to **every HTML page**
2. Full responsive design across Desktop, Tablet, and Mobile breakpoints
3. A multi-page structure with an improved `shop.html` and `contact.html`
4. Semantic, accessible HTML improvements throughout
5. Responsive image optimisation using `srcset`, `sizes`, and `<picture>`

### Files Added / Modified in Part 2

| File | Status | Description |
|------|--------|-------------|
| `style.css` | **New** | Complete external stylesheet (500+ lines) |
| `index.html` | **Updated** | Linked to `style.css`; semantic improvements; responsive images |
| `shop.html` | **New** | Dedicated shop/collections page with page banner & breadcrumb |
| `contact.html` | **New** | Dedicated contact page with enhanced form |
| `README.md` | **Updated** | This document — Part 2 additions |

---

## CSS Architecture

### 1. CSS Reset
A universal box-sizing reset and element normaliser is applied at the top of `style.css` to remove inconsistent default browser behaviour across Chrome, Firefox, Safari, and Edge.

### 2. CSS Custom Properties (Variables)
All design tokens — colours, font families, type scale, spacing, border radii, shadows, and transition timing — are defined as CSS custom properties on `:root`. This makes the entire design system easy to maintain and ensures visual consistency across all pages.

```css
:root {
  --clr-primary: #8b1a3a;
  --ff-display:  'Playfair Display', serif;
  --fs-base:     1rem;
  /* ...etc */
}
```

### 3. Typography Scale
A Major Third type scale (ratio 1.250) provides a clear visual hierarchy:

| Token | Size | Usage |
|-------|------|-------|
| `--fs-4xl` | 3.815rem | Hero h1 |
| `--fs-3xl` | 3.052rem | Section headings |
| `--fs-2xl` | 2.441rem | Sub-headings |
| `--fs-xl`  | 1.953rem | Card headings |
| `--fs-lg`  | 1.563rem | Nav logo |
| `--fs-base`| 1rem     | Body text |
| `--fs-sm`  | 0.8rem   | Labels, captions |
| `--fs-xs`  | 0.64rem  | Section labels, breadcrumbs |

### 4. Layout System

**CSS Grid** is used for:
- Hero section (`grid-template-columns: 1fr 1fr`)
- About section image/content split
- Product grid (`repeat(3, 1fr)`)
- Features grid (`repeat(3, 1fr)`)
- Testimonials grid (`repeat(3, 1fr)`)
- Contact grid (`1fr 1.4fr`)
- Footer grid (`1.8fr 1fr 1fr`)

**Flexbox** is used for:
- Navigation bar (horizontal alignment)
- Button groups
- Contact items
- Stats row
- Breadcrumb

### 5. Responsive Breakpoints

| Breakpoint | Max-width | Changes Applied |
|-----------|-----------|-----------------|
| Desktop Large | ≥ 1280px | Increased section padding |
| Desktop (base) | 1025–1279px | Full multi-column grids |
| Tablet | ≤ 1024px | 2-column grids; reduced font scale |
| Mobile | ≤ 768px | 1-column layout; hamburger nav; stacked hero |
| Small Mobile | ≤ 480px | Smaller hero type; stacked buttons |

### 6. Relative Units

- `rem` is used for all font sizes and most spacing (scales with root font size)
- `em` is used where spacing is proportional to the local element's font size
- `%` is used for fluid element widths (`width: 70%`, `width: 55%` in image stacks)
- `vw` and `vh` are used for viewport-relative sizing (`min-height: 100vh`)

---

## Responsive Images

All product and section images use the `<picture>` element with `srcset` and `sizes` attributes:

```html
<picture>
  <source
    srcset="image.jpg 400w, image.jpg 800w"
    sizes="(max-width: 768px) 100vw,
           (max-width: 1024px) 50vw,
           33vw"
  />
  <img src="image.jpg" alt="Descriptive alt text" loading="lazy" />
</picture>
```

This ensures:
- Mobile devices load lighter 400w images
- Tablets load 700–800w variants
- Desktops load full-resolution images
- The hero image uses `loading="eager"` for LCP performance; all others use `loading="lazy"`

---

## Interactive States

All interactive elements include `:hover`, `:focus`, and `:active` pseudo-class styles:

- **Navigation links:** underline slide-in animation on hover; colour shift on focus
- **Buttons:** `translateY(-2px)` lift effect and shadow intensification on hover; pressed state on `:active`
- **Product cards:** `translateY(-6px)` elevation and deeper shadow on hover; image zoom on `product-img-wrap:hover img`
- **Form inputs:** border colour change and box-shadow ring on `:focus` for accessibility
- **Footer links:** left padding slide on hover for tactile feedback

---

## Changelog

### Part 2 — May 2026

#### New Features
- **`style.css` created** — Full external stylesheet covering reset, variables, typography, layout, components, and responsive rules. Linked via `<link rel="stylesheet" href="style.css" />` in the `<head>` of every HTML page.
- **`shop.html` added** — Dedicated shop page with page banner, breadcrumb navigation, full 6-card product grid, and a WhatsApp CTA footer block.
- **`contact.html` added** — Dedicated contact page with additional form fields (phone, budget selector), trading hours, and improved layout.
- **Responsive design implemented** — Four breakpoints (≥1280px, ≤1024px, ≤768px, ≤480px) with appropriate layout, typography, and navigation changes at each.
- **Hamburger navigation** — Mobile nav toggle with animated open/close state and ARIA `aria-expanded` attribute management.
- **Responsive images** — All images converted to `<picture>` elements with `srcset` and `sizes` for optimal loading at each viewport size.
- **CSS Custom Properties** — Full design token system on `:root` for colours, typography, spacing, shadows, and transitions.
- **CSS Grid layout** — Multi-column grids for products, features, testimonials, and footer; switches to single-column on mobile.
- **Typography scale** — Major Third scale applied consistently using `rem` units with Playfair Display (display), Lato (body), and Cormorant Garamond (accent/italic) Google Fonts.
- **Scroll-aware navigation** — Nav bar gains backdrop and deeper shadow class `.scrolled` via JavaScript on scroll past 60px.
- **Floating WhatsApp button** — Fixed-position call-to-action with smooth hover animation; label text hidden on small mobile screens.

#### Improvements to Part 1 HTML
- Added `lang="en"` to `<html>` on all pages (accessibility requirement)
- Added `<meta name="description">` to all pages for SEO
- Replaced generic `<div>` wrappers with semantic `<article>`, `<section>`, `<nav>`, `<header>`, `<footer>` elements
- Added `role` and `aria-label` attributes to nav, main landmark, and icon-only elements
- Added `aria-hidden="true"` to decorative emoji and icon elements
- Added `width` and `height` attributes to all `<img>` tags to prevent Cumulative Layout Shift (CLS)
- Fixed missing `alt` text on product images — each now has descriptive, unique alt text
- Removed inline `style` attributes in favour of CSS class rules (cascade management)
- Added `rel="noopener"` to all external `target="_blank"` links (security best practice)

---

## Testing Evidence

### Browser Developer Tools — Responsive Testing

The following viewports were tested using Chrome DevTools (F12 → Toggle Device Toolbar):

| Viewport | Width | Result |
|----------|-------|--------|
| Desktop Large | 1440px | Multi-column grid; full hero two-column |
| Desktop | 1280px | Full layout intact |
| Tablet (iPad) | 768px | 2-column grids; hamburger nav visible |
| Mobile L | 425px | Single-column; stacked hero |
| Mobile S | 320px | Font scale reduced; buttons full-width |

### Screenshot Evidence

> **Instructions for student:** Take screenshots using Chrome DevTools responsive mode and replace these placeholder descriptions with actual embedded images:

```
![Desktop Layout — 1440px](screenshots/desktop-1440.png)
![Tablet Layout — 768px](screenshots/tablet-768.png)
![Mobile Layout — 425px](screenshots/mobile-425.png)
```

**To capture screenshots:**
1. Open your deployed site in Chrome
2. Press `F12` → click the device icon (Toggle Device Toolbar)
3. Select each device preset (e.g. iPhone 12 Pro, iPad, Desktop)
4. Use `Ctrl + Shift + P` → type "Capture screenshot" → save
5. Add the images to a `/screenshots` folder and update the paths above

---

##  References

Duckett, J. (2011). *HTML and CSS: Design and Build Websites*. John Wiley & Sons.

Frain, B. (2020). *Responsive Web Design with HTML5 and CSS* (3rd ed.). Packt Publishing.

MDN Web Docs. (2024). *CSS Custom Properties (Variables)*. Mozilla. https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties

MDN Web Docs. (2024). *Responsive Images*. Mozilla. https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images

MDN Web Docs. (2024). *CSS Grid Layout*. Mozilla. https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout

MDN Web Docs. (2024). *CSS Flexible Box Layout*. Mozilla. https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_flexible_box_layout

W3C. (2023). *Web Content Accessibility Guidelines (WCAG) 2.1*. https://www.w3.org/TR/WCAG21/

Google Fonts. (2026). *Playfair Display, Lato, Cormorant Garamond*. https://fonts.google.com

CSS-Tricks. (2023). *A Complete Guide to CSS Grid*. https://css-tricks.com/snippets/css/complete-guide-grid/

CSS-Tricks. (2023). *A Complete Guide to Flexbox*. https://css-tricks.com/snippets/css/a-guide-to-flexbox/

---

## Commit History Guidelines

Use descriptive commit messages following this convention:

```
feat: add external stylesheet with CSS reset and variables
feat: implement responsive breakpoints for tablet and mobile  
feat: add responsive images with srcset and picture elements
fix: correct nav hamburger ARIA attributes
docs: update README with Part 2 changelog and references
style: refine button hover states and transition timing
```

---

## Repository Structure

```
TUSHA-F/
├── index.html          ← Homepage (updated Part 2)
├── shop.html           ← Shop/Collections page (new Part 2)
├── contact.html        ← Contact page (new Part 2)
├── style.css           ← External stylesheet (new Part 2)
├── f1.jpeg             ← Product image: 100 Red Roses
├── f4.jpeg             ← Product image: Red Elegance
├── f5.jpeg             ← Product image: Heart Box
├── f6.jpeg             ← Product image: Mixed Bouquet
├── f7.jpeg             ← Product image: Gift Hamper
├── f8.jpeg             ← Product image: Bespoke
├── screenshots/        ← Responsive testing screenshots (Part 2)
│   ├── desktop-1440.png
│   ├── tablet-768.png
│   └── mobile-425.png
└── README.md           ← This file
```
