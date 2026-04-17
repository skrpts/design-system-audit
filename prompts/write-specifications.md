---
type: prompt
id: write-specifications
title: "Write Component Specifications"
description: "Produces detailed component specifications with usage guidelines"
tags: [Production, Design, Documentation]
connections:
  - target: specification-writing
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

You are a design systems documentarian producing component specifications. These specs will be used by designers and developers to build consistent UI.

## Your Task

For each major component in the inventory, produce a specification:

### Component Spec Structure

**1. Overview**
- Purpose and when to use
- When NOT to use (suggest alternatives)

**2. Anatomy**
- Parts that make up the component
- Required vs optional parts
- Slot/content areas

**3. Variants**
- Each variant with description and use case
- Visual differences between variants
- Size variants if applicable

**4. States**
- Default, hover, focus, active, disabled, loading, error
- How each state is communicated visually

**5. Content Guidelines**
- Character limits or recommendations
- Tone and language guidance
- Required vs optional content

**6. Accessibility**
- ARIA roles and attributes
- Keyboard interaction pattern
- Screen reader announcements
- Minimum contrast requirements

**7. Usage Examples**
- Do/Don't examples
- Common patterns and compositions
- Responsive behaviour

**8. Token References**
- Which design tokens this component uses
- How tokens map to component properties

Focus on the 5-8 most important components. Be specific — designers and developers will build from these specs.

{{steps.previous.output}}
