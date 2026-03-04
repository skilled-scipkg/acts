---
name: acts-pages
description: This skill should be used when users ask about pages in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Pages

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
