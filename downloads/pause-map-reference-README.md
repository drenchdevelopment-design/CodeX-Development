# FiveM dark city map — reference-style edition (5.0)

Updated artwork inside the supplied YTD texture dictionaries. This is the map shown in the pause menu. The resource streams textures only and has no HUD, NUI, speedometer, or client script.

## Visual changes

- A cleaner dark phone-map style closely following the supplied visual reference: near-black water, navy land, blue street lines, green shorelines and parks, and plain white borough labels.
- Detailed miniature illustrations for Times Square, Brooklyn Bridge, and the Statue of Liberty, replacing the simple drawn icons from version 4.
- Smaller place markers for parks, the airport, lighthouse, and Coney Island; no postal pins or postal numbers.
- Large district label panels removed. Building detail and baked street-name clutter are reduced to make the street network readable at city scale.
- Both normal and sea variants receive the same artwork.

This is a recreation of the reference's visual style using your supplied map, not the map author's original artwork. Landmark illustrations were generated for this edition; editable PNG assets are included. Place-marker placement follows the illustrated reference and should be checked against your server's custom locations.

## Geometry and source limits

Installed tiles retain their dimensions, placement, texture names, formats, mip counts, and original alpha blocks. There is no map re-projection or GPS coordinate change. The street drawing is derived from the supplied raster roads, with narrower strokes and simplified detail. Short road connections underneath the original oversized titles are interpolated from visible entries; the original hidden pixels are unavailable. Source boundaries between 1024- and 3072-pixel tiles, and some compression artifacts, remain. This cannot be a pixel-for-pixel copy of the reference from a screenshot alone.

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

Live FiveM rendering and GPS alignment were not available to test here. Tile placement and transparency are preserved; check GPS overlays and the reconstructed title areas on your server before rollout.

## Editable build tools

`scripts/build-map.py` performs the in-place BC3 payload rebuild. `scripts/cartography.py` supplies road extraction, colors, labels, and landmark composition. Landmark artwork is under `source/landmarks/illustrations/`. `scripts/validate-map.py` validates against the original resource. DejaVu fonts and their license are included under `source/fonts/`.

To rebuild with Python 3, NumPy, OpenCV, scikit-image, and Pillow 12.3.0 or newer with BCn encoding support:

```sh
python -m pip install numpy Pillow==12.3.0 opencv-python-headless scikit-image==0.25.2
python scripts/build-map.py /path/to/original/mini-map
python scripts/validate-map.py /path/to/original/mini-map
python scripts/build-preview.py
```

Use the original resource from your uploaded ZIP as input, not the newly styled output. These scripts use no FiveM or proprietary editing tool installation.
