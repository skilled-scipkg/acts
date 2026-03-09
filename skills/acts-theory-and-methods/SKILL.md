---
name: acts-theory-and-methods
description: This skill should be used when users ask about theory and methods in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Theory and Methods

## High-Signal Playbook
### Route conditions
- Use this skill for track-fitting formalism, method comparison, and derivation-level questions.
- Route operational tuning and runtime workflow questions to `acts-simulation-workflows` or `acts-groups`.
- Route legacy-only wording questions to `acts-old` when the docs and current code diverge.

### Triage questions
- Is the question about Kalman fitting, GSF, GX2F, or a specific update/smoother component?
- Do you need derivation-level explanation or current implementation anchors?
- Is the legacy doc sufficient, or must it be reconciled with current code/tests?

### Canonical workflow
1. Start with `docs/old/core/reconstruction/track_fitting.md`.
2. Map the named method to current headers and implementations via `references/source_map.md`.
3. Use the nearest unit test before giving prescriptive tuning or correctness guidance.
4. Call out explicitly where legacy terminology differs from current interfaces.

### Pitfalls and fixes
- The main theory doc is legacy; do not assume it reflects current defaults without code/test cross-checks.
- GSF and Kalman terminology overlaps, but their material-loss treatment and mixture handling differ.
- Method comparisons are not actionable unless trajectory model and updater/smoother settings are matched.

### Convergence/validation checks
- The named method maps to a current header/implementation pair.
- Recommended behavior is backed by a current unit test when available.
- Historical claims from the legacy doc are labeled as historical if interfaces drifted.

## Scope
- Handle questions about theoretical background and algorithmic methods.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/old/core/reconstruction/track_fitting.md`

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
- `Core/src/TrackFitting/MbfSmoother.cpp`
- `Core/src/TrackFitting/KalmanFitterError.cpp`
- `Core/src/TrackFitting/GsfUtils.cpp`
- `Core/src/TrackFitting/GsfMixtureReduction.cpp`
- `Core/src/TrackFitting/GsfError.cpp`
- `Core/src/TrackFitting/GlobalChiSquareFitterError.cpp`
- `Core/src/TrackFitting/GlobalChiSquareFitter.cpp`
- `Core/src/TrackFitting/GainMatrixUpdaterImpl.cpp.in`
- `Core/include/Acts/TrackFitting/KalmanFitter.hpp`
- `Core/include/Acts/TrackFitting/GaussianSumFitter.hpp`
- `Core/include/Acts/TrackFitting/GlobalChiSquareFitter.hpp`
- `Tests/UnitTests/Core/TrackFitting/KalmanFitterTests.cpp`
- `Tests/UnitTests/Core/TrackFitting/GsfTests.cpp`
- `Tests/UnitTests/Core/TrackFitting/Gx2fTests.cpp`
- `Tests/UnitTests/Core/TrackFitting/GainMatrixUpdaterTests.cpp`
- `Tests/UnitTests/Core/TrackFitting/GainMatrixSmootherTests.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
