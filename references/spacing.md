# Spacing

## The Philosophy

Whitespace is not empty. It is structure. It is meaning. It is the silence between notes that makes music.

## The System

Use a base unit. Everything derives from it.

```css
--space-unit: 0.25rem; /* 4px at default */

--space-1: calc(var(--space-unit) * 1);   /* 4px - hairline */
--space-2: calc(var(--space-unit) * 2);   /* 8px - tight */
--space-3: calc(var(--space-unit) * 3);   /* 12px - compact */
--space-4: calc(var(--space-unit) * 4);   /* 16px - base */
--space-6: calc(var(--space-unit) * 6);   /* 24px - comfortable */
--space-8: calc(var(--space-unit) * 8);   /* 32px - spacious */
--space-12: calc(var(--space-unit) * 12); /* 48px - section */
--space-16: calc(var(--space-unit) * 16); /* 64px - major break */
--space-24: calc(var(--space-unit) * 24); /* 96px - hero */
```

## Proximity

Elements that are related should be close. Elements that are separate should be distant.

The space *between* groups should always exceed the space *within* groups. This is non-negotiable.

## Rhythm

Vertical rhythm creates scannability:
- Consistent spacing between similar elements
- Larger gaps signal new sections
- Smaller gaps signal continuation

```css
/* Cards in a grid */
gap: var(--space-6);

/* Items within a card */
gap: var(--space-3);

/* Sections on a page */
margin-block: var(--space-16);
```

## Padding vs Margin

- Padding: Internal breathing room
- Margin: External relationships

Containers have padding. Elements have margin (or use gap).

## Touch Targets

Minimum 44x44px for interactive elements. This is accessibility, not preference.

```css
.button {
  min-height: 44px;
  padding-inline: var(--space-4);
}
```

## The Feel

- Too tight: Cramped, anxious, cheap
- Too loose: Disconnected, empty, lost
- Just right: Calm, confident, premium

When in doubt, add more space. Density is rarely the answer.
