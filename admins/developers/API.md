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
    LandWorld landWorld = api.getWorld(location.getWorld());
    LandPlayer landPlayer = api.getLandPlayer(player.getUniqueId());
    if (landWorld != null && landPlayer != null) { // Lands is enabled in this world, the player's data is loaded
        if (landWorld.hasRoleFlag(landPlayer, location, Flags.BLOCK_BREAK, material, false)) {
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
    LandWorld landWorld = api.getWorld(location.getWorld());
    if (landWorld != null) { // Lands is enabled in this world
        if (landWorld.hasNaturalFlag(location, Flags.MONSTER_SPAWN)) {
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
4. Creating sub areas\
   Like lands (``Land.of(...)``), nations and roles, sub areas are created with a factory method: ``LandArea.of(...)``.
   The region between both corners must be inside claims of the land and must not overlap another sub area.
   The future completes with ``null`` if that's not the case, or if another plugin cancelled the ``AreaCreateEvent``.
    ````java
    LandArea.of(land, "Market", corner1, corner2, api.getLandPlayer(player.getUniqueId())).thenAccept(area -> {
        if (area == null) {
            // the region isn't inside the land or overlaps another sub area
        }
    });
    ````
   Delete it again with ``LandArea#delete(LandPlayer)``. This calls the ``AreaDeleteEvent``.
5. Relations and war declarations\
   Lands and nations send alliance requests and declare wars with the same checks as the commands. Pass the player who
   does it to check their role flag and the requirements of the server, or ``null`` to skip the checks of a player
   (like an admin). A land in a nation acts for its nation. The futures can complete on another thread.
    ````java
    land.requestAlliance(target, landPlayer).thenAccept(result -> {
        // RelationResult.SUCCESS: the target accepts it with RelationRequest#accept
    });
    land.addEnemy(target, landPlayer);
    land.declareWar(target, null, null, landPlayer).thenAccept(result -> {
        // WarDeclarationResult.SUCCESS: land.getWarDeclaration() is the declaration
    });
    for (RelationRequest request : target.getReceivedRelationRequests()) {
        request.accept(null);
    }
    ````
   Requests call the ``MemberHolderRelationRequestEvent`` (cancellable), changes of a relation the
   ``MemberHolderRelationChangeEvent``. ``removeAlly`` and ``requestNeutralization`` end relations again.
6. War shields\
   Every change of a war shield calls the cancellable ``WarShieldChangeEvent`` with its reason (the end of a war, a
   declaration, an admin or a plugin through ``MemberHolder#setWarShield``/``addWarshield``). Cancel it to keep the
   shield as it is.
