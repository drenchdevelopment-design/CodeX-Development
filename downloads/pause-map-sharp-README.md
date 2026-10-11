# FiveM pause map — sharper Queens/Bronx edition 5.1

Fixes the low-resolution Queens/Bronx tile in the dark reference-style map. The two affected YTD dictionaries are rebuilt at **4096 × 4096**, up from 1024 × 1024. Street paths and labels are rendered again at output resolution; this is not an enlargement of the finished blurry map image.

## Install

1. Back up your existing `mini-map` folder.
2. Replace it with the included `mini-map` folder. Keep `ensure mini-map` in server.cfg and only one resource streaming these texture names.
3. Restart the server and reconnect so FiveM loads the updated textures.

If already using version 5, you can instead replace only these two files in your existing `mini-map/stream` folder:

- `minimap_0_1.ytd`
- `minimap_sea_0_1.ytd`

This is a map-only update. Your multicharacter/identity resources are separate and need no changes.

## What changed

- 4× the texture width and height for Queens, The Bronx, and nearby park labels: 16× as many pixels.
- Labels rendered from fonts at 4K, and road paths redrawn as antialiased lines.
- Eleven BC3 mip levels, from 4096 to 4 pixels, for zoomed and distant views.
- Updated graphics allocation, dimensions, texture stride, and mip metadata in the RSC7 files. No virtual pointer, texture name, map extent, or tile position changes.
- Exact source transparency retained at corresponding scales. The new upper levels replicate the original BC3 alpha indices; existing lower mip alpha blocks are retained verbatim.
- Every other streamed asset matches version 5 byte for byte. Detailed landmarks, colors, and the no-postal-pins choice remain.

Each upgraded dictionary has a 32 MiB graphics allocation, previously 2 MiB. Its BC3 mip payload is about 21.33 MiB. These are actual higher-resolution game textures, with the corresponding memory cost.

## Preview and validation

Open `preview.html` in a browser and choose **Queens / Bronx detail**. The slider compares the previous 1024px release with the new decoded 4K YTD at identical map extent and display zoom. The same views are provided as `previews/queens-before.png` and `previews/queens-after.png`.

275 HD asset checks passed: RSC7 allocation/page metadata, dimensions/stride, every mip decoding, exact alpha preservation at equivalent scales, identical normal/sea mip payloads, unchanged pointers/names, and unchanged companion assets. The offline preview passed Chromium checks. The archive was integrity-checked.

Live FiveM rendering was not available here. Verify close/far zoom, tile boundaries, blip placement and texture streaming on your server. Source geography was originally flattened and low-resolution; rendering it sharply cannot restore missing geographic detail. Game texture settings and streaming can also affect the result.

## Editable tools

Requires Python 3, NumPy, OpenCV, scikit-image, and Pillow with BC3 encoding support:

```sh
python -m pip install numpy Pillow==12.3.0 opencv-python-headless scikit-image==0.25.2
python scripts/build-map.py /path/to/original/mini-map
python scripts/validate-map.py /path/to/original/mini-map
python scripts/build-hd.py /path/to/original/mini-map
python scripts/validate-hd.py /path/to/original/mini-map
python scripts/build-preview.py
```

Use the original uploaded mini-map as the source. The base builder makes version 5; the HD builder then upgrades the two low-resolution tiles. The final validator checks the HD release against the source and the supplied version-5 asset hashes.

Resource layout was checked against CodeWalker's documented implementations of Texture, ResourcePagesInfo, and RpfResourcePageFlags. The editable build scripts are included; FiveM does not need Python or these development dependencies.
