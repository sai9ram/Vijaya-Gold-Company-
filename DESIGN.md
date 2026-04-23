# Design System Document: High-End Editorial Jewelry Aesthetic

## 1. Overview & Creative North Star
**Creative North Star: "The Gilded Manuscript"**

This design system moves away from the rigid, boxy constraints of traditional fintech and e-commerce. Instead, it draws inspiration from high-end editorial magazines and archival jewelry catalogs. The goal is to create a digital experience for a gold buying business that feels as valuable as the asset itself.

We break the "template" look through **intentional asymmetry**, generous use of whitespace (breathing room), and a focus on **tonal depth** rather than structural lines. The UI should feel like a series of layered, premium materials—fine paper, frosted glass, and polished gold—rather than a flat digital screen.

---

## 2. Colors & Surface Philosophy
The color palette balances the warmth of light orange gold with the stability of charcoal and cream.

### The "No-Line" Rule
**Prohibit the use of 1px solid borders for sectioning.** 
In this system, boundaries are defined exclusively through background color shifts. To separate a testimonial section from a hero section, transition from `surface` (#FFFBF5) to `surface_container_low` (#FAF4EB). This creates a sophisticated, seamless flow that mimics the physical world.

### Surface Hierarchy & Nesting
Treat the UI as a physical stack of materials. Use the `surface-container` tiers to define importance:
*   **Base Layer:** `surface` (#FFFBF5) for main page backgrounds.
*   **Nesting:** Place a `surface_container_lowest` (#ffffff) card on top of a `surface_container_low` (#FAF4EB) background to create a "soft lift."
*   **Depth:** Reserve `surface_container_highest` (#e8e0d6) for persistent elements like sidebars or utility drawers.

### The "Glass & Gradient" Rule
To avoid a flat, "out-of-the-box" appearance:
*   **Signature Textures:** Use subtle linear gradients for primary CTAs, transitioning from `primary` (#C17F24) at 0% to `primary_container` (#E8A840) at 100% at a 135-degree angle.
*   **Glassmorphism:** For floating navigation bars or overlays, use `surface` with 80% opacity and a `20px` backdrop-blur. This allows the "gold" accents of the content below to bleed through, softening the interface.

---

## 3. Typography
The typography strategy pairs the authority of a classic serif with the modern efficiency of a geometric sans-serif.

*   **Display & Headlines (Noto Serif):** Used for storytelling and high-level headings. The serif typeface conveys legacy, trust, and the "High-End Jewelry" aesthetic. Use `display-lg` for hero statements with tight letter-spacing (-0.02em) to feel like a masthead.
*   **Body & Labels (Manrope):** A modern, high-legibility sans-serif. Used for technical details, gold weight tables, and transactional data. 
*   **Hierarchy Note:** Use high-contrast sizing. A large `display-md` headline paired with a small, all-caps `label-md` (tracked out to +0.1em) creates an editorial look that guides the eye with intention.

---

## 4. Elevation & Depth
We reject traditional drop shadows in favor of **Tonal Layering**.

*   **The Layering Principle:** Depth is achieved by stacking surface tokens. A card should not "float" with a shadow; it should "sit" on a slightly darker or lighter surface.
*   **Ambient Shadows:** If an element must float (e.g., a modal), use an ultra-diffused shadow: `box-shadow: 0 20px 40px rgba(28, 28, 25, 0.05)`. The color is a tint of `on_surface`, never pure black.
*   **The "Ghost Border" Fallback:** If accessibility requires a container definition, use the `outline_variant` (#d4c4a8) at **15% opacity**. This creates a whisper of a line that defines space without cluttering the visual field.
*   **Interactive Depth:** On hover, instead of increasing a shadow, shift the background color from `surface_container_low` to `surface_container_lowest`.

---

## 5. Components

### Buttons
*   **Primary:** Uses the "Signature Gradient" (Primary to Primary Container). Text is `on_primary`. Shape is `DEFAULT` (0.25rem) for a structured, architectural feel.
*   **Secondary:** `surface_container_lowest` with a "Ghost Border."
*   **Tertiary:** Text-only in `primary`, using `label-md` in all-caps with a 1px underline offset by 4px.

### Input Fields
*   **Style:** Minimalist. No four-sided boxes. Use a `surface_container_low` background with a bottom-only border using the `outline` token.
*   **Focus State:** The bottom border transitions to `primary` gold, and the label (using `label-sm`) shifts to `primary`.

### Cards & Lists
*   **Strict Rule:** No divider lines. Use vertical whitespace (32px or 48px) to separate list items. 
*   **Cards:** Use `surface_container_low` with a padding of `2rem` (32px). Elements within the card should be asymmetrical—for example, an image aligned left with text offset to the right.

### Custom Component: The "Gold Quote" Ticker
*   A specialized component for live gold prices. Use a `surface_dim` background with `primary` text for the price and `secondary` for the "Last Updated" timestamp. Ensure the typography uses tabular nums for visual stability during price updates.

---

## 6. Do's and Don'ts

### Do
*   **Do** use asymmetrical layouts where text overlaps gold-textured image containers.
*   **Do** prioritize whitespace. If a section feels crowded, double the padding.
*   **Do** use `notoSerif` for numbers when they represent value (e.g., currency amounts) to make them feel prestigious.

### Don't
*   **Don't** use 100% black. Use `on_background` (#1c1b18) for text to maintain a softer, premium contrast.
*   **Don't** use standard Material Design "elevated" buttons with heavy shadows.
*   **Don't** use icons as primary navigation without labels. The brand must feel communicative and sophisticated, not cryptic.
*   **Don't** use rounded corners larger than `xl` (0.75rem) for containers; it breaks the "Fine Stationery" aesthetic and begins to look too "app-like" and playful.