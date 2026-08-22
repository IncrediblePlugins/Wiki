# Usage

Allows you to forward chat in-game to Discord and vice versa.

# Setup

1. Make sure the [Bot](Bot.md) module is enabled and connected.
2. Execute ``/config set chat_channel textchannel:<channel>`` in your Discord server. This defines the channel used by the chat bridge.
3. Edit `DiscordBridge/Modules/chat.yml` to choose which directions are forwarded.

# Options

| Option | What it controls |
| --- | --- |
| `forward.discord.enabled` | Whether messages from the configured Discord channel are sent to Minecraft. |
| `forward.discord.force-link` | Whether Discord users must link their account before their messages are sent to Minecraft. |
| `forward.discord.format` | Format used for Discord messages that appear in Minecraft. PlaceholderAPI placeholders are supported. |
| `forward.discord.all-servers` | Whether Discord messages are also forwarded to other configured Discord servers. |
| `forward.discord.bots` | Whether messages from other Discord bots are forwarded. |
| `forward.minecraft.enabled` | Whether Minecraft chat is sent to Discord. |
| `forward.minecraft.ignore-cancelled` | Whether DiscordBridge should still forward chat events cancelled by another chat plugin. |

# Player Notes

Player-facing chat behavior is documented in [Chat Bridge](../players/Chat.md).
