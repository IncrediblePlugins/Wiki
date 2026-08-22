# Start

This page explains the first steps for using ChestProtect.

Most examples use `/chestprotect`. Many servers also enable the shorter `/cp` alias and shortcuts
such as `/lock`, `/unlock`, `/trust`, and `/untrust`.

Some features depend on your server's setup. Your server may change which objects are protectable,
how much locking costs, which worlds allow protections, and how many protections each player can
own.

# 1. Open the Menu

Use `/chestprotect` or `/chestprotect menu` to open the main menu.

The main menu shows your protection limits and lets you open:

| Menu | What it is for |
| --- | --- |
| Protections | View and edit your locked objects. |
| Groups | Share trusted players across multiple protections. |
| Settings | Change your personal ChestProtect settings. |

# 2. Lock an Object

Use `/chestprotect lock` and click the object you want to protect.

If your server has auto lock enabled for you, placing a protectable object can lock it
automatically. You can toggle auto lock in your personal settings if you have permission.

By default, common protectable objects include containers such as chests, barrels, furnaces, and
shulker boxes, plus doors, hoppers, item frames, armor stands, and some entities. Your server can
enable or disable each type.

If locking fails because of money or limits, read [Limits and Costs](Limits-and-Costs.md).

# 3. Open a Locked Object

Right-click a protection to use it.

Only the owner, trusted players with the right role, public flags, or staff bypass permissions can
access a protection. If you are denied access, the message will usually tell you who owns it.

# 4. Open a Protection's Menu

Sneak and left-click a protection to open its management menu.

The protection menu lets you manage trusted players, edit flags, rename the protection, assign a
group, or unlock it.

# 5. Trust Another Player

Use `/chestprotect trust <player>` and click the protection.

You can also trust players from the protection menu:

1. Open the protection menu.
2. Open the members menu.
3. Choose the trust option.

Trusted players receive a role. Roles decide what they can do at the protection.

If you want to share the same players across many protections, read [Groups](Groups.md).

# 6. Stop a Click Mode

Lock, unlock, trust, and untrust commands put you into a click mode. Use `/chestprotect exit` to
leave the active mode.

If your personal persistent mode setting is disabled, ChestProtect leaves the mode automatically
after a successful action.
