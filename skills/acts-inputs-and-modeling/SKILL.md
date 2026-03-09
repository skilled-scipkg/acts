---
name: acts-inputs-and-modeling
description: This skill should be used when users ask about inputs and modeling in acts; it prioritizes documentation references and then source inspection only for unresolved details.
---

# acts: Inputs and Modeling

## High-Signal Playbook
### Route conditions
- Use this skill for detector geometry/material setup, track/event-data structures, field/model choices, and input configuration integrity.
- Route to `acts-simulation-workflows` for full end-to-end run control and restart logic.
- Route to `acts-examples-and-tutorials` for script selection and usage walkthroughs.
- Route to `acts-groups` when the question is purely algorithm-family internals (seeding, track finding, vertexing APIs).

### Triage questions
- Which detector description path is used (ODD/DD4hep/GeoModel/TGeo/custom)?
- Is the issue in geometry construction/material mapping or in track/event-data containers and parameter conventions?
- Are you mapping material to surfaces, volumes, or both?
- Do you already have a geometry JSON map, or do you need to generate/edit one?
- What map format do you need (`.json`, `.cbor`, ROOT side products)?
- Are Geant4 material tracks already available, or do you need recording first?
- Are you seeing configuration warnings (mapping type, surface association, binning sparsity)?

### Canonical workflow
1. Ensure required build options are enabled for the intended path (examples + Geant4 + JSON plugin; optionally DD4hep/ROOT for ODD flows) from `docs/old/examples/howto/material_mapping.rst`.
2. Generate detector geometry inventory via `Examples/Scripts/Python/geometry.py` (JSON output path in same doc).
3. Select mapping targets and binning (`mapMaterial`, `bins`, `mappingType`) in geometry JSON; optionally use `writeMapConfig.py` and `configureMap.py`.
4. Record material with geantino scan using `Examples/Scripts/Python/material_recording.py`.
5. Produce material map with `Examples/Scripts/Python/material_mapping.py` (surface/volume switches, `mappingStep`, cache mode).
6. Validate map with `Examples/Scripts/Python/material_validation.py` and ROOT validation macros listed in the how-to.
7. Iterate binning/mapping targets until validation ratios and coverage stabilize.

### Minimal working example
```bash
git submodule init
git submodule update

python3 Examples/Scripts/Python/geometry.py
python3 Examples/Scripts/Python/material_recording.py -n 10 -t 200
python3 Examples/Scripts/Python/material_mapping.py -o material-map.json
python3 Examples/Scripts/Python/material_validation.py
```

### Pitfalls and fixes
- Mapping on surfaces inside material volumes can silently distort results; follow the surface/volume separation warning in `docs/old/examples/howto/material_mapping.rst`.
- `PostMapping` after `PreMapping`/`Sensor` can absorb inter-surface material unexpectedly; adjust mapping-type ordering.
- Too-large `mappingStep` biases volume mapping; keep it small versus bin size (same doc).
- Reusing cached surface info after changing mapped surfaces gives inconsistent output; disable cache when mapping topology changes.
- Validation mismatches can come from different generation distributions (`z0`/`d0`, `theta` vs `eta`); align settings before judging quality.
- Track-EDM debugging often comes from mixing free/bound parameter conventions; cross-check with the EventData tests before changing storage code.
- ODD flows fail if detector submodule/config is missing; initialize/update submodules before running scripts.

### Convergence/validation checks
- Geometry JSON contains intended `mapMaterial=true` surfaces/volumes and reasonable bin counts.
- Mapping run emits expected outputs (`material-map.json`/`.cbor` and material-track ROOT files).
- Surface/volume validation plots are stable across reruns with fixed seeds and event counts.
- Material ratio plots are near-unity in tuned detector regions and improve with binning iterations.
- Track containers/proxies expose the expected reference-surface and parameter state in the nearest EventData unit tests.
- Chosen field/material provider pairing is consistent with the propagation path under study.

### Source-code entry links
- `Examples/Scripts/Python/geometry.py` (detector/geometry inventory and JSON emission).
- `Examples/Scripts/Python/geomodel.py` (GeoModel-to-ACTS geometry conversion path).
- `Examples/Scripts/Python/blueprint.py` (blueprint geometry authoring path).
- `Examples/Scripts/Python/material_recording.py` (Geant4 material-track production path).
- `Examples/Scripts/Python/material_mapping.py` (surface/volume mapper configuration and writer wiring).
- `Core/include/Acts/Material/TrackingGeometryMaterial.hpp` (material model interfaces).
- `Core/include/Acts/EventData/GenericBoundTrackParameters.hpp` (bound parameter conventions and creation helpers).
- `Core/include/Acts/EventData/TrackStateProxy.hpp` (track-state proxy semantics for current Track EDM).
- `Core/include/Acts/EventData/AnyTrackStateProxy.hpp` (type-erased track-state access for mixed containers).
- `Core/include/Acts/EventData/TrackContainer.hpp` (high-level track container and proxy entry point).
- `Core/src/Geometry/MaterialDesignatorBlueprintNode.cpp` (material assignment on geometry blueprint nodes).
- `Plugins/Json/src/MaterialMapJsonConverter.cpp` (JSON material map conversion path).
- `Plugins/Root/src/RootMaterialMapIo.cpp` (ROOT material map IO path).
- `Core/include/Acts/Geometry/GeometryHierarchyMap.hpp` (geometry hierarchy mapping primitives).

## Scope
- Handle questions about inputs, system setup, models, and physical parameterization.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/old/core/geometry/index.md`
- `docs/pages/tracking.md`
- `docs/old/tracking.md`
- `docs/old/contribution/documentation_cheatsheet.md`
- `docs/groups/eventdata/tracks.md`
- `docs/old/examples/howto/material_mapping.rst`
- `docs/old/core/geometry/concepts.md`
- `docs/old/examples/howto/add_new_algorithm.md`
- `docs/old/core/misc/grid_axis.md`
- `docs/old/core/geometry/surfaces.md`
- `docs/old/core/geometry/construction.md`
- `docs/old/core/eventdata/tracks.md`

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
- `Examples/Scripts/Python/geomodel.py`
- `Examples/Scripts/Python/blueprint.py`
- `Examples/Scripts/Python/material_recording.py`
- `Examples/Scripts/Python/material_mapping.py`
- `Core/include/Acts/Material/TrackingGeometryMaterial.hpp`
- `Core/include/Acts/EventData/GenericBoundTrackParameters.hpp`
- `Core/include/Acts/EventData/TrackStateProxy.hpp`
- `Core/include/Acts/EventData/AnyTrackStateProxy.hpp`
- `Core/include/Acts/EventData/MultiComponentTrackParameters.hpp`
- `Core/include/Acts/EventData/TrackContainer.hpp`
- `Core/include/Acts/EventData/MultiTrajectory.hpp`
- `Core/include/Acts/Geometry/BlueprintOptions.hpp`
- `Core/include/Acts/Geometry/ContainerBlueprintNode.hpp`
- `Plugins/Json/src/MaterialMapJsonConverter.cpp`
- `Plugins/Root/src/RootMaterialMapIo.cpp`
- `Plugins/Json/include/ActsPlugins/Json/GeometryHierarchyMapJsonConverter.hpp`
- `Plugins/GeoModel/src/GeoModelMaterialConverter.cpp`
- `Plugins/GeoModel/include/ActsPlugins/GeoModel/GeoModelMaterialConverter.hpp`
- `Tests/UnitTests/Core/EventData/AnyTrackStateProxyTests.cpp`
- `Tests/UnitTests/Core/EventData/MultiTrajectoryTests.cpp`
- `Tests/UnitTests/Plugins/Json/GeometryHierarchyMapJsonConverterTests.cpp`
- `Core/src/Geometry/MaterialDesignatorBlueprintNode.cpp`
- `Core/src/Geometry/MaterialDesignator.hpp`
- `Core/include/Acts/Geometry/MaterialDesignatorBlueprintNode.hpp`
- `Core/include/Acts/Geometry/GeometryHierarchyMap.hpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).
