You can configure these flags inside your `config.yml` file. Options: 
* default_2_list
* display_2_list`

These flags are applied to new players. Existing players can toggle these flags in their personal settings GUI menu, by executing ``/lands menu main`` and then navigating to the personal settings menu.
They only control bahaviour related to this single player, such as receiving invites.

# Available Personal Flags
Each flag has their own toggle permission, which is required for the player to toggle the flag.

* **RECEIVE_INVITES**\
Allow other lands to invite the player to their land?\
*Toggle permission: lands.player.setting.receive_invites*

* **ENTER_MESSAGES**\
Show enter and leave messages when the player enters or leaves a land?\
*Toggle permission: lands.player.setting.enter_messages*

* **SHOW_INBOX**\
Show inbox messages, from lands the player is part of, in chat?\
*Toggle permission: lands.player.setting.show_inbox*

# Config
Here can configure default flags for new players and decide which flags should be displayed in the GUI menu.
```yaml
# Players can toggle personal flags to customize their experience.
player:
  flags:
    # Configure a default list of flags that is enabled.
    # This only applies to new players, or those who haven't toggeled any flags yet.
    default_2_list:
      - 'receive_invites'
      - 'enter_messages'
      - 'show_inbox'

    # Configure which flags should be displayed in the menu.
    # ALL = all flags are displayed.
    display_2_list:
      - 'all'
```