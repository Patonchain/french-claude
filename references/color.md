# Color

## The Truth

Most interfaces need very little color. A monochromatic base with one accent handles 90% of cases.

Color is meaning. Use it only when something needs to *mean*.

## The Palette

Start with neutrals. Build a scale:

```css
--gray-50: hsl(0 0% 98%);
--gray-100: hsl(0 0% 96%);
--gray-200: hsl(0 0% 90%);
--gray-300: hsl(0 0% 83%);
--gray-400: hsl(0 0% 64%);
--gray-500: hsl(0 0% 45%);
--gray-600: hsl(0 0% 32%);
--gray-700: hsl(0 0% 25%);
--gray-800: hsl(0 0% 15%);
--gray-900: hsl(0 0% 9%);
```

Add a subtle temperature. Pure gray is clinical:

```css
/* Warm gray */
--gray-500: hsl(30 5% 45%);

/* Cool gray */
--gray-500: hsl(220 5% 45%);
```

## Semantic Colors

Colors that mean something:

```css
--color-primary: hsl(220 80% 50%);   /* Actions, links, focus */
--color-success: hsl(145 60% 40%);   /* Confirmation, complete */
--color-warning: hsl(35 90% 50%);    /* Caution, attention */
--color-error: hsl(0 70% 50%);       /* Problems, destructive */
```

## Contrast

WCAG AA minimum:
- Normal text: 4.5:1 contrast ratio
- Large text (18px+): 3:1 contrast ratio
- UI components: 3:1 contrast ratio

Test your combinations. Always.

## Dark Mode

Do not invert. Redesign.

Dark backgrounds need:
- Reduced saturation
- Softer whites (not pure #fff)
- Adjusted hierarchy (what was light gray becomes dark gray)

```css
/* Light mode */
--text-primary: hsl(0 0% 9%);
--bg-primary: hsl(0 0% 100%);

/* Dark mode */
--text-primary: hsl(0 0% 90%);
--bg-primary: hsl(0 0% 9%);
```

## Practical Application

- **Text**: 2-3 tones (primary, secondary, muted)
- **Backgrounds**: 2-3 levels (base, elevated, sunken)
- **Borders**: Subtle, never heavy
- **Accent**: Sparingly, for emphasis

## The Mistake

Do not use color alone to convey meaning. Combine with icons, text, or patterns for accessibility.

## The Test

Remove all color. Convert to grayscale. Does the hierarchy still work? If not, your design depends too much on color.
