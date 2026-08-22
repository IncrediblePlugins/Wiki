# Status and Limits

The status item in the spawner menu tells you whether a spawner is running or paused.

If it is paused, the item explains the reason. Some reasons are caused by your spawner's upgrades,
and some are caused by server-wide limits.

# Running

The spawner is active and can spawn when its interval is ready.

It still needs a valid spawn location. If the area around the spawner is blocked, the spawner may
skip that spawn attempt.

# No Player Nearby

At least one player must be within the spawner's player distance.

Upgrade Player Distance if your server allows it, or stand closer to the spawner.

# Max Nearby Entities

There are too many nearby entities of the same type.

Remove nearby entities, move farms farther apart, or upgrade Nearby Entities if your server allows
it.

# Max Period Entities

The spawner reached its spawn limit for the current period.

Wait until the period resets, or upgrade Spawns During Period if your server allows it.

# Max Entities in Area

Too many entities spawned by UpgradeableSpawners are already in the surrounding area. This limit can
include nearby chunks, depending on the server configuration.

Remove spawned entities or spread spawners farther apart.

# Paused Manually

Someone with edit access paused the spawner from the spawner menu.

Click the status item again to resume it. It will only resume if the other limits are currently met.

# Redstone Signal

Your server can pause spawners while they receive redstone power.

Remove the redstone signal if you want the spawner to run.

# Hopper Missing

Butcher mode is enabled and your server requires an UpgradeableHoppers hopper below the spawner.

Place an upgradeable hopper below the spawner, or disable butcher mode if your server allows it.
