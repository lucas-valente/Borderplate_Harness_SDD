---
description: "Use for all frontend changes. Requires the frontend-guidance skill as mandatory UX/UI baseline for layout, controls, hierarchy, and responsive quality."
applyTo: "frontend/**, web/**, app/**, src/**/*.tsx, src/**/*.jsx, src/**/*.vue, src/**/*.svelte, src/**/*.css, src/**/*.scss"
---

# Frontend Guidance Enforcement

For any matched frontend change:

1. Read `.github/skills/frontend-guidance/SKILL.md` before coding.
2. Apply the guidance as default, unless the user explicitly requests another direction.
3. Preserve the existing design system first when it conflicts with generic UI patterns.
4. Validate desktop and mobile behavior (text fit, spacing, non-overlap, stable layout).
5. If a dev server is needed for runtime verification, run it and report the URL.
