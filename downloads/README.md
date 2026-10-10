# The Ville downloads — 2.1.0

- **the-ville-multichar-updated.zip** — All four updated FiveM resources, editable UI source, tests, screenshots, and installation instructions. Extract the ZIP and read README.md before installing.
- **the-ville-preview.html** — Standalone interactive preview. Download this file and open it in Chrome or Edge; no server is needed.

To download on GitHub, open the file and use **Download raw file**. The HTML file is a browser preview with sample data, not a live FiveM session.

Automated browser checks and 70 Lua assertions passed. Live FiveM/ESX/MySQL integration still requires testing on your staging server.

SHA256SUMS.txt records checksums for both files.

## What changed in 2.1.0

- Full-screen, opaque background, including ultrawide displays.
- Fixed the ESX player-proxy comparison that could incorrectly return `no_player` during registration; errors no longer stack raw notifications.
- Native ped headshots replace faction/archetype artwork on character selection. Offline preview uses placeholders because real ped textures exist only in FiveM.

Replace the complete resource folders, including the new portraits client script and updated manifest. Preserve your custom configuration, restart your server, and reconnect.

### Registration image adjustment

The “Choose your path” cards now show the complete portrait images using taller, responsive image areas and contain scaling, without cropping.
