1. Stop your server.
2. Place the Lands.jar file in your plugins folder.
3. Start your server.
4. Edit the configurations to your liking. You can find explanations in the comments located in your config file. The config can be found in the plugin's folder (`/plugins/Lands`). A important configuration is the `claim-worlds_list`, which defines in which worlds players should be allowed to claim.
5. [Setup permissions.](../permissions/Recommended-Permission-Setup.md)
6. Restart your server

Please always stop your server before installing updates. The config and locale files automatically remove new entries and remove no longer existing entries.

## Video
The following video shows the initial steps of the setup to get you started.
{% embed url="https://www.youtube.com/watch?v=YH9FwoY54O8" %}

# Basic Mode
If you want to turn all advanced features off and only want to have simple claiming features, you can
enable ``basic-mode`` in the config. This option disables all advanced features.

If you want a specific feature to be enabled with basic mode:
Basic mode is meant to be basic. You can create your own basic mode by just disabling the inbuilt basic mode and
disabling all features that you don't want. The inbuilt basic mode does nothing else other than disabling options in the config.
Enabling basic mode once and then disabling it will keep the features disabled until manually enabled again. So you can use the inbuilt basic mode as a preset for your
own basic mode.

# Disable Claming for Regular Players
The ``claim-worlds`` option in the config file defines a list of world where claiming should be disabled. There you can add worlds and still decide whether 
regular players should be able to claim there or just server admins. Read the comments in the config file for that option to understand how you can achieve that:
````yaml
  # Worlds where players should be able to claim. You can add all worlds by adding * to the list.
  # You can also set optional parameters such as, if claiming should be enabled for regular players without admin perms (permission: lands.admin.disabled-features)
  # and the minimum and maximum claim height. The format is a follows: <worldname>:<claiming>:<min-height>:<max-height>
  # NOTE: Minimum height can't be lower than your server's min height and maximum height can't be higher than your servers maximum height. The claim height of admin lands will always be maxed out.
  # NOTE: This setting requires server reload / restart.
  # Examples:
  #   'world' -> This results in the max claim height and claiming enabled for players.
  #   'world:true:30:319' -> This results in a claim height of 30 to 319 and claiming enabled for players.
  #   'world:false' -> Only server admins can claim in this world to create admin lands etc.
  claim-worlds_list:
    - 'world'
````

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
