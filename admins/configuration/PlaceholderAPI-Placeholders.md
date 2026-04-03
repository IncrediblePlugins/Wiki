# IMPORTANT: Display for current Location

You can display a placeholder for a player's current location, by just appending `_here` to the placeholder.

# Limit the Length of a Placeholder

Append `_length(<number>)` to the placeholder and replace `<number>` with a number of your choice.

# Placeholders

Here is a list of all available placeholders.

## General

`%lands_lands%`\
List of lands the player owns or is trusted in. Example: land1, land2

`%lands_lands_amount%`\
Amount of lands the player owns and is trusted in.

`%lands_lands_own%`\
List of lands the player owns. Example: `ownland1, ownland2`

`%lands_lands_own_amount%`\
Amount of lands the player owns.

`%lands_lands_trusted%`\
List of lands the player is trusted in, but doesn't own. Example: trustedland1, trustedland2

`%lands_lands_trusted_amount%`\
Amount of lands the player is trusted in. This doesn't include owned lands.

`%lands_next_tax%`\
Time until taxes are collected on the server. This will be the same as `%lands_next_upkeep%`.

`%lands_next_upkeep%`\
Time until upkeep is collected on the server. This will be the same as `%lands_next_tax%`.

`%lands_affiliation%`\
Combination of land and nation name. You can edit the format in your language file.

`%affiliation_name_or_tag%`\
Combination of land and nation tag. If the land or nation has no tag set, the name will be used instead. You can edit the format in your language file.

`%lands_affiliation_color%`\
Get the color of the nation, the player is in. If the land isn't part of any nation, the land color will be returned
instead.

`%lands_land_bool%`\
If you don't append _here: returns true if player owns or is part of a land. If you append _here: returns true, if the
chunk at the player's location is claimed.

`%lands_land_trusted_bool%`\
Returns true, if the player is trusted in the area.

`%lands_player_limit_<limit>%`\
The limit value. Replace `<limit>` with any limit from the [player-limits.yml file](https://github.com/IncrediblePlugins/Lands/blob/main/player-limits.yml).
Example: `%lands_player_limit_player_chunks%` returns the maxium amount of chunks a player can claim in total. Whereas
``%lands_player_limit_land_chunks%`` returns the max. size of lands that the player owns.

`%lands_player_chunks_claimed%`\
Returns the amount of chunks the player has claimed for all lands in total. This includes lands the player is trusted in
and lands that they own.

`%lands_player_chunks_left%`\
Returns the amount of chunks the player has left. It's the same as subtracting %lands_player_chunks_claimed% from %lands_player_limit_player_chunks%.

`%lands_player_chat%`\
Displays whether the player has /lands chat or /nations chat toggled to send every message into land or nation chat.

`%lands_player_chat_bool%`\
Displays "true" if the player has enabled that all chat messages of them end up in land or nation chat. Otherwise
returns "false".

`%lands_combat-tag%`\
Whether or not the player has a combat tag.

`%lands_combat-tag_bool%`\
Same as `%lands_combat-tag%`, but returns fixed values: `true` or `false`.

## Lands

`%lands_land_name%`\
The name of the edit land, including formatting and color. If you want to display the land at the players current
location: [append _here to it](#important-display-for-current-location).

`%lands_land_name_plain%`\
The name of land without any color or formatting.

`%lands_land_name_cmd%`\
Get name of land that is used for commands. Basically, this replaces all spaces in the land name, with underscores and
doesn't contain any color or format.

`%lands_land_tag%`\
The tag of the land, including formatting and color.

`%lands_land_tag_plain%`\
The tag of the land without any color or formatting.

`%lands_land_owner%`\
The name of the land owner.

`%lands_land_category%`\
Name of the land's category.

`%lands_land_role_name%`\
Name of the role including formatting and color.

`%lands_land_role_name_plain%`\
Get the role name without any color or formatting.

`%lands_land_role_type%`\
Get the role type. View
types [here](https://javadoc.jitpack.io/com/github/angeschossen/LandsAPI/7.15.20/javadoc/me/angeschossen/lands/api/role/enums/RoleType.html).

`%lands_land_role_name_color%`\
Get the role color only.

`%lands_land_members%`\
Amount of members in the land.

`%lands_land_members_online_amount%`\
Amount of members of the land that are online.

`%lands_land_members_online%`\
Names of the land members that are currently online.

`%lands_land_balance%`\
The balance of the land bank.

`%lands_land_balance_short%`\
Balance of the land bank in short format. This depends on the `general.eco-format.short-unit` option in `config.yml`.
Config:

````yaml
    # The short format will use the normal format if the value is lower than 1000.
    # If the value is higher or equal than 1000, it will return {value} divided by 1000.
    # This format is only used by a small amount of messages.
    short: '${value}k'
````

`%lands_land_balance_members%`\
The balance of all land members combined.

`%lands_land_balance_members_short%`\
The balance of all land members combined with same formatting as `%lands_land_balance_short%`.

`%lands_land_chunks%`\
The amount of claimed chunks of the land.

`%lands_land_chunks_max%`\
Max claim amount for the land.

`%lands_land_chunks_remaining%`\
Remaining possible claims for the land.

`%lands_land_tax%`\
Displays the taxes that the player has to pay to the land or the current area if you append `_here` to it.

`%lands_land_upkeep%`\
The upkeep costs of the land.

`%lands_land_chunk_cost_next%`\
The cost of the next claim.

`%lands_land_level%`\
The name of the current level.

`%lands_land_level_index%`\
The index of the current level. Example: `1`

`%lands_land_level_next%`\
The name of the next level.

`%lands_land_level_next_index%`\
The index of the next level. Example: `1`

`%lands_land_shield%`\
Get the remaining shield time.

`%lands_land_color%`\
Get the land color only.

`%lands_land_ulid%`\
Unique ID of the land.

`%lands_land_area_name%`\
Name of the default area. If you append `_here` to it, it will return the name of the area in which the player is
currently standing.

`%lands_land_area_name_plain%`\
Name of the subarea without color.

`%lands_land_icon%`\
Returns the item type of the lands icon. Will return "AIR", if there's no land.

## Nations

### _any Option

Display placeholders for any nation the player is in. So not just their current /edit land or the land at their
position.
Just append `_any` to the placeholder, to display the information for any nation the player is in.

`%lands_nation_name%`\
The name of the nation that belongs to the edit land. This includes formatting and color. If you want to display the
nation at the players current location: [append _here to it](#important-display-for-current-location).

`%lands_nation_name_plain%`\
The name of the nation without any color or formatting.

`%lands_nation_name_cmd%`\
Get name of nation that is used for commands. Basically, this replaces all spaces in the nation name, with underscores
and doesn't contain any color or format.

`%lands_nation_tag%`\
The tag of the nation, including formatting and color.

`%lands_nation_tag_plain%`\
The tag of the nation without any color or formatting.

`%lands_nation_color%`\
Get the nation color only.

`%lands_nation_balance%`\
The balance of the nation bank.

`%lands_nation_balance_short%`\
Balance of the nation bank in short format. This depends on the `general.eco-format.short-unit` option in `config.yml`.
Config:

````yaml
    # The short format will use the normal format if the value is lower than 1000.
    # If the value is higher or equal than 1000, it will return {value} divided by 1000.
    # This format is only used by a small amount of messages.
    short: '${value}k'
````

`%lands_nation_balance_members%`\
The balance of all members (players) combined.

`%lands_nation_balance_members_short%`\
The balance of all members (players) combined with same formatting as `%lands_nation_balance_short%`.

`%lands_nation_balance_lands%`\
The balance of all lands in the nation combined.

`%lands_nation_balance_lands_short%`\
The balance of all lands in the nation combined with same formatting as `%lands_nation_balance_short%`.

`%lands_nation_level%`\
The current level of the nation.

`%lands_nation_level_index%`\
The index of the current nation level. Example: `1`

`%lands_nation_level_next%`\
The next level of the nation.

`%lands_nation_level_next_index%`\
The index of the next nation level. Example: `1`

`%lands_nation_shield%`\
Get the remaining shield time.

`%lands_nation_ulid%`\
Unique ID of the nation.

`%lands_nation_bool%`\

* If you don't append `_here`: returns `true` if player owns or is part of a nation.
* If you append `_here`: returns `true`, if the chunk at the player's location belongs to a nation.

## Wars

`%lands_war_enemy%`\
The enemy in the current war.

`%lands_war_time%`\
Remaining time of the current state (preparation or fight).

`%lands_war_state%`\
The current state of the war (preparation or fight).

## Relation Placeholders

These placeholders involve more than one player. Please make sure that your plugin supports that. If it doesn't work,
it's likely that your plugin doesn't.

`%rel_lands_war_relation%`\
Returns relation of two players (enemy, ally) during war. Returns an empty string while if the two players are not
taking part in the same war.

`%rel_lands_relation%`\
Returns relation of two players (enemy, ally, neutral) during war and while not in a war.

## Top Lands and Nations

Format: `%lands_top_<context>_<sorting>_<place>_<value>%`

### Parameter Explanation

* `<context>` - needs to be replaced with either `land` or `nation`.
* `<sorting>` - needs to be replaced with `balance`, `chunks`, `members`, `level`, `ratio-kd` (kills/deaths in wars
  ratio) or `ratio-wl` (won/lost wars ratio).
* `<place>` - needs to be replaced with the place. Example: `1`
* `<value>` - needs to be replaced with `name`, `owner`, `balance`, `size`, `members`, `ratio-kd` or `ratio-wl`.
