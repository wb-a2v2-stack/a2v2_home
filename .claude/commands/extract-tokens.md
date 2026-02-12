# Extract Design Tokens Command

You are converting the design tokens documented in `docs/design-analysis.md` into code. This bridges Phase 1 (Design Analysis) and Phase 3 (Build).

## Input
$ARGUMENTS — optional: specific token category to extract (colors, typography, spacing, all)

## Prerequisites
- `docs/design-analysis.md` MUST exist. If it doesn't, tell the engineer to run `/analyze-design` first.
- Read the Design Token Map section of the analysis doc before generating anything.

## Task
Generate the following files from the documented design tokens:

### 1. Tailwind Config Extension (`tailwind.config.ts`)
Extend the default Tailwind config with the exact token values from the design:
- Custom colors under `theme.extend.colors`
- Custom font families under `theme.extend.fontFamily`
- Custom font sizes with line-height under `theme.extend.fontSize`
- Custom spacing values under `theme.extend.spacing`
- Custom border radius under `theme.extend.borderRadius`
- Custom box shadows under `theme.extend.boxShadow`

### 2. CSS Variables (`src/styles/tokens.css`)
Generate CSS custom properties as a fallback and for use outside Tailwind:
```css
:root {
  /* Colors */
  --color-primary: #...;
  /* Typography */
  --font-family-heading: '...';
  /* Spacing */
  --space-1: 4px;
  /* etc. */
}
```

### 3. TypeScript Constants (`src/styles/tokens.ts`)
Export typed constants for programmatic use:
```typescript
export const colors = { ... } as const;
export const typography = { ... } as const;
export const spacing = { ... } as const;
```

## Rules
- Use EXACT values from the design analysis. Never approximate.
- If a value is missing from the analysis, flag it — do not guess.
- Name tokens semantically (e.g., `color-text-primary` not `color-gray-900`).
- Comment each token with its Figma source if known.
- After generation, list any tokens from the design that could NOT be mapped.

Remind the engineer: "Tokens generated. Every component from this point forward must reference these tokens — no hardcoded values."
