# Limits and Roles

FasterFurnaces uses limits and roles to control how many furnaces players can own and who can access each furnace.

## Player Limits

`player-limits.yml` defines limit packs. A limit pack can be assigned by permission, and the first matching pack in the file is used when a player joins.

The default file contains:

| Pack | Permission | Purpose |
| --- | --- | --- |
| `admin` | `fasterfurnaces.admin.no_limits` | Removes most limits for staff. |
| `default` | None | Default player limits. |

The default pack contains these limits:

| Limit | Description |
| --- | --- |
| `player_groups` | Amount of player groups a player can create. |
| `block_members` | Amount of players a player can trust to each furnace or group. |

Changes to `player-limits.yml` can be applied with `/fasterfurnaces admin reload`.

## Numbered Permission Limits

The plugin also checks numbered permissions for the maximum amount of furnaces and members:

| Permission | Description |
| --- | --- |
| `fasterfurnaces.furnaces.<number>` | Maximum amount of placed upgradeable furnaces a player can own. |
| `fasterfurnaces.members.<number>` | Maximum amount of players a player can trust to a furnace. |

Replace `<number>` with the actual amount, such as `fasterfurnaces.furnaces.10`.

## Roles

`roles.yml` defines the default role flags for furnace protection.

Default roles:

| Role | Flags |
| --- | --- |
| `owner` | `ALL` |
| `admin` | `MANAGE`, `OPEN` |
| `member` | `OPEN` |
| `visitor` | None |

Available role flags used by FasterFurnaces:

| Flag | Description |
| --- | --- |
| `OPEN` | Allows opening the furnace inventory. |
| `MANAGE` | Allows opening the management and upgrade menu. |
| `DELETE` | Allows removing the upgradeable furnace. |

The owner role has `ALL`, so owners can open, manage, and delete their furnaces by default.
