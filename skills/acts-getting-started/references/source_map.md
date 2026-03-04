# acts source map: Getting Started

Generated from source roots:
- `Alignment`
- `Core`
- `Fatras`
- `Plugins`
- `Python`
- `codegen`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `quickstart`
- `propagation`
- `seeding`
- `track_finding`
- `python`
- `examples`

## Fast source navigation
- `rg -n "Sequencer|Options|randomNumbers|events" Examples/Framework/src`
- `rg -n "Propagation|Seeding|TrackFinding|Navigation" Examples/Scripts/Python Python/Core/src`
- `rg -n "Propagator|Navigator|SeedFinder|CombinatorialKalman" Core/include Core/src Tests/UnitTests/Core`

## Suggested source entry points
- `Examples/Scripts/Python/geometry.py` | first geometry/load sanity check script.
- `Examples/Scripts/Python/propagation.py` | minimal propagation run path.
- `Examples/Scripts/Python/seeding.py` | starter seeding configuration and execution.
- `Examples/Scripts/Python/ckf_tracks.py` | simple track finding pipeline.
- `Examples/Scripts/Python/truth_tracking_kalman.py` | end-to-end truth + fitting starter flow.
- `Examples/Framework/src/Framework/Sequencer.cpp` | sequencing and algorithm scheduling semantics.
- `Examples/Framework/src/Utilities/Options.cpp` | CLI option defaults and overrides.
- `Python/Core/src/Propagation.cpp` | Python bindings for propagator behavior.
- `Python/Core/src/Navigation.cpp` | Python bindings for navigation behavior.
- `Python/Core/src/Seeding.cpp` | Python bindings for seeding APIs.
- `Python/Core/src/TrackFinding.cpp` | Python bindings for track-finding APIs.
- `Core/include/Acts/Propagator/Propagator.hpp` | propagation interface anchor.
- `Core/include/Acts/Propagator/Navigator.hpp` | navigator behavior anchor.
- `Core/include/Acts/Seeding/SeedFinder.hpp` | seeding interface anchor.
- `Tests/UnitTests/Core/Propagator/KalmanExtrapolatorTests.cpp` | propagation behavior checks.
- `Tests/UnitTests/Core/Seeding/SeedFinderTest.cpp` | seeding behavior checks.
- `Tests/UnitTests/Core/TrackFinding/CombinatorialKalmanFilterTests.cpp` | CKF behavior checks.
