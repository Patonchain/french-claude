# Motion

## The Philosophy

Animation is choreography. You are directing dancers. If you do not direct them, they flail. If you direct them well, they perform.

Motion is never decoration. It is communication:
- A button lifts to say "I am interactive"
- Content fades up to say "I have arrived"
- An icon tilts to say "You noticed me"
- A card scales to say "You are selecting me"

## Timing

Fast enough to not interrupt. Slow enough to perceive.

```css
--duration-instant: 50ms;   /* Immediate feedback */
--duration-fast: 150ms;     /* Micro-interactions */
--duration-normal: 300ms;   /* UI transitions */
--duration-slow: 500ms;     /* Emphasis, reveals */
```

## Easing

Nothing in nature moves linearly. Your curves should feel physical.

```css
/* Standard — smooth deceleration */
--ease-out: cubic-bezier(0.0, 0.0, 0.2, 1);

/* Spring — overshoots slightly, feels alive */
--ease-spring: cubic-bezier(0.34, 1.56, 0.64, 1);

/* Soft — gentle, no hard stops */
--ease-soft: cubic-bezier(0.4, 0.0, 0.2, 1);

/* Bounce — playful, use sparingly */
--ease-bounce: cubic-bezier(0.68, -0.55, 0.265, 1.55);
```

**When to use what:**
- `ease-out` — Default for most transitions
- `ease-spring` — Buttons, interactive elements, things that "pop"
- `ease-soft` — Fades, color changes, subtle shifts
- `ease-bounce` — Notifications, celebrations, moments of delight

## The Signature Moves

### The Lift

Buttons and cards that rise to meet the finger.

```css
.button {
  transition: transform var(--duration-fast) var(--ease-spring),
              box-shadow var(--duration-fast) var(--ease-out);
}

.button:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
}

.button:active {
  transform: translateY(0);
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}
```

### The Tilt

Icons that acknowledge attention with a playful rotation.

```css
.icon {
  transition: transform var(--duration-fast) var(--ease-spring);
}

.icon:hover {
  transform: rotate(8deg) scale(1.05);
}

/* Variation: tilt the other way */
.icon-alt:hover {
  transform: rotate(-8deg) scale(1.05);
}
```

### The Reveal

Content that arrives with grace, not suddenly.

```css
.reveal {
  animation: fadeUp var(--duration-normal) var(--ease-out) both;
}

@keyframes fadeUp {
  from {
    opacity: 0;
    transform: translateY(16px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Variation: fade from side */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateX(-8px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* Variation: scale up */
@keyframes scaleIn {
  from {
    opacity: 0;
    transform: scale(0.95);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}
```

### The Stagger

Multiple elements entering like musicians joining a piece.

```css
.stagger > * {
  animation: fadeUp var(--duration-normal) var(--ease-out) both;
}

.stagger > *:nth-child(1) { animation-delay: 0ms; }
.stagger > *:nth-child(2) { animation-delay: 50ms; }
.stagger > *:nth-child(3) { animation-delay: 100ms; }
.stagger > *:nth-child(4) { animation-delay: 150ms; }
.stagger > *:nth-child(5) { animation-delay: 200ms; }
.stagger > *:nth-child(6) { animation-delay: 250ms; }
```

For JavaScript-driven stagger:

```javascript
items.forEach((item, i) => {
  item.style.animationDelay = `${i * 50}ms`;
});
```

### The Glow

Focus states that breathe, not just appear.

```css
.input {
  transition: box-shadow var(--duration-fast) var(--ease-out);
}

.input:focus {
  outline: none;
  box-shadow: 0 0 0 3px var(--accent-glow);
}

/* Variation: ring that expands */
.input:focus {
  outline: none;
  box-shadow: 0 0 0 3px var(--accent-glow);
  animation: focusRing var(--duration-fast) var(--ease-out);
}

@keyframes focusRing {
  from { box-shadow: 0 0 0 0 var(--accent-glow); }
  to { box-shadow: 0 0 0 3px var(--accent-glow); }
}
```

### The Slide

Panels, drawers, menus that slide in from edges.

```css
.panel {
  transform: translateX(100%);
  transition: transform var(--duration-normal) var(--ease-out);
}

.panel.open {
  transform: translateX(0);
}

/* With backdrop */
.backdrop {
  opacity: 0;
  transition: opacity var(--duration-normal) var(--ease-out);
}

.backdrop.visible {
  opacity: 1;
}
```

### The Expand

Accordions, dropdowns, collapsibles.

```css
.collapsible {
  display: grid;
  grid-template-rows: 0fr;
  transition: grid-template-rows var(--duration-normal) var(--ease-out);
}

.collapsible.open {
  grid-template-rows: 1fr;
}

.collapsible-content {
  overflow: hidden;
}
```

## Scroll-Triggered Animation

Use IntersectionObserver, not scroll events.

```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('.reveal-on-scroll').forEach(el => {
  observer.observe(el);
});
```

```css
.reveal-on-scroll {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity var(--duration-normal) var(--ease-out),
              transform var(--duration-normal) var(--ease-out);
}

.reveal-on-scroll.visible {
  opacity: 1;
  transform: translateY(0);
}
```

## Accessibility

Always. Non-negotiable.

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

## What to Animate

**Yes:**
- `opacity` — cheap, smooth
- `transform` — GPU accelerated
- `box-shadow` — use sparingly
- `background-color` — subtle shifts

**Non:**
- `width`, `height` — causes layout thrashing
- `top`, `left` — use transform instead
- `margin`, `padding` — reflows the page
- `border-width` — jarring

## The Test

If you removed the animation, would anything be lost?

If no — remove it.
If yes — you designed it well.
