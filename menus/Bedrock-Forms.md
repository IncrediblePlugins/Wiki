Bedrock players can join Java edition Minecraft servers with the help of the Geyser and floodgate plugin.

# Does this Plugin support Bedrock Clients?
In general, Bedrock players can use the plugin. However, there are some minor restrictions. Like shift + left click, which is not available for these clients. That means that Bedrock players would not be able to use such function in GUI menus. All known restrictions apply to the GUI menus only, because of the mentioned click types.

# Does the Plugin provide special Features for Bedrock Clients?
Confirmation prompts will open a dedicated confirmation GUI, when floodgate is installed. Also chat inputs, like entering the name of a player, will open a dedicated GUI. Floodgate must be installed to provide these features.

# General
The GUI file is located under: /plugins/PLUGINNAME/Language.
To use this functionality, floodgate must be installed on the server.

# Button Icons
Most buttons can have an image.

## Icons from Resource Packs
Notice that `image` is set to the path of the texture in the resource pack. You can find a resource pack sample here: https://github.com/Mojang/bedrock-samples/releases
````
      back:
        name: '&4Back'
        image: 'textures/blocks/stone.png'
````

## Icons from URL
````
      back:
        name: '&4Back'
        image: 'https://example.com/someimage.png'
````

# Disabling Buttons, Commands etc.
Bedrock buttons support the same features as vanilla items, except you can't set enchantments to the buttons, etc. More info: https://github.com/Angeschossen/PluginFrameworkAPI/wiki/GUI-Menus

# If Bedrock Menus don't open
Please follow the floodgate installation instructions for both "Paper / Spigot" and "Proxy Servers" (if you use a proxy): https://wiki.geysermc.org/floodgate/setup