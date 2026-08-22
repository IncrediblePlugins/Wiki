This page explains the first steps for using DiscordBridge.

Some features only exist if your server enabled the matching module. Your server may also limit commands by permission or Discord role.

# 1. Join the Discord Server

If the server configured an invite link, use `/discordbridge invite` in Minecraft to get it.

The main command also has the `/discord` alias on many servers, so `/discord invite` may work too.

# 2. Link Your Accounts

Linking proves that your Minecraft account and Discord account belong to the same player.

Use `/account` or `/discordbridge account` in Minecraft to open the account menu. If your account is not linked yet, click the link option or use `/account link`.

Minecraft will show a short verification code. In the Discord server, run:

```text
/account link code:<code>
```

The code is only valid for about 5 minutes. If it expires, run the Minecraft command again to get a new one.

Read [Account Linking](Account-Linking.md) for the full linking and unlinking flow.

# 3. Use the Chat Bridge

If the chat module is enabled, normal Minecraft chat can appear in a Discord chat channel.

Messages sent in the configured Discord chat channel can also be sent back to Minecraft. Some servers require you to link your account before Discord messages are forwarded.

Read [Chat Bridge](Chat.md) for details.

# 4. Use Discord Features

Common Discord-side features include:

| Feature | What you do |
| --- | --- |
| Online players | Use `/online` in Discord to view online Minecraft players. |
| Tickets | Use the server's ticket creation message to open a private support channel. |
| Lands channels | If Lands integration is enabled, land or nation owners can create linked Discord channels. |

# 5. Ask Staff if a Feature Is Missing

DiscordBridge is modular. If a command, channel, ticket panel, or link reward is missing, it may be disabled or limited by the server's setup.
