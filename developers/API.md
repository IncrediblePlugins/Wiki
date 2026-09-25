[![Package](https://img.shields.io/maven-metadata/v?metadataUrl=https://repo.incredibleplugins.com/releases/com/incredibleplugins/betterfarming-api/maven-metadata.xml)](https://repo.incredibleplugins.com/#/releases/com/incredibleplugins/betterfarming-api)

The API is in our repository: [repo.incredibleplugins.com](https://repo.incredibleplugins.com/#/releases/com/incredibleplugins/betterfarming-api)

# Javadoc
The Javadoc can be found here: [repo.incredibleplugins.com](https://repo.incredibleplugins.com/javadoc/releases/com/incredibleplugins/betterfarming-api/latest)

# Info
The API is accessible through an implementation of the ``BetterFarmingAPI`` interface.
BetterFarming needs to be loaded before this API can be used. It doesn't need to be enabled though.
````java
BetterFarmingAPI api = BetterFarmingAPI.getInstance();
````

# Farm IDs

`Farm.getId()` returns a `String` (a ULID), not an `int`. This is a breaking change from earlier versions where farm IDs were incrementing integers - if you stored or compared farm IDs as numbers, update to string handling.

# Events

Farm events live under `me.angeschossen.betterfarming.api.events.farm`:

| Event | Cancellable | When |
| --- | --- | --- |
| `FarmPlaceEvent` | Yes | A farm is being created. |
| `FarmBreakEvent` | Yes (except `Reason.ADMIN`) | A farm is being deleted. |
| `FarmStatusChangeEvent` | No | A farm's status actually changes (e.g. running, paused for fuel or storage). Fired synchronously, after the change already took effect. |
| `FarmHarvestEvent` | No | A growable block inside a farm reaches its max age and is harvested. Fired asynchronously, since farm growth is calculated off the main thread. |
| `FarmUpgradeEvent` | No | A farm's level (radius, growth interval, and storage capacity together) has been upgraded and the cost has already been taken from the player. `getOldLevel()`/`getNewLevel()` are the level's own index, `getOldLevelName()`/`getNewLevelName()` its configured display name. |
| `FarmRefueledEvent` | No | Fuel time is added to a farm - manually, through a purchase, or via the API. |

`FarmBreakEvent.Reason`'s two claim-related constants were renamed from `LAND_UNCLAIM`/`LAND_UNTRUST` to `REGION_UNCLAIM`/`REGION_UNTRUST` (`PLAYER`/`ADMIN`/`EXPLOSION`/`INVALID` are unchanged) - a breaking change if you match on the old names.
