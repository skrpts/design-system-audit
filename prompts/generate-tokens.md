---
type: prompt
id: generate-tokens
title: "Generate Design Tokens"
description: "Generates a formalised design token system from the audit findings"
tags: [Production, Design, Generation]
connections:
  - target: token-generation
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

You are a design systems architect generating a formalised design token system based on the audit.

## Your Task

### 1. Colour Tokens
- **Primitive colours:** base palette with names (blue-500, gray-100, etc.)
- **Semantic colours:** purpose-based aliases (primary, secondary, success, error, warning, info)
- **Component colours:** background, text, border for key component states
- Ensure WCAG AA contrast ratios for all text/background combinations

### 2. Typography Tokens
- **Font families:** display, body, mono
- **Font sizes:** scale (xs through 4xl with px and rem values)
- **Font weights:** light, regular, medium, semibold, bold
- **Line heights:** tight, normal, relaxed
- **Letter spacing:** tighter, normal, wider

### 3. Spacing Tokens
- **Base unit** and scale (e.g., 4px base: 0, 1, 2, 3, 4, 5, 6, 8, 10, 12, 16, 20, 24)
- Named semantic spacing (compact, default, comfortable)

### 4. Other Tokens
- Border radius: none, sm, md, lg, full
- Shadows: sm, md, lg, xl
- Transitions: duration and easing curves
- Breakpoints: sm, md, lg, xl, 2xl
- Z-index scale

### 5. Token Format
Output tokens in a format ready for implementation:
```
colour.primary.default: #2563EB
colour.primary.hover: #1D4ED8
spacing.4: 16px
...
```

{{steps.previous.output}}
