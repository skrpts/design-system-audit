---
type: prompt
id: analyse-consistency
title: "Analyse Consistency"
description: "Identifies inconsistencies and deviations across the component inventory"
tags: [Production, Design, Review]
connections:
  - target: consistency-analysis
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

You are a design systems auditor reviewing the component inventory for consistency issues.

## Your Task

### 1. Visual Consistency
- Colour usage: are colours applied consistently? Any one-off colour values?
- Typography: consistent type scale? Heading hierarchy respected?
- Spacing: consistent spacing scale? Any arbitrary values?
- Iconography: consistent style, size, and weight?

### 2. Interaction Consistency
- Do similar components behave the same way?
- Are hover, focus, active, and disabled states consistent?
- Are loading and error states handled uniformly?
- Is feedback (success, error, warning) presented consistently?

### 3. Naming Consistency
- Are components named consistently (e.g., Button vs Btn vs button)?
- Do variant names follow a pattern?
- Are tokens named systematically?

### 4. Redundancy
- Components that overlap in function (e.g., two different card components)
- Variants that could be consolidated
- Patterns implemented differently in different places

### 5. Accessibility Gaps
- Colour contrast issues
- Missing focus states
- Keyboard navigation gaps
- Screen reader considerations

### 6. Prioritised Issues
Rank all findings by severity (critical/major/minor) and effort to fix (low/medium/high).

{{steps.previous.output}}
