---
type: workflow
id: design-system-audit
title: Design System Audit
description: "Audit existing components, identify inconsistencies, generate design tokens, and produce component specifications"
tags: [Production, Customer-Facing, Design, Audit, Documentation]
connections:
  - target: component-inventory
    type: uses
  - target: consistency-analysis
    type: uses
  - target: token-generation
    type: uses
  - target: specification-writing
    type: uses
  - target: language-polish
    type: uses
  - target: consistency-check
    type: uses
  - target: llm-service
    type: runs_on
metadata:
  estimated_duration: "15-25 minutes"
  trigger: manual
output_step: "language-polish"
composite_steps:
  - "component-inventory"
  - "consistency-analysis"
  - "token-generation"
  - "specification-writing"
  - "language-polish"
  - "consistency-check"
execution:
  - skill: "component-inventory"
    prompt: "catalogue-components"
    step_type: "synthesis"
  - skill: "consistency-analysis"
    prompt: "analyse-consistency"
    step_type: "review"
  - skill: "token-generation"
    prompt: "generate-tokens"
    step_type: "generation"
  - skill: "specification-writing"
    prompt: "write-specifications"
    step_type: "generation"
  - skill: "language-polish"
    prompt: "polish-language"
    step_type: "content"
    context:
      voice_profile: ""
      grammar_strictness: ""
  - parallel:
    - skill: "consistency-check"
      prompt: "check-consistency"
      step_type: "review"
      context:
        voice_profile: ""
        consistency_strictness: ""
---

## Overview

This workflow audits an existing design system — cataloguing components, identifying inconsistencies, generating a formalised token system, and producing component specifications. The output is a comprehensive audit report with actionable improvements and implementation-ready specs.

## Pipeline Stages

### Stage 1: Component Inventory

**Input:** System description, brand guidelines, target platforms

Invoke the **component-inventory** skill to catalogue all design components, patterns, and existing tokens.

**Output:** Complete component catalogue with variants, usage contexts, and gap analysis.

### Stage 2: Consistency Analysis

**Input:** Component inventory from Stage 1

Invoke the **consistency-analysis** skill to identify visual, interaction, naming, and accessibility inconsistencies across the system.

**Output:** Prioritised consistency issues ranked by severity and effort.

### Stage 3: Token Generation

**Input:** Audit findings from Stages 1-2

Invoke the **token-generation** skill to produce a formalised design token system covering colours, typography, spacing, and other primitives.

**Output:** Complete token specification ready for implementation.

### Stage 4: Component Specifications

**Input:** Tokens and audit findings

Invoke the **specification-writing** skill to produce detailed specs for the 5-8 most important components.

**Output:** Component specifications with anatomy, states, variants, accessibility, and usage guidelines.

### Stage 5: Language Polish

Invoke **language-polish** for final cleanup.

### Stage 6: Consistency Check (Parallel)

Invoke **consistency-check** to verify token references and terminology are consistent across all specs.

## Error Handling

- If the system description is brief, the inventory focuses on what's described and flags gaps
- If no brand guidelines are provided, tokens are generated from the described components
- If platform information is missing, specifications default to web

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.system_description}}` | Yes | Your current design system | `React component library with buttons, forms, cards, modals...` |
| `{{input.brand_guidelines}}` | No | Brand colours, typography, principles | `Primary: #2563EB, Font: Inter` |
| `{{input.platforms}}` | No | Target platforms | `Web and iOS` |

## Outputs

| Name | Description |
|------|-------------|
| Component inventory | Complete catalogue with variants and gap analysis |
| Consistency audit | Prioritised issues by severity |
| Design tokens | Formalised token system for colours, typography, spacing |
| Component specifications | Detailed specs for major components |

## Setup

1. No external services required — describe your design system as input.
2. Include as much detail as possible about existing components, variants, and usage.
3. Brand guidelines improve token generation accuracy.

## Provider Notes

- Stronger models produce more nuanced consistency analysis and better specification writing.
- Token generation works well on most capable models.

## Example Input

```
System Description: "We have a React component library built with Tailwind CSS. Components: Button (primary, secondary, ghost — each in sm, md, lg), TextInput, TextArea, Select, Checkbox, Radio, Card (default, elevated, outlined), Modal, Toast notifications, Navigation bar with dropdown menus, Breadcrumbs, Pagination, Data table with sorting and filtering, Badge, Avatar, Tooltip. Some components use custom CSS overrides that don't follow the Tailwind config. The table component was built by a different team and looks slightly different from everything else."
Brand Guidelines: "Primary: #2563EB (blue), Secondary: #10B981 (green), Error: #EF4444, Warning: #F59E0B. Font: Inter for everything. Base size 14px in the app, 16px on marketing pages."
Platforms: "Web (React) — mobile web is responsive, no native apps yet"
```
