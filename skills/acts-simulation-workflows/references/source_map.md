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
- `sequencer`
- `full_chain`
- `gbts`
- `itk`
- `material_mapping`
- `ckf`
- `ambiguity`
- `ml_ambiguity`
- `vertexing`
- `fatras`
- `onnx`

## Fast source navigation
- `rg -n "full_chain_odd|full_chain_itk_Gbts|ckf_tracks|truth_tracking_|material_(recording|mapping|validation)" Examples/Scripts/Python`
- `rg -n "addAmbiguityResolution|addScoreBasedAmbiguityResolution|addAmbiguityResolutionML|addCKFTracks|addVertexFitting" Python/Examples/python`
- `rg -n "AmbiguityResolution|ScoreBasedAmbiguityResolution|solveAmbiguity|GreedyAmbiguityResolution" Core/include/Acts/AmbiguityResolution`
- `rg -n "AmbiguityResolutionMLAlgorithm|ScoreBasedAmbiguityResolutionAlgorithm|Onnx" Examples/Algorithms Python/Examples/src`
- `rg -n "OnnxRuntimeBase|MLTrackClassifier|GnnPipeline|Simulation" Plugins/Onnx Plugins/Gnn Fatras`
- `rg -n "test_ML_Ambiguity_Solver|test_material|test_examples|test_propagation" Python/Examples/tests`

## Suggested source entry points
- `Examples/Scripts/Python/full_chain_odd.py` | canonical ODD full-chain driver and ambiguity mode selection.
- `Examples/Scripts/Python/full_chain_odd_LRT.py` | long-lived-track full-chain variant.
- `Examples/Scripts/Python/full_chain_itk_Gbts.py` | ITk GBTS full-chain workflow and experimental seeding path.
- `Examples/Scripts/Python/ckf_tracks.py` | CKF-specific workflow baseline.
- `Examples/Scripts/Python/truth_tracking_kalman.py` | truth-tracking plus Kalman flow.
- `Examples/Scripts/Python/material_recording.py` | material-track generation stage.
- `Examples/Scripts/Python/material_mapping.py` | material map creation stage.
- `Examples/Framework/src/Framework/Sequencer.cpp` | algorithm scheduling and event-loop behavior.
- `Examples/Framework/src/Utilities/Options.cpp` | runtime option parsing and defaults.
- `Examples/Algorithms/AmbiguityResolution/src/ScoreBasedAmbiguityResolutionAlgorithm.cpp` | example-level score-based ambiguity orchestration.
- `Examples/Algorithms/TrackFindingML/src/AmbiguityResolutionMLAlgorithm.cpp` | example-level ML ambiguity workflow wiring.
- `Python/Examples/python/reconstruction.py` | helper wrappers and default configs for seeding, CKF, ambiguity, and vertexing.
- `Python/Examples/src/plugins/Onnx.cpp` | Python examples ONNX binding surface used by ML ambiguity flows.
- `Fatras/include/ActsFatras/Kernel/Simulation.hpp` | Fatras simulation kernel interface.
- `Fatras/include/ActsFatras/Kernel/detail/SimulationActor.hpp` | stepwise simulation execution behavior.
- `Core/include/Acts/AmbiguityResolution/GreedyAmbiguityResolution.hpp` | baseline duplicate-removal logic.
- `Core/include/Acts/AmbiguityResolution/ScoreBasedAmbiguityResolution.hpp` | score-based ambiguity scoring and pruning.
- `Core/include/Acts/AmbiguityResolution/AmbiguityResolutionML.hpp` | ONNX-backed ambiguity solver interface.
- `Plugins/Onnx/src/OnnxRuntimeBase.cpp` | ONNX session setup and runtime behavior.
- `Plugins/Onnx/src/MLTrackClassifier.cpp` | ML classifier plumbing for ambiguity workflows.
- `Plugins/Gnn/src/GnnPipeline.cpp` | graph-neural-network orchestration path.
- `Plugins/Gnn/src/runSessionWithIoBinding.hpp` | GPU and IO-binding execution path.
- `Plugins/Root/src/RootMaterialTrackIo.cpp` | ROOT material-track IO behavior.
- `Tests/UnitTests/Core/AmbiguityResolution/ScoreBasedAmbiguityResolutionTest.cpp` | ambiguity scoring behavior checks.
- `Python/Examples/tests/test_examples.py` | end-to-end script smoke and regression coverage, including ML ambiguity.
- `Python/Examples/tests/test_material.py` | material pipeline behavior checks.
- `Python/Examples/tests/test_propagation.py` | propagation workflow behavior checks.
- `Tests/IntegrationTests/README.md` | integration-test execution model.
