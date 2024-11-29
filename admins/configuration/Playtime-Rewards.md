**You need to enable time-reward option in config to use this feature.**
Time rewards are permission based. If you ever want to reset a player's progress, you can do so by editing their permissions in your permission plugin. The permissions can be found [here](../permissions/Permissions.md).

# How does it work?
Players can get a reward, for example ONE chunk, every x seconds.

***

# Configuration
````yaml
    time-reward:
      enabled_17: false
      # Time settings
      # After how many seconds
      # should the players
      # get rewarded with plus 1
      # chunk, land, own land
      # or member.
      # NOTE: Timeunit is seconds
      time:
        # /lands claim
        chunks: 3060
        # Lands the player can be part of.
        lands: 43200
        # Max land members (How many players can the land have?)
        members: 21600
        # Lands the player can create.
        # /lands create
        lands-own: 86400
````

***

# Playtime maximum Rewards
Only needed if playtime rewards are enabled in the config.

`lands.chunks.max.<number>`\
The player wont be able to get any chunks rewarded if his current lands.chunks.<number> permission is equal or higher.

`lands.ownlands.max.<number>`\
The player wont be able to get any land creations rewarded if his current lands.ownlands.<number> permission is equal or higher.

`lands.lands.max.<number>`\
The player wont be able to get any land joins rewarded if his current lands.lands.<number> permission is equal or higher.

`lands.members.max.<number>`\
The player wont be able to get any member limit rewarded if his current lands.members.<number> permission is equal or higher.

`lands.chunks.support.max.<number>`\
The player wont be able to get any support chunks rewarded if his current lands.chunks.support.<number> permission is equal or higher.