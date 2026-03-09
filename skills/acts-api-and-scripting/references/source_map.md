# acts source map: API and Scripting

Generated from source roots:
- `Alignment`
- `Core`
- `Fatras`
- `Plugins`
- `Python`
- `codegen`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `bindings`
- `pybind`
- `setup.sh`
- `ActsPythonBindings`
- `reconstruction`
- `event_data`
- `geometry`
- `visualization`
- `root`
- `json`
- `logging`
- `versioning`

## Fast source navigation
- `rg -n "PYBIND11_MODULE|ActsPythonBindings|add_submodule" Python/Core/src Python/Examples/src Python/Examples/src/plugins Python/Plugins/src`
- `rg -n "setup.sh|ActsPythonBindings|Onnx" Python/Core/setup.sh.in docs/pages/examples/python_bindings.md Python/Examples/python Python/Examples/src/plugins`
- `rg -n "TrackContainer|TrackStateProxy|AnyTrackStateProxy|MultiTrajectory|GenericBoundTrackParameters|Blueprint" Core/include/Acts/EventData Core/include/Acts/Geometry Python/Core/src`
- `rg -n "test_core_basics|test_event_data|test_blueprint|test_alignmentdecorator|AnyTrackStateProxy|MultiTrajectory" Python/Core/tests Python/Examples/tests Tests/UnitTests/Core/EventData`

## Suggested source entry points
- `Python/Core/src/CoreModuleEntry.cpp` | core pybind module initialization and registration.
- `Python/Core/python/__init__.py` | public Python package surface and import glue.
- `Python/Core/setup.sh.in` | generated environment-setup template.
- `Python/Examples/python/reconstruction.py` | high-level helper wrappers and ambiguity configs used by example scripts.
- `Python/Core/src/Propagation.cpp` | propagation bindings.
- `Python/Core/src/Seeding.cpp` | seeding bindings.
- `Python/Core/src/TrackFinding.cpp` | track-finding and ambiguity-related bindings.
- `Python/Core/src/Geometry.cpp` | geometry bindings.
- `Python/Core/src/Visualization.cpp` | 3D visualization bindings.
- `Python/Core/src/MagneticField.cpp` | magnetic-field provider bindings.
- `Python/Core/src/Definitions.cpp` | fundamental enums and types exposed to Python.
- `Python/Examples/src/ExamplesModuleEntry.cpp` | examples module initialization.
- `Python/Examples/src/Framework.cpp` | sequencer and framework bindings.
- `Python/Examples/src/plugins/Alignment.cpp` | alignment plugin bindings.
- `Python/Examples/src/plugins/Onnx.cpp` | ONNX plugin bindings surfaced to Python example workflows.
- `Python/Plugins/src/Root.cpp` | ROOT plugin bindings.
- `Python/Plugins/src/Json.cpp` | JSON plugin bindings.
- `Python/Plugins/src/Geant4.cpp` | Geant4 plugin bindings.
- `Core/include/Acts/EventData/TrackContainer.hpp` | track container surface presented through Python helpers.
- `Core/include/Acts/EventData/TrackStateProxy.hpp` | track-state proxy semantics.
- `Core/include/Acts/EventData/AnyTrackStateProxy.hpp` | type-erased track-state proxy surface.
- `Core/include/Acts/EventData/MultiTrajectory.hpp` | multi-trajectory data model behind high-level track helpers.
- `Core/include/Acts/EventData/GenericBoundTrackParameters.hpp` | bound-parameter conventions surfaced in bindings.
- `Core/include/Acts/Geometry/BlueprintOptions.hpp` | blueprint options exposed to Python geometry helpers.
- `Plugins/Root/src/RootMaterialMapIo.cpp` | ROOT material-map backend reached through plugin bindings.
- `Plugins/Json/src/MaterialMapJsonConverter.cpp` | JSON material-map backend reached through plugin bindings.
- `Python/Core/tests/test_core_basics.py` | binding smoke tests.
- `Python/Core/tests/test_event_data.py` | EventData binding behavior checks.
- `Python/Core/tests/test_blueprint.py` | blueprint binding coverage.
- `Tests/UnitTests/Core/EventData/AnyTrackStateProxyTests.cpp` | track-state proxy behavior checks behind Python-facing EDM helpers.
- `Tests/UnitTests/Core/EventData/MultiTrajectoryTests.cpp` | multi-trajectory behavior checks behind Python-facing EDM helpers.
- `Python/Examples/tests/test_examples.py` | script-level regression coverage.
- `Python/Examples/tests/test_alignmentdecorator.py` | alignment binding and example coverage.
