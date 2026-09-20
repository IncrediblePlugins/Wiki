# Admin Flags

Farm flags are per-farm settings shown in the farm menu.

The regular **Public** flag can be changed by players with the farm's `CONFIGURE` role flag. The admin-only flag below is only shown to players with its admin permission.

# AUTO_REPLANT

`AUTO_REPLANT` changes how the farm handles harvestable blocks.

When enabled:

* the farm no longer performs automatic harvests into storage
* broken harvestable blocks are replaced during farm intervals
* players still need the correct farm role or public access to interact with the farm

Toggle permission:

`betterfarming.admin.flag.auto_replant`

# AUTO_SELL

`AUTO_SELL` sells harvested storage items with a configured `sell-price` (see [Farm Types](../config/Farm-Types.md)) automatically, instead of storing them or moving them into a hopper. Items without a sell price are unaffected.

The toggle in the storage menu is only shown if the farm type has at least one sellable item.

Toggle permission:

`betterfarming.admin.flag.auto_sell`

# WorldGuard Flag

Use this WorldGuard flag to allow farm creation in WorldGuard regions:

`betterfarming-create`
