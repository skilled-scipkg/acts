---
name: acts-developer-guide
description: This skill should be used when users ask about developer guide in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Developer Guide

## High-Signal Playbook
### Route conditions
- Use this skill for contribution mechanics, plugin extension points, release flow, and static-analysis policy.
- Route toolchain/bootstrap blockers to `acts-build-and-install`.
- Route API usage details to `acts-api-and-scripting` and runnable workflow behavior to `acts-examples-and-tutorials`.

### Triage questions
- Is this a release task, a PR/CI quality task, or a plugin-extension task?
- Which plugin family is touched (`JSON`, `ROOT`, `DD4hep`, `Geant4`, `GNN`, `ONNX`, etc.)?
- Are failures from `clang-tidy`, compile/link, or runtime behavior?
- Do you need C++ plugin internals, Python plugin bindings, or both?
- For release work: do you have access to push `releases` and inspect generated draft release metadata?
- Are ROOT hash changes intended algorithm updates or unintended regressions?

### Canonical workflow
1. Pick path: release (`docs/pages/contributing/release.md`), clang-tidy (`docs/pages/contributing/clang_tidy.md`), or plugin docs (`docs/groups/plugins/index.md` then the specific plugin page).
2. For releases, follow the three-step flow exactly: update `releases`, prepare milestone, publish generated draft release.
3. For quality issues, reproduce locally with matching build flags (e.g., `ACTS_RUN_CLANG_TIDY=ON`) before CI-only diagnosis.
4. For plugin changes, verify component flags/dependencies in top-level and plugin CMake files.
5. If outputs changed, run/inspect ROOT hash checks before updating references.
6. Escalate from docs to `references/source_map.md` only when behavior details are still ambiguous.

### Minimal working example
```bash
# Release branch update path (docs/pages/contributing/release.md)
git checkout releases
git fetch upstream
git merge --no-ff upstream/main
git push -u upstream releases

# Local clang-tidy path
cmake -S . -B build-tidy -DACTS_RUN_CLANG_TIDY=ON
cmake --build build-tidy -j
```

### Pitfalls and fixes
- Release note grouping depends on conventional commit prefixes; malformed PR titles degrade auto-generated notes.
- Publishing wrong release target commit is a common operator error; verify draft release commit hash before publish.
- `clang-tidy` failures often need rule-specific fixes, not blanket suppressions; use reported check IDs.
- Hash updates without output inspection can hide regressions; inspect changed ROOT content first.
- Plugin build/link errors often come from missing option dependencies; confirm flag propagation in `CMakeLists.txt` and `Plugins/CMakeLists.txt`.
- Python plugin import errors can stem from not building/installing corresponding plugin bindings (for example `Python/Plugins/src/Json.cpp`, `Python/Plugins/src/Root.cpp`, `Python/Plugins/src/Geant4.cpp`).

### Convergence/validation checks
- CI/local `clang-tidy` results are clean or reduced to intentionally scoped findings.
- Release automation produces expected version bump and draft release name/target commit.
- Target plugin libraries and optional Python modules are present for requested components.
- Hash regression checks either pass or have manually reviewed, justified updates.
- Documentation references in responses point to the exact contributing/plugin page actually used.

### Source-code entry links
- `CMakeLists.txt` and `Plugins/CMakeLists.txt` (feature-flag and dependency propagation).
- `Plugins/Json/src/MaterialMapJsonConverter.cpp` and `Plugins/Json/src/DetrayJsonHelper.cpp` (JSON plugin internals).
- `Plugins/Root/src/RootMaterialMapIo.cpp` (ROOT plugin IO path).
- `Plugins/Gnn/src/OnnxEdgeClassifier.cpp` (GNN/ONNX integration anchor).
- `Python/Plugins/src/Json.cpp`, `Python/Plugins/src/Root.cpp`, `Python/Plugins/src/Geant4.cpp` (Python plugin bindings).

## Scope
- Handle questions about developer architecture, extension points, and contribution workflow.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/groups/plugins/index.md`
- `docs/groups/contributing/index.md`
- `docs/pages/contributing/release.md`
- `docs/old/contribution/clang_tidy.md`
- `docs/pages/contributing/clang_tidy.md`
- `docs/old/plugins/plugins.rst`
- `docs/old/plugins/json.md`
- `docs/old/contribution/root_hash_checks.md`
- `docs/old/contribution/guide.rst`
- `docs/old/contribution/contribution.md`
- `docs/groups/plugins/root.md`
- `docs/groups/plugins/onnx.md`

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
- `CMakeLists.txt`
- `Plugins/CMakeLists.txt`
- `Plugins/Json/src/DetrayJsonHelper.cpp`
- `Plugins/Gnn/src/OnnxEdgeClassifier.cpp`
- `Plugins/Json/src/MaterialMapJsonConverter.cpp`
- `Plugins/Json/include/ActsPlugins/Json/DetrayJsonHelper.hpp`
- `Plugins/Gnn/include/ActsPlugins/Gnn/OnnxEdgeClassifier.hpp`
- `Plugins/Root/src/RootMaterialMapIo.cpp`
- `Plugins/Root/include/ActsPlugins/Root/RootMaterialMapIo.hpp`
- `Plugins/Json/include/ActsPlugins/Json/ActsJson.hpp`
- `Python/Plugins/src/Root.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
