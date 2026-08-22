# Managing Protections

This page explains what you can do with a protection after it has been created.

# Open the Protection Menu

Sneak and left-click a protection to open its menu. You need edit access to open this menu.

From the protection menu you can:

| Option | What it does |
| --- | --- |
| Members | Trust players, remove trusted players, and change roles. |
| Edit Flags | Toggle behavior for this one protection. |
| Name | Set a display name for the protection. |
| Edit Group | Assign the protection to one of your groups. |
| Unlock | Delete the protection. |

# View Your Protections

Open `/chestprotect` and choose `Protections`.

Protections are grouped by type, such as chests, barrels, furnaces, shulker boxes, doors, and other
enabled objects. From the list you can open a protection's menu, teleport to it if your server
allows that, or delete it.

Your main menu also shows how many block and entity protections you own compared with your limit.

# Protection Flags

Protection flags change the behavior of a single protection. Servers can decide which flags are
available on each object type.

| Flag | What it does |
| --- | --- |
| `REDSTONE` | Allows redstone signals to affect the protection. |
| `PUBLIC_TAKE` | Allows everyone to take items without being trusted. |
| `PUBLIC_INSERT` | Allows everyone to insert items without being trusted. |
| `HOLOGRAM` | Shows a hologram with information such as the protection name and storage space. |

These flags do not replace roles. For example, `PUBLIC_INSERT` can allow everyone to insert items,
while role flags still decide who may open or manage the protection.

# Unlock a Protection

Use one of these options:

1. Run `/chestprotect unlock` and click the protection.
2. Open the protection menu and choose `Unlock`.

Unlocking removes the protection. Depending on your server's economy settings, you may receive a
cashback amount from the original lock cost.

# Nearby Protection View

Use `/chestprotect view` to visualize nearby protections. This is useful when you are trying to
find what is locked around you.

Run `/chestprotect view` again to turn the visualization off.
