# Usage
Allows you to forward chat in-game to Discord and vice versa. Also land and nation owners can create a text and voice channel in the Discord server. This can be disabled and configured.

# Requirements
Requires DiscordBridge the Lands plugin to be installed.
* SpigotMC: [Lands](https://www.spigotmc.org/resources/53313), [DiscordBridge](https://www.spigotmc.org/resources/114986/)
* Polymart: [Lands](https://polymart.org/resource/876), [DiscordBridge](https://polymart.org/resource/5476)

# Setup
1. Optional: Execute ``/config set LANDS_CHAT_CATEGORY`` in the Discord server. Lands chat and voice channels will be created under this category via the ``/lands channel create`` and ``/nations channel create`` Discord command.
2. Optional: Execute ``/config set LANDS_BROADCAST_CHANNEL`` in the Discord server. Lands announcements, such as land deletions, wars, etc. will be sent there.

## Notification Roles for Broadcast Messages
Command: ``/config set LANDS_NOTIFY_<broadcast_category>``\
You must replace `broadcast_category` with a broadcast category. 
