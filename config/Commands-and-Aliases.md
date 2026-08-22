# Commands and Aliases

Command aliases and shortcuts are configured in `config.yml`.

# Root Command Aliases

The main command is `/chestprotect`.

The default config also adds:

```yaml
command:
  alias:
    chestprotect_list:
      - "cp"
      - "protect"
      - "protection"
```

After a restart, players can use `/cp`, `/protect`, or `/protection` where the docs show
`/chestprotect`.

# Shortcut Commands

The current command handler registers shortcuts for:

| Shortcut | Same as |
| --- | --- |
| `/lock` | `/chestprotect lock` |
| `/unlock` | `/chestprotect unlock` |
| `/trust <player>` | `/chestprotect trust <player>` |
| `/untrust <player>` | `/chestprotect untrust <player>` |

These are controlled by:

```yaml
command:
  shortcut:
    lock: true
    unlock: true
    trust: true
    untrust: true
```

Restart the server after changing command aliases or shortcuts.

# SetRole Shortcut

The default config currently contains a `setrole` shortcut option, but the current ChestProtect
command handler does not register a standalone `setrole` command. Players change roles through the
protection members menu.
