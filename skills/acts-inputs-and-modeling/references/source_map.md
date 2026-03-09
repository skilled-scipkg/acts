# acts source map: Inputs and Modeling

Generated from source roots:
- `Alignment`
- `Core`
- `Fatras`
- `Plugins`
- `Python`
- `codegen`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `geometry`
- `material`
- `geomodel`
- `blueprint`
- `hierarchy_map`
- `eventdata`
- `track_parameters`
- `track_container`
- `surface`
- `volume_builder`

## Fast source navigation
- `rg -n "geometry.py|geomodel.py|blueprint.py|material_(recording|mapping|validation)" Examples/Scripts/Python`
- `rg -n "GenericBoundTrackParameters|MultiComponentTrackParameters|TrackContainer|TrackProxy|TrackStateProxy|AnyTrackStateProxy|MultiTrajectory" Core/include/Acts/EventData`
- `rg -n "BlueprintOptions|ContainerBlueprintNode|GeometryHierarchyMap|CuboidVolumeBuilder|CylinderVolumeBuilder" Core/include/Acts/Geometry Core/src/Geometry`
- `rg -n "MaterialMapJsonConverter|RootMaterialMapIo|GeoModelMaterialConverter" Plugins/Json Plugins/Root Plugins/GeoModel`
- `rg -n "TrackTests|AnyTrackProxyTests|AnyTrackStateProxyTests|MultiTrajectoryTests|BoundTrackParametersTests|GeometryHierarchyMapTests|GeometryHierarchyMapJsonConverterTests|CylinderVolumeBuilderTests|CuboidVolumeBuilderTests" Tests/UnitTests/Core Tests/UnitTests/Plugins`

## Suggested source entry points
- `Examples/Scripts/Python/geometry.py` | detector inventory and JSON geometry export.
- `Examples/Scripts/Python/geomodel.py` | GeoModel conversion path and blueprint-to-builder handoff.
- `Examples/Scripts/Python/blueprint.py` | minimal blueprint geometry authoring example.
- `Examples/Scripts/Python/material_recording.py` | geantino material-track production.
- `Examples/Scripts/Python/material_mapping.py` | surface and volume material mapping driver.
- `Core/include/Acts/Material/TrackingGeometryMaterial.hpp` | top-level material interfaces on tracking geometry.
- `Core/include/Acts/Geometry/GeometryHierarchyMap.hpp` | geometry hierarchy addressing primitives.
- `Core/include/Acts/Geometry/BlueprintOptions.hpp` | blueprint build options and validation.
- `Core/include/Acts/Geometry/ContainerBlueprintNode.hpp` | hierarchical geometry container node.
- `Core/include/Acts/Geometry/ApproachDescriptor.hpp` | layer and approach-surface association.
- `Core/include/Acts/Geometry/CuboidVolumeBuilder.hpp` | cuboid volume construction interface.
- `Core/include/Acts/Geometry/CylinderVolumeBuilder.hpp` | cylindrical volume construction interface.
- `Core/include/Acts/Geometry/CylinderVolumeHelper.hpp` | helper utilities for layered tracking volumes.
- `Core/include/Acts/Geometry/DetectorElementBase.hpp` | detector-element transform and thickness contract.
- `Core/include/Acts/EventData/GenericBoundTrackParameters.hpp` | bound-parameter creation and reference-surface semantics.
- `Core/include/Acts/EventData/TrackStateProxy.hpp` | per-state proxy access patterns in the current Track EDM.
- `Core/include/Acts/EventData/AnyTrackStateProxy.hpp` | type-erased state proxy used across mixed trajectory backends.
- `Core/include/Acts/EventData/MultiComponentTrackParameters.hpp` | multi-component track-parameter representation.
- `Core/include/Acts/EventData/TrackContainer.hpp` | high-level track container API and mutation entry point.
- `Core/include/Acts/EventData/TrackProxy.hpp` | proxy accessors for per-track state.
- `Core/include/Acts/EventData/AnyTrackProxy.hpp` | type-erased track-proxy surface.
- `Core/include/Acts/EventData/MultiTrajectory.hpp` | underlying multi-trajectory storage model.
- `Plugins/Json/include/ActsPlugins/Json/GeometryHierarchyMapJsonConverter.hpp` | hierarchy-map JSON conversion.
- `Plugins/Json/src/MaterialMapJsonConverter.cpp` | material-map JSON IO behavior.
- `Plugins/Root/src/RootMaterialMapIo.cpp` | ROOT material-map IO behavior.
- `Plugins/GeoModel/src/GeoModelMaterialConverter.cpp` | GeoModel material-conversion path.
- `Core/src/Geometry/MaterialDesignator.hpp` | internal blueprint material-designator helper.
- `Tests/UnitTests/Core/EventData/TrackTests.cpp` | track container and proxy behavior checks.
- `Tests/UnitTests/Core/EventData/AnyTrackStateProxyTests.cpp` | type-erased state-proxy behavior.
- `Tests/UnitTests/Core/EventData/MultiTrajectoryTests.cpp` | multi-trajectory storage behavior.
- `Tests/UnitTests/Core/EventData/AnyTrackProxyTests.cpp` | type-erased proxy behavior.
- `Tests/UnitTests/Core/EventData/BoundTrackParametersTests.cpp` | bound-parameter semantics.
- `Tests/UnitTests/Core/EventData/MultiComponentBoundTrackParametersTests.cpp` | multi-component parameter behavior.
- `Tests/UnitTests/Core/Geometry/GeometryHierarchyMapTests.cpp` | hierarchy-map behavior checks.
- `Tests/UnitTests/Plugins/Json/GeometryHierarchyMapJsonConverterTests.cpp` | hierarchy-map JSON conversion checks.
- `Tests/UnitTests/Core/Geometry/CylinderVolumeBuilderTests.cpp` | cylindrical builder behavior.
- `Tests/UnitTests/Core/Geometry/CuboidVolumeBuilderTests.cpp` | cuboid builder behavior.
- `Python/Examples/tests/test_geometry.py` | Python geometry example regression checks.
- `Python/Examples/tests/test_material.py` | material workflow regression checks.
