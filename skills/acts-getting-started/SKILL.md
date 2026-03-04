---
name: acts-getting-started
description: This skill should be used when users ask about getting started in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Getting Started

## High-Signal Playbook
### Route conditions
- Use this skill for first successful runs, quick orientation, and baseline pipeline sanity checks.
- Route configure/build/install blockers to `acts-build-and-install`.
- Route detector/material setup depth to `acts-inputs-and-modeling`.
- Route full-chain runtime tuning to `acts-simulation-workflows`.

### Triage questions
- Do you already have a working build with Python bindings (`import acts` works)?
- Are you starting from generic detector scripts or ODD full-chain scripts?
- Do you need only one stage (propagation/seeding) or a full reconstruction chain?
- What output artifact do you need to confirm success (`.root`, logs, track counters)?

### Canonical workflow
1. Verify runtime environment (`source <build>/python/setup.sh`).
2. Start with `geometry.py` and `propagation.py` for lightweight baseline checks.
3. Move to `seeding.py` and then `ckf_tracks.py` once baseline is stable.
4. Keep event counts small during setup; increase only after outputs are validated.
5. Use tests as behavior anchors if script output is unclear.
6. Escalate from docs to `references/source_map.md` for function-level implementation details.

### Minimal working example
```bash
source build/python/setup.sh

python3 Examples/Scripts/Python/geometry.py
python3 Examples/Scripts/Python/propagation.py
python3 Examples/Scripts/Python/seeding.py --algorithm GridTriplet
python3 Examples/Scripts/Python/ckf_tracks.py
```

### Pitfalls and fixes
- `import acts` errors after successful build usually mean `setup.sh` was not sourced.
- Running high-stat jobs too early can hide setup issues; use low-stat scripts first.
- Mixed detector/material inputs between runs invalidate quick comparisons.
- Missing example output files often indicate writer options/plugin support mismatch.

### Convergence/validation checks
- Baseline scripts complete without runtime exceptions.
- The propagation summary ROOT output is produced and non-empty.
- Seeding/CKF runs produce non-empty track-related output collections.
- Re-running the same low-stat script yields stable high-level event counters.

## Scope
- Handle questions about initial setup, quickstarts, and core concepts.
- Keep responses practical and execution-focused.

## Primary documentation references
- `docs/index.md`
- `docs/SNIPPETS.md`
- `docs/old/getting_started.md`
- `docs/old/core/propagation.md`
- `docs/groups/errors.md`
- `docs/old/examples/python_bindings.rst`

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
- `Examples/Scripts/Python/geometry.py`
- `Examples/Scripts/Python/propagation.py`
- `Examples/Scripts/Python/seeding.py`
- `Examples/Scripts/Python/ckf_tracks.py`
- `Examples/Framework/src/Framework/Sequencer.cpp`
- `Examples/Framework/src/Utilities/Options.cpp`
- `Python/Core/src/Propagation.cpp`
- `Python/Core/src/Seeding.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
