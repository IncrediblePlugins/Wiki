# Start

This page explains the first steps for using UpgradeableSpawners.

# 1. Get a Spawner

Use `/spawners get` to get one spawner item.

Use `/spawners get <amount>` if you want more than one at once. Your server may charge money for
each spawner item and may ask you to confirm the purchase.

Some servers give spawners through shops, crates, quests, or staff instead of the command.

# 2. Place the Spawner

Place the spawner in a world where UpgradeableSpawners is enabled.

Your server can also require one or more of these:

* You must be trusted in the claim where you place it.
* You must place it inside a claim instead of wilderness.
* You must stay below your personal placed-spawner limit.
* The chunk must stay below the server's maximum spawner limit.
* The item must belong to you.

If placement fails, read the message in chat. It usually tells you which rule stopped the
placement.

# 3. Open the Spawner Menu

Right-click one of your upgradeable spawners to open its menu.

The menu lets you upgrade the spawner, change its entity type, pause or resume it, enable butcher
mode, and see why it is currently paused.

If you are holding a spawn egg and your server allows egg changes, right-clicking may change the
entity type instead of opening the menu.

# 4. Upgrade the Spawner

The spawner has separate upgrades. Buying one upgrade does not increase the others.

Read [Upgrades](Upgrades.md) for a full explanation of each upgrade type.

# 5. Change the Entity Type

Open the spawner menu and click the entity type item.

Entity types may cost money and may require a permission. If you buy a new entity type, it is saved
on that spawner and can be selected again later.

Read [Entity Types](Entity-Types.md) for details.

# 6. Pause, Resume, or Use Butcher Mode

The status item in the spawner menu shows whether the spawner is running or paused. If it is paused,
the menu explains why.

Butcher mode instantly handles spawned entities and drops their loot instead of keeping visible
entities around the spawner. Read [Butcher Mode and Hoppers](../general/Butcher-Mode-and-Hoppers.md)
before using it.

# 7. Pick Up the Spawner

Break the spawner with an allowed tool to pick it up. Your server may require Silk Touch and the
`uspawners.silktouch` permission. If Silk Touch pickup is disabled, your server may still require
the `uspawners.drop-item` permission before the spawner item is returned.

The dropped spawner item keeps its upgrades, selected entity type, purchased entity types, and
period progress. If the server uses owner-locked spawner items, the owner stored on the item is used
again when it is placed.
