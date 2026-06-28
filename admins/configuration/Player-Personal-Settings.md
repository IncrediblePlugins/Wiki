# Player Personal Settings

Personal settings control behavior for one player only. They do not change a land, role, nation, or war.

Players can edit these settings in their personal settings menu if the flag is displayed and they have the matching `lands.player.setting.<flag>` permission.

# Configuration

Personal flags are configured in `config.yml` under `player.flags`.

`default_2_list` sets the enabled personal flags for new players.

`display_2_list` controls which personal flags appear in the menu. Use `all` to display every personal flag.

# Available Personal Flags

| Flag | What it controls | Toggle permission |
| --- | --- | --- |
| `RECEIVE_INVITES` | Whether the player can receive land invites. | `lands.player.setting.receive_invites` |
| `ENTER_MESSAGES` | Whether the player sees land enter and leave messages. | `lands.player.setting.enter_messages` |
| `SHOW_INBOX` | Whether inbox messages are shown in chat. | `lands.player.setting.show_inbox` |

# Example

```yaml
player:
  flags:
    default_2_list:
      - receive_invites
      - enter_messages
      - show_inbox

    display_2_list:
      - all
```
