# CSS Basics - Unlocking Layout with display and position

<details open>
  <summary>Table of Contents</summary>

- [Intro](#intro)
- [Display](#display)
  - [1. `block`](#1-block)
  - [2. `inline`](#2-inline)
  - [3. `inline-block`](#3-inline-block)
  - [4. `none`](#4-none)
  - [5. `flex`](#5-flex)
  - [6. `grid`](#6-grid)
- [Position](#postition)

  - [1. `static`](#1-static-default)
  - [2. `relative`](#2-relative)
  - [3. `absolute`](#3-absolute)
  - [4. `fixed`](#4-fixed)
  - [5. `sticky`](#5-sticky)

</details>

## Intro

In CSS, two of the most powerful tools for controlling layout and structure are the `display` and `position` properties. They define not just **how elements appear**, but also **how they behave in relation to other elements** on the page.

Today, we’ll explore both of these core concepts:

- `display`: determines **how an element behaves in the layout flow**, whether it’s inline like a word, block-level like a section, or a layout container like a flex or grid.
- `position`: defines **where an element is placed** in the document, whether it follows the normal flow or is moved somewhere else entirely — even fixed to the screen.

Understanding how these properties work (and how they interact with the **box model** — width, height, margin, padding, and border) is essential for building modern, responsive, and well-structured web pages.

By the end of this guide, you'll be able to:

- Choose the right `display` value for your layout goals.
- Use `position` to control element placement with precision.
- Avoid common layout pitfalls and create more flexible, maintainable designs.

[Back to top](#css-basics---unlocking-layout-with-display-and-position)

## Display

The `display` property controls **how elements appear in the layout** and how their **box model** (width, height, margin, padding, border) is applied. Different values unlock different layout behaviors, from simple inline flow to complex grid systems.

### **Available Values**

### **1. `block`**

- **Behavior:** The element starts on a new line and expands horizontally to fill the entire width of its parent container (unless a specific width is set). It pushes content before and after it downward, behaving like a paragraph or a section.

- **Box model:**

  - ✅ `width` and `height` are fully respected.

  - ✅ `margin` and `padding` work in **all directions**.

  - ✅ `border` is fully supported.

- **Use case:** Ideal for creating structural layout blocks. Used by default on `<div>`, `<section>`, `<article>`, and most layout elements.

**Analogy:** Like a big building block that always demands its own row and full space to breathe.

[Back to top](#css-basics---unlocking-layout-with-display-and-position)

### **2. `inline`**

- **Behavior:** The element flows along with text, sitting on the same line as other inline elements. It doesn’t break onto a new line and only takes up as much width as its content needs.

- **Box model:**

  - ❌ `width` and `height` are **ignored** — the element sizes to fit its content.

  - ⚠️ `padding` and `margin` only work **horizontally** (left/right).

  - ✅ `border` works, but vertical borders don’t push anything.

- **Use case:** Styling words or phrases inside text, like with `<span>`, `<a>`, `<strong>`. Use when you want content to flow naturally.

**Analogy:** Like a word in a sentence — it fits into the flow without disrupting it.

[Back to top](#css-basics---unlocking-layout-with-display-and-position)

### **3. `inline-block`**

- **Behavior:** Like `inline`, it flows with other elements and doesn't start a new line — but unlike `inline`, it behaves like a block-level box. You can set its size and apply full spacing around it.
- **Box model:**

  - ✅ `width` and `height` are fully supported.

  - ✅ `margin`, `padding`, and `border` all work **in every direction**.

- **Use case:** Buttons, icons, images with labels, or any inline layout where you need sizing control without breaking onto new lines.

**Analogy:** Like a box sitting neatly inside a sentence — it has dimensions but still plays nicely with inline content.

[Back to top](#css-basics---unlocking-layout-with-display-and-position)

### **4. `none`**

- **Behavior:** The element is completely removed from the layout and the DOM rendering. It takes up no space and is not visible or interactive.

- **Box model:**

  - ❌ None of the box model properties apply, since the element doesn’t render at all.

- **Use case:** Show/hide elements with JavaScript or CSS (like modals, dropdowns, tab content).

**Analogy:** Like a disappearing act — the element is gone from the stage entirely.

[Back to top](#css-basics---unlocking-layout-with-display-and-position)

### **5. `flex`**

- **Behavior:** Turns the element into a **flex container**, allowing its direct children to be flex items. You gain full control over alignment, spacing, direction (row or column), wrapping, and item sizing — all without float hacks or extra wrappers.

- **Box model (container):**
  ✅ `width`, `height`, `margin`, `padding`, and `border` all apply normally.
- **Box model (flex items):**
  ✅ All properties apply, but layout behavior is also controlled via `flex` properties like `flex-grow`, `flex-shrink`, `align-self`, etc.
- **Use case:** Horizontal navbars, vertical sidebars, responsive layouts, or equal-height cards that align dynamically.

**Analogy:** Like giving your container magical control over how its children arrange themselves — no float, no struggle.

[Back to top](#css-basics---unlocking-layout-with-display-and-position)

### **6. `grid`**

- **Behavior:** Turns the element into a **grid container**, allowing you to define rows and columns for precise placement of children. You can control both vertical and horizontal layout simultaneously.

- **Box model (container):**
  ✅ Full support for `width`, `height`, `margin`, `padding`, and `border`.
- **Box model (grid items):**
  ✅ All properties apply. Grid placement is determined by properties like `grid-column`, `grid-row`, `justify-self`, etc.
- **Use case:** Layouts that need more structure — like dashboards, complex UIs, calendars, or image galleries.

**Analogy:** Like drawing a grid on graph paper and snapping elements into exact positions.

[Back to top](#css-basics---unlocking-layout-with-display-and-position)

## Postition

The `position` property in CSS controls **how an element is placed** in the document layout. It determines **whether** the element follows normal flow or is positioned relative to something else (like a parent or the viewport).

### **Why it's used**

To:

- Precisely control element placement.
- Create UI components that float, overlay, or stay fixed.
- Enable layered layouts with `z-index`.

### **Common Use Cases**

- `relative`: slight nudges, tooltip anchors.
- `absolute`: dropdowns, modals, badges inside containers.
- `fixed`: sticky headers, floating buttons, back-to-top links.

---

### **Available Values**

### **1. `static` (default)**

- **Behavior:** Element flows in the normal document layout.
- **Offset properties (`top`, `right`, etc.):** Ignored.
- **Use case:** Default positioning.

### **2. `relative`**

- **Behavior:** The element stays in the normal document flow but can be _visually shifted_ from its original position.
- **Offset properties:** `top`, `right`, `bottom`, and `left` move the element without affecting the layout of surrounding elements. If you use two directions on the same axis (e.g. `left` and `right`), only one takes effect — `left` overrides `right`, and `top` overrides `bottom`. These offsets do not act as constraints and do not affect the element’s size.
- **Use case:** Slight visual adjustments, like nudging an element without disrupting layout flow.

### **3. `absolute`**

- **Behavior:** Removed from the normal flow. Positioned relative to the nearest _positioned ancestor_ (`relative`, `absolute`, `fixed`, or `sticky`).
- **Offset properties:** Fully respected.
- **Use case:** Dropdowns, tooltips, overlays inside containers.

### **4. `fixed`**

- **Behavior:** Removed from flow. Positioned _relative to the viewport_ and stays fixed during scrolling.
- **Offset properties:** Fully respected.
- **Use case:** Sticky headers, floating buttons.

### **5. `sticky`**

- **Behavior:** Acts like `relative` until a scroll threshold is reached, then "sticks" in place like `fixed`.
- **Offset properties:** The threshold is defined by `top`, `left`, `right`, or `bottom` — e.g. `top: 0` means it sticks when it reaches the top of the viewport.
- **Use case:** Sticky table headers or navigation bars that stay visible while scrolling.

[Back to top](#css-basics---unlocking-layout-with-display-and-position)
