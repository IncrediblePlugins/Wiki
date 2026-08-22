# Upgrades

UpgradeableSpawners uses separate upgrade levels for each spawner. There is not one combined
"spawner level."

Open a spawner menu by right-clicking the spawner. Hover an upgrade item to see the current value,
the next value, and the cost. Click the upgrade item to buy the next level.

Your server controls all upgrade values and costs in its configuration. Some servers may hide or
disable specific upgrades.

# Upgrade Types

| Upgrade | What it changes |
| --- | --- |
| Spawn Interval | How often the spawner tries to spawn. A lower interval is better. |
| Spawn Amount | How many entities the spawner tries to spawn each time it runs. |
| Spawns During Period | How many entities this spawner may spawn during the configured period. When the limit is reached, the spawner pauses until the period resets. |
| Player Distance | How far away a player can be while still keeping the spawner active. |
| Nearby Entities | How many nearby entities of the same type are allowed before the spawner pauses. |

# Buying Upgrades

To buy upgrades, you usually need:

* Permission to upgrade spawners.
* Enough money or the economy item used by your server.
* Access to edit that spawner.

If you cannot buy an upgrade, the menu will usually show whether you are missing money, permission,
or the next level.

# When an Upgrade Looks Different

Some entity types can use a custom spawning mode configured by the server. Those spawners still use
the same upgrade names, but the server handles the spawn checks itself instead of relying only on
Minecraft's vanilla spawner behavior.

From a player point of view, the important part is the same: the spawner menu shows the current
values and the status item tells you why the spawner is paused.
