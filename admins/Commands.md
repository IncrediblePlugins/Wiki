# Admin Commands

These commands are intended for staff and server administrators.

| Command | Description | Permission |
| --- | --- | --- |
| `/fasterfurnaces list [player]` | Opens the furnace list for yourself or another player. Viewing another player's furnaces requires the admin list permission. | `fasterfurnaces.command.list` and, for other players, `fasterfurnaces.admin.command.list` |
| `/fasterfurnaces admin` | Parent command for admin actions. | `fasterfurnaces.admin.command` |
| `/fasterfurnaces admin give <player> <type> <amount>` | Gives upgradeable furnace items to a player. The item starts at the first configured level of the selected furnace type. | `fasterfurnaces.admin.command.give` |
| `/fasterfurnaces admin reload` | Reloads supported configuration values, messages, GUI files, translations, and player limits. | `fasterfurnaces.admin.command.reload` |

Admin subcommand permissions follow this format:

`fasterfurnaces.admin.command.<subcommand>`

Example:

`/fasterfurnaces admin give` uses `fasterfurnaces.admin.command.give`.

## Reload Notes

Use `/fasterfurnaces admin reload` for supported config, GUI, message, translation, and `player-limits.yml` changes. Some values in `config.yml` still require a server restart, as noted by comments in the file.

Changes to `furnaces.yml` require a full server restart. Furnace types and levels are loaded on startup, and changing them while the server is running can leave already placed furnaces using the old level setup until restart.
