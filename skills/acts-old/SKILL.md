---
name: acts-old
description: This skill should be used when users ask about old in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Old

## High-Signal Playbook
### Route conditions
- Use this skill only when the user explicitly references content under `docs/old/` or historical ACTS behavior.
- Route modern implementation guidance to domain skills (`acts-build-and-install`, `acts-inputs-and-modeling`, `acts-groups`, `acts-examples-and-tutorials`) after legacy context is identified.
- Treat this as an archival/migration bridge, not a default source for current production guidance.

### Triage questions
- Which exact legacy page or concept is being referenced (for example `docs/old/core/reconstruction/track_fitting.md`)?
- Is the goal historical understanding or a current implementation decision?
- Do you need a modern equivalent page/path for migration?
- Is this a docs-build warning question (`docs/old/known-warnings.txt`) or a runtime/algorithm question?
- Which subsystem is affected (seeding, event data, Fatras, units/definitions)?

### Canonical workflow
1. Start at `docs/old/index.rst` to frame scope and archival status.
2. Open the exact legacy page and capture terminology and assumptions.
3. Locate the closest modern counterpart in `docs/pages/` or `docs/groups/` when available.
4. Verify critical behavior against current code using `references/source_map.md` entry points.
5. Call out any semantic drift explicitly (legacy-only note vs still-current behavior).
6. Return a migration-safe recommendation with both legacy and current file paths.

### Minimal working example
```bash
rg -n "Seeding|Track Finding|Track Event Data Model" docs/old docs/pages docs/groups
rg -n "SpacePoint|ParticleHypothesis|Units" Core/include/Acts Core/src Fatras
```

### Pitfalls and fixes
- `docs/old/index.rst` is archival; do not assume it reflects latest defaults without cross-checking current docs/source.
- `docs/old/known-warnings.txt` intentionally filters many historical Sphinx warnings; do not treat it as runtime issue evidence.
- Legacy example docs can describe internal development tooling; validate against current examples before recommending usage.
- Old naming/options may no longer match current CMake/runtime flags; map to modern equivalents before execution.
- Legacy algorithm descriptions can lag source behavior; confirm with current headers/implementations before giving prescriptive advice.

### Convergence/validation checks
- Every user-facing recommendation cites both the legacy path and a current path (or marks no current replacement).
- Mentioned symbols/classes are confirmed to exist in current source tree.
- Migration advice avoids legacy-only flags/workflows unless explicitly requested.
- If behavior differs, the response states which behavior is historical vs current.

### Source-code entry links
- `Core/src/Seeding/CompositeSpacePointLineSeeder.cpp` and `Core/src/Seeding/CompositeSpacePointLineFitter.cpp` (legacy seeding concepts vs current code).
- `Core/include/Acts/EventData/ParticleHypothesis.hpp` (event-data concept anchoring).
- `Core/src/EventData/SpacePointContainer2.cpp` and `Core/include/Acts/EventData/SpacePointContainer2.hpp` (space-point container lineage).
- `Fatras/src/EventData/Particle.cpp` (legacy Fatras event-data behavior anchor).
- `Core/include/Acts/Definitions/Units.hpp` (legacy docs on units mapped to current definitions).

## Scope
- Handle questions about documentation grouped under the 'old' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/old/index.rst`
- `docs/old/core/reconstruction/index.md`
- `docs/old/core/misc/index.md`
- `docs/old/core/eventdata/index.md`
- `docs/old/known-warnings.txt`
- `docs/old/authors.rst`
- `docs/old/fatras/fatras.md`
- `docs/old/core/reconstruction/pattern_recognition/seeding.md`
- `docs/old/license.rst`
- `docs/old/glossary.md`
- `docs/old/core/eventdata/measurements.md`
- `docs/old/misc/misc.rst`

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
- `Fatras/src/EventData/Particle.cpp`
- `Fatras/include/ActsFatras/EventData/Particle.hpp`
- `Core/include/Acts/Definitions/Units.hpp`
- `Core/include/Acts/EventData/ParticleHypothesis.hpp`
- `Core/src/Seeding/CompSpacePointAuxiliaries.cpp`
- `Core/src/Seeding/CompositeSpacePointLineSeeder.cpp`
- `Core/src/Seeding/CompositeSpacePointLineFitter.cpp`
- `Core/src/EventData/SpacePointContainer2.cpp`
- `Core/include/Acts/Seeding/SpacePointGrid.hpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
