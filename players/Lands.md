# Lands Integration

If your server also uses Lands, DiscordBridge can connect Lands features with Discord.

The exact features depend on the server setup. Server owners can enable land and nation chat channels, voice channels, broadcast messages, and top lists.

# Link Your Account First

Most Lands Discord actions need a linked account. DiscordBridge uses your linked Minecraft account to check whether you own the land or nation and whether you should have access to its channel.

Read [Account Linking](Account-Linking.md) if you are not linked yet.

# Land and Nation Chat Channels

Land or nation owners can create Discord channels for their land or nation if the server enabled channel creation.

| Command | What it does |
| --- | --- |
| `/lands channel create land:<land>` | Creates the configured land text and/or voice channel. |
| `/lands channel delete name:<land>` | Deletes the Discord channel for a land. |
| `/nations channel create nation:<nation>` | Creates the configured nation text and/or voice channel. |
| `/nations channel delete name:<nation>` | Deletes the Discord channel for a nation. |

When used inside the matching channel, the delete command may also work without the `name` argument.

Only the linked owner can create or delete a channel, unless the Discord member has administrator permission.

# Chat in a Land or Nation Channel

Messages sent in a created land or nation text channel are sent to the matching Lands chat in Minecraft.

Messages sent from that Lands chat in Minecraft are sent back to the matching Discord channel.

If DiscordBridge says your account is not linked, link your Minecraft and Discord accounts first.

# View Inboxes

Use these commands inside a land or nation Discord channel:

| Command | What it does |
| --- | --- |
| `/lands inbox` | Shows the inbox for the land connected to the current channel. |
| `/nations inbox` | Shows the inbox for the nation connected to the current channel. |

The inbox can be filtered by category, such as economy, members, and wars.

# View Top Lists

Use these commands in Discord:

| Command | What it does |
| --- | --- |
| `/lands top` | Shows top lands. |
| `/nations top` | Shows top nations, if nations are enabled on the server. |

# If You Cannot See or Use a Channel

Make sure your account is linked and that your Minecraft account is a member of the land or nation.

If you recently joined the Discord server, changed Lands membership, or changed ownership, it may take a moment for access to update. Ask staff or the owner to check the channel if access still looks wrong.
