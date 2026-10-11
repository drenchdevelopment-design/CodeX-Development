# Upstate extension — island draft

Built around X -331.6414, Y 6749.6025. The terrain surface is Z 8.0 so it sits above the water; the supplied Z -0.5570 is below the new surface.

**Bridge connection is unfinished.** The existing city's road XYZ coordinate is still needed to place the bridge landing at the correct position and elevation. This download contains the completed island portion and matching map artwork, not a connected bridge. It is a development draft and has not been tested in a running FiveM server.

Included:
- 72 relocated supplied residential buildings and 3 market buildings, with their embedded collision.
- Compiled YMAP placements, custom YDR terrain/streets/sidewalks/driveways/plaza, world YBN collision, registered YTYP archetypes, and YTD materials.
- 302 total entity placements including stock GTA trees, streetlights, benches, and bins.
- Full mini-map resource based on your previous sharp dark map. The island's coast, roads and building footprints come from the actual world layout. The affected normal and sea tiles are 4096×4096 with 11 mip levels.
- No postal pins. No original Los Santos replacement YMAPs from the upload are installed.

## Install for inspection
1. Back up your existing `mini-map` resource.
2. Copy `resources/certi_upstate` to your server resources directory.
3. Replace your existing `mini-map` directory with `resources/mini-map`. Run only one resource supplying these minimap texture filenames.
4. Keep your existing Liberty City/world map enabled. Add:

```
ensure mini-map
ensure certi_upstate
```

5. Reconnect and use your existing admin teleport tool to inspect `-331.6414, 6749.6025, 10.0`.

The district is a static exterior map. Store interiors, business scripts, population/navmesh and GPS route nodes are not included. Stock GTA terrain removal depends on your existing city resource. Server collision, streaming and final bridge connection require in-game checking.

## Preview and validation
`preview/upstate-map.png` is decoded from the built YTD. `preview/island-geometry.png` is an offline geometry render made during development; it uses proxies for stock vegetation and predates the final driveway/extra-tree pass. Neither is an in-game screenshot.

`validation.json` records binary resource checks. YMAP/YTYP/YBN files were decoded again with CodeWalker; this checks serialization, not gameplay.

`source/layout.json` is the shared metric plan. Editable CodeWalker XML is included under `source/`; imported building textures remain in their compiled dictionaries. The generator scripts retain development workspace paths and are included as build references, not as a portable installer.

## Asset origin
Neighborhood buildings/textures were reused from the ZIP you supplied, identified there as WayTooCerti Downtown Suburbs. GTA props are referenced by model name and are not redistributed. Terrain, streets, placement, driveways and map extension were authored for this request. Binary resources were compiled using CodeWalker.Core (dexyfex/CodeWalker).
