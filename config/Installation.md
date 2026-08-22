# Installation

1. Stop your server.
2. Place the downloaded FasterFurnaces plugin file in your server's `plugins` folder.
3. Start the server once so FasterFurnaces can create its configuration files.
4. Stop the server again before editing startup-only files such as `furnaces.yml`.
5. Configure the plugin and set permissions in your permissions plugin. See [Permissions](../permissions/Permissions.md).
6. Start the server.

Please always stop your server before installing updates. Config and locale files automatically add new entries and remove entries that no longer exist.

## Reloading

Use `/fasterfurnaces admin reload` for reloadable values and files such as supported config values, GUI files, messages, translations, and `player-limits.yml`.

Some values in `config.yml` still require a restart, as noted by comments in the file.

Changes to `furnaces.yml` require a full server restart. This file defines furnace types and level progressions, and those values are loaded during startup.

## Important Files

| File | Use it for |
| --- | --- |
| `config.yml` | General settings, worlds, database, vanilla furnace behavior, integrations, teleportation, and economy. |
| `furnaces.yml` | Furnace types, item materials, level costs, upgrade attributes, and furnace flags. Requires restart after changes. |
| `player-limits.yml` | Limit packs, such as how many member entries players can add. Can be reloaded. |
| `roles.yml` | Default role names and role flags for owners, admins, members, and visitors. |

See [General Settings](General-Settings.md), [Database](Database.md), [Furnaces](Furnaces.md), and [Limits and Roles](Limits-and-Roles.md) for the main admin configuration pages.
