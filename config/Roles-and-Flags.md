# Roles and Role Flags

Roles and their flags are configured in `roles.yml`.

Roles decide what trusted players can do at a protection. Servers can rename roles and change their
flags.

# Default Roles

| Role | Default flags |
| --- | --- |
| `owner` | `ALL` |
| `admin` | `HOPPER_TRANSFER`, `OPEN`, `PLAYER_TRUST`, `PLAYER_UNTRUST`, `PLAYER_SETROLE` |
| `member` | `HOPPER_TRANSFER`, `OPEN` |
| `visitor` | None |

# Role Flags

| Flag | What it allows | Toggle permission |
| --- | --- | --- |
| `OPEN` | Open or use the protection. | `chestprotect.setting.open` |
| `HOPPER_TRANSFER` | Use hoppers to transfer items. | `chestprotect.setting.hopper_transfer` |
| `PLAYER_TRUST` | Trust players to the protection. | `chestprotect.setting.player_trust` |
| `PLAYER_UNTRUST` | Remove trusted players from the protection. | `chestprotect.setting.player_untrust` |
| `PLAYER_SETROLE` | Change another trusted player's role. | `chestprotect.setting.player_setrole` |
| `UNLOCK` | Unlock the protection. | `chestprotect.setting.unlock` |
| `EDIT_FLAGS` | Change protection flags. | `chestprotect.setting.edit_flags` |

The toggle permission controls whether a player may toggle that role flag in menus.

# Bypass Permissions

Role flags also expose bypass permissions in the pattern `chestprotect.bypass.<flag>`.

Examples:

| Flag | Bypass permission |
| --- | --- |
| `OPEN` | `chestprotect.bypass.open` |
| `HOPPER_TRANSFER` | `chestprotect.bypass.hopper_transfer` |
| `PLAYER_TRUST` | `chestprotect.bypass.player_trust` |
| `UNLOCK` | `chestprotect.bypass.unlock` |
| `EDIT_FLAGS` | `chestprotect.bypass.edit_flags` |
