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
- `blueprint`
- `seeding2`
- `gbts`
- `multilayer_navigation`

## Fast source navigation
- `rg -n "Acts::Experimental|namespace Experimental" Core Plugins Examples Python`
- `rg -n "Blueprint|MaterialDesignator|GraphBasedTrackSeeder|Gbts|MultiLayerNavigation" Core/include Core/src`
- `rg -n "BlueprintTests|HistogramTests" Tests/UnitTests/Core`

## Suggested source entry points
- `Core/include/Acts/Geometry/Blueprint.hpp` | experimental geometry blueprint interface.
- `Core/src/Geometry/Blueprint.cpp` | blueprint construction and node wiring behavior.
- `Core/include/Acts/Geometry/BlueprintNode.hpp` | experimental node contract.
- `Core/src/Geometry/BlueprintNode.cpp` | node build/resolve behavior.
- `Core/include/Acts/Geometry/MaterialDesignatorBlueprintNode.hpp` | material annotation blueprint node.
- `Core/src/Geometry/MaterialDesignatorBlueprintNode.cpp` | material designator implementation.
- `Core/include/Acts/Seeding2/GraphBasedTrackSeeder.hpp` | seeding2 graph-based seeder interface.
- `Core/src/Seeding2/GraphBasedTrackSeeder.cpp` | seeding2 graph-based algorithm behavior.
- `Core/include/Acts/Seeding2/GbtsTrackingFilter.hpp` | GBTS filtering interface.
- `Core/src/Seeding2/GbtsTrackingFilter.cpp` | GBTS filtering implementation.
- `Core/include/Acts/Navigation/MultiLayerNavigationPolicy.hpp` | experimental multilayer navigation policy.
- `Core/src/Navigation/MultiLayerNavigationPolicy.cpp` | multilayer navigation behavior.
- `Core/include/Acts/Utilities/Histogram.hpp` | experimental histogram utility API.
- `Core/src/Utilities/Histogram.cpp` | histogram utility implementation.
- `Plugins/Json/include/ActsPlugins/Json/Seeding2ConfigJsonConverter.hpp` | seeding2 JSON configuration conversion API.
- `Plugins/Json/src/Seeding2ConfigJsonConverter.cpp` | seeding2 JSON conversion behavior.
- `Tests/UnitTests/Core/Geometry/BlueprintTests.cpp` | blueprint behavior checks.
- `Tests/UnitTests/Core/Geometry/BlueprintApiTests.cpp` | blueprint API compatibility checks.
- `Tests/UnitTests/Core/Utilities/HistogramTests.cpp` | histogram behavior checks.
