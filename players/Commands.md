# Commands

Most examples use `/chestprotect`. Many servers also enable `/cp`, `/protect`, and `/protection`
as aliases. Your server may also enable the direct shortcuts `/lock`, `/unlock`, `/trust`, and
`/untrust`.

Only commands you have permission to use are shown in command help.

| Command | What it does | Permission |
| --- | --- | --- |
| `/chestprotect` | Opens the main menu. This is the same as `/chestprotect menu`. | `chestprotect.command.menu` |
| `/chestprotect menu` | Opens the main menu. | `chestprotect.command.menu` |
| `/chestprotect lock` | Enters lock mode. Click a protectable object to lock it. | `chestprotect.command.lock` |
| `/chestprotect unlock` | Enters unlock mode. Click one of your protections to unlock it. | `chestprotect.command.unlock` |
| `/chestprotect trust <player>` | Enters trust mode. Click a protection to trust that player. | `chestprotect.command.trust` |
| `/chestprotect untrust <player>` | Enters untrust mode. Click a protection to remove that player. | `chestprotect.command.untrust` |
| `/chestprotect view` | Shows nearby protections with particles. Run it again to turn the view off. | `chestprotect.command.view` |
| `/chestprotect exit` | Leaves lock, unlock, trust, or untrust mode. | `chestprotect.command.exit` |
| `/chestprotect confirmtp` | Confirms an unsafe teleport destination after ChestProtect corrects or blocks a menu teleport. | None |
| `/chestprotect help [page]` | Shows the commands available to you. | `chestprotect.command.help` |

# Click Modes

`lock`, `unlock`, `trust`, and `untrust` do not immediately change a protection. They put you into a
mode and wait for you to click the target object.

Use `/chestprotect exit` if you started the wrong mode. Running the same mode command again can also
toggle that mode off.

# Shortcuts

If your server enables shortcuts, these commands do the same thing as the matching subcommands:

| Shortcut | Same as |
| --- | --- |
| `/lock` | `/chestprotect lock` |
| `/unlock` | `/chestprotect unlock` |
| `/trust <player>` | `/chestprotect trust <player>` |
| `/untrust <player>` | `/chestprotect untrust <player>` |
