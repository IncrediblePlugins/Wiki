# Chat Bridge

DiscordBridge can forward chat between Minecraft and Discord.

Your server may enable Minecraft-to-Discord chat, Discord-to-Minecraft chat, both directions, or neither.

# Minecraft to Discord

When Minecraft-to-Discord chat is enabled, normal Minecraft chat messages are sent to the configured Discord chat channel.

Messages are sent through the bot's webhook. This lets Discord show the Minecraft player's name and avatar instead of only the bot name.

Only chat text is forwarded. The server controls the final channel, format, and whether cancelled chat events are forwarded.

# Discord to Minecraft

When Discord-to-Minecraft chat is enabled, messages sent in the configured Discord chat channel are shown in Minecraft.

Important details:

| Detail | What it means |
| --- | --- |
| Correct channel | Only the configured Discord chat channel is forwarded. |
| Linked accounts | Some servers require your Discord account to be linked before your messages are sent to Minecraft. |
| Text only | Message text is forwarded. Attachments and embeds are not sent as Minecraft chat messages. |
| Bots | Bot messages are ignored unless the server explicitly allows them. |
| Threads | Thread messages are not forwarded by the chat bridge. |

If linking is required and your account is not linked, the bot replies with linking instructions.

# Lands Chat Channels

Lands integration uses separate land and nation channels. Messages in those channels are sent to the matching land or nation chat, not to the global Minecraft chat channel.

Read [Lands Integration](Lands.md) if your server uses Lands.

# If Messages Do Not Appear

Check that you are using the correct Discord channel, that your account is linked if required, and that the feature is enabled on the server.

If everything looks correct, ask staff to check the DiscordBridge chat module configuration and bot permissions.
