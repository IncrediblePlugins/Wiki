# Javadoc
The Javadoc can be found here: [repo.incredibleplugins.com](https://repo.incredibleplugins.com/javadoc/releases/com/incredibleplugins/chestprotect-api/latest)

# API Usage Explained
First, include the API in your build file. Example snippets for your build file can be found here: [Maven, Gradle, SBT](https://repo.incredibleplugins.com/#/releases/com/incredibleplugins/chestprotect-api)
> You can also download the API file from there, if you want to add it to your libraries manually.

Declare ChestProtect as a dependency in your `plugin.yml` so Bukkit loads it before your plugin:

```yaml
depend:
  - ChestProtect
```

Use `softdepend` instead if ChestProtect is optional for your plugin.

## Getting the API instance

The API is accessible through an implementation of the [ChestProtectAPI](https://repo.incredibleplugins.com/javadoc/releases/com/incredibleplugins/chestprotect-api/latest/.cache/unpack/me/angeschossen/chestprotect/api/ChestProtectAPI.html) interface. Access it after ChestProtect is loaded (e.g. in `onEnable`):

```java
ChestProtectAPI api = ChestProtectAPI.getInstance();
```

> Calling `getInstance()` before ChestProtect is loaded throws a `NullPointerException`. If you used `softdepend`, guard the call with a null-check on `Bukkit.getPluginManager().getPlugin("ChestProtect")`.

---

## Checking and looking up protections

### Is a block or entity protectable?

```java
ProtectionManager manager = api.getProtectionManager();

boolean canProtectBlock  = manager.isProtectableBlock(Material.CHEST);
boolean canProtectEntity = manager.isProtectableEntity(EntityType.ITEM_FRAME);
```

### Look up a block protection

```java
// By Block object
BlockProtection protection = api.getBlockProtectionByBlock(block); // null if not protected

// By world + coordinates
ProtectionWorld world = api.getProtectionWorld(bukkitWorld);
if (world != null) {
    BlockProtection protection = world.getBlockProtection(x, y, z);
}
```

### Look up an entity protection

```java
EntityProtection protection = api.getEntityProtection(entity); // null if not protected
```

---

## Working with protections

Every `BlockProtection` and `EntityProtection` extends `Protection`, which provides:

```java
UUID owner      = protection.getOwner();
boolean trusted = protection.isTrusted(playerUUID);
String name     = protection.getDisplayName(); // player-defined name, may be null

// Trust / untrust
protection.trustPlayer(playerUUID);
protection.untrustPlayer(playerUUID);

// Flags (e.g. PUBLIC_TAKE, REDSTONE, HOLOGRAM)
boolean isPublic = protection.hasFlag(ProtectionFlag.PUBLIC_TAKE);
protection.toggleFlag(ProtectionFlag.PUBLIC_TAKE);

// Delete
protection.delete(protectPlayer);        // sends unlock message to deleter
protection.delete(protectPlayer, false); // silent delete
```

---

## Creating protections

You must provide a `ProtectionHook` that identifies your plugin as the creator. Protections created by a hook are automatically deleted if the owning plugin has not been active for 30 days.

### 1. Implement ProtectionHook

```java
public class MyHook extends ProtectionHook {

    public MyHook(Plugin plugin) {
        super(plugin);
    }

    @Override
    public boolean hasItem(ItemStack item) {
        // Return true if this item belongs to your plugin.
        // ChestProtect uses this to skip auto-lock for your custom items.
        return false;
    }
}
```

### 2. Register the hook on enable

```java
@Override
public void onEnable() {
    myHook = new MyHook(this);
    myHook.register();
}
```

### 3. Create a protection

```java
ProtectionManager manager = api.getProtectionManager();
ProtectPlayer protectPlayer = api.getProtectPlayer(player); // must be online

if (manager.isProtectableBlock(block.getType())) {
    BlockProtection protection = manager.createBlockProtection(myHook, block, protectPlayer);
}

if (manager.isProtectableEntity(entity.getType())) {
    EntityProtection protection = manager.createEntityProtection(myHook, entity, protectPlayer);
}
```

> `createBlockProtection` / `createEntityProtection` throw `IllegalArgumentException` if the block or entity type is not protectable, and `IllegalStateException` if the block or entity is already protected.

---

## Player data

### Online player

```java
ProtectPlayer protectPlayer = api.getProtectPlayer(player); // null if unloaded
int blockCount  = protectPlayer.getBlockProtectionsAmount();
int entityCount = protectPlayer.getEntityProtectionsAmount();
```

### Offline player

Offline player data is fetched asynchronously from the database:

```java
api.getProtectOfflinePlayer(uuid).thenAccept(offlinePlayer -> {
    if (offlinePlayer.hasData()) {
        int blockCount = offlinePlayer.getBlockProtectionsAmount();
    }
});
```

### Player flags

```java
boolean autoLock = protectPlayer.hasFlag(PlayerFlag.AUTO_LOCK);
protectPlayer.toggleFlag(PlayerFlag.NOTIFICATIONS);
```

---

## Events

Listen to ChestProtect events the same way as any Bukkit event:

| Event | Fired when |
|-------|-----------|
| `ProtectionPreCreationEvent` | Before a protection is created — cancellable |
| `ProtectionCreatedEvent` | After a protection has been created |
| `ProtectionDeletedEvent` | After a protection has been deleted |
| `PlayerOpenProtectionEvent` | When a player opens a protection — cancellable |
| `ProtectionChunkAddedEvent` | A chunk receives its first protection |
| `ProtectionChunkDeletedEvent` | The last protection in a chunk is deleted |

```java
@EventHandler
public void onProtectionCreated(ProtectionCreatedEvent event) {
    Protection protection = event.getProtection();
    // ...
}

@EventHandler
public void onProtectionPreCreation(ProtectionPreCreationEvent event) {
    if (someCondition) {
        event.setCancelled(true);
    }
}
```