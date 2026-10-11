# The Ville downloads — 2.3.0

- **the-ville-multichar-updated.zip** — Updated resources, editable source, tests, screenshots, and installation instructions.
- **the-ville-preview.html** — Download and open in Chrome or Edge for the offline interactive preview.

Use **Download raw file** on GitHub. SHA256SUMS.txt contains checksums.

## Latest update

Fixes hidden selector focus that could leave the cursor visible and block movement/chat after finishing illenium-appearance. Releases each outgoing resource's focus, removes duplicate appearance-opening retries, and prevents late identity preparation from freezing the ped after registration.

Startup now has an opaque native cover and immediate loading UI. The cover remains until the current browser screen has painted, so waiting for character data does not expose the ped. Initials and prior identity/server fixes remain included.

Replace **esx_multicharacter** and **esx_identity** together, including their `dist` folders; preserve your custom configuration. Restart the server and reconnect. No database changes are required for this fix. Keep illenium-appearance's ESX bridge enabled.

96 mocked Lua assertions, 53 Lua syntax checks, and Chromium browser checks passed. Live FiveM/illenium-appearance verification is still required.

The separate mini-map/pause-map downloads are unchanged.
