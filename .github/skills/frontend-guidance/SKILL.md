---
name: frontend-guidance
description: "Global frontend guidance for UI/UX work. Use for pages, components, layouts, styling, interactions, dashboards, and responsive behavior."
---

# Frontend Guidance

Default guidance for frontend work in this boilerplate.

## Core Principle

Respect existing product language first. Improve clarity, usability, and consistency without breaking established patterns.

## UX Baseline

- prioritize user tasks over decorative layout;
- keep visual hierarchy clear;
- keep interactions predictable;
- ensure keyboard + pointer usability;
- include loading, empty, error, and success states.

## Layout And Visual Rules

- avoid nested card-inside-card composition unless design system requires;
- use spacing scale consistently;
- keep text readable and non-overlapping on mobile and desktop;
- use stable component dimensions for controls/grids/tables when dynamic data may shift layout;
- preserve brand and design-token conventions when they exist.

## Control Rules

- use the right control for the job (toggle, checkbox, segmented control, select, tabs, slider, stepper);
- use icon buttons only when icon meaning is obvious, otherwise add labels/tooltips;
- keep forms explicit and validation messages actionable.

## Accessibility Baseline

- ensure contrast is sufficient;
- ensure focus states are visible;
- ensure labels and aria text exist for interactive controls;
- ensure text can wrap without clipping.

## Responsive Validation

Check at minimum:

- small mobile viewport;
- standard tablet viewport;
- desktop viewport.

Validate:

- no overlap;
- no hidden critical actions;
- no broken navigation flow.

## Runtime Rule

If the frontend requires a dev server, run it and provide the URL for review/QA.
