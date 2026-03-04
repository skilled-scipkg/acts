# acts source map: Build and Install

Generated from source roots:
- `Alignment`
- `Core`
- `Fatras`
- `Plugins`
- `Python`
- `codegen`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `build`
- `cmake`
- `dependencies`
- `plugins`
- `python_bindings`
- `install`
- `downstream`

## Fast source navigation
- `rg -n "ACTS_BUILD_|option\(|find_package|add_subdirectory" CMakeLists.txt Plugins Python Examples Tests`
- `rg -n "ActsPythonBindings|ExamplesModuleEntry|CoreModuleEntry|setup.sh" Python/Core Python/Examples`
- `rg -n "DownstreamProject|IntegrationTests" Tests`

## Suggested source entry points
- `CMakePresets.json` | presets used for dev/CI configure paths.
- `CMakeLists.txt` | top-level option graph and dependency gates.
- `Plugins/CMakeLists.txt` | plugin option wiring and component dependencies.
- `Python/Core/CMakeLists.txt` | core Python module build and setup script generation.
- `Python/Examples/CMakeLists.txt` | examples module wiring and plugin-conditional bindings.
- `Examples/Framework/CMakeLists.txt` | framework linking behavior for optional components.
- `Python/Core/src/CoreModuleEntry.cpp` | pybind module entry for `acts`.
- `Python/Examples/src/ExamplesModuleEntry.cpp` | pybind module entry for `acts.examples`.
- `Python/Examples/src/Framework.cpp` | bindings that expose sequencer/runtime orchestration.
- `Examples/Framework/src/Framework/Sequencer.cpp` | runtime execution flow for example chains.
- `Examples/Framework/src/Utilities/Options.cpp` | CLI/config option parsing used by examples.
- `Plugins/Geant4/CMakeLists.txt` | Geant4-specific build requirements and flags.
- `Plugins/DD4hep/CMakeLists.txt` | DD4hep-specific build requirements and flags.
- `Plugins/Gnn/CMakeLists.txt` | GNN/ONNX plugin build toggles and dependencies.
- `Plugins/Onnx/CMakeLists.txt` | ONNX runtime build linkage.
- `Tests/DownstreamProject/CMakeLists.txt` | reference downstream integration wiring.
- `Tests/DownstreamProjectNodeps/CMakeLists.txt` | minimal downstream wiring without optional deps.
- `Tests/IntegrationTests/CMakeLists.txt` | integration-test target registration semantics.
