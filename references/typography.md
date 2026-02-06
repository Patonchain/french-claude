# Typography

## The Foundation

Typography is not choosing fonts. Typography is giving language a visual voice.

## Hierarchy

You need exactly 3-4 levels of hierarchy. More than that and you have not understood your content.

```
Level 1: Display / Hero - The thing you cannot miss
Level 2: Headings - Section breaks, scannable anchors
Level 3: Body - The reading experience
Level 4: Supporting - Captions, labels, metadata
```

## Scale

Use a mathematical scale. The eye recognizes harmony.

```css
/* Major Third (1.25) - Calm, readable */
--text-xs: 0.64rem;
--text-sm: 0.8rem;
--text-base: 1rem;
--text-lg: 1.25rem;
--text-xl: 1.563rem;
--text-2xl: 1.953rem;
--text-3xl: 2.441rem;
--text-4xl: 3.052rem;
```

## Line Height

- Headings: 1.1 - 1.2 (tight, impactful)
- Body: 1.5 - 1.6 (readable, breathing)
- Small text: 1.6 - 1.7 (needs more air)

## Line Length

45-75 characters per line. This is not a suggestion. Beyond this, the eye loses its place.

```css
max-width: 65ch; /* The sweet spot */
```

## Font Pairing

One font family is often enough. If you pair:
- Contrast in structure (serif + sans)
- Harmony in character (same era, same spirit)
- Never pair fonts that are too similar

## Weight and Emphasis

**Bold** is for emphasis within text. Overuse destroys meaning.

Use weight to create hierarchy between elements, not within paragraphs.

Regular (400) and Semibold (600) handle most interfaces. You rarely need more.

## The Details

- Letter-spacing: Loosen uppercase, tighten large headings
- Hanging punctuation: Align the text, not the quotes
- Proper quotes: "These" not "these"
- Figures: Tabular for data, proportional for prose
