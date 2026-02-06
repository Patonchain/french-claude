# Motion

## The Principle

Animation is not decoration. It is communication. It tells the user what happened, what is related, what to focus on.

Gratuitous animation is worse than no animation.

## Duration

Fast enough to not interrupt. Slow enough to perceive.

```css
--duration-instant: 50ms;   /* State changes (active, focus) */
--duration-fast: 150ms;     /* Micro-interactions (hovers, toggles) */
--duration-normal: 250ms;   /* UI transitions (modals, dropdowns) */
--duration-slow: 400ms;     /* Significant changes (page transitions) */
--duration-slower: 600ms;   /* Dramatic emphasis (onboarding, celebration) */
```

## Easing

The physics of motion. Nothing in nature moves linearly.

```css
/* Entering: Start fast, ease in */
--ease-out: cubic-bezier(0.0, 0.0, 0.2, 1);

/* Leaving: Start slow, accelerate out */
--ease-in: cubic-bezier(0.4, 0.0, 1, 1);

/* Moving: Smooth throughout */
--ease-in-out: cubic-bezier(0.4, 0.0, 0.2, 1);

/* Emphasis: Overshoot slightly */
--ease-spring: cubic-bezier(0.34, 1.56, 0.64, 1);
```

## What to Animate

**Yes:**
- Opacity (fade in/out)
- Transform (move, scale, rotate)
- Color (with restraint)

**Avoid:**
- Width/height (causes layout thrashing)
- Top/left (use transform instead)
- Box-shadow (expensive)

## Patterns

**Hover states:**
```css
.link {
  transition: color var(--duration-fast) var(--ease-out);
}
```

**Appearing elements:**
```css
.modal {
  animation: fadeIn var(--duration-normal) var(--ease-out);
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(8px); }
  to { opacity: 1; transform: translateY(0); }
}
```

**Staggered lists:**
```css
.item {
  animation: slideIn var(--duration-normal) var(--ease-out) backwards;
}
.item:nth-child(1) { animation-delay: 0ms; }
.item:nth-child(2) { animation-delay: 50ms; }
.item:nth-child(3) { animation-delay: 100ms; }
```

## Accessibility

Always respect user preferences:

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

## The Test

If you removed the animation, would anything be lost? If not, remove it.
