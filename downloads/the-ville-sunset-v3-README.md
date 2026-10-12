# The Ville — Sunset Character Portal 3.0

Built from `the-ville-multichar-updated (4).zip`.

## Install

1. Back up your current resources and custom configuration.
2. Replace `esx_multicharacter`, `esx_identity`, and `v5_ss` together with the folders inside `[multichar]`. Include their generated `dist` / `web` assets and the new `v5_ss/fxmanifest.lua`; replacing only HTML will not fix spawning.
3. Merge your existing configuration values back into their `config.lua` files. Keep the new scripts and manifest. This package retains your six custom Liberty City destinations.
4. Restart the server and reconnect. Do not run duplicate copies of these resources.

Dependency order:

```cfg
ensure oxmysql
ensure ox_lib
ensure spawnmanager
ensure es_extended
ensure illenium-appearance
ensure esx_identity
ensure v5_ss
ensure esx_multicharacter
```

Keep your current illenium-appearance ESX compatibility bridge enabled. The bundled `cr-3dnui` is retained for compatibility with other resources; this spawn menu no longer needs it. No database schema changes were introduced in 3.0.

## Design

Full-screen, opaque Central Park sunset background, local blackletter font, four tall character slots by default, small settings buttons, and a compact left-aligned creator with pink age/height controls. Character initials are retained from your earlier request; no unrelated faction photos represent your characters. The background is original generated artwork inspired by the reference, rather than the identical source photograph.

Click a character, then **Enter the city**. The gear opens the existing delete confirmation. Empty slots create a character. The creator keeps the supported male/female ESX values. Age presets set January 1 of the corresponding year; expand **Birthday & character details** for an exact birthday, other ages, weight, build, and archetype. Identity saving and appearance customization retain the previous readiness and focus fixes.

## Spawn fix

The previous browser's confirmation button only displayed a preview toast, with no call to the spawn handler. The old scene also pinned the player and relied on separate keyboard controls.

The new **Freeroam** menu is a fullscreen NUI page. Choose Harlem, Downtown, Queens, Brooklyn, The Bronx, Woodbridge, or Last location, then **Enter freeroam**. Mouse and keyboard confirmation send a validated one-based index to `v5_ss/spawn`. The client restores camera, focus, visibility, gravity, collision, movement and the previous routing bucket, teleports to the configured coordinates, and calls the existing multicharacter completion callback exactly once. A bounded collision-streaming wait allows the destination to load. Missing last-location data falls back to Harlem. There is no bus-stop scene, DUI panel, animation wait or pinning loop.

The `openSpawnSelector(lastCoords, callback)` export is retained. `v5_ss/config.lua` contains the destination coordinates. If you change their order/count, update `locations` in `ui-src/app.js` too and rebuild. These coordinates require your custom Liberty City map; this package does not include it.

## Preview and editing

Open **preview.html** in a browser; it is self-contained and works offline. Top-right preview tabs switch screens. Preview actions use sample data; they do not connect to FiveM or teleport a player.

Edit `ui-src/app.js`, `ui-src/app.css`, or `ui-src/assets/`, then run:

```sh
python3 scripts/build-ui.py
```

All runtime assets are bundled. The gothic font includes its OFL license. Server installation needs no Node/npm build step.

## Verification

Automated checks passed: 53 Lua files parsed; 156 mocked Lua assertions covering identity validation, server authorization, persistence, UI focus handoffs, all seven spawn choices, repeated clicks, invalid indexes, failed callbacks, last-location fallback, and resource-stop cleanup. Browser checks passed for offline workflows, responsive layouts, registration, disabled characters, and real NUI spawn POSTs.

```sh
npm ci
npm test
npx playwright install chromium
npm run test:browser
```

Set `CHROMIUM_EXECUTABLE` to an existing Chromium binary when needed. FiveM/GTA and your live SQL server are unavailable here. Verify Harlem and Last location in-game, plus appearance save → movement/chat and reconnect. The included tests cannot verify the ground height or collision at your custom map coordinates.
