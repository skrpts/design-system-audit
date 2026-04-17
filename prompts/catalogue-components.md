---
type: prompt
id: catalogue-components
title: "Catalogue Components"
description: "Catalogues existing design components from the user's description"
tags: [Production, Design, Audit]
connections:
  - target: component-inventory
    type: derived_from
inputs:
  system_description:
    label: "System Description"
    description: "Describe your current design system — components, patterns, and how they are used"
    example: "We have a React component library with buttons (3 variants), form inputs, cards, modals, navigation bar, and a data table. Styles are in Tailwind with some custom CSS overrides."
    required: true
    type: text
  brand_guidelines:
    label: "Brand Guidelines"
    description: "Brand colours, typography, and design principles if available"
    example: "Primary: #2563EB, Secondary: #10B981, Font: Inter for UI, Merriweather for headings"
    required: false
    type: text
  platforms:
    label: "Platforms"
    description: "Target platforms — web, mobile, both"
    example: "Web and iOS"
    required: false
    type: text
---

You are a design systems specialist conducting a component inventory. Catalogue every design component described.

## System Description
{{input.system_description}}

## Brand Guidelines
{{input.brand_guidelines}}

## Platforms
{{input.platforms}}

## Your Task

### 1. Component Catalogue
For each component identified:
- **Name** and category (navigation, input, feedback, layout, data display)
- **Variants** — all known variations (size, colour, state)
- **Usage context** — where and when it's used
- **Dependencies** — other components it relies on or contains
- **Platform availability** — which platforms have this component

### 2. Pattern Inventory
- Recurring layout patterns (page templates, grid systems)
- Interaction patterns (how users navigate, submit forms, receive feedback)
- Content patterns (how text, images, and data are presented)

### 3. Token Inventory
Document existing design tokens observed:
- Colours (primary, secondary, semantic, neutrals)
- Typography (families, sizes, weights, line heights)
- Spacing (scale, padding, margins)
- Border radius, shadows, transitions

### 4. Gap Analysis
- Components that seem to be missing for common use cases
- Variants that exist informally but aren't formalised
- Platform inconsistencies
