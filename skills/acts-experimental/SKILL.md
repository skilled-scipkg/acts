---
name: acts-experimental
description: This skill should be used when users ask about experimental in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Experimental

## High-Signal Playbook
### Route conditions
- Use this skill for unstable or opt-in ACTS features, especially blueprint geometry, alignment, Seeding2/GBTS, ITk GBTS example flows, and multilayer navigation.
- Route stable geometry/material questions to `acts-inputs-and-modeling`.
- Route end-to-end runtime tuning back to `acts-simulation-workflows` once the experimental feature is identified.
- Route track-fitting formalism to `acts-theory-and-methods`.
- Route binding mechanics to `acts-api-and-scripting`.

### Triage questions
- Is the question about blueprint node construction, alignment, Seeding2/GBTS, ITk GBTS workflows, or experimental navigation?
- Do you need the current C++ behavior, Python binding surface, or both?
- Is the feature actually under `Acts::Experimental`, or is it a stable API that should route elsewhere?

### Canonical workflow
1. Confirm the feature is explicitly experimental or belongs to the `Alignment` module.
2. Open the nearest example or test first (`Examples/Scripts/Python/blueprint.py`, `Examples/Scripts/Python/full_chain_itk_Gbts.py`, `Python/Examples/tests/test_alignmentdecorator.py`, or `Tests/UnitTests/Core/Geometry/BlueprintTests.cpp`).
3. Inspect the matching headers and implementation files from `references/source_map.md`.
4. Validate against the nearest unit or Python test before assuming the API is stable.

### Pitfalls and fixes
- `docs/experimental.md` is only a namespace-level pointer, so most concrete answers need source/tests quickly.
- Experimental APIs can change without the stability guarantees described in `docs/pages/versioning.md`.
- Alignment helpers are unavailable unless the Alignment library and its Python plugin were built.
- Blueprint/material-designator behavior is easier to verify in unit tests than in sparse docs.

### Convergence/validation checks
- The nearest unit test or Python example still matches the intended API.
- Python imports for the feature succeed when bindings are expected.
- Experimental geometry changes preserve the expected volume or alignment state in tests.

## Scope
- Handle questions about documentation grouped under the 'experimental' theme, especially unstable geometry, alignment, and Seeding2 features.
- Keep responses architectural first, then switch to source/test anchors quickly because the docs are intentionally sparse.

## Primary documentation references
- `docs/experimental.md`

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
- `Examples/Scripts/Python/blueprint.py`
- `Examples/Scripts/Python/full_chain_itk_Gbts.py`
- `Python/Examples/src/plugins/Alignment.cpp`
- `Alignment/include/ActsAlignment/Kernel/Alignment.hpp`
- `Alignment/include/ActsAlignment/Kernel/detail/AlignmentEngine.hpp`
- `Core/include/Acts/Geometry/Blueprint.hpp`
- `Core/src/Geometry/Blueprint.cpp`
- `Core/include/Acts/Geometry/BlueprintOptions.hpp`
- `Core/src/Geometry/MaterialDesignator.hpp`
- `Core/include/Acts/Geometry/ContainerBlueprintNode.hpp`
- `Core/src/Geometry/MaterialDesignatorBlueprintNode.cpp`
- `Core/include/Acts/Seeding2/GraphBasedTrackSeeder.hpp`
- `Core/src/Seeding2/GraphBasedTrackSeeder.cpp`
- `Core/src/Seeding2/TripletSeedFinder.cpp`
- `Core/include/Acts/Navigation/MultiLayerNavigationPolicy.hpp`
- `Core/src/Navigation/MultiLayerNavigationPolicy.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
