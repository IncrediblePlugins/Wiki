The ``player-limits.yml`` file is used to modify numbered limits such as max lands etc. for the Lands plugin or other limits such as placed hoppers etc. for my other plugins.

# Limit Packs
In the file you can configure limit packs in the ``packs`` section. You can assign a required permission to each pack.
If the player has the required permission, the pack will be assigned to them. If a player has permissions from multiple packs, they
will get the last pack in the file, for which they had the required permission, assigned.

# Playtime Rewards
You can increase limits on top of the packs, by rewarding players for their total time
played on the server. The configuration for that is in the ``playtime-rewards`` section of the file.

# Total Limit
The total limit for a player is the result of: ``the limit pack + manually given limit through admin command + time rewards``
Limits in the Lands plugin might also be increased by land and nation levels.

# Disabling Limits
Limits can be disabled. Disabled limits basically mean that the player has an unlimited amount of something.
This might be abused by players in some way specific to the plugin and case. However, if you're sure about disabling a limit,
just set it's value to -1 to disable the limit.