---
name: merge
description: "Validate builds and run the merge trail (develop -> staging -> main) with declarative commit messages."
---

Validate the builds for all apps in the project using `npm run build` (or the project's build command). If all builds pass, run the merge trail `develop -> staging -> main` with declarative non-generic messages.

Use the develop commit message as the base, and prefix merges with `merge: <same message as develop commit>`.

Example:
- develop commit: `feat: add barbeiro filter to agenda`
- staging merge: `merge: feat: add barbeiro filter to agenda`
- main merge: `merge: feat: add barbeiro filter to agenda`
