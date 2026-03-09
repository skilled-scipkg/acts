---
name: acts-tests
description: This skill should be used when users ask about tests in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Tests

## High-Signal Playbook
### Route conditions
- Use this skill for regression checks, behavior validation, and test triage.
- Route build/link/bootstrap failures to `acts-build-and-install` before test debugging.
- Route workflow semantics to `acts-simulation-workflows` when failures are in end-to-end scripts.

### Triage questions
- Is the failure in C++ unit tests, integration tests, or Python example tests?
- Which subsystem is involved (propagation, seeding, track finding, material, IO)?
- Is the issue deterministic or flaky across reruns?
- Do you need a minimal reproducer test command or source-level root cause mapping?

### Canonical workflow
1. Reproduce with a narrow test target (`ctest -R <pattern>` or one `pytest` file).
2. Confirm environment/setup assumptions (bindings sourced, required plugins enabled).
3. Inspect failing test source and expected fixtures.
4. Map failing assertions to implementation anchors via `references/source_map.md`.
5. Propose the smallest fix and rerun targeted tests before broad suites.

### Minimal working example
```bash
ctest --test-dir build -R Seeding --output-on-failure
ctest --test-dir build -R CombinatorialKalmanFilter --output-on-failure

source build/python/setup.sh
pytest -q Python/Examples/tests/test_propagation.py
pytest -q Python/Examples/tests/test_material.py
```

### Pitfalls and fixes
- Running tests without sourced Python environment causes import failures unrelated to algorithm behavior.
- Broad suite runs before a narrow reproducer make failure localization slower.
- Hash/checksum mismatches should be inspected before updating reference baselines.
- Plugin-conditional tests can fail when optional components were not built.

### Convergence/validation checks
- Targeted reproducer command is stable across reruns.
- Fixes pass the originally failing narrow test set.
- Related neighboring tests (same subsystem) still pass.
- Any updated expected artifacts are justified and documented.

## Scope
- Handle questions about tests, validation, and regression behavior.
- Keep responses focused on reproducing and isolating behavior quickly.

## Primary documentation references
- `Tests/IntegrationTests/README.md`
- `Tests/Data/README.md`
- `Tests/UnitTests/Core/Seeding/sp.txt`
- `docs/pages/examples/python_bindings.md`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use tests as behavior or regression references first.
- If ambiguity remains after docs/tests, inspect `references/source_map.md` and start with the listed source entry points.
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
- `Tests/UnitTests/Core/Seeding/SeedFinderTest.cpp`
- `Tests/UnitTests/Core/TrackFinding/CombinatorialKalmanFilterTests.cpp`
- `Tests/UnitTests/Core/Propagator/KalmanExtrapolatorTests.cpp`
- `Tests/UnitTests/Core/Material/MaterialValidaterTests.cpp`
- `Tests/UnitTests/Core/EventData/AnyTrackStateProxyTests.cpp`
- `Tests/UnitTests/Core/EventData/MultiTrajectoryTests.cpp`
- `Tests/UnitTests/Plugins/Json/GeometryHierarchyMapJsonConverterTests.cpp`
- `Tests/UnitTests/Plugins/Root/RootMaterialMapIoTests.cpp`
- `Python/Examples/tests/test_examples.py`
- `Python/Examples/tests/test_propagation.py`
- `Python/Examples/tests/test_material.py`
- `Core/include/Acts/Seeding/SeedFinder.hpp`
- `Core/include/Acts/TrackFinding/CombinatorialKalmanFilter.hpp`
- `Core/include/Acts/Propagator/Propagator.hpp`
- `Core/include/Acts/EventData/TrackStateProxy.hpp`
- `Core/include/Acts/EventData/MultiTrajectory.hpp`
- `Plugins/Json/include/ActsPlugins/Json/GeometryHierarchyMapJsonConverter.hpp`
- `Plugins/Root/src/RootMaterialMapIo.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
