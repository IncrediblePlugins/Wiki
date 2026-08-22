# Start Using BetterFarming

This page explains the basic player flow for BetterFarming.

Commands in this guide use `/farm`, the short command alias. `/betterfarming` works as the full command on every server. Some servers may also enable extra aliases, such as `/farms`.

# 1. Get a Farm Item

Use:

`/farm get [type] [amount]`

If you do not enter a type, the server's default farm type is used. Depending on the server, getting a farm item may cost money, experience, levels, or configured currency items.

If your server requires purchase confirmation, click the confirm message or repeat the command with `confirm` when prompted.

# 2. Place the Farm

Place the farm item on the ground.

Your server may block placement if:

* the world is not enabled for BetterFarming
* the farm would overlap another farm
* the item belongs to another player
* you reached your farm limit
* the server requires farms to be placed inside a claim
* you are not trusted in the claim where you are placing it
* the target block is water, lava, or not valid ground

After placement, the farm item becomes the center of the farm. The protected area reaches outward by the farm's radius and also has a vertical protection range configured by the server.

# 3. Add Harvestable Blocks

Place crops, saplings, or other configured harvestable blocks inside the farm radius.

Use the farm menu's **Harvestable Blocks** page to see what that farm type accepts. The default configuration includes crop farms for crops such as wheat, carrots, potatoes, beetroots, melons, pumpkins, sweet berries, nether wart, sugar cane, and cactus. It also includes tree farms for common saplings.

Servers can add, remove, rename, or disable farm types and harvest blocks.

# 4. Keep the Farm Running

Farms grow blocks on a timer. When a configured block is ready, the farm harvests it into internal storage and resets it for another cycle.

A farm can pause if:

* it is out of fuel
* its storage is full
* it has no harvestable blocks inside the radius
* the owner is offline and the farm type requires the owner to be online
* the chunk is unloaded
* a player paused it manually

Open the farm menu to see the current status and the next thing to fix.

# 5. Collect Items

Right-click the farm to open its storage.

You can collect individual items or use **Collect All**. If your inventory fills up, remaining items stay in farm storage.

If your server uses UpgradeableHoppers integration, placing an upgradeable hopper directly below the farm lets BetterFarming move harvested items into that hopper automatically.

# 6. Upgrade the Farm

Left-click the farm to open the farm menu. You can also open your farms from `/farm list`.

Depending on your permissions and the server economy, you may be able to upgrade:

* **Growth Interval** - shorter intervals make growth cycles faster
* **Radius** - larger radius lets the farm cover more blocks
* **Storage Capacity** - more storage slots before the farm pauses from full storage

Upgrades can have costs and may be locked behind permissions on some servers.

# 7. Remove a Farm

Collect anything you still want from the farm storage before removing the farm.

Sneak and left-click the farm item to remove it.

You need permission through ownership, role access, or a server bypass permission. Removing a valid loaded farm gives the farm item back to you, or drops it at the farm if your inventory is full.
