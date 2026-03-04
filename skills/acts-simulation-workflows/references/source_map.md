# acts source map: Simulation Workflows

Generated from source roots:
- `Alignment`
- `Core`
- `Fatras`
- `Plugins`
- `Python`
- `codegen`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `simulation`
- `full_chain`
- `material_mapping`
- `ckf`
- `gsf`
- `workflow`
- `plugins`

## Fast source navigation
- `rg -n "full_chain|truth_tracking|material_mapping|material_recording" Examples/Scripts/Python`
- `rg -n "Sequencer|IAlgorithm|WhiteBoard|Options" Examples/Framework/src`
- `rg -n "Simulation|GnnPipeline|OnnxRuntimeBase|RootMaterial" Fatras Plugins`
- `rg -n "test_propagation|test_material|test_examples" Python/Examples/tests`

## Suggested source entry points
- `Examples/Scripts/Python/full_chain_odd.py` | canonical ODD full-chain driver.
- `Examples/Scripts/Python/full_chain_odd_LRT.py` | long-lived track full-chain variant.
- `Examples/Scripts/Python/ckf_tracks.py` | CKF-specific workflow entry.
- `Examples/Scripts/Python/truth_tracking_kalman.py` | truth-tracking + Kalman flow.
- `Examples/Scripts/Python/truth_tracking_gsf.py` | truth-tracking + GSF flow.
- `Examples/Scripts/Python/material_recording.py` | material-track generation stage.
- `Examples/Scripts/Python/material_mapping.py` | material map creation stage.
- `Examples/Scripts/Python/material_validation.py` | material-map validation stage.
- `Examples/Framework/src/Framework/Sequencer.cpp` | algorithm scheduling and event loop behavior.
- `Examples/Framework/src/Utilities/Options.cpp` | run-time option parsing and defaults.
- `Fatras/include/ActsFatras/Kernel/Simulation.hpp` | Fatras simulation kernel interface.
- `Fatras/include/ActsFatras/Kernel/detail/SimulationActor.hpp` | simulation actor execution behavior.
- `Plugins/Onnx/src/OnnxRuntimeBase.cpp` | ONNX runtime execution path.
- `Plugins/Gnn/src/GnnPipeline.cpp` | GNN pipeline orchestration path.
- `Plugins/Gnn/src/runSessionWithIoBinding.hpp` | ONNX IO binding fast path.
- `Plugins/Root/src/RootMaterialTrackIo.cpp` | ROOT material-track IO behavior.
- `Python/Examples/tests/test_examples.py` | end-to-end examples smoke coverage.
- `Python/Examples/tests/test_material.py` | material pipeline behavioral checks.
- `Python/Examples/tests/test_propagation.py` | propagation workflow checks.
- `Tests/IntegrationTests/README.md` | integration test execution model.
