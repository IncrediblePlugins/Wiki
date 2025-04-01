[![](https://jitpack.io/v/IncrediblePlugins/UpgradeableHoppersAPI.svg)](https://jitpack.io/#IncrediblePlugins/UpgradeableHoppersAPI)

# Javadoc

Can be found [here](https://jitpack.io/com/github/incredibleplugins/UpgradeableHoppersAPI/latest/javadoc/).

# API Usage Explained

Include the API using Gradle:

```groovy
repositories {
    maven { url 'https://jitpack.io' }
}

dependencies {
    compileOnly "com.github.angeschossen:UpgradeableHoppersAPI:version"
}
```

Replace `version` with the version that you want to use.

Include the API using Maven:

```xml

<repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://jitpack.io</url>
    </repository>
</repositories>

<dependencies>
<dependency>
    <groupId>com.github.angeschossen</groupId>
    <artifactId>UpgradeableHoppersAPI</artifactId>
    <version>version</version>
    <scope>provided</scope>
</dependency>
</dependencies>
```

Replace `version` with the version that you want to use.

The API is accessible through an implementation of
the [UpgradeableHoppersAPI](https://javadoc.jitpack.io/com/github/angeschossen/UpgradeableHoppersAPI/4.13.10/javadoc/me/angeschossen/upgradeablehoppers/api/UpgradeableHoppersAPI.html)
interface.
UpgradeableHoppers needs to be loaded before this API can be used. It doesn't need to be enabled though.

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
