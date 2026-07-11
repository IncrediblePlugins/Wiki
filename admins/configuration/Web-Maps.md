# Web Maps

Lands can render claims and land spawns on supported web map plugins.

Configuration file:

`web.yml`

Supported integrations:

* Dynmap
* BlueMap
* squaremap
* Pl3xMap

Multiple integrations can be enabled at the same time.

Changes in `web.yml` require a server reload or restart.

# General Options

Common options are under `map.general`.

| Setting | What it does |
| --- | --- |
| `hide` | Hides the Lands layer by default. |
| `layer` | Name of the map layer. |
| `update_time` | Adds a fixed update interval. Use this if you want less real-time player activity leakage. |
| `land.show-admin` | Shows admin lands on the web map. |
| `land.only-nation` | Only shows lands that are part of a nation. |
| `land.color` | Default fill colors or name-based colors. |
| `border.color` | Default border colors or name-based colors. |

# Links for Players

Each map integration has a `link` option.

If at least one active integration has a link, players can use:

`/lands map link`

Permission:

`lands.command.map`

The locale message must contain the matching placeholder, such as `{dynmap}`, `{bluemap}`, `{squaremap}`, or `{pl3xmap}`.

# Dynmap

Dynmap options are under `map.dynmap`.

Common settings include:

* `enabled`
* `link`
* `spawn.icon`
* `spawn.icon-capital`
* `spawn.min-zoom`
* `land.opacity`
* `border.opacity`
* `border.thickness`

# BlueMap

BlueMap options are under `map.bluemap`.

BlueMap supports spawn icons, capital spawn icons, icon anchors, marker height, opacity, and optional 3D land markers.

Icon paths are relative to the BlueMap folder.

# squaremap and Pl3xMap

squaremap options are under `map.squaremap`.

Pl3xMap options are under `map.Pl3xMap`.

Both support links, spawn icons, capital icons, land opacity, border opacity, and border thickness.

# Troubleshooting

If claims do not appear:

* Confirm the map plugin is installed and enabled.
* Confirm the matching `enabled` option in `web.yml` is true.
* Restart after changing `web.yml`.
* Check console logs for integration startup messages.
* Make sure Lands and the map plugin versions are compatible.

If `/lands map link` is missing or empty:

* Set a `link` for the active map integration.
* Make sure the locale `map.link` message includes the matching placeholder.
