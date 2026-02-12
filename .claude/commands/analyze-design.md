# Design Analysis Command

You are performing Phase 1 of the Figma-to-React Engineering System. This is the highest-leverage time investment in the entire workflow. No code will be written until this analysis is complete.

## Input
The engineer will provide: $ARGUMENTS
This should be a Figma link, a Figma selection, or a description of the design to analyze.

## Your Task

Use the Figma MCP server to inspect the design. Then produce a comprehensive `design-analysis.md` file in the `docs/` directory covering ALL of the following sections.

### 1. Component Inventory
Identify every unique component visible in the design. Group them into categories:
- **Navigation**: Nav bars, breadcrumbs, tabs, sidebars
- **Layout**: Containers, grids, sections, dividers
- **Content**: Cards, lists, tables, media blocks
- **Forms**: Inputs, selects, checkboxes, radio buttons, toggles
- **Feedback**: Modals, toasts, alerts, tooltips, loading states
- **Actions**: Buttons, links, icon buttons, FABs

For each component, note:
- Name (use the Figma layer/component name if available)
- Variants visible in the design
- Whether it appears reusable or is a one-off

### 2. Design Token Map
Extract EXACT values from the Figma inspection. Do not approximate.

**Colors:**
- Primary, secondary, accent, background, surface, text colors
- State colors: success, warning, error, info
- Note hex values AND any opacity variations

**Typography:**
- Font family (check if it's a Google Font or custom)
- Each text style: name, size (px), weight, line-height, letter-spacing
- Heading scale (H1 through H6 if present)
- Body, caption, label, overline styles

**Spacing:**
- Padding values used (list unique values)
- Margin values used
- Gap values (from auto-layout)
- Identify the spacing scale if one is consistent (e.g., 4px, 8px, 12px, 16px, 24px, 32px, 48px)

**Other tokens:**
- Border radius values
- Shadow definitions (x, y, blur, spread, color)
- Border widths and colors
- Opacity values

### 3. Interactive State Matrix
For EVERY interactive component, document which states are present in the design:

| Component | Default | Hover | Active | Focus | Disabled | Loading | Error | Empty |
|-----------|---------|-------|--------|-------|----------|---------|-------|-------|

Mark each as: ✅ (designed), ❓ (not in design — needs designer clarification), or ➖ (not applicable).

**CRITICAL**: If states are missing, list them explicitly as open questions. Do NOT invent states that aren't in the design.

### 4. Responsive Behavior
- List all breakpoints visible in the design (mobile, tablet, desktop frames)
- For each breakpoint, note how the layout changes:
  - Column count changes
  - Components that hide/show
  - Typography scale changes
  - Navigation pattern changes (e.g., hamburger menu on mobile)
- If no responsive frames exist, flag this as: "⚠️ No responsive designs provided. Clarification needed from designer."

### 5. Asset Inventory
- Icons: List each unique icon, note if they should be SVG or icon library
- Images: List placeholder images, note if they need specific aspect ratios
- Illustrations/graphics: Note any custom artwork
- Logos: Note variations (full, mark, monochrome)

### 6. Open Questions for Designer
List anything that is ambiguous, missing, or needs clarification before development can begin. Common questions include:
- Missing interactive states
- Unclear responsive behavior
- Animations or transitions not specified
- Edge cases (long text, empty states, error states)
- Accessibility requirements not visible in the design

## Output Format
Save the analysis as `docs/design-analysis.md` with clear markdown headings for each section.

After creating the file, provide a brief summary to the engineer:
- Total unique components identified
- Number of design tokens extracted
- Number of open questions that need designer input
- Recommended build order based on dependencies

Remind the engineer: "Phase 1 complete. Do NOT proceed to code generation until open questions are resolved with the designer. Next step: Phase 2 — Architecture Planning."
