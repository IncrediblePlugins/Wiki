# Upgrades

A spawner has **one combined upgrade level**. Buying the next level raises every stat below at
once, for one combined cost — there is no way to raise one stat without the others.

Open a spawner menu by right-clicking the spawner. The upgrade item shows your current level, what
each stat becomes at the next level, and the cost. Click it to buy the next level.

Your server controls all level values and costs in its configuration. Some servers may hide or
disable the upgrade item entirely.

# What a Level Changes

| Stat | What it changes |
| --- | --- |
| Spawn Interval | How often the spawner tries to spawn. A lower interval is better. |
| Spawn Amount | How many entities the spawner tries to spawn each time it runs. |
| Spawns During Period | How many entities this spawner may spawn during the configured period. When the limit is reached, the spawner pauses until the period resets. |
| Player Distance | How far away a player can be while still keeping the spawner active. |
| Nearby Entities | How many nearby entities of the same type are allowed before the spawner pauses. |

# Buying Upgrades

To buy the next level, you usually need:

* Permission to upgrade spawners.
* Enough money or the economy item used by your server.
* Access to edit that spawner.

If you cannot buy the next level, the menu will usually show whether you are missing money,
permission, or are already at the maximum level.

# Stacked Spawners

Upgrading a stacked spawner upgrades every spawner inside the stack at once. Your server may scale
the upgrade cost with the stack size. Read [Spawner Stacking](../general/Spawner-Stacking.md) for
details.

# When an Upgrade Looks Different

Some entity types can use a custom spawning mode configured by the server. Those spawners still use
the same level and stats, but the server handles the spawn checks itself instead of relying only on
Minecraft's vanilla spawner behavior.

From a player point of view, the important part is the same: the spawner menu shows the current
level's stats and the status item tells you why the spawner is paused.
