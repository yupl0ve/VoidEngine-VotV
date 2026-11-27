# VoidEngine - Changelog

## [v1.03]
- **Fixed:** Balcony telescope (`SceneCapture` sky lens now renders properly at all times without sacrificing base FPS).
- **Added (Farming & Irrigation):** Whitelisted `farmPot`, `growingPlant`, `sprinkler`, `faucet`, and `beehive` so crops and mushrooms grow at full 1:1 vanilla speed while away from the base.
- **Added (Base Equipment):** Whitelisted crypto mining rigs (`miner`), 3D printers, battery chargers, Roombas, delivery drones, and kitchen appliances (`oven`, `microwave`, `cookingPad`, `coffeeMaker`, buckets, woodchipper) to prevent background timer slowdown.
- **Added (Story & Events):** Global protection for all `trigger` actors and `event` spawners (including rare Ariral events and wall graffiti) to ensure 100% vanilla story progression.

## [v1.02]
- **[Game Breaking] Bugfix:** Signals now download and process at 100% normal speed without any issues.
- **[Game Breaking] Story Protection:** Excluded important map triggers so story events won't break.

## [v1.01]
- **[Game Breaking] Bugfix:** Tapes and cassette players now work properly.
- **Bugfix:** Radar now updates and tracks entities properly.
- **Improvement:** Increased safe initialization delay from 18 seconds to 30 seconds after world load.

## [v1.0]
- Initial release of VoidEngine (Native Rust Rayon Core + Blueprint/C++ Spatial Culling + In-Game `[DELETE]` Overlay).
