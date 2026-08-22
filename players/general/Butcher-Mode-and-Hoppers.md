# Butcher Mode and Hoppers

Butcher mode makes a spawner instantly handle the entities it would spawn. Instead of leaving
visible entities alive, the spawner creates the drops directly.

This can improve server performance and keeps farms cleaner, but it also means you are not fighting
the spawned entities yourself.

# Enable or Disable Butcher Mode

1. Right-click the spawner to open its menu.
2. Click the butcher item.

Some entity types can have butcher mode forced by the server. If butcher mode is forced, the menu
will show that it cannot be toggled for that entity type.

# Drops

Butcher mode drops loot at the spawner location.

If your server uses UpgradeableHoppers, place an upgradeable hopper below the spawner to move
butcher-mode drops into the hopper automatically.

If the hopper is full, your server decides whether leftover loot drops on the ground.

# Hopper Required

Some servers require an upgradeable hopper before butcher mode can run. If that setting is enabled
and no hopper is connected, the spawner pauses with a hopper-missing status.

Place an upgradeable hopper below the spawner or disable butcher mode if the server allows it.
