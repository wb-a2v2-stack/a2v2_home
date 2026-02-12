# Architecture Planning Command

You are performing Phase 2 of the Figma-to-React Engineering System. The design has been analyzed. Now plan the technical implementation before generating any code.

## Input
$ARGUMENTS — optional: specific page or feature to plan architecture for

## Prerequisites
- `docs/design-analysis.md` MUST exist. If it doesn't, tell the engineer to run `/analyze-design` first.
- All open questions from the design analysis should be resolved before architecture planning.

## Task
Read the design analysis and produce an architecture plan.

### 1. Component Tree
Map every component from the inventory to a React component. Define:
- File path (following the project's file structure standard)
- Props interface (name and types)
- Children/composition relationships
- Which components are shared atoms vs. feature-specific

### 2. Build Dependency Order
Determine the order components must be built in based on dependencies:
```
Layer 1 (no deps): Button, Input, Badge, Avatar, Icon
Layer 2 (uses Layer 1): Card, FormGroup, ListItem
Layer 3 (uses Layer 2): Sidebar, Header, ContentArea
Layer 4 (uses Layer 3): DashboardPage, SettingsPage
```

### 3. State Management Plan
For each component that needs state:
- Local state: What's managed with useState/useReducer
- Shared state: What crosses component boundaries (Context, Zustand, etc.)
- Server state: What comes from APIs (data shapes as TypeScript interfaces)

### 4. Route Map (if applicable)
Define routes and which page components they render.

### 5. Estimated Build Sequence
Provide a numbered list of what the engineer should build in what order, with estimated complexity (S/M/L) for each.

## Output
Save as `docs/architecture-plan.md`.

Remind the engineer: "Architecture planned. Begin Phase 3 by running `/extract-tokens` to generate the design token files, then build Layer 1 components first."
