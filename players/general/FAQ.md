# Frequently Asked Questions

Read [Start](../basics/Start.md) first if you are new to UpgradeableSpawners.

# Why is my spawner paused?

Open the spawner menu and look at the status item. Common reasons are:

* No player is close enough.
* Too many nearby entities of the same type.
* The spawner reached its spawn limit for the current period.
* Too many UpgradeableSpawners entities are already in the surrounding area.
* The spawner was paused manually.
* The spawner is powered by redstone and your server pauses spawners on redstone signal.
* Butcher mode requires a hopper, but no upgradeable hopper is connected.

# Why can I not place a spawner?

Your server may block placement because of the world, claim, ownership, personal spawner limit, or
per-chunk spawner limit.

Read the chat message after placement fails. It usually names the rule that stopped you.

# Why did I not get the spawner item after breaking it?

Your server may require a specific tool, Silk Touch, the `uspawners.silktouch` permission, the
`uspawners.drop-item` permission, or a configured chance to successfully retrieve spawners.

If Silk Touch pickup is disabled on your server, you still need whatever pickup permission your
server gives to players.

# Do upgrades reset when I break a spawner?

No. Upgradeable spawner items store their upgrade levels, selected entity type, purchased entity
types, and period progress.

# Why can I not upgrade?

You may be missing permission, money, or access to edit that spawner. The upgrade may also already
be at its maximum level.

# Why can I not change the entity type?

The entity type may cost money, require a permission, or be disabled by the server.

Use the entity type menu to see which types are available to you.

# Why are entities stacked?

UpgradeableSpawners can merge spawned entities into stacks for performance. A visible stacked entity
represents multiple entities.

# Why do drops appear without visible entities?

That spawner is probably using butcher mode. Butcher mode handles the spawned entities instantly and
drops their loot instead of leaving them alive.
