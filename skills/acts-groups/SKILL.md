---
name: acts-groups
description: This skill should be used when users ask about groups in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Groups

## High-Signal Playbook
### Route conditions
- Use this skill when the question is framed by ACTS doc groups (`detector_descr`, `dataprep`, `pattern_recog`, `eventdata`, `vertexing`, `propagation`, `track_fitting`, `context`).
- Route build/debug environment issues to `acts-build-and-install`.
- Route runnable chain setup to `acts-examples-and-tutorials` or `acts-simulation-workflows`.
- Route legacy-only references to `acts-old`.

### Triage questions
- Which group is primary for the request (one of `detector_descr`, `dataprep`, `pattern_recog`, `eventdata`, `vertexing`, `propagation`)?
- Is the user asking conceptual behavior, API usage, or source-level implementation?
- Does the issue involve branching track-state behavior or linear trajectories?
- Are they tuning quality/performance (seeding/finding/fitting) or debugging data-model correctness?
- Do they need C++ symbol anchors for deep dives?

### Canonical workflow
1. Classify the request into a single dominant group and open the exact repo-local page first: `docs/groups/pattern_recog/index.md`, `docs/groups/eventdata/index.md`, `docs/groups/detector_descr/index.md`, `docs/groups/dataprep/index.md`, `docs/groups/vertexing.md`, `docs/groups/propagation.md`, `docs/groups/track_fitting.md`, or `docs/groups/context.md`.
2. Pull one adjacent group only if needed (for example `eventdata` + `pattern_recog`).
3. Extract required invariants and warnings from docs before touching source.
4. Map doc concepts to concrete symbols using `references/source_map.md` (vertexing, track helpers, event-data classes).
5. Validate assumptions with the nearest example/test artifact if behavior is non-obvious.
6. Provide a narrow implementation path, then route to a more specific skill if scope expands.

### Minimal working example
```cpp
auto track = getTrackFromSomewhere();
for (const auto trackState : track.trackStatesReversed()) {
  // process from tip to stem
}
```

```cpp
// Only safe for non-branching sequences
track.linkForward();
for (const auto trackState : track.trackStates()) {
  // process forward
}
```

### Pitfalls and fixes
- Forward iteration without forward-linking is invalid for default branching layouts; use `trackStatesReversed()` unless explicitly linked.
- Calling `linkForward()` on branching trajectories corrupts branching; copy/linearize first.
- In-place smoothing on shared/branching states can overwrite previous results; avoid one-by-one smoothing on shared ancestors.
- Group index pages are intentionally brief; jump to grouped leaf pages (`track_finding`, `seeding`, `measurement`, etc.) for details.
- Mixing conceptual and implementation layers causes confusion; lock terminology from docs before source debugging.

### Convergence/validation checks
- Chosen group scope cleanly covers the question without pulling unrelated groups.
- Track-state iteration direction matches the algorithm assumption.
- Branching assumptions are explicit before any forward-link operation.
- Source symbol lookup resolves to current files listed in `references/source_map.md`.
- Any recommended tuning is paired with an observable check (track counts, fit quality, or vertex consistency).

### Source-code entry links
- `Core/src/Vertexing/TrackDensityVertexFinder.cpp` and `Core/include/Acts/Vertexing/TrackDensityVertexFinder.hpp`.
- `Core/src/Vertexing/NumericalTrackLinearizer.cpp` and `Core/include/Acts/Vertexing/NumericalTrackLinearizer.hpp`.
- `Core/src/Seeding/EstimateTrackParamsFromSeed.cpp` and `Core/include/Acts/Seeding/EstimateTrackParamsFromSeed.hpp`.
- `Core/src/EventData/TrackParameters.cpp` and `Core/src/EventData/VectorTrackContainer.cpp`.
- `Core/src/Utilities/TrackHelpers.cpp` and `Core/include/Acts/Utilities/TrackHelpers.hpp`.

## Scope
- Handle questions about documentation grouped under the 'groups' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/groups/pattern_recog/index.md`
- `docs/groups/eventdata/index.md`
- `docs/groups/detector_descr/index.md`
- `docs/groups/dataprep/index.md`
- `docs/groups/vertexing.md`
- `docs/groups/utilities.md`
- `docs/groups/track_fitting.md`
- `docs/groups/propagation.md`
- `docs/groups/context.md`
- `docs/groups/pattern_recog/track_finding.md`
- `docs/groups/pattern_recog/seeding.md`
- `docs/groups/eventdata/measurement.md`

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
- `Core/src/Vertexing/TrackDensityVertexFinder.cpp`
- `Core/src/Vertexing/NumericalTrackLinearizer.cpp`
- `Core/src/Vertexing/HelicalTrackLinearizer.cpp`
- `Core/src/Vertexing/GaussianTrackDensity.cpp`
- `Core/src/Vertexing/GaussianGridTrackDensity.cpp`
- `Core/src/Vertexing/AdaptiveGridTrackDensity.cpp`
- `Core/src/Utilities/TrackHelpers.cpp`
- `Core/src/Seeding/EstimateTrackParamsFromSeed.cpp`
- `Core/src/EventData/TrackParameters.cpp`
- `Core/src/EventData/VectorTrackContainer.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
