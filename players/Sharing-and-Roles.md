# Sharing and Roles

ChestProtect lets you share a protection with specific players. Trusted players receive a role, and
that role decides what they can do.

# Trust a Player

Use `/chestprotect trust <player>` and click the protection.

You can also trust players from the protection menu:

1. Sneak and left-click the protection.
2. Open `Members`.
3. Choose `Trust Player`.
4. Enter or select the player.

Your server may limit how many players can be trusted to one protection or group.

# Untrust a Player

Use `/chestprotect untrust <player>` and click the protection.

You can also remove players from the `Members` menu. If a player is trusted through a group, remove
them from that group instead.

# Roles

Roles are configured by your server. The default roles are:

| Role | Default access |
| --- | --- |
| Owner | Can do everything at the protection. |
| Admin | Can open the protection, use hoppers, trust players, untrust players, and change roles. |
| Member | Can open the protection and use hoppers. |
| Visitor | Has no trusted-player access by default. |

Servers can rename roles and change which flags each role has.

# Role Flags

Role flags decide what trusted players may do.

| Flag | What it allows |
| --- | --- |
| `OPEN` | Open or use the protection. |
| `HOPPER_TRANSFER` | Use hoppers to transfer items. |
| `PLAYER_TRUST` | Trust players to the protection. |
| `PLAYER_UNTRUST` | Remove trusted players from the protection. |
| `PLAYER_SETROLE` | Change another trusted player's role. |
| `UNLOCK` | Unlock the protection. |
| `EDIT_FLAGS` | Change protection flags. |

Players usually cannot edit members with an equal or higher role priority than their own role.

# Claim and Region Members

If your server uses Lands, WorldGuard, PlotSquared, BentoBox, SuperiorSkyblock2, or another
supported region plugin, ChestProtect may apply extra rules for where protections can be created
and who can access them.

Some servers also let a protection automatically trust members of the claim or region it is inside.
When this is available, it appears in the protection's member menu.
