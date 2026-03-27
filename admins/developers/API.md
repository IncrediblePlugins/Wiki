[![](https://jitpack.io/v/Angeschossen/LandsAPI.svg)](https://jitpack.io/#Angeschossen/LandsAPI)

# Javadoc
The JavaDoc can be found here: [JitPack](http://jitpack.io/com/github/angeschossen/LandsAPI/7.10.13/javadoc)

# API Usage explained

Include the API using Gradle:
```groovy
repositories {
   maven { url 'https://jitpack.io' }
}

dependencies {
    compileOnly "com.github.angeschossen:LandsAPI:version"
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
        <artifactId>LandsAPI</artifactId>
        <version>version</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```
Replace `version` with the version that you want to use.

The API is accessible through an implementation of the ``LandsIntegration`` interface.
It is recommended to bind this instance to a variable of a singleton class, if possible.
````java
LandsIntegration api = LandsIntegration.of(plugin);
````

#### Common Use-Cases
1. Checking Role-Flag States for Players\
   Using [LandWorld](https://javadoc.jitpack.io/com/github/angeschossen/LandsAPI/7.10.6/javadoc/me/angeschossen/lands/api/land/LandWorld.html) to check flag states has the benefit that it also checks wilderness flags. Some use cases might not intent that. In this case you can use [LandsIntegration#getArea(location)](https://javadoc.jitpack.io/com/github/angeschossen/LandsAPI/7.10.6/javadoc/me/angeschossen/lands/api/LandsIntegration.html#getArea(org.bukkit.Location)) and check the flag state of the area instead.
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
   [LandWorld](https://javadoc.jitpack.io/com/github/angeschossen/LandsAPI/7.10.6/javadoc/me/angeschossen/lands/api/land/LandWorld.html) does check wilderness and claimed lands if applicable. If you want to
   limit the check to claimed land, use [LandsIntegration#getArea(location)](https://javadoc.jitpack.io/com/github/angeschossen/LandsAPI/7.10.6/javadoc/me/angeschossen/lands/api/LandsIntegration.html#getArea(org.bukkit.Location)) instead of getting the world.
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
3. Registering your own Flags\
   This one is simple as well. Just use the factory methods of the needed flag type's interface: [RoleFlag.of(...)](https://javadoc.jitpack.io/com/github/angeschossen/LandsAPI/7.10.6/javadoc/me/angeschossen/lands/api/flags/type/RoleFlag.html#of(me.angeschossen.lands.api.LandsIntegration,me.angeschossen.lands.api.flags.enums.FlagTarget,me.angeschossen.lands.api.flags.enums.RoleFlagCategory,java.lang.String)), [NaturalFlag.of(...)](https://javadoc.jitpack.io/com/github/angeschossen/LandsAPI/7.10.6/javadoc/me/angeschossen/lands/api/flags/type/NaturalFlag.html#of(me.angeschossen.lands.api.LandsIntegration,me.angeschossen.lands.api.flags.enums.FlagTarget,java.lang.String)) etc.
   Please note that flags need to registered after Lands was loaded, but before Lands enables. You can ensure that, by using this method in your `onLoad` method of your plugins main class: [LandsIntegration#onLoad](https://javadoc.jitpack.io/com/github/angeschossen/LandsAPI/7.10.6/javadoc/me/angeschossen/lands/api/LandsIntegration.html#onLoad(java.lang.Runnable))

    ````java
    RoleFlag flag = RoleFlag.of(api, FlagTarget.PLAYER, RoleFlagCategory.ACTION, "flag_name");
    ````
   It is recommended to set further attributes:
    ````java
    flag.setDisplayName("Name")
        .setIcon(itemstack)
        .setDescription(description);
    ````