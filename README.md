# Figma-to-React Engineering System — Project Setup

## Prerequisites

1. **Claude Code** installed globally:
   ```bash
   npm install -g @anthropic-ai/claude-code
   ```
   Requires a Claude Pro, Claude Max subscription, or Anthropic API key.

2. **Figma account** with a Dev or Full seat (required for MCP server access).

3. **Node.js 18+** and npm installed.

---

## Quick Start

### Step 1: Connect Figma MCP Server

You have two options:

**Option A — Remote server (recommended, works with browser Figma):**
```bash
claude mcp add --transport http figma https://mcp.figma.com/mcp
```
Then type `/mcp` in Claude Code, select `figma`, and authenticate.

**Option B — Desktop server (requires Figma desktop app):**
1. Open Figma desktop app → Menu → Preferences → Enable Dev Mode MCP Server
2. The `.mcp.json` in this repo is already configured for the desktop server at `http://127.0.0.1:3845/mcp`

### Step 2: Verify Connection
```bash
cd figma-to-react-project
claude
```
Inside Claude Code, type:
```
/mcp
```
You should see `figma` listed as connected with available tools.

### Step 3: Initialize the Project
```bash
npm install
```

---

## The Workflow (Every Task, Every Time)

### Phase 1: Design Analysis (30-60 minutes)
```
/analyze-design [paste Figma link or select a frame in Figma desktop]
```
This creates `docs/design-analysis.md` with component inventory, token map, state matrix, responsive behavior, and open questions.

**⛔ You cannot skip this phase. No code generation happens without a completed design analysis.**

### Phase 2: Architecture Planning
```
/plan-architecture [feature name]
```
Creates `docs/architecture-plan.md` with component tree, build order, and state management plan.

### Phase 3: Build (AI-Assisted)
```
/extract-tokens
```
Generates design token files from the analysis. Then build components following the order in your architecture plan — atoms first, compose upward.

### Phase 4: QA & Polish
```
/qa-check src/components/[component-file]
```
Runs the full QA checklist against the design analysis. Fix any ❌ items before proceeding.

### Phase 5: Review & Ship
Create your PR with:
- Screenshot of implementation next to Figma design
- Link to the Figma frame
- Note any deviations from design and why
- Confirm Phase 4 QA checklist passed

---

## Project Structure

```
.
├── CLAUDE.md                          # Claude Code project memory (auto-loaded every session)
├── .mcp.json                          # Figma MCP server configuration
├── .claude/
│   ├── settings.json                  # Hooks, permissions, environment
│   └── commands/
│       ├── analyze-design.md          # /analyze-design — Phase 1
│       ├── plan-architecture.md       # /plan-architecture — Phase 2
│       ├── extract-tokens.md          # /extract-tokens — Phase 2→3 bridge
│       └── qa-check.md               # /qa-check — Phase 4
├── docs/
│   ├── design-analysis-TEMPLATE.md    # Reference template
│   ├── design-analysis.md            # Current task analysis (generated)
│   └── architecture-plan.md          # Current task architecture (generated)
└── src/
    ├── components/
    │   ├── ui/                        # Atomic primitives
    │   └── [feature]/                 # Feature-specific components
    ├── layouts/                       # Page-level layouts
    ├── pages/                         # Route-level pages
    ├── hooks/                         # Custom hooks
    ├── lib/                           # Utilities
    ├── styles/
    │   ├── tokens.css                 # CSS custom properties (generated)
    │   └── tokens.ts                  # TypeScript token constants (generated)
    └── types/                         # TypeScript definitions
```

---

## Custom Slash Commands Reference

| Command | Phase | What It Does |
|---------|-------|-------------|
| `/analyze-design [figma-link]` | 1 | Full design analysis → `docs/design-analysis.md` |
| `/plan-architecture [feature]` | 2 | Architecture plan → `docs/architecture-plan.md` |
| `/extract-tokens` | 2→3 | Converts tokens to Tailwind config + CSS vars + TS constants |
| `/qa-check [filepath]` | 4 | Runs QA checklist against design analysis |

---

## Rules for the Team

1. **Never write code before completing Phase 1.** The 30-60 minutes of design analysis prevents hours of rework.
2. **Never paste a Figma link and say "build this."** That's vibe coding, not engineering.
3. **Never skip the state matrix.** Missing hover/error/loading states are the #1 source of rework.
4. **Never hardcode values.** If it's a color, size, spacing, or shadow — it comes from tokens.
5. **Always build atoms first.** The Button component built in the first hour gets reused 50 times.
6. **Always review AI-generated code line by line.** Claude Code is a pair programmer, not an autopilot.
7. **Always include Figma links in PRs.** Reviewers need to verify design fidelity.
