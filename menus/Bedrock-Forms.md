Bedrock players can join Java edition Minecraft servers with the help of the Geyser and floodgate plugin.

# Does the Plugin Provide Special Features for Bedrock Clients?
Confirmation prompts will open a dedicated confirmation GUI, when floodgate is installed. Also chat inputs, like entering the name of a player, will open a dedicated GUI. Floodgate must be installed to provide these features. Lands and UpgradeableSpawners also provide Bedrock forms for the menus instead of the vanilla ones (this only affects Bedrock players and can be disabled).

# General
The Bedrock form file is located under: `/plugins/<plugin>/Locale` - whereas `<plugin>` needs to be replaced with the plugin name (the folder was previously called `Language`). Bedrock forms are in the `..._gui-bedrock.yml` file (e.g. `en-US_gui-bedrock.yml`). To use this functionality, floodgate must be installed on the server.

Button and form text is written in **MiniMessage**, the same as everywhere else — see [Text Formatting](../config/Text-Formatting.md). The old `&`/`§` color codes no longer work. Bedrock forms render on a dark panel, so `theme.yml`'s `theme.bedrock` section adjusts the theme tokens for that surface automatically.

# Button Icons
Most buttons can have an image.

## Icons from Resource Packs
Notice that `image` is set to the path of the texture in the resource pack. You can find a resource pack sample here: https://github.com/Mojang/bedrock-samples/releases
````yaml
back:
  name: '<t:regular_heading>Back'
  image: 'textures/blocks/stone.png'
````

## Icons from URL
````yaml
back:
  name: '<t:regular_heading>Back'
  image: 'https://example.com/someimage.png'
````

# Disabling Buttons, Commands etc.
Bedrock buttons support the same features as vanilla items, except you can't set enchantments to the buttons, etc. More info: [Link](GUI-Menus.md)

# If Bedrock Menus Don't Open
Please follow the floodgate installation instructions for both "Paper / Spigot" and "Proxy Servers" (if you use a proxy): [Link](https://wiki.geysermc.org/floodgate/setup)
