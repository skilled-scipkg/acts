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
- Is the call going through high-level helpers in `Python/Examples/python` or direct pybind classes?
- Do you need symbol-level API mapping from Python to C++ implementation?
- Is the issue import/setup, missing module registration, runtime behavior, or API contract mismatch?
- Are plugin bindings (`Root`, `Json`, `Geant4`, `Onnx`, `Gnn`) required?

### Canonical workflow
1. Verify that the bindings were built and the environment is sourced (`ActsPythonBindings`, then `source <build>/python/setup.sh`).
2. Reproduce behavior with a minimal import or script call before inspecting internals.
3. Map high-level helper usage to `Python/Examples/python` before dropping to the pybind translation units in `Python/Core/src`.
4. For plugin APIs, inspect matching bindings (for example `Python/Plugins/src/Json.cpp`, `Python/Plugins/src/Root.cpp`, or `Python/Examples/src/plugins/Onnx.cpp`) and then the plugin C++ sources.
5. Use the nearest `Python/Core/tests` or `Python/Examples/tests` case before escalating to `references/source_map.md`.

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
- Most import/runtime issues are unsourced `build/python/setup.sh` or missing `ActsPythonBindings` artifacts, not API regressions.
- Plugin-specific classes are unavailable unless matching plugin bindings were built.
- Helper wrappers in `Python/Examples/python` can hide defaults; compare them before concluding the C++ layer regressed.
- Comparing Python and C++ behavior requires matching defaults (seeds, threads, geometry, field).
- API drift across docs can happen; verify against current binding source files.
- ROOT hash regressions are opt-in via `ROOT_HASH_CHECKS=ON`; do not expect them during a default `pytest` run.

### Convergence/validation checks
- `import acts` and `import acts.examples` both succeed.
- Minimal script runs complete and emit expected outputs.
- Mapped Python entry points resolve to concrete binding files.
- Plugin-dependent calls only used when corresponding plugin bindings are present.

## Scope
- Handle questions about language bindings, APIs, and programmatic interfaces.
- Keep responses practical and symbol-oriented.

## Primary documentation references
- `docs/pages/examples/python_bindings.md`
- `docs/old/codeguide.md`
- `docs/groups/logging.md`
- `docs/old/core/magnetic_field.md`
- `docs/old/core/misc/logging.md`
- `docs/old/versioning.rst`
- `docs/pages/versioning.md`
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
- `Python/Core/python/__init__.py`
- `Python/Core/setup.sh.in`
- `Python/Examples/python/reconstruction.py`
- `Python/Core/src/Propagation.cpp`
- `Python/Core/src/Seeding.cpp`
- `Python/Core/src/TrackFinding.cpp`
- `Python/Core/src/Geometry.cpp`
- `Python/Core/src/Visualization.cpp`
- `Python/Core/src/MagneticField.cpp`
- `Python/Core/src/Definitions.cpp`
- `Python/Examples/src/ExamplesModuleEntry.cpp`
- `Python/Examples/src/Framework.cpp`
- `Python/Examples/src/plugins/Alignment.cpp`
- `Python/Examples/src/plugins/Onnx.cpp`
- `Python/Plugins/src/Root.cpp`
- `Python/Plugins/src/Json.cpp`
- `Python/Plugins/src/Geant4.cpp`
- `Core/include/Acts/EventData/AnyTrackStateProxy.hpp`
- `Core/include/Acts/EventData/TrackContainer.hpp`
- `Core/include/Acts/EventData/TrackStateProxy.hpp`
- `Core/include/Acts/EventData/MultiTrajectory.hpp`
- `Plugins/Root/src/RootMaterialMapIo.cpp`
- `Plugins/Json/src/MaterialMapJsonConverter.cpp`
- `Tests/UnitTests/Core/EventData/AnyTrackStateProxyTests.cpp`
- `Tests/UnitTests/Core/EventData/MultiTrajectoryTests.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
