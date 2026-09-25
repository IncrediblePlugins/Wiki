# Trust and Roles

Each farm has its own owner and roles. Roles decide who can build, harvest, configure settings, upgrade, or remove the farm.

Trusting and untrusting players, and changing their role, is entirely handled by ChestProtect - BetterFarming has no trust menu or command of its own. If your server has ChestProtect installed and protections enabled in the farm's world, a farm placed there automatically gets a ChestProtect protection, and you manage access to it the same way you would any other ChestProtect-protected block or area. See ChestProtect's own documentation for how to trust/untrust players and change roles.

If a farm has no ChestProtect protection (ChestProtect isn't installed, or the world it's in has protections disabled), only the owner has access to it - there is no way to trust anyone on that farm until a protection exists.

# Default Roles

Servers can rename roles or change their flags. In the default configuration:

| Role | Default access |
| --- | --- |
| Owner | Full access to the farm. |
| Admin | Can harvest, plant, break blocks, place blocks, interact, configure the farm, and upgrade it. |
| Member | Can harvest, plant, break blocks, place blocks, interact, and upgrade the farm. |
| Visitor | No farm access by default. |

Which role a trusted player has is set through ChestProtect's own trust menu, not a BetterFarming setting - the table above only decides what each role is allowed to do on a farm specifically.

# Region Members

If the farm is inside a supported claim, BetterFarming can allow members of that claim to use the farm automatically as if they were trusted at the Member role, depending on your server's claim plugin and a server-wide setting - see your server's own configuration for whether this is enabled.

# Public Farms

The **Public** option in the farm menu allows all players to use public farm actions: planting, harvesting, and interacting.

Opening a farm uses the interact action, so public farms can also allow basic farm interaction such as storage access on a default setup.

Public access does not make them farm managers. They still cannot upgrade, delete, or configure the farm unless they also have the required role (through ChestProtect) or server permission.
