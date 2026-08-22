# Farm Menu

Open the farm menu by left-clicking the placed farm item. You can also use `/farm list` and select one of your farms.

Right-clicking the placed farm opens storage directly.

# Status

The status item shows whether the farm is running or paused.

Common paused states:

| Status | What to do |
| --- | --- |
| Fuel empty | Add valid fuel items in the fuel menu. |
| Storage full | Collect items from storage or connect an upgradeable hopper if your server supports it. |
| No blocks | Place harvestable blocks inside the farm radius. |
| Owner offline | The farm type requires the owner to be online. The farm continues when the owner returns. |
| Chunk unloaded | The farm's chunk needs to be loaded. |
| Paused manually | Click the status item again to resume, if the other requirements are met. |

Players with configure access can click the status item to pause or resume a manually paused farm.

# Storage

The storage menu contains the harvested items produced by the farm.

Click an item to collect it, or use **Collect All** to move as much as possible into your inventory. If your inventory does not have enough space, the remaining items stay in the farm storage.

Upgrading **Storage Capacity** increases the number of storage slots. When storage is full, the farm pauses until space is available.

# Fuel

Some farm types require fuel. Open the fuel menu, place valid fuel items into the fuel slots, and close the menu to add the fuel time.

Use the **Fuel Items** page in the menu to see which items your server accepts and how much time each item adds.

# Upgrades

The default farm menu has three upgrade categories:

| Upgrade | Effect |
| --- | --- |
| Growth Interval | Reduces the time between growth cycles. |
| Radius | Increases how far the farm can reach. |
| Storage Capacity | Adds more internal storage slots. |

Upgrades can cost money, experience, levels, or configured item currency. Some servers require the `betterfarming.upgrade` permission before any farm can be upgraded.

Radius upgrades can fail if the larger farm would overlap another farm, leave a required claim, or reach into a claim where you are not trusted.

# Harvestable Blocks

The **Harvestable Blocks** page shows which blocks this farm type can use.

Only configured blocks placed inside the farm radius are tracked. If a farm says it has no blocks, check this page and place one of the listed blocks near the farm.

# Public Access

The **Public** option lets other players use basic public actions on the farm, such as planting, harvesting, and interacting. It does not give them management access, upgrades, deletion, or permission to change trusted players.

# Hopper Output

If your server has UpgradeableHoppers support enabled, place an upgradeable hopper directly underneath the farm. BetterFarming can then move harvested items from farm storage into the hopper for transport.
