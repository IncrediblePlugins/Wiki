# Land Categories

Land categories are configured in `categories.yml`.

They help players find lands in `/lands list`, such as shops, PvP arenas, mob farms, or lands looking for members.

# Enable Categories

Use:

```yaml
land:
  enabled: true
```

Each entry below `land.categories` defines one category.

Changes require a server reload or restart.

# Category Format

Example:

```yaml
land:
  categories:
    shop:
      enabled: true
      name: '&cShop $'
      description:
        - '&7This land contains shops.'
```

Fields:

| Setting | What it does |
| --- | --- |
| `enabled` | Shows or hides the category. |
| `default` | If `true`, new lands start with this category instead of none. At most one category should be marked default. |
| `name` | Display name in menus. |
| `description` | Lore shown for the category. |

# Looking for Members

The default `members` category has one extra option:

```yaml
allow-auto-accept: true
```

If enabled, land owners can let membership requests be accepted automatically while their land uses the members category.

If disabled, the option is also disabled for existing lands after restart.

# Player Workflow

Players change their land category in the land menu.

Players browse and filter lands with `/lands list`.

The player-facing explanation is in [Land Discovery and Categories](../../players/general/Land-Discovery-and-Categories.md).
