---
name: acts-simulation-workflows
description: This skill should be used when users ask about simulation workflows in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Simulation Workflows

## High-Signal Playbook
### Route conditions
- Use this skill for end-to-end chain setup (generation/simulation/reconstruction), runtime controls, and workflow staging.
- Route build/bootstrap failures to `acts-build-and-install`.
- Route detector/material-model preparation to `acts-inputs-and-modeling`.
- Route API-level binding questions to `acts-api-and-scripting`.

### Triage questions
- Which workflow stage is failing: generation, simulation, digitization, seeding/CKF, ambiguity, or vertexing?
- Are you using classical, score-based, or ML ambiguity resolution, and are the ONNX model files available?
- Are you running the ODD full chain, the ITk GBTS flow, generic detector scripts, or custom detector inputs?
- Do you need `Fatras` or `Geant4` simulation mode?
- Which outputs are required (`ROOT`, `CSV`, `OBJ`) and what is the required event scale?
- Is the goal fast debug iteration or performance/physics-quality comparison?

### Canonical workflow
1. Start from one script baseline (`full_chain_odd.py`, `ckf_tracks.py`, or `truth_tracking_kalman.py`) and keep defaults for the first run.
2. Run low statistics first (`-n 5` to `-n 20`) with explicit output directory.
3. Verify expected artifacts/log counters before changing algorithm knobs.
4. Change one axis at a time (simulation mode, seeding options, ambiguity solver, output writers) and keep wrapper defaults in `Python/Examples/python/reconstruction.py` visible.
5. Use the nearest unit/integration tests when behavior is unclear, especially for ambiguity scoring and material pipelines.
6. Escalate from docs to `references/source_map.md` only for unresolved function-level behavior.

### Minimal working example
```bash
source build/python/setup.sh
export ODD_PATH=thirdparty/OpenDataDetector

python3 Examples/Scripts/Python/full_chain_odd.py \
  -n 5 \
  -o odd_output \
  --output-root \
  --output-csv \
  --output-obj
```

```bash
python3 Examples/Scripts/Python/material_recording.py -n 10 -t 200
python3 Examples/Scripts/Python/material_mapping.py -o material-map.json
python3 Examples/Scripts/Python/material_validation.py
```

### Pitfalls and fixes
- Missing `ODD_PATH` or detector assets causes ODD full-chain setup failures.
- Running high event counts before baseline validation can hide configuration errors and waste runtime.
- Comparing `Fatras` and `Geant4` outputs without fixed event/seed settings leads to non-actionable differences.
- Ambiguity-solver comparisons are only meaningful when upstream seeding/CKF configuration is identical.
- ML ambiguity workflows fail early if the ONNX models under `Examples/Scripts/Python/MLAmbiguityResolution` are absent or mismatched.
- Material validation results are unstable if recording/mapping configuration changes between runs.

### Convergence/validation checks
- Output directory contains expected non-empty artifacts (`.root`, optional `.csv`/`.obj`).
- Sequencer log event counts match requested `-n`/`--skip` settings.
- Track/vertex collections are non-empty in baseline runs before tuning.
- Material mapping flow generates map + validation outputs without missing-input warnings.
- Repeated low-stat runs with fixed settings show stable high-level counters.

## Scope
- Handle questions about simulation setup, execution flow, and runtime controls.
- Keep responses focused and practical; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `Examples/Scripts/GsfDebugger/README.md`
- `docs/old/plugins/MLAlgorithms.md`
- `docs/pages/tracking.md`
- `docs/old/examples/howto/run_ckf_auto_tuning.rst`
- `docs/old/examples/full_chain_odd.md`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use examples/tests as executable behavior references.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the listed source entry points.
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
- `Examples/Scripts/Python/full_chain_odd_LRT.py`
- `Examples/Scripts/Python/full_chain_itk_Gbts.py`
- `Examples/Scripts/Python/ckf_tracks.py`
- `Examples/Scripts/Python/truth_tracking_kalman.py`
- `Python/Examples/python/reconstruction.py`
- `Python/Examples/src/plugins/Onnx.cpp`
- `Examples/Framework/src/Framework/Sequencer.cpp`
- `Examples/Framework/src/Utilities/Options.cpp`
- `Examples/Algorithms/AmbiguityResolution/src/ScoreBasedAmbiguityResolutionAlgorithm.cpp`
- `Examples/Algorithms/TrackFindingML/src/AmbiguityResolutionMLAlgorithm.cpp`
- `Fatras/include/ActsFatras/Kernel/Simulation.hpp`
- `Fatras/include/ActsFatras/Kernel/detail/SimulationActor.hpp`
- `Core/include/Acts/AmbiguityResolution/GreedyAmbiguityResolution.hpp`
- `Core/include/Acts/AmbiguityResolution/ScoreBasedAmbiguityResolution.hpp`
- `Core/include/Acts/AmbiguityResolution/AmbiguityResolutionML.hpp`
- `Plugins/Gnn/src/GnnPipeline.cpp`
- `Plugins/Onnx/src/MLTrackClassifier.cpp`
- `Plugins/Onnx/src/OnnxRuntimeBase.cpp`
- `Plugins/Root/src/RootMaterialTrackIo.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
