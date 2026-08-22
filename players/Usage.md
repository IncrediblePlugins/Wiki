# Usage

FasterFurnaces lets you place special furnace blocks that can be upgraded. Upgraded furnaces work like normal Minecraft furnaces, blast furnaces, or smokers, but their level can improve smelting speed, fuel duration, and experience rewards.

The exact furnace types, prices, level names, and upgrade values are configured by the server. By default, the common types are `furnace`, `blast_furnace`, and `smoker`.

## Get a Furnace

Use `/fasterfurnaces get [type] [amount]` in game.

Examples:

* `/fasterfurnaces get`
* `/fasterfurnaces get furnace 1`
* `/fasterfurnaces get smoker 3`

If you do not enter a type, the server's default type is used. Some servers may also give upgradeable furnaces through shops, crates, kits, or staff rewards instead of the command.

If you want more than one item, include the type name before the amount, such as `/fasterfurnaces get furnace 3`.

## Place and Use a Furnace

Place the upgradeable furnace item like a normal block.

* Right-click the furnace to open its normal smelting inventory.
* Left-click the furnace while not sneaking to open its upgrade and management menu.
* Sneak before breaking the furnace if you want to pick it up or move it.

Your server may limit where upgradeable furnaces can be placed. For example, placement may be limited to specific worlds, claimed regions, or the amount of furnaces you are allowed to own.

## Upgrade a Furnace

Open the upgrade menu by left-clicking the furnace while not sneaking. The menu shows the current level, the next level, the upgrade cost, and the stats that will change.

When you buy an upgrade, the furnace level is saved on that block. The new stats apply automatically the next time the furnace starts smelting, burns fuel, or drops experience.

## Upgrade Effects

Furnace levels can affect these stats:

* `cook-time`: Changes how long a smelt takes. Lower values make the furnace faster.
* `fuel-time`: Changes how long fuel lasts. Higher values make each fuel item last longer.
* `exp`: Changes how much experience is dropped when items are taken out.

The default setup improves cook time and fuel time as the furnace levels up. Experience rewards are unchanged by default, but your server may configure them differently.

## Protection and Access

The player who places a furnace owns it. Owners can manage the furnace through the upgrade menu and can open the protection menu from there.

Default access roles:

| Role | What it can do |
| --- | --- |
| Owner | Full access, including opening, managing, and deleting the furnace. |
| Admin | Manage and open the furnace. |
| Member | Open the furnace. |
| Visitor | No access. |

Your server may allow region members to use furnaces in claimed areas, depending on its setup.

## List and Teleport

Use `/fasterfurnaces list` to view your placed furnaces. The list menu can be used to open a furnace's management menu. If teleportation is enabled on your server, the list can also teleport you near a furnace. Follow the menu lore or buttons for the available actions.

If a teleport location may be unsafe, FasterFurnaces can ask you to confirm it with `/fasterfurnaces confirmtp`.

## Remove or Move a Furnace

Sneak and break the furnace to remove it. If you are allowed to delete the furnace, the block is removed and the upgradeable furnace item is returned.

Items stored inside the furnace are dropped at the furnace location. Breaking an upgradeable furnace in creative mode without sneaking is blocked to help prevent accidental removal.

## Common Issues

If you cannot place a furnace, you may have reached your furnace limit, be in a disabled world, be outside a required claim, or not have permission to get/place more furnaces.

If you cannot open or manage a furnace, ask the owner to trust you with a role that can open or manage it.

If a furnace does not seem faster, make sure it is an upgradeable furnace and that it has been upgraded. Server owners can change the upgrade values, so the exact speed can differ between servers.
