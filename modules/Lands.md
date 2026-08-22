# Usage

Connects [Lands](https://www.spigotmc.org/resources/53313) with DiscordBridge.

Land and nation owners can create Discord text and voice channels, land and nation chat can be forwarded between Minecraft and Discord, and Lands broadcast messages can be sent to Discord.

# Requirements

Requires DiscordBridge and the Lands plugin to be installed.

* SpigotMC: [Lands](https://www.spigotmc.org/resources/53313), [DiscordBridge](https://www.spigotmc.org/resources/114986/)
* Polymart: [Lands](https://polymart.org/resource/876), [DiscordBridge](https://polymart.org/resource/5476)

# Setup

1. Optional: Execute ``/config set lands_chat_category category:<category>`` in the Discord server. Lands chat and voice channels will be created under this category via the ``/lands channel create`` and ``/nations channel create`` Discord command.
2. Optional: Execute ``/config set lands_broadcast_channel textchannel:<channel>`` in the Discord server. Lands announcements, such as land deletions, wars, etc. will be sent there.
3. Optional: Edit `DiscordBridge/Modules/lands.yml` to choose whether text channels, voice channels, or both can be created.

## Notification Roles for Broadcast Messages

Command: ``/config set lands_notify_<broadcast_category> role:<role>``\
You must replace `broadcast_category` with a broadcast category. 

# Discord Commands

| Command | What it does |
| --- | --- |
| `/lands top` | Shows top lands. |
| `/lands channel create land:<land>` | Creates the configured Discord channel for a land. |
| `/lands channel delete name:<land>` | Deletes the Discord channel for a land. |
| `/lands inbox` | Shows the inbox for the land connected to the current Discord channel. |
| `/nations top` | Shows top nations, if nations are enabled. |
| `/nations channel create nation:<nation>` | Creates the configured Discord channel for a nation. |
| `/nations channel delete name:<nation>` | Deletes the Discord channel for a nation. |
| `/nations inbox` | Shows the inbox for the nation connected to the current Discord channel. |

Channel create and delete actions require the Discord account to be linked to the Minecraft owner of the land or nation, unless the Discord member has administrator permission.

# Player Guide

Player-facing Lands usage is documented in [Lands Integration](../players/Lands.md).
