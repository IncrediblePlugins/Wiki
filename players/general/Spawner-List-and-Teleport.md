# Spawner List and Teleport

Use `/spawners list` to open a menu with your placed spawners.

Each entry shows the spawner's location, entity type, and upgrade values.

# Open a Spawner from the List

Click a spawner entry to open its spawner menu.

The spawner's chunk must be loaded. If the chunk is unloaded, the menu cannot safely open that
spawner.

# Teleport to a Spawner

Right-click a spawner entry to teleport to it, if teleportation is enabled on your server.

Teleportation can have:

* A money cost.
* A short wait time.
* A permission requirement.
* A safety check for the destination.

Do not move while waiting for teleportation, or it may be cancelled.

# Unsafe Destinations

If the destination is not safe, the teleport is cancelled.

Use `/spawners confirmtp` only if you really want to teleport anyway. The destination may be
dangerous.
