---
name: acts-theory-and-methods
description: This skill should be used when users ask about theory and methods in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Theory and Methods

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
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
