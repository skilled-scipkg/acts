---
name: acts-pages
description: This skill should be used when users ask about pages in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Pages

## High-Signal Playbook
### Route conditions
- Use this skill for repo status pages (`bugs`, `deprecated`, `todo`) and repo-wide diagnostics policy questions.
- Route subsystem debugging to the owning domain skill once the affected component is clear.

### Triage questions
- Is the request about a deprecated API, a documented bug, or an open TODO?
- Do you need a replacement API path or only the current status?
- Is this a docs-only issue, or do you need to inspect runtime diagnostics/error helpers in code?

### Canonical workflow
1. Open the exact page first: `docs/pages/bugs.md`, `docs/pages/deprecated.md`, or `docs/pages/todo.md`.
2. Extract the affected subsystem and any replacement guidance.
3. If runtime behavior matters, inspect `references/source_map.md` for diagnostics/error helpers.
4. Hand off to the owning skill once the concrete subsystem is known.

### Pitfalls and fixes
- `docs/pages/todo.md` is backlog context, not an implementation guarantee.
- Deprecated APIs may still compile; prefer the documented replacement path before editing code.
- Bug pages scope the subsystem but rarely give the root cause by themselves.

### Convergence/validation checks
- The answer states whether the item is backlog, deprecation, or a confirmed bug note.
- Any replacement or diagnostic link points to a current repo file.
- Runtime debugging is handed off to the right domain skill when needed.

## Scope
- Handle questions about documentation grouped under the 'pages' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/pages/todo.md`
- `docs/pages/deprecated.md`
- `docs/pages/bugs.md`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use tutorials/examples as executable usage patterns when available.
- Use tests as behavior or regression references when available.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

## Tutorials and examples
- `Examples`
- `Python/Examples`

## Test references
- `Tests`
- `Python/Core/tests`
- `Python/Examples/tests`
- `Python/Fatras/tests`

## Optional deeper inspection
- `Alignment`
- `Core`
- `Fatras`
- `Plugins`
- `Python`
- `codegen`

## Source entry points for unresolved issues
- `Core/ActsVersion.hpp.in`
- `Python/CMakeLists.txt`
- `Python/Core/python/__init__.py`
- `Python/conftest.py`
- `Plugins/CMakeLists.txt`
- `Fatras/CMakeLists.txt`
- `Core/CMakeLists.txt`
- `Alignment/CMakeLists.txt`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
