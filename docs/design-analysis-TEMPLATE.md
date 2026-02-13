# Design Analysis: [Feature/Page Name]

> **Status**: 🔴 Not Started | 🟡 In Progress | 🟢 Complete
> **Figma Link**: [paste link here]
> **Analyst**: [engineer name]
> **Date**: [date]

---

## 1. Component Inventory

### Navigation
| Component | Figma Name | Variants | Reusable? |
|-----------|-----------|----------|-----------|
| _example_ | _NavBar_  | _desktop, mobile_ | _Yes_ |

### Layout
| Component | Figma Name | Variants | Reusable? |
|-----------|-----------|----------|-----------|

### Content
| Component | Figma Name | Variants | Reusable? |
|-----------|-----------|----------|-----------|

### Forms
| Component | Figma Name | Variants | Reusable? |
|-----------|-----------|----------|-----------|

### Feedback
| Component | Figma Name | Variants | Reusable? |
|-----------|-----------|----------|-----------|

### Actions
| Component | Figma Name | Variants | Reusable? |
|-----------|-----------|----------|-----------|

---

## 2. Design Token Map

### Colors
| Token Name | Hex | Usage |
|------------|-----|-------|
| _primary_ | _#0F3460_ | _Buttons, links_ |

### Typography
| Style Name | Font | Weight | Size | Line Height | Letter Spacing |
|------------|------|--------|------|-------------|----------------|
| _heading-1_ | _Inter_ | _700_ | _32px_ | _40px_ | _-0.02em_ |

### Spacing Scale
| Token | Value |
|-------|-------|
| _space-1_ | _4px_ |

### Borders & Shadows
| Token | Value |
|-------|-------|
| _radius-sm_ | _4px_ |
| _shadow-card_ | _0 2px 8px rgba(0,0,0,0.08)_ |

---

## 3. Interactive State Matrix

| Component | Default | Hover | Active | Focus | Disabled | Loading | Error | Empty |
|-----------|---------|-------|--------|-------|----------|---------|-------|-------|
| _Button_  | ✅ | ✅ | ❓ | ❓ | ✅ | ➖ | ➖ | ➖ |

**Legend**: ✅ Designed | ❓ Missing — needs designer input | ➖ Not applicable

---

## 4. Responsive Behavior

### Breakpoints Found
- [ ] Mobile (375px)
- [ ] Tablet (768px)
- [ ] Desktop (1024px)
- [ ] Large Desktop (1440px)

### Layout Changes
| Breakpoint | Changes |
|------------|---------|
| _Mobile_ | _Single column, hamburger nav, stacked cards_ |

> ⚠️ If no responsive frames exist: "No responsive designs provided. Clarification needed from designer before development."

---

## 5. Asset Inventory

### Icons
| Icon | Source | Format |
|------|--------|--------|
| _search_ | _Lucide_ | _SVG_ |

### Images
| Image | Aspect Ratio | Notes |
|-------|-------------|-------|

---

## 6. Open Questions for Designer

1. _[Example: Hover state for card component is not specified — what should happen?]_
2. _[Example: Mobile layout not provided — should we follow standard responsive patterns?]_
3. _[Example: Loading state for form submission not shown — spinner, skeleton, or disabled?]_

---

## Summary

- **Total unique components**: _X_
- **Design tokens extracted**: _X_
- **Open questions**: _X_ ⚠️
- **Recommended build order**: _[tokens → atoms → composed → layout → page]_

> ✅ Phase 1 complete. Do NOT proceed to code generation until open questions above are resolved with the designer.
