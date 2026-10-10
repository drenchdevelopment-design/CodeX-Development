# City navigation — mini-map 2.0

A standalone FiveM minimap update with a charcoal frame, mint details, compass, street/cross-street information, vehicle speed, and compact health/armor bars. Works without ESX or QBCore. Your original custom city textures and streaming assets are preserved byte-for-byte.

## Install

1. Back up your current `mini-map` resource.
2. Stop the old resource and replace it with the `mini-map` folder in this ZIP. Do not nest the folder inside another `mini-map` folder.
3. Keep `ensure mini-map` in `server.cfg` and restart the server, or use `refresh` followed by `ensure mini-map` for a stopped resource.
4. Disable the radar frame, placement, speed, and health/armor portions of any competing HUD to avoid duplicate overlays. This resource controls radar visibility and position.

The runtime resource has no package installation, database migration, external fonts, network assets, or keyboard/mouse capture. The preview and documentation stay outside the installed resource.

## Preview

Open `preview.html` in a browser. It is self-contained and works offline. Try Driving / On foot, the speed slider, and the route toggle. Preview player information and the illustrated route are sample data. In-game GPS lines, map rotation, and blips remain native GTA rendering.

## Options

Edit `mini-map/config.lua`:

- `SpeedUnit`: `mph` or `kmh`.
- `ShowOnFoot`: show the map while walking, or only in vehicles.
- `ShowVitals`: show the replacement health/armor bars. When false, the native strip is retained.
- `Accent`: six-digit hex color.
- `Placement`: native radar coordinates, relative to the left/bottom anchors. The default reserves room for the information panel on smaller screens.
- `CustomPlacement`: use false only for the stock radar anchor. Another resource moving the radar will also require matching frame coordinates.
- `UpdateInterval`: information refresh interval in milliseconds, minimum 100.

Street and district text use GTA's native street/zone names. The supplied ZIP contains texture artwork, not a street-name database; custom city label replacements depend on your server's naming resource. The example location in the browser preview is illustrative.

## Validation and deployment check

Passed Lua parsing; 23 client behavior assertions using mocked GTA natives; browser checks for the offline preview controls, mobile fit, NUI show/hide, transparent map window, clamped values, safe text rendering, and the vitals option. All original stream file hashes match. ZIP integrity checked.

A FiveM client was not available in this environment. Before deploying to players, check the map/frame alignment at your preferred resolution and safe-zone setting, GPS route visibility, driving/walking, pause menu behavior, and conflicts with your existing HUD. GTA-rendered placement cannot be validated by the browser preview.

No server logo is added by this HUD. Logos from unrelated resources are not modified.
