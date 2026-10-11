# Modern FiveM pause map — texture edition

Updated artwork inside the supplied YTD texture dictionaries. This is the map shown in the pause menu. The resource streams textures only and has no HUD, NUI, speedometer, or client script.

## Visual changes

- Graphite land and buildings, deep petrol water, and brighter road contrast.
- Softer water-depth bands and mint bridge/road accents.
- New clean district labels for Woodbridge, Elizabeth, Harlem, Downtown, The Bronx, Queens, Brooklyn, and State Prison, covering the existing baked label areas.
- The normal and sea tile variants match.

All installed map tiles keep their original dimensions, pixel coordinates, texture names, formats, mip counts, and alpha blocks. No tile is moved, rotated, cropped, or rescaled in the installed resource. Label plates replace the previous oversized district artwork at the same locations; street geometry elsewhere is retained.

## Install

1. Back up your existing `mini-map` folder.
2. Replace that folder completely with the `mini-map` folder from this ZIP. Keep only one active resource that streams these map texture names.
3. Keep `ensure mini-map` in `server.cfg`, restart the server, and reconnect so FiveM reloads the streamed dictionaries.
4. Open the pause-menu map and check normal zoom, close zoom, tile boundaries, and GPS/blips on your staging server.

No database changes or additional resource dependencies are required. Your custom city/map geometry resource must still be installed. If replacing the earlier minimap HUD package, use a complete folder replacement: this release supplies the pause-map artwork.

## Preview

Open `preview.html` locally in a browser. The slider compares the original textures with images decoded from the actual rebuilt YTDs. Switch between the city overview and native-resolution street detail. It works offline. The PNGs in `previews/` provide the same comparison without browser controls.

## Scope

Nine map YTDs were restyled: `minimap_0_0`, `minimap_0_1`, `minimap_1_0`, `minimap_1_1`, their four `minimap_sea_*` equivalents, and the low-resolution `minimap_lod_128` overview.

The four blank tiles, icon/HUD atlas (`minimap.ytd`), and every YDD remain byte-for-byte unchanged. The supplied low-resolution overview contains stock geography; its colors were updated while retaining that original projection. This release does not recalibrate the overview or replace it with guessed custom-map bounds.

The original Queens/Bronx tile is 1024 pixels wide; the other populated tiles are 3072. That source-resolution difference is retained. This update does not invent missing street detail or change map calibration.

## Validation

214 asset checks passed: RSC7 headers and metadata, file allocations, all BC3 mip levels decoding, exact alpha preservation, normal/sea consistency, changed-file scope, and unchanged companion assets. The archive was integrity-checked. The offline comparison was tested in Chromium.

Live FiveM rendering and GPS alignment were not available to test here. Texture geometry and transparency are preserved, but confirm the result on your server before rollout.

## Editable build tools

`scripts/build-map.py` performs the recoloring, label replacement, and in-place BC3 payload rebuild. `scripts/validate-map.py` validates against the original resource. DejaVu fonts and their license are included under `source/fonts/`.

To rebuild with Python 3, NumPy, and Pillow 12.3.0 or newer with BCn encoding support:

```sh
python scripts/build-map.py /path/to/original/mini-map
python scripts/validate-map.py /path/to/original/mini-map
python scripts/build-preview.py
```

Use the original resource from your uploaded ZIP as input, not the newly styled output. These scripts use no FiveM or proprietary editing tool installation.
