---
name: acts-analysis-and-output
description: This skill should be used when users ask about analysis and output in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Analysis and Output

## High-Signal Playbook
### Route conditions
- Use this skill for output artifact interpretation, visualization paths, and post-processing guidance.
- Route chain-execution setup to `acts-simulation-workflows`.
- Route build/runtime dependency issues to `acts-build-and-install`.
- Route plugin internals (ROOT/JSON/ONNX) to `acts-developer-guide` when needed.

### Triage questions
- Which outputs are expected (`ROOT`, `CSV`, `OBJ`, visualization objects)?
- Is this a content-quality issue (missing tracks/vertices) or writer/output-format issue?
- Do you need quick artifact sanity checks or deep function-level output behavior?
- Are physmon/hash checks part of the validation requirement?

### Canonical workflow
1. Confirm writer flags and output directory from the run command.
2. Validate artifact presence/non-emptiness before deep analysis.
3. Map missing/incorrect outputs to the corresponding writer or visualization components.
4. Use physmon/hash references for regression interpretation when applicable.
5. Escalate to `references/source_map.md` for function-level behavior in visualization/output classes.

### Minimal working example
```bash
source build/python/setup.sh
python3 Examples/Scripts/Python/full_chain_odd.py -n 5 -o odd_output --output-root --output-csv --output-obj
ls -lh odd_output
```

```bash
pytest -q Python/Examples/tests/test_writer.py
pytest -q Python/Examples/tests/test_reader.py
```

### Pitfalls and fixes
- Empty output files often indicate upstream filtering/selection rather than writer defects.
- Comparing outputs across runs without fixed seeds/settings is not actionable.
- Physmon/hash changes should be inspected, not blindly accepted.
- Visualization outputs depend on geometry/material setup consistency.

### Convergence/validation checks
- Expected output files exist and are non-empty.
- Reader/writer tests pass for affected output formats.
- Run logs and output counts are internally consistent.
- Any output changes are traceable to explicit configuration or code changes.

## Scope
- Handle questions about output formats, analysis, and post-processing.
- Keep responses practical and validation-oriented.

## Primary documentation references
- `docs/old/core/visualization/index.md`
- `docs/old/core/visualization/svg.md`
- `docs/old/contribution/physmon.md`
- `docs/pages/contributing/physmon.md`
- `docs/pages/examples/python_bindings.md`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use examples/tests as executable behavior references.
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
- `Python/Core/src/Visualization.cpp`
- `Core/src/Visualization/GeometryView3D.cpp`
- `Core/src/Visualization/ObjVisualization3D.cpp`
- `Core/src/Visualization/EventDataView3D.cpp`
- `Examples/Framework/src/Root/MuonVisualization.cpp`
- `Core/include/Acts/Visualization/ViewConfig.hpp`
- `Core/include/Acts/EventData/MultiTrajectory.hpp`
- `Core/src/EventData/VectorMultiTrajectory.cpp`
- `Examples/Io/EDM4hep/src/EDM4hepMultiTrajectoryOutputConverter.cpp`
- `Tests/UnitTests/Core/Visualization/EventDataView3DTests.cpp`
- `Tests/UnitTests/Core/Visualization/Visualization3DTests.cpp`
- `Python/Examples/tests/test_writer.py`
- `Python/Examples/tests/test_reader.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
