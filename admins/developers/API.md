[![Package](https://img.shields.io/maven-metadata/v?metadataUrl=https://repo.incredibleplugins.com/releases/com/incredibleplugins/lands-api/maven-metadata.xml)](https://repo.incredibleplugins.com/#/releases/com/incredibleplugins/lands-api)

The API is in our repository: [repo.incredibleplugins.com](https://repo.incredibleplugins.com/#/releases/com/incredibleplugins/lands-api)

# Javadoc
The Javadoc can be found here: [repo.incredibleplugins.com](https://repo.incredibleplugins.com/javadoc/releases/com/incredibleplugins/lands-api/latest)

# API Usage Explained
First, include the API in your build file. Example snippets for your build file can be found here: [Maven, Gradle, SBT](https://repo.incredibleplugins.com/#/releases/com/incredibleplugins/lands-api)
> You can also download the API file from there, if you want to add it to your libraries manually.

The API is accessible through an implementation of the ``LandsIntegration`` interface.
It is recommended to bind this instance to a variable of a singleton class, if possible.
````java
LandsIntegration api = LandsIntegration.of(plugin);
````

#### Common Use-Cases
1. Checking Role-Flag States for Players\
   Using ``LandWorld`` to check flag states has the benefit that it also checks wilderness flags. Some use cases might not intent that. In this case you can use ``LandsIntegration#getArea(location)`` and check the flag state of the area instead.
    ````java
    LandWorld world = api.getWorld(world);
    if (world != null) { // Lands is enabled in this world
        if (world.hasFlag(api.getLandPlayer(player), location, material, Flags.BLOCK_BREAK, false)) {
            // the player is allowed to break blocks with the given material at the given location
        } else {
            // the player isn't allowed to break this block in wilderness or a claimed land at this position
        }
    }
    ````

2. Checking Natural-Flag States\
   ``LandWorld`` does check wilderness and claimed lands if applicable. If you want to
   limit the check to claimed land, use ``LandsIntegration#getArea(location)`` instead of getting the world.
    ````java
    LandWorld world = api.getWorld(world);
    if (world != null) { // Lands is enabled in this world
        if (world.hasNaturalFlag(location, Flags.MONSTER_SPAWN)) {
            // monsters are allowed to spawn at this location
        } else {
            // they aren't allowed to spawn at this location
        }
    }
    ````
3. Registering custom Flags\
   This one is simple as well. Just use the factory methods of the needed flag type's interface: ``RoleFlag.of(...)``, ``NaturalFlag.of(...)`` etc.
   Please note that flags need to registered after Lands was loaded, but before Lands enables. You can ensure that, by using this method in your `onLoad` method of your plugins main class: ``LandsIntegration#onLoad``

    ````java
    RoleFlag flag = RoleFlag.of(api, FlagTarget.PLAYER, RoleFlagCategory.ACTION, "flag_name");
    ````
   It is recommended to set further attributes:
    ````java
    flag.setDisplayName("Name")
        .setIcon(itemstack)
        .setDescription(description);
    ````
