# QA & Polish Check Command

You are performing Phase 4 of the Figma-to-React Engineering System.

## Input
$ARGUMENTS — the component or page file path to QA check

## Task
Read the component code AND the design analysis, then evaluate against every item below.

### Design Fidelity
- [ ] Spacing values (padding, margin, gap) match design within 2px
- [ ] Typography matches: font family, weight, size, line-height, letter-spacing, color
- [ ] Colors match exactly (use design tokens, no hardcoded hex)
- [ ] Border radius, shadows, and opacity match
- [ ] All interactive states implemented: hover, focus, active, disabled, loading, error, empty
- [ ] Responsive behavior matches design at 375px, 768px, 1024px, 1440px

### Accessibility
- [ ] All interactive elements keyboard accessible (Tab, Enter, Escape, Arrows)
- [ ] Visible focus indicators with sufficient contrast
- [ ] Images have alt text or aria-hidden
- [ ] Form inputs have associated labels
- [ ] Color is not the sole means of conveying information
- [ ] ARIA roles and attributes where needed

### Code Quality
- [ ] TypeScript strict: no `any`, all props typed
- [ ] No hardcoded values (uses design tokens)
- [ ] Component is properly exported and named
- [ ] No unused imports or variables
- [ ] Follows project file structure convention

### Performance
- [ ] No unnecessary re-renders (check dependency arrays)
- [ ] Images optimized and lazy loaded where appropriate
- [ ] No unused dependencies imported

## Output
Produce a QA report listing:
- ✅ Items that pass
- ❌ Items that fail with specific details on what needs fixing
- Total score: X/Y checks passed

If any ❌ items exist, do NOT mark Phase 4 as complete. List the fixes needed.
