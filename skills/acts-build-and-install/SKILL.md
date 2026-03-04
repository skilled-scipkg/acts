---
name: acts-build-and-install
description: This skill should be used when users ask about build and install in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Build and Install

## High-Signal Playbook
### Route conditions
- Use this skill for configure/build/install/setup blockers and dependency wiring.
- Route to `acts-api-and-scripting` for runtime Python orchestration questions after build succeeds.
- Route to `acts-examples-and-tutorials` for pipeline semantics (what an example does), not toolchain setup.
- Route to `acts-developer-guide` for release process and contribution policy.

### Triage questions
- Are you building only `Acts::Core` or also examples/plugins (`DD4hep`, `Geant4`, `ROOT`, `GNN`)?
- Which dependency environment is intended: local packages, CVMFS/LCG, container, or Spack?
- Which compiler/CMake versions are available (docs require C++20 and CMake >= 3.14)?
- Do you need Python bindings (`acts` and `acts.examples`) or C++ only?
- Is the failure at configure time, compile/link time, or runtime library loading?
- Are you using presets (`CMakePresets.json`) or manual `-D` options?

### Canonical workflow
1. Confirm prerequisites and optional dependency needs from `docs/pages/contributing/building_acts.md`.
2. Pick configuration path: `cmake --preset dev` (from `CMakePresets.json`) or explicit `cmake -S . -B <build>`.
3. Enable optional components with documented CMake options (`ACTS_BUILD_EXAMPLES`, `ACTS_BUILD_PYTHON_BINDINGS`, and plugin flags such as `ACTS_BUILD_PLUGIN_JSON`/`ACTS_BUILD_PLUGIN_ROOT` in `CMakeLists.txt`).
4. Build with `cmake --build <build>` (or target-specific builds if needed).
5. For Spack runtime deps, source `<build>/this_acts_withdeps.sh` (`docs/pages/contributing/spack.md`).
6. For Python workflows, source `<build>/python/setup.sh` (`docs/pages/examples/python_bindings.md`).
7. Smoke-test with a tiny import or one example script before long runs.
8. Only after a stable build, run heavier tests (including optional ROOT hash checks).

### Minimal working example
```bash
cmake --preset dev -S . -B build
cmake --build build -j

cmake -S . -B build-py \
  -DACTS_BUILD_EXAMPLES=ON \
  -DACTS_BUILD_PYTHON_BINDINGS=ON \
  -DACTS_BUILD_PLUGIN_JSON=ON
cmake --build build-py --target ActsPythonBindings
source build-py/python/setup.sh
python -c "import acts, acts.examples; print('ok')"
```

### Pitfalls and fixes
- Missing compiler/deps at configure time: re-check prerequisite list in `docs/pages/contributing/building_acts.md`.
- Deprecated flag usage: prefer `ACTS_BUILD_EXAMPLES=ON` + `ACTS_BUILD_PYTHON_BINDINGS=ON` (see deprecation note in top-level `CMakeLists.txt`).
- DD4hep factory lookup failures under Spack: source `<build>/this_acts_withdeps.sh` (`docs/pages/contributing/spack.md`).
- Python import failures after successful build: source `<build>/python/setup.sh` before running scripts/tests.
- ROOT hash mismatches: inspect output first, then update hashes carefully; use `ROOT_HASH_FILE` for local-only baselines (`docs/pages/examples/python_bindings.md`).
- Plugin symbol/link issues: verify plugin build flags and plugin CMake component dependencies in `Plugins/CMakeLists.txt`.

### Convergence/validation checks
- `cmake` configure finishes without unresolved required packages for requested components.
- Requested targets build (`Acts::Core`, optional plugin libs, and `ActsPythonBindings` when enabled).
- `python -c "import acts"` and `python -c "import acts.examples"` both succeed when Python bindings are requested.
- A representative example script starts (for example `Examples/Scripts/Python/geometry.py --help`).
- Optional regression tests run in intended mode (`ROOT_HASH_CHECKS=ON pytest` only when hash checks are required).

### Source-code entry links
- `CMakePresets.json` (preset defaults used by developers/CI).
- `CMakeLists.txt` (option graph and option dependency propagation).
- `Plugins/CMakeLists.txt` plus plugin sub-CMake files (component enable/disable logic).
- `Python/Core/CMakeLists.txt` (core Python module build and `setup.sh` generation).
- `Python/Examples/CMakeLists.txt` (examples Python module wiring and conditional plugin bindings).
- `Examples/Framework/CMakeLists.txt` (framework/plugin-dependent link behavior).

## Scope
- Handle questions about build, installation, compilation, and environment setup.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/examples/python_bindings.md`
- `Python/Examples/CMakeLists.txt`
- `Examples/Framework/CMakeLists.txt`
- `docs/pages/examples/python_bindings.md`
- `docs/pages/contributing/spack.md`
- `docs/pages/contributing/profiling.md`
- `docs/pages/contributing/building_acts.md`
- `docs/old/plugins/geant4.md`
- `docs/old/plugins/dd4hep.md`
- `docs/old/misc/spack.md`
- `docs/old/contribution/run_formatting.md`
- `docs/old/contribution/profiling.md`

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
- `CMakePresets.json`
- `CMakeLists.txt`
- `Python/Examples/CMakeLists.txt`
- `Plugins/Gnn/CMakeLists.txt`
- `Plugins/Geant4/CMakeLists.txt`
- `Plugins/DD4hep/CMakeLists.txt`
- `Core/src/Geometry/CMakeLists.txt`
- `Plugins/CMakeLists.txt`
- `Core/CMakeLists.txt`
- `Python/Plugins/CMakeLists.txt`
- `Python/Core/CMakeLists.txt`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
