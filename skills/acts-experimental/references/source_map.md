# acts source map: Experimental

Generated from source roots:
- `Alignment`
- `Core`
- `Fatras`
- `Plugins`
- `Python`
- `codegen`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `experimental`
- `alignment`
- `blueprint`
- `itk`
- `material_designator`
- `seeding2`
- `gbts`
- `triplet_seed`
- `multilayer_navigation`

## Fast source navigation
- `rg -n "Acts::Experimental|namespace Experimental|Alignment|full_chain_itk_Gbts" Alignment Core/include Core/src Python/Examples/src Examples/Scripts/Python`
- `rg -n "Blueprint|ContainerBlueprintNode|MaterialDesignator|AlignmentEngine|GraphBasedTrackSeeder|TripletSeedFinder|Gbts|MultiLayerNavigation" Alignment Core/include Core/src`
- `rg -n "BlueprintTests|AlignmentContextTests|test_alignmentdecorator|HistogramTests" Tests/UnitTests/Core Python/Examples/tests`

## Suggested source entry points
- `Examples/Scripts/Python/blueprint.py` | minimal blueprint authoring example.
- `Examples/Scripts/Python/full_chain_itk_Gbts.py` | ITk GBTS workflow using experimental seeding components.
- `Python/Examples/src/plugins/Alignment.cpp` | Python alignment plugin bindings.
- `Alignment/include/ActsAlignment/Kernel/Alignment.hpp` | alignment kernel API.
- `Alignment/include/ActsAlignment/Kernel/AlignmentMask.hpp` | alignment parameter masking.
- `Alignment/include/ActsAlignment/Kernel/detail/AlignmentEngine.hpp` | derivative accumulation and per-track alignment state.
- `Alignment/src/Kernel/detail/AlignmentEngine.cpp` | alignment engine implementation.
- `Core/include/Acts/Geometry/Blueprint.hpp` | experimental blueprint root object.
- `Core/src/Geometry/Blueprint.cpp` | blueprint construction behavior.
- `Core/include/Acts/Geometry/BlueprintNode.hpp` | blueprint node contract.
- `Core/src/Geometry/BlueprintNode.cpp` | node build and resolve behavior.
- `Core/src/Geometry/StaticBlueprintNode.cpp` | static blueprint node behavior.
- `Core/src/Geometry/LayerBlueprintNode.cpp` | layered blueprint node behavior.
- `Core/include/Acts/Geometry/BlueprintOptions.hpp` | blueprint build options.
- `Core/include/Acts/Geometry/ContainerBlueprintNode.hpp` | composite blueprint node behavior.
- `Core/src/Geometry/MaterialDesignator.hpp` | internal helper for blueprint material designation.
- `Core/include/Acts/Geometry/MaterialDesignatorBlueprintNode.hpp` | material designator node.
- `Core/src/Geometry/MaterialDesignatorBlueprintNode.cpp` | material designator implementation.
- `Core/include/Acts/Seeding2/GraphBasedTrackSeeder.hpp` | Seeding2 graph-based seeder interface.
- `Core/src/Seeding2/GraphBasedTrackSeeder.cpp` | Seeding2 algorithm behavior.
- `Core/src/Seeding2/TripletSeedFinder.cpp` | triplet seed generation used by GBTS flows.
- `Core/include/Acts/Seeding2/GbtsTrackingFilter.hpp` | GBTS filter interface.
- `Core/src/Seeding2/GbtsTrackingFilter.cpp` | GBTS filtering behavior.
- `Core/include/Acts/Navigation/MultiLayerNavigationPolicy.hpp` | experimental multilayer navigation policy.
- `Core/src/Navigation/MultiLayerNavigationPolicy.cpp` | multilayer navigation behavior.
- `Tests/UnitTests/Core/Geometry/BlueprintTests.cpp` | blueprint behavior checks.
- `Tests/UnitTests/Core/Geometry/BlueprintApiTests.cpp` | blueprint API compatibility checks.
- `Tests/UnitTests/Core/Geometry/AlignmentContextTests.cpp` | geometry and alignment interaction checks.
- `Python/Examples/tests/test_alignmentdecorator.py` | Python alignment decorator coverage.
- `Tests/UnitTests/Core/Utilities/HistogramTests.cpp` | histogram utility coverage used by experimental helpers.
