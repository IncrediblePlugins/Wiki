# Installation

1. Stop your server.
2. Put `ChestProtect.jar` in your `plugins` folder.
3. Start the server once to generate the files.
4. Stop the server again.
5. Edit the files in `plugins/ChestProtect`.
6. Start the server.

If you use Paper, make sure `hopper.disable-move-event` is set to `false`. ChestProtect needs
hopper move events to protect containers from unauthorized hopper transfers.

# Updating

Always stop your server before installing updates.

The config and locale files automatically add new entries and remove no longer existing entries.

# First Setup Checklist

After installing, review these files:

| File | Use it for |
| --- | --- |
| `config.yml` | Worlds, database, default player settings, teleportation, economy, integrations, and general behavior. |
| `protectables.yml` | Lockable blocks/entities, lock costs, cashback, and hologram defaults. |
| `player-limits.yml` | Protection, group, member, and free-protection limits. |
| `roles.yml` | Default roles and their role flags. |
| `Locale/` | Messages and GUI text. |

Then run `/chestprotect admin reload` or restart the server after config changes. Database type,
command aliases, and some integration changes should be applied with a full restart.
