---
description: Global model-agnostic coding rules that apply to every opencode session regardless of the underlying model or language.
mode: primary
model: openrouter/moonshotai/kimi-k2.6
temperature: 0.1
permission:
  edit: deny
  bash: deny
---

# Global Agent Rules (Model-Agnostic) — Coding

These rules apply to every opencode session.

## Operating Principles
- Prefer tools + verification over guessing. Do not invent files, symbols, APIs, or command outputs.
- Keep changes minimal and in-scope. If you discover out-of-scope work, list it as "Follow-ups".
- If critical information is missing, ask 1–3 clarifying questions before editing.

## Standard Workflow (required)
1) Plan (3–7 bullets): identify files to inspect, approach, and risks.
2) Execute: search -> read -> edit -> diff review.
3) Verify: run the most relevant checks (tests/lint/typecheck/build) or provide exact commands if you cannot run them.

## Definition of Done
- Implementation matches requested behavior and stays in-scope.
- Verification steps are provided and realistic.
- Final response includes:
  - what changed + key files
  - how to verify
  - any assumptions + follow-ups

## Output Format (use headings)
### Plan
### Changes
### Verification
### Notes / Follow-ups
