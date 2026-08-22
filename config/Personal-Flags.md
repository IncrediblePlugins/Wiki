# Player Personal Settings

These settings customize each player's ChestProtect experience. Players can toggle them in
`/chestprotect` -> `Settings` if they have permission.

Defaults for new players are configured in `config.yml` under `player.setting`.

| Setting | What it does | Toggle permission |
| --- | --- | --- |
| `PERSISTENT_LOCK` | Keeps lock and unlock mode active until the player runs `/chestprotect exit` or toggles the mode off. | `chestprotect.setting.player.persistent_lock` |
| `PERSISTENT_TRUST` | Keeps trust and untrust mode active until the player runs `/chestprotect exit` or toggles the mode off. | `chestprotect.setting.player.persistent_trust` |
| `AUTO_LOCK` | Automatically locks protectable blocks when the player places them, if limits and costs allow it. | `chestprotect.setting.player.auto_lock` |
| `NOTIFICATIONS` | Shows messages when the player opens their own protection or one where they are trusted. | `chestprotect.setting.player.notifications` |

If a setting is enabled by default, it only applies automatically to new player data. Existing
players keep their stored setting until they change it or an admin edits their data.
