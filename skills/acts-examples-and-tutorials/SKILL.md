---
name: acts-examples-and-tutorials
description: This skill should be used when users ask about examples and tutorials in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Examples and Tutorials

## High-Signal Playbook
### Route conditions
- Use this skill for runnable example selection, quick adaptation, and expected outputs.
- Route build/configuration blockers to `acts-build-and-install`.
- Route algorithm tuning depth (beyond example wiring) to `acts-simulation-workflows` or `acts-groups`.
- Route Python binding internals/API surface to `acts-api-and-scripting`.

### Triage questions
- Do you want a Python script flow or C++ executable flow?
- Are you using ODD, DD4hep, GeoModel, or another detector source?
- Is this full-chain (sim + reco + vertexing) or one stage (digitization/material/seeding)?
- What output format is needed (`ROOT`, `CSV`, `OBJ`, JSON configs)?
- Do you need deterministic/debug runs (event count, seed, single-thread mode)?
- Are you adapting an existing example or creating a new downstream project?

### Canonical workflow
1. Pick a baseline from `Examples/README.md` and old walkthrough docs (especially `docs/old/examples/full_chain_odd.md`).
2. Ensure required runtime setup is sourced (`<build>/python/setup.sh`) before Python examples.
3. Run minimal-event baseline first (small `-n`, controlled output dir).
4. Verify expected artifacts, then adjust one config axis at a time (digitization/seeding/ambiguity options).
5. For digitization modeling, generate/edit smearing config with the documented helper script.
6. Use tests/hash checks only after baseline outputs are stable.

### Minimal working example
```bash
source build/python/setup.sh
export ODD_PATH=/path/to/OpenDataDetector

python3 Examples/Scripts/Python/full_chain_odd.py \
  -n 5 \
  -o odd_output \
  --output-root \
  --output-csv \
  --output-obj
```

```bash
Examples/Algorithms/Digitization/scripts/smearing-config.py \
  --digi-smear-volume=8 \
  --digi-smear-indices=0:1:5 \
  --digi-smear-types=0:0:3 \
  --digi-smear-parameters=10:20:2.5:-25:25
```

### Pitfalls and fixes
- `Examples/README.md` explicitly marks these as internal development tools; avoid presenting them as production frameworks.
- Missing `ODD_PATH`/detector assets causes ODD scripts to fail; verify detector path/submodule state first.
- Forgetting `source <build>/python/setup.sh` leads to `import acts` failures even when build succeeded.
- Large default event/multiplicity settings can be expensive; start with small `-n` for debugging.
- `Tests/DownstreamProject/` and `Tests/DownstreamProjectNodeps/` are demonstration projects and not part of regular build/test targets.
- `Geant4` mode uses different runtime characteristics; keep thread/event settings explicit when comparing outputs.

### Convergence/validation checks
- Output directory contains expected artifacts for enabled writers (`.root`, `.csv`, `.obj`).
- Event counts and configured options in logs match CLI arguments.
- Repeated small runs with fixed seeds produce stable high-level outputs.
- Full-chain outputs include non-empty reconstructed-track/vertex products before deeper tuning.
- Any config adaptation is traceable to a specific baseline doc/script.

### Source-code entry links
- `Examples/Scripts/Python/full_chain_odd.py` (canonical end-to-end ODD script).
- `Examples/Scripts/Python/material_recording.py` and `Examples/Scripts/Python/material_mapping.py` (material flow examples).
- `Examples/Algorithms/Digitization/scripts/smearing-config.py` (digitization config generator).
- `Examples/Framework/src/Framework/Sequencer.cpp` (execution orchestration behavior).
- `Examples/Framework/src/Utilities/Options.cpp` (CLI/options wiring used by examples).
- `Examples/Configs/odd-digi-smearing-config.json` and `Examples/Configs/odd-seeding-config.json` (baseline configs referenced by scripts).

## Scope
- Handle questions about worked examples, tutorials, and cookbook usage.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `Examples/README.md`
- `Tests/DownstreamProjectNodeps/README.md`
- `Tests/DownstreamProject/README.md`
- `docs/old/core/howto/index.md`
- `docs/old/examples/full_chain_odd.md`
- `docs/old/examples/howto/digitization_config.md`
- `docs/old/examples/examples.rst`
- `docs/old/examples/alignment.md`
- `Examples/Scripts/GsfDebugger/requirements.txt`
- `docs/old/examples/howto/howto.md`

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
- `Examples/Scripts/Python/full_chain_odd.py`
- `Examples/Scripts/Python/material_recording.py`
- `Examples/Scripts/Python/material_mapping.py`
- `Examples/Algorithms/Digitization/scripts/smearing-config.py`
- `Examples/Framework/src/Framework/Sequencer.cpp`
- `Examples/Framework/src/Utilities/Options.cpp`
- `Examples/Configs/odd-digi-smearing-config.json`
- `Examples/Configs/odd-seeding-config.json`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
