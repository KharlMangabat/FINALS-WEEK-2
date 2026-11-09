# Developer Handoff: Jollibee Structural Wireframe

This document details the functional specifications, structural hierarchy, and layout constraints for translating the Jollibee homepage wireframe into a high-fidelity frontend build.

---

## 1. Global Design System (Tokens)

While the wireframe uses a neutral grayscale profile for spatial planning, the final implementation must adopt official brand assets:

| Token Name | Value / Hex Code | Usage |
| :--- | :--- | :--- |
| **Primary Brand Red** | `#D61C2C` | Headers, primary CTA buttons, branding accents |
| **Primary Brand Yellow** | `#FCD116` | Secondary accents, highlights, star rating elements |
| **Background Light** | `#F4F4F4` | Main page body canvas background |
| **Card Canvas White** | `#FFFFFF` | Menu item grids, header backgrounds |
| **Typography (Primary)** | `Inter`, `Arial`, sans-serif | UI controls, labels, layout grid text |

---

## 2. Layout & Dom Structure Breakdown

### 2.1 Navigation Header (`<header>`)
* **Behavior:** Fixed or Sticky to the top viewport boundary (`position: sticky; top: 0; z-index: 1000;`).
* **Flexbox Blueprint:** Space-between distribution for the elements.
  * Left: Brand Logo wrapper (`<a>` anchor targeting root).
  * Center: Ordered navigation links (`<nav> <ul> <li>`).
  * Right: Action items wrapper containing two call-to-actions ("Order Now" & "Login").

### 2.2 Hero Campaign Canvas (`<section class="hero-section">`)
* **Container Strategy:** Fluid width with a hard max-width safety limit (`max-width: 1200px;`).
* **Aspect Ratio Rule:** Aspect ratio must remain stable across screen shifts. Suggested scaling dimensions: `width: 100%; height: auto; min-height: 350px;`.
* **Asset Payload:** Targeted placeholder slot reserved for the main creative marketing asset (e.g., Chickenjoy or active promotional campaign banner).

### 2.3 Menu Item Catalog Grid (`<section class="menu-highlights">`)
* **CSS Grid Engine:** Uses an implicit grid layout engine that handles responsive item counts natively without media query boilerplate:
  ```css
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  ```
* **Card Component Assembly:**
  * **Top Asset Slot:** Structural block reserved for food item photography (`object-fit: cover;`).
  * **Title Slot:** Content title placeholder text.
  * **Interactive CTA:** Full-width structural block element containing the operational action behavior trigger ("Add to Cart").

### 2.4 Footer Base Layer (`<footer>`)
* **Column Setup:** Asymmetric, wrapping auto-fit grid layout structure. 
* **Content Categorization:** 
  * Column 1: Core Navigation Links (e.g., Terms of Use, Privacy Policy).
  * Column 2: Support Channels / Contact Maps.
  * Column 3: Corporate and Social Media Profile integrations.

---

## 3. Responsive Web Targets

The layout shifts dynamically across three major breakpoints:

* **Desktop (`>= 1024px`):** Full horizontal navigation links exposed. Grid displays 4 distinct items per row.
* **Tablet (`768px - 1023px`):** Grid adjusts automatically to display 2 items per row.
* **Mobile (`< 768px`):** Main navigation links collapse behind a mobile toggle overlay interface. Grid adjusts to display 1 item per row.
