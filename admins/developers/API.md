[![Package](https://img.shields.io/maven-metadata/v?metadataUrl=https://repo.incredibleplugins.com/releases/com/incredibleplugins/upgradeablehoppers-api/maven-metadata.xml)](https://repo.incredibleplugins.com/#/releases/com/incredibleplugins/lands-api)

The API is in our repository: [repo.incredibleplugins.com](https://repo.incredibleplugins.com/#/releases/com/incredibleplugins/upgradeablehoppers-api)

# Javadoc
The Javadoc can be found here: [repo.incredibleplugins.com](https://repo.incredibleplugins.com/javadoc/releases/com/incredibleplugins/upgradeablehoppers-api/latest)


Replace `version` with the version that you want to use.

The API is accessible through an implementation of the UpgradeableHoppersAPI interface. UpgradeableHoppers needs to be loaded before this API can be used. It doesn't need to be enabled though.

````java
UpgradeableHoppersAPI api = UpgradeableHoppersAPI.getInstance();
````

# Preventing Item Pickup

## Just a Specific Item

If you want to prevent a specific item being picked up by the hoppers, just add the
"NO_PICKUP" metadata to the item entity.

## Items in Regions of your Custom Region Plugin

Enable the following option in ``config.yml`` and listen to the HopperItemPickupEvent.
This should be the last resort. If you only want to prevent a specific item from being picked up, use the solution above
instead.

````yaml
  # If enabled, the plugin calls the HopperItemPickupEvent for 3rd party plugins to listen to.
  # That way they can for example cancel the hopper picking up items from an untrusted region.
  call-item-pickup-event: true
````

# Listening to Item Transfer

Enable the following option in ``config.yml`` and listen to the HopperItemTransferEvent.
It's called whenever a hopper transfers an item to one of its links, and can be cancelled to
prevent that specific transfer.

````yaml
  # If enabled, the plugin calls the HopperItemTransferEvent for 3rd party plugins to listen to.
  # That way they can for example cancel a hopper transferring an item to one of its links.
  call-item-transfer-event: true
````
