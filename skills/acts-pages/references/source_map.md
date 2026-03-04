# acts source map: Pages

Generated from source roots:
- `Alignment`
- `Core`
- `Fatras`
- `Plugins`
- `Python`
- `codegen`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `bugs`
- `deprecated`
- `todo`
- `diagnostics`

## Fast source navigation
- `rg -n "deprecated|TODO|FIXME|warning|error" Core/include Core/src Plugins Python`
- `rg -n "Result|Logger|ThrowAssert|PropagatorError|SurfaceError" Core/include Core/src`
- `rg -n "LoggerTests|ResultTests|Error" Tests/UnitTests/Core`

## Suggested source entry points
- `Core/include/Acts/Utilities/Result.hpp` | result/error propagation helper used across algorithms.
- `Core/include/Acts/Utilities/Logger.hpp` | logging contracts and level semantics.
- `Core/src/Utilities/Logger.cpp` | logging backend behavior and formatting.
- `Core/include/Acts/Utilities/ThrowAssert.hpp` | assertion/exception boundary behavior.
- `Core/include/Acts/Utilities/Diagnostics.hpp` | warning/diagnostic suppression and policy points.
- `Core/include/Acts/Definitions/Algebra.hpp` | deprecated alias markers and compatibility notes.
- `Core/include/Acts/Definitions/TrackParametrization.hpp` | deprecated matrix aliases and migration hints.
- `Core/include/Acts/Geometry/GeometryContext.hpp` | deprecated constructor path and replacement API.
- `Core/include/Acts/Surfaces/Surface.hpp` | deprecated surface APIs and preferred replacements.
- `Core/include/Acts/Propagator/PropagatorError.hpp` | propagator error taxonomy.
- `Core/src/Propagator/PropagatorError.cpp` | propagator error category implementation.
- `Core/include/Acts/Surfaces/SurfaceError.hpp` | surface error taxonomy.
- `Core/src/Surfaces/SurfaceError.cpp` | surface error category implementation.
- `Tests/UnitTests/Core/Utilities/ResultTests.cpp` | regression checks for result semantics.
- `Tests/UnitTests/Core/Utilities/LoggerTests.cpp` | regression checks for logger behavior.
