# Usage

Send messages to Discord, if specific events happen on the server.

# Setup

1. Make sure the [Bot](Bot.md) module is enabled and connected.
2. Execute ``/config set event_channel textchannel:<channel>`` in your Discord server. Event messages are sent to this channel.
3. Optional: Disable events that you want to exclude by editing `DiscordBridge/Modules/events.yml`.

# Events

| Event | Config option |
| --- | --- |
| Server started | Sent when the events module starts after the bot is ready. |
| Server stopping | Sent when DiscordBridge disables. |
| Player join | `events.player.join` |
| Player quit | `events.player.quit` |
| Player death | `events.player.death.death-reasons` |
| Player advancement | `events.player.advancement.advancements` |
| Playtime milestone | `events.player.playtime.playtime-announcements` |

Use `*` in death reasons or advancements to include all supported values. Use an empty list to disable the filtered event type.

Player join, quit, death, and advancement messages are skipped for vanished players when DiscordBridge can detect vanish state through a supported vanish integration.
