# Upstate 1.1 — compatibility rebuild with bridge

## Replace the old build
1. Stop the server. Remove the previous `certi_upstate` folder and replace it with this ZIP's `resources/certi_upstate`.
2. Replace your existing `mini-map` folder with this ZIP's `resources/mini-map`. Do not keep another enabled copy of the draft or the same map texture files under a different resource name.
3. Keep your original Liberty City world resource enabled. Use:

```
ensure mini-map
ensure certi_upstate
```

4. Restart the server and reconnect. Inspect the island at `-331.6414, 6749.6025, 10.0` with your existing admin teleport tool.

## Changes
- Added a roughly 562 m bridge in seven compiled sections, with deck collision, raised parapets, sidewalks, lane markings and support piers. Its line is included in both affected radar/menu-map dictionaries.
- Restored all seven reused building models byte-for-byte from your upload, avoiding the previous model/embedded-texture re-export.
- Compiled both replacement minimap dictionaries through CodeWalker instead of manually repacking resource pages. These two textures now use 2048 pixels and 10 mip levels, reducing their texture payload by 75% versus the draft's 4K pair. Other map tiles retain the previous sharp-map files.
- Deduplicated custom collision vertices so adjacent triangles share edges.
- Reduced house drawing distances from 800 m to 350 m and markets from 850 m to 400 m.
- Recomputed streaming and entity extents from actual model bounds, including the bridge.

## What remains unverified
This is a compatibility repair attempt, not a confirmed diagnosis of your crash. No FiveM crash message was supplied, and this environment cannot run your server/client. Binary loading, mesh indices and resource bounds were checked offline; see `validation.json`.

The bridge meets the north Harlem road shown in your map at approximately `-331.6414, 5844.0, 8.025`. Its city-side road elevation was estimated because the underlying city world geometry was not supplied. Verify this landing in game; the bridge and island surface meet at Z 8.025. An elevation adjustment may be needed. The center span rises to about Z 18.025.

If it still crashes, paste the FiveM crash name/error text. To isolate the resource, stop `certi_upstate` and reconnect with `mini-map` still enabled; report whether that changes the crash.

This is a static exterior map. GPS routing nodes, population/navmesh, business scripts and new shop interiors are not included. The map coastline and roads are generated from the same metric plan as the 3D geometry; no postal pins are added.

## Contents and source
Compiled YMAP, YDR, YBN, YTYP and YTD files are included. Neighborhood assets come from the uploaded WayTooCerti resource. Stock GTA props are referenced by model name. The original Los Santos replacement YMAPs from the upload are not installed. `source/layout.json` contains the metric layout and bridge endpoint. `preview/upstate-map.png` is decoded from the built radar texture.
