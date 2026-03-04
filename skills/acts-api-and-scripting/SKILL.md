---
name: acts-api-and-scripting
description: This skill should be used when users ask about api and scripting in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: API and Scripting

## High-Signal Playbook
### Route conditions
- Use this skill for Python/C++ binding usage, script-level orchestration, and API surface questions.
- Route build/install issues to `acts-build-and-install`.
- Route end-to-end chain semantics to `acts-simulation-workflows`.
- Route detector/material modeling depth to `acts-inputs-and-modeling`.

### Triage questions
- Is the request about Python bindings (`acts`, `acts.examples`) or C++ API internals?
- Do you need symbol-level API mapping from Python to C++ implementation?
- Is the issue import/setup, runtime behavior, or API contract mismatch?
- Are plugin bindings (`Root`, `Json`, `Geant4`, `Onnx`, `Gnn`) required?

### Canonical workflow
1. Verify environment and imports first (`source <build>/python/setup.sh`, then `import acts`).
2. Reproduce behavior with a minimal script call before inspecting internals.
3. Map Python call-sites to binding files in `Python/Core/src` and `Python/Examples/src`.
4. For plugin APIs, inspect matching bindings (for example `Python/Plugins/src/Json.cpp` and `Python/Plugins/src/Root.cpp`) and plugin C++ sources.
5. Escalate to `references/source_map.md` for function-level source anchors when docs are insufficient.

### Minimal working example
```bash
source build/python/setup.sh
python - <<'PY'
import acts
import acts.examples
print("acts version:", acts.__version__)
print("bindings ok")
PY
```

```bash
python3 Examples/Scripts/Python/propagation.py
python3 Examples/Scripts/Python/ckf_tracks.py
```

### Pitfalls and fixes
- Most import/runtime issues are environment setup errors, not API regressions.
- Plugin-specific classes are unavailable unless matching plugin bindings were built.
- Comparing Python and C++ behavior requires matching defaults (seeds, threads, geometry, field).
- API drift across docs can happen; verify against current binding source files.

### Convergence/validation checks
- `import acts` and `import acts.examples` both succeed.
- Minimal script runs complete and emit expected outputs.
- Mapped Python entry points resolve to concrete binding files.
- Plugin-dependent calls only used when corresponding plugin bindings are present.

## Scope
- Handle questions about language bindings, APIs, and programmatic interfaces.
- Keep responses practical and symbol-oriented.

## Primary documentation references
- `docs/old/codeguide.md`
- `docs/groups/logging.md`
- `docs/old/core/magnetic_field.md`
- `docs/old/core/misc/logging.md`
- `docs/old/versioning.rst`
- `docs/pages/versioning.md`
- `docs/pages/examples/python_bindings.md`
- `docs/old/examples/howto/gsf_debugger.md`
- `docs/old/core/visualization/3d.md`
- `Python/Examples/tests/root_file_hashes.txt`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use runnable scripts/tests as behavior references before deep source dives.
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
- `Python/Core/src/CoreModuleEntry.cpp`
- `Python/Core/src/Propagation.cpp`
- `Python/Core/src/Seeding.cpp`
- `Python/Core/src/TrackFinding.cpp`
- `Python/Core/src/Visualization.cpp`
- `Python/Examples/src/ExamplesModuleEntry.cpp`
- `Python/Examples/src/Framework.cpp`
- `Python/Plugins/src/Root.cpp`
- `Python/Plugins/src/Json.cpp`
- `Plugins/Root/src/RootMaterialMapIo.cpp`
- `Plugins/Json/src/MaterialMapJsonConverter.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
