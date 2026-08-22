# Discord Configuration

DiscordBridge stores per-Discord-server settings through the Discord `/config` command.

Run these commands inside your Discord server, not in DMs. Use Discord's autocomplete after `/config set` to select the exact key and value type.

Non-list values are set with `/config set <setting> <value-option>`. For example:

```text
/config set chat_channel textchannel:#minecraft-chat
```

Values can be removed by running the same `/config set <setting>` command without a value.

List values are managed with their own command groups:

```text
/config linking_allowed_roles add role:@Member
/config linking_allowed_roles remove role:@Member
```

# Core Settings

| Setting | Command shape | Use it for |
| --- | --- |
| `administrator_role` | `/config set administrator_role role:<role>` | Allows members with this role to configure the Discord bot. Discord administrators can configure it as well. |
| `chat_channel` | `/config set chat_channel textchannel:<channel>` | Channel used by the chat module for Discord-to-Minecraft and Minecraft-to-Discord chat. |
| `event_channel` | `/config set event_channel textchannel:<channel>` | Channel used by the events module for server and player event messages. |

# Linking Settings

| Setting | Command shape | Use it for |
| --- | --- |
| `linking_allowed_roles` | `/config linking_allowed_roles add role:<role>` | Limits account linking to Discord members with one of these roles. Leave empty to allow all members to link. |
| `linking_roles` | `/config linking_roles add ingame_permission:<permission> discord_role:<role>` | Gives Discord roles to linked players based on in-game permissions. |
| `linking_groups` | `/config linking_groups add discord_role:<role> ingame_group:<group>` | Gives LuckPerms groups in Minecraft based on Discord roles. |
| `linking_name_sync_ignore_roles` | `/config linking_name_sync_ignore_roles add role:<role>` | Excludes members with these roles from Discord nickname sync. |

Use the matching `remove` subcommand to remove entries from these lists.

# Lands Settings

| Setting | Command shape | Use it for |
| --- | --- |
| `lands_chat_category` | `/config set lands_chat_category category:<category>` | Category where land and nation channels are created. |
| `lands_broadcast_channel` | `/config set lands_broadcast_channel textchannel:<channel>` | Channel for Lands broadcast messages, such as land deletions, relationship changes, and war updates. |
| `lands_notify_<broadcast_category>` | `/config set lands_notify_<broadcast_category> role:<role>` | Role to mention for one Lands broadcast category. Replace `<broadcast_category>` with the category shown by autocomplete. |

# Ticket Settings

| Setting | Command shape | Use it for |
| --- | --- |
| `tickets_category_closed` | `/config set tickets_category_closed category:<category>` | Category where closed tickets are moved before deletion. |
| `tickets_creation_channel` | `/config set tickets_creation_channel textchannel:<channel>` | Channel where DiscordBridge posts the ticket creation message. |
| `tickets_role_support` | `/config set tickets_role_support role:<role>` | Staff role that can see and work on all tickets. |
| `tickets_member_max_tickets` | `/config set tickets_member_max_tickets number:<amount>` | Maximum active tickets per Discord member. |
| `tickets_deletion_time` | `/config set tickets_deletion_time time:<time>` | How long closed tickets remain before deletion. Supports `d`, `h`, `m`, and `s`. |
| `tickets_remind_submitter` | `/config set tickets_remind_submitter boolean:<true|false>` | Whether the submitter is reminded after staff responds and the submitter has not replied. |
| `tickets_staff_unavailable` | `/config set tickets_staff_unavailable text:<message>` | Optional message sent when no support staff is available. |

`tickets_category_open` is deprecated for new setups. Set the open category on each ticket type with `/config type upsert`.

# Ticket Structure Commands

Ticket types decide what users can open. Fields decide what the user must fill out.

| Command | What it does |
| --- | --- |
| `/config type upsert` | Creates or updates a ticket type. This also sets the open-ticket category for that type. |
| `/config type delete` | Deletes a ticket type. |
| `/config field upsert` | Creates or updates a form field for a ticket type. |
| `/config field delete` | Deletes a form field from a ticket type. |
| `/config info create` | Adds predefined information that staff can request from a ticket submitter. |
| `/config info delete` | Deletes predefined requestable information. |
| `/config reason create` | Adds a predefined reason for a ticket action, such as closing a ticket. |
| `/config reason delete` | Deletes a predefined reason. |

# Recommended Setup Order

1. Set `administrator_role`.
2. Configure the channels and roles needed by the modules you enabled.
3. If tickets are enabled, create ticket types and fields.
4. Set `tickets_creation_channel` with `/config set tickets_creation_channel textchannel:<channel>` after ticket types exist, so the ticket creation message can include them.
5. Test with a non-admin account when possible.
