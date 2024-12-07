1. Stop your server.
2. Place the Lands.jar file in your plugins folder.
3. Start your server.
4. Edit the configurations to your liking. You can find explanations in the comments located in your config file. The config can be found in the plugin's folder (`/plugins/Lands`). A important configuration is the `claim-worlds_list`, which defines in which worlds players should be allowed to claim. However, you could still retrict this with per world permissions for the claim commands. 
5. [Setup permissions.](../permissions/Recommended-Permission-Setup.md)
6. Restart your server

Please always stop your server before installing updates. The config and locale files automatically remove new entries and remove no longer existing entries.

# Basic Mode
If you want to turn all advanced features off and only want to have simple claiming features, you can
enable ``basic-mode`` in the config. This option disables all advanced features.

If you want to use a specific features with basic mode, please don't post a suggestion on our Discord to have it included
in basic mode. Basic mode is meant to be basic. You can create your own basic mode by just disabling the inbuilt basic mode and
disabling all features that you don't want. The inbuilt basic mode does nothing else other than disabling options in the config.

# Import Claims
You can import claimed chunks and trusted members from other plugins. Just execute `/lands admin import <plugin>`.\
Currently supported plugins: 
* Towny
* WorldGuard
* GriefPrevention
* GriefDefender
* Residence
* ClaimChunk
* RedProtect
* Factions

You can join our [Discord Server](https://discord.incredibleplugins.com), if your current claim plugin isn't listed.

***
