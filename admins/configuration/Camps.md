# Camps

Camps are temporary lands. Players can create them by placing a camp item or by using `/lands createcamp [name]`, if camps are enabled.

Camps do not pay upkeep. They expire after the configured time unless expiration is disabled.

Note: The option list on this page highlights the most important camp config options. It is not a complete list; check your generated config file for every available option.

Give camp items with `/lands admin player <player> give camp <radius> <amount> [silent]`.

You can also give all enabled first-join items with `/lands admin player <player> give first-join-items`.

# Configuration

Camps are configured in `config.yml` under `camp`.

Important options:

* `camp.enabled_21`: enables camps and `/lands createcamp`.
* `camp.costs_8`: cost to create a camp, including its claims.
* `camp.expire_time`: time until camps are deleted. `0` means never.
* `camp.radius`: default claim radius.
* `camp.default-name`: default camp name.

Camp items on first join are configured in `general.first-join-items.camp`.

The maximum number of camps a player can create is controlled by limits. Use `player-limits.yml` for new servers. The legacy numbered permission is `lands.camps.<number>`.
