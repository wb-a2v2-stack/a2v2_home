# Figma-to-React Engineering System

## About This Project
This is a React front-end project that follows a structured 5-phase workflow for converting Figma designs into production-ready code. Every engineer must follow this system.

## The 5 Phases (NEVER skip a phase)
1. **Design Analysis** (30-60 min) — Inspect Figma, document tokens, components, states
2. **Architecture** — Plan component tree, file structure, state management
3. **AI-Assisted Build** — Generate code from specs using Claude Code + Figma MCP
4. **QA & Polish** — Pixel-perfect verification, accessibility, performance
5. **Review & Ship** — PR with Figma link, screenshots, deviation notes

## Critical Rule
**Phase 1 must be completed before ANY code generation.** If no `design-analysis.md` exists in `docs/` for the current task, stop and create one first using the `/analyze-design` command.

## Tech Stack
- React 18+ with TypeScript (strict mode)
- Tailwind CSS for styling
- Component library: shadcn/ui (when applicable)
- Build tool: Vite
- Testing: Vitest + React Testing Library
- Linting: ESLint + Prettier

## Figma MCP Integration
This project uses the Figma MCP server for design context. Two methods:
- **Selection-based**: Select a frame in Figma desktop, then prompt Claude Code
- **Link-based**: Paste a Figma frame URL into your prompt

Always extract design tokens BEFORE generating components.

## File Structure
```
src/
  components/
    ui/           # Atomic primitives (Button, Input, Badge, Avatar, Icon)
    [feature]/    # Feature-specific composed components
  layouts/        # Page-level wrappers (Sidebar, TopNav, ContentArea)
  pages/          # Route-level page components
  hooks/          # Custom hooks
  lib/            # Utilities, constants, helpers
  styles/         # Global tokens, theme config, CSS variables
  types/          # TypeScript type definitions
docs/
  design-analysis.md   # Current task design analysis (Phase 1 output)
  component-inventory/ # Per-feature component breakdowns
```

## Code Standards
- One component per file. Named export matches filename.
- All props must have TypeScript interfaces. No `any`.
- Co-locate styles with components (Tailwind classes or CSS Modules).
- Every interactive element must be keyboard accessible.
- All images must have meaningful alt text or aria-hidden.
- Never hardcode colors, spacing, or typography. Use design tokens.

## Component Build Order (ALWAYS follow this sequence)
1. Design tokens → CSS variables or Tailwind config extension
2. Atomic components → Button, Input, Typography, Icon wrappers
3. Composed components → Card, ListItem, FormGroup
4. Layout components → Sidebar, PageShell, Header
5. Page assembly → Combine layouts and composed components

## Prompt Engineering Rules for Figma-to-Code
When generating components from Figma designs, every prompt MUST include:
1. Reference to the design analysis doc or specific token values
2. Component name, props interface, and all interactive states
3. Tech stack context (React + TypeScript + Tailwind)
4. Example of an existing component if one has been built (for pattern matching)
5. Accessibility and responsive requirements

## Common Commands
```bash
npm run dev          # Start dev server
npm run build        # Production build
npm run test         # Run tests
npm run lint         # Lint check
npm run format       # Prettier format
```

## What Claude Code Should NOT Do
- Never generate entire pages in a single prompt. Build atoms first, compose upward.
- Never skip design analysis. If you don't have token values, stop and extract them.
- Never blindly regenerate. If a component is 80% correct, fix the specific issues.
- Never hardcode values that should come from the design system.
- Never generate security-critical code (auth, data validation) without human review.
