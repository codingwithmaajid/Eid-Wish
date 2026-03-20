```markdown
# Design System Specification: The Monochromatic Glass Ethos

## 1. Overview & Creative North Star: "The Digital Curator"
This design system rejects the "boxed-in" nature of standard web templates. Our North Star is **The Digital Curator**—a philosophy that treats the user interface not as a series of containers, but as a gallery of floating, high-fidelity objects. 

We move beyond "modern" by embracing **Tonal Minimalism**. By utilizing a monochromatic palette and glassmorphism, we create a UI that feels light, airy, and expensive. We break the rigid grid through intentional asymmetry, using vast whitespace (the "Breathing Room" principle) to let content command authority. Every element should feel like a pane of precision-cut glass suspended in a neutral void.

---

## 2. Colors & Surface Architecture
The palette is rooted in absolute neutrals. We achieve depth through light transmission and tonal shifts, never through heavy lines.

### The "No-Line" Rule
Traditional 1px solid borders are strictly prohibited for sectioning. To separate content, use:
- **Tonal Transitions:** Transition from `surface` to `surface_container_low`.
- **Negative Space:** Use the `24` (6rem) or `16` (4rem) spacing tokens to create a natural visual break.
- **Glass Refraction:** Use a `backdrop-blur` (12px–20px) to define the boundary of a floating element.

### Surface Hierarchy & Nesting
Treat the UI as a physical stack of materials.
1.  **Base Layer:** `surface` (#f9f9f9).
2.  **Sectional Layer:** `surface_container_low` (#f3f3f3) for secondary content areas.
3.  **Object Layer:** `surface_container_lowest` (#ffffff) for cards or interactive modules.
4.  **Floating Layer:** Glassmorphic elements using `surface` at 70% opacity with `saturate-150` and `blur-xl`.

### Signature Textures
Main CTAs or Hero backgrounds should use a subtle "Ink Gradient": 
`linear-gradient(135deg, var(--primary) 0%, var(--primary_container) 100%)`. This adds a tactile, velvety depth to the flat black.

---

## 3. Typography: Editorial Authority
We pair the utilitarian perfection of **Inter** with the technical precision of **Space Grotesk** (Monospace).

- **Display & Headlines:** Use `display-lg` and `headline-lg` (Inter) with tight letter-spacing (-0.02em). These are your "Anchors." They should be bold and unapologetic.
- **Body:** `body-md` (Inter) is the workhorse. Maintain a line-height of 1.6 for maximum readability.
- **The Technical Accent:** All labels (`label-md`, `label-sm`) must use **Space Grotesk**. This monospace font acts as a "metadata layer," signaling technical data, timestamps, or small UI hints. It provides a high-end, "blueprinted" aesthetic.

---

## 4. Elevation & Depth: The Layering Principle
We do not use shadows to create "pop." We use them to simulate environmental light.

- **Ambient Shadows:** For floating elements (Headers, Sheets), use a shadow color derived from `on_surface` at 4% opacity. 
  - *Spec:* `box-shadow: 0 20px 40px rgba(26, 28, 28, 0.04);`
- **The "Ghost Border" Fallback:** If a border is required for accessibility on a light background, use `outline_variant` at 20% opacity. It should be felt, not seen.
- **Glassmorphism Spec:** 
  - Background: `rgba(255, 255, 255, 0.65)` (Light Mode) / `rgba(0, 0, 0, 0.5)` (Dark Mode)
  - Backdrop Blur: `20px`
  - Border: `1px solid rgba(255, 255, 255, 0.2)`

---

## 5. Component Guidelines

### Floating Header
The header must not be pinned to the top of the viewport with a hard edge. 
- **Style:** A floating "pill" or detached bar.
- **Tokens:** `surface_container_lowest` (70% opacity), `rounded-xl`, `spacing-4` margin from top/sides.
- **Interaction:** On scroll, the backdrop blur increases from 10px to 25px.

### Buttons (The Precision Triggers)
- **Primary:** Background `primary` (#000000), text `on_primary`. Radius: `md` (0.375rem). No shadow.
- **Secondary:** Background `surface_container_high`. No border.
- **Glass (Tertiary):** Transparent background with `backdrop-blur-md` and a `Ghost Border`.

### Input Fields
- **Style:** Remove the "box" look. Use a `surface_container_low` background with a bottom-only `outline_variant` focus state.
- **Typography:** Placeholder text should use `label-md` (Space Grotesk) to differentiate user-input from system-labels.

### Sheet (Drawer)
- **Positioning:** Sheets should slide in from the right or bottom with a `xl` (0.75rem) corner radius.
- **Scrim:** The background overlay (scrim) should use `on_surface` at 20% opacity with a `blur-sm` effect on the content behind it.

### Cards & Lists
- **Rule:** Forbid divider lines.
- **Implementation:** Use `surface_container_low` for the card background. For lists, use `spacing-3` (0.75rem) between items. To separate data types, use a shift to `label-sm` (Monospace).

---

## 6. Do’s and Don’ts

### Do
- **Do** use `primary_fixed` (#5f5e61) for secondary text that needs to remain legible in both light and dark modes.
- **Do** use asymmetrical padding (e.g., more padding on the bottom than the top) to create a sense of gravity and editorial intent.
- **Do** leverage the `rounded-full` token for utility chips to contrast against the `md` and `xl` corners of the main containers.

### Don't
- **Don't** use `#000000` for borders. It creates "visual noise." Use `outline_variant` at low opacity.
- **Don't** use standard "drop shadows." If an object needs to feel elevated, increase the `surface_container` tier (e.g., move from `low` to `highest`).
- **Don't** use Inter for metadata. Always use the Monospace `label` tokens for technical details.
- **Don't** use 100% opaque backgrounds for floating navigation; the "Glass" effect is mandatory for the signature look.

### Additional Recommended Component: The "Contextual HUD"
A small, floating glassmorphic tooltip/bar that appears at the bottom-center of the screen for non-destructive actions (e.g., "Draft Saved"). It should use `surface_container_highest` with 80% opacity and `rounded-full`.```