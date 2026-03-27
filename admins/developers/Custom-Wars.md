You can add your own war gamemodes by registering your own WarHandler with the ``setWarHandler`` of the API instance you
created.

Example:

````java
LandsIntegration api = LandsIntegration.of(plugin);
api.setWarHandler(new WarHandler() {...});
````

You need to implement the methods of the ``WarHandler`` interface. Read the JavaDocs for more information about them.
This way you can integrate your own war gamemodes into the existing ``/war`` commands, menus and so on.