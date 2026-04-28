---
description: TypeScript-specific coding rules that extend the base model-agnostic guidelines, covering strict-mode conventions, tooling baseline, testing, and project structure.
mode: primary
model: openrouter/moonshotai/kimi-k2.6
temperature: 0.1
permission:
  edit: deny
  bash: deny
---

# Global Agent Rules (Model-Agnostic) — TypeScript Projects

These rules extend the base coding rules and apply to every opencode session on a TypeScript project.

## Language & Compiler

- Always target **TypeScript strict mode** (`"strict": true` in `tsconfig.json`).
- Never use `any`; prefer `unknown` and narrow with type guards when the type is truly dynamic.
- Prefer explicit return types on exported functions and class methods.
- Use `as const` for literal objects and arrays that must not be widened.
- Avoid non-null assertions (`!`); use optional chaining (`?.`) or explicit guards instead.
- Prefer `interface` over `type` alias for object shapes; use `type` for unions, intersections, and utility types.

## Tooling Baseline

| Tool | Command | Notes |
|------|---------|-------|
| Compile | `tsc --noEmit` | type-check only; no emit needed for checks |
| Lint | `eslint . --ext .ts,.tsx` | requires `@typescript-eslint` |
| Format | `prettier --check .` | fix with `--write` |
| Test | `vitest run` or `jest` | depend on project setup |
| Build | `tsc -p tsconfig.build.json` | or `tsup`, `esbuild`, `vite build` |

> Always run `tsc --noEmit` before declaring a change correct.

## Operating Principles

- Prefer tools + verification over guessing. Do not invent types, APIs, or command outputs.
- Keep changes minimal and in-scope. If you discover out-of-scope work, list it as "Follow-ups".
- If critical information is missing, ask 1–3 clarifying questions before editing.

## Standard Workflow (required)

1) **Plan** (3–7 bullets): identify files to inspect, types to update, risks.
2) **Execute**: search → read → edit → `tsc --noEmit` → diff review.
3) **Verify**: run `tsc --noEmit`, then lint/tests. Provide exact commands if you cannot run them.

## Coding Conventions

- **Imports**: use named imports; avoid default exports in library code.
- **Enums**: prefer `const enum` or an `as const` map for tree-shakeable builds.
- **Error handling**: use typed error classes (`class AppError extends Error`) rather than throwing raw strings.
- **Async**: always `await` or return promises explicitly; do not mix callbacks with async/await.
- **Generics**: constrain with `extends` wherever possible; avoid unconstrained `<T>`.
- **File naming**: `kebab-case.ts` for modules, `PascalCase.ts` for class/component files.

## Testing

- Co-locate unit tests next to source files: `foo.ts` → `foo.test.ts`.
- Integration/e2e tests go in a top-level `tests/` directory.
- Prefer `describe` + `it` blocks with clear descriptions.
- Mock only external I/O (network, file system, time); do not mock business logic.
- Assert on observable behavior, not internal implementation details.

## Project Structure (reference)

```
src/
  index.ts          # public entry point
  auth/             # example feature directory (replace with your feature name)
    index.ts        # barrel
    auth.ts         # implementation
    auth.test.ts
tests/              # integration / e2e
tsconfig.json
tsconfig.build.json # (optional) emit-only config
package.json
```

## Definition of Done

- All TypeScript errors resolved (`tsc --noEmit` exits 0).
- Lint passes with no new warnings.
- Relevant tests pass.
- Final response includes:
  - what changed + key files
  - how to verify (`tsc --noEmit`, test command)
  - any assumptions + follow-ups

## Output Format (use headings)

### Plan
### Changes
### Verification
### Notes / Follow-ups
