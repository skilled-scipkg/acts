# acts source map: Tests

Generated from source roots:
- `Alignment`
- `Core`
- `Fatras`
- `Plugins`
- `Python`
- `codegen`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `integrationtests`
- `unittests`
- `seeding`
- `trackfinding`
- `propagation`
- `material`

## Fast source navigation
- `rg -n "BOOST_AUTO_TEST|TEST_CASE|EXPECT" Tests/UnitTests/Core Tests/IntegrationTests Python/Examples/tests`
- `rg -n "SeedFinder|CombinatorialKalman|KalmanExtrapolator|Material" Core/include Core/src Tests/UnitTests/Core`
- `rg -n "pytest|hash|writer|reader|propagation|material" Python/Examples/tests`

## Suggested source entry points
- `Tests/IntegrationTests/README.md` | integration-test conventions and execution model.
- `Tests/Data/README.md` | data fixture conventions.
- `Tests/UnitTests/Core/Seeding/SeedFinderTest.cpp` | core seeding behavior checks.
- `Tests/UnitTests/Core/Seeding/EstimateTrackParamsFromSeedTest.cpp` | seed-parameter estimation checks.
- `Tests/UnitTests/Core/TrackFinding/CombinatorialKalmanFilterTests.cpp` | CKF behavior checks.
- `Tests/UnitTests/Core/Propagator/KalmanExtrapolatorTests.cpp` | propagation behavior checks.
- `Tests/UnitTests/Core/Material/MaterialValidaterTests.cpp` | material validation behavior checks.
- `Tests/UnitTests/Core/EventData/MultiTrajectoryTests.cpp` | trajectory data-structure behavior checks.
- `Tests/UnitTests/Core/Visualization/EventDataView3DTests.cpp` | visualization behavior checks.
- `Python/Examples/tests/test_examples.py` | python examples smoke coverage.
- `Python/Examples/tests/test_propagation.py` | python propagation checks.
- `Python/Examples/tests/test_material.py` | python material-flow checks.
- `Core/include/Acts/Seeding/SeedFinder.hpp` | implementation anchor for seeding tests.
- `Core/src/Seeding/EstimateTrackParamsFromSeed.cpp` | implementation anchor for seed parameter tests.
- `Core/include/Acts/TrackFinding/CombinatorialKalmanFilter.hpp` | implementation anchor for CKF tests.
- `Core/include/Acts/Propagator/Propagator.hpp` | implementation anchor for propagation tests.
