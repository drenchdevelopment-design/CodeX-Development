# Upstate 1.2 — integrated collision rebuild

This replaces the crashing `certi_upstate` addon. The bridge remains included. Keep the `mini-map` resource from the previous bridge package.

## Install
1. Stop the server.
2. DELETE the old `certi_upstate` resource directory before extracting this replacement. Copying over the old directory leaves obsolete YBN files behind.
3. Put the included `certi_upstate` directory in your server resources directory. Keep `ensure certi_upstate` in server.cfg.
4. Restart the server and reconnect. Run only one copy of this addon.

## Targeted change
The previous build referenced its standalone world collision files through the placement YMAP's physicsDictionaries array. This build removes that dependency path and embeds each collision mesh in its matching YDR, with model-local coordinates and matching YTYP physics registration. The obsolete standalone YBN files are removed from the streamed resource. Collision is still present inside the YDR files.

Eleven custom models were rebuilt, including all seven bridge sections. Buildings, materials, placements and the minimap layout are preserved. No additional GTA assets or altered game configuration are required.

## Checks and limits
Every rebuilt model was loaded again with CodeWalker. Collision triangle counts were preserved, world-space vertex positions were checked against the previous collision geometry, and render indices were checked against their vertex buffers. All three YMAPs were decoded again and checked for empty external physics-dictionary dependency lists. Unmodified buildings and texture dictionaries match the last package byte-for-byte.

These checks do not run GTA/FiveM. The user confirmed that version 1.1 crashes with fifteen-diet-montana; this is a targeted rebuild of the addon's collision loading, not a verified explanation of that crash address or a guarantee that the crash is resolved. If this version still crashes, it needs runtime investigation; further unrelated memory/texture changes would not establish a diagnosis.

The bridge city-side landing remains estimated at (-331.6414, 5844.0, 8.025), and still needs an in-game elevation check against your city resource. The island center is (-331.6414, 6749.6025), surface Z 8.0.

Neighborhood assets derive from the supplied WayTooCerti archive. Binary resources were rebuilt with CodeWalker.Core. `validation.json` records the checks and coordinate errors; `source/` contains the modified XML.
