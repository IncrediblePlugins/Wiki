# Frequently Asked Questions

# Why can't I lock this object?

Common reasons are:

| Reason | What it means |
| --- | --- |
| The object is not protectable. | Your server has not enabled this block or entity type. |
| The world is disabled. | ChestProtect protections are not enabled in this world. |
| The region does not allow it. | A claim, region, island, or plot plugin is blocking protection creation there. |
| You reached your limit. | You already own the maximum number of block or entity protections. |
| You cannot pay the cost. | Your server requires money or item currency to lock the object. |

# How do I open the menu for a protection?

Sneak and left-click the protection. You need edit access to open the menu.

# How do I stop lock or trust mode?

Use `/chestprotect exit`.

# Why can someone insert or take items without being trusted?

The protection may have `PUBLIC_INSERT` or `PUBLIC_TAKE` enabled. Open the protection menu and check
its flags.

# Why do hoppers not work with my protection?

Hopper access is controlled by the `HOPPER_TRANSFER` role flag and by your server's hopper
settings. If hoppers are blocked, check the trusted player's role or ask staff how hopper access is
configured.

# Why can't I untrust a player?

The player may be trusted through a group, or their role may have equal or higher priority than
yours. Remove group members from the group menu, or ask the owner to change the role.

# How do I find my protections?

Open `/chestprotect` and choose `Protections`. You can also use `/chestprotect view` to visualize
nearby protections.

# What happens when I unlock a protection?

The protection is removed. Depending on the server's economy settings, you may receive cashback
from the original lock cost.
