Bedrock players can join Java edition Minecraft servers with the help of the Geyser and floodgate plugin.

# Does the Plugin Provide Special Features for Bedrock Clients?
Confirmation prompts will open a dedicated confirmation GUI, when floodgate is installed. Also chat inputs, like entering the name of a player, will open a dedicated GUI. Floodgate must be installed to provide these features. Lands and UpgradeableSpawners also provide Bedrock forms for the menus instead of the vanilla ones (this only affects Bedrock players and can be disabled).

# General
The GUI file is located under: `/plugins/<plugin>/Language` - whereas `<plugin>` needs to be replaced with the plugin name. To use this functionality, floodgate must be installed on the server.

# Button Icons
Most buttons can have an image.

## Icons from Resource Packs
Notice that `image` is set to the path of the texture in the resource pack. You can find a resource pack sample here: https://github.com/Mojang/bedrock-samples/releases
````yaml
back:
  name: '&4Back'
  image: 'textures/blocks/stone.png'
````

## Icons from URL
````yaml
back:
  name: '&4Back'
  image: 'https://example.com/someimage.png'
````

# Disabling Buttons, Commands etc.
Bedrock buttons support the same features as vanilla items, except you can't set enchantments to the buttons, etc. More info: [Link](GUI-Menus.md)

# If Bedrock Menus Don't Open
Please follow the floodgate installation instructions for both "Paper / Spigot" and "Proxy Servers" (if you use a proxy): [Link](https://wiki.geysermc.org/floodgate/setup)
