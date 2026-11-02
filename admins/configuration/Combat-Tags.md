# Combat Tags

A combat tag keeps a fight going once it has started. If two players fight where PvP is allowed, both get tagged.
While they are tagged, they can keep attacking each other everywhere in the claim worlds, also inside lands where PvP
is turned off. A player can't escape a fight by running into a land that doesn't allow PvP.

The tag only applies between the players who fought. Other players can't attack a tagged player because of the tag:
for them, the land's PvP settings apply as usual.

Combat tags don't affect wars. Players in the same war can always fight each other; wars have their own combat
settings in `wars.yml`.

# How it works

* A player is tagged when they hit another player, or are hit by one, and the hit is allowed. This includes hits with
  projectiles and harmful potions.
* Both players must be in survival mode. Players in creative, adventure or spectator mode aren't tagged.
* The tag lasts for the configured time (`tag_time`) after the last hit between the two players. Every hit between them
  starts the time again.
* A player can be in combat with several players at once. The tag ends when the time of the last of them has run out.
* While tagged, a boss bar shows the time that is left.

# Configuration

Combat tags are configured in `config.yml` under `land.combat.tag`:

```yaml
land:
  combat:
    tag:
      # How long a fight keeps players tagged after the last hit. 0s = combat tags are disabled.
      tag_time: 10s
      # The worlds in which combat tags are used.
      # If empty, it's enabled in all claim worlds from claim-worlds_list.
      tag-worlds_list: [ ]
      # Kill a player who logs out while having a combat tag?
      quit-kill: false
      # Commands that are executed by the console when a player logs out with a combat tag. Player name: {player}
      quit-cmds_list: [ ]
      # Remove the combat tag when the player dies?
      death-remove: true
      # Deny teleportation while having a combat tag?
      deny-teleport: true
      # Disable flying while having a combat tag?
      disable-fly: true
```

* `tag_time`: set it to `0s` to disable combat tags. Players can then only fight where the land (or the wilderness)
  allows PvP.
* `tag-worlds_list`: tags are only set in these worlds. Leave it empty to use them in all claim worlds.
* `quit-kill`: kills players who leave the server during a fight (combat logging). The death message says that they
  left while being in a fight. This option can't be used on Folia and is turned off there.
* `quit-cmds_list`: run your own commands for combat loggers, for example to punish them with another plugin. Example:
  `- 'broadcast {player} left during a fight'`.
* `death-remove`: when a tagged player dies, their tag ends and their opponents are free again.
* `deny-teleport`: tagged players can't teleport, for example with `/lands spawn` or commands of other plugins.
  Ender pearls and chorus fruit still work. The message tells the player how long they have to wait.
* `disable-fly`: players in survival mode who are flying stop flying when they get tagged.

## Other combat options

These options are also under `land.combat`, but aren't part of the combat tag:

```yaml
land:
  combat:
    # Should players, which are members in a common land, be able to fight in wilderness?
    ally-wilderness: true
    # Block village raids if the initiator is not allowed to attack players in the claim?
    block-raids: true
```

* `ally-wilderness`: if disabled, players who are members of the same land can't attack each other in the wilderness.
  To let them fight anyway, allow PvP for them in the land's role settings (for example for an arena).
* `block-raids`: a village raid can't be started in a land by a player who isn't allowed to attack players there.

# Messages

The boss bar and the other messages are in your locale file:

* `combat.tag`: the boss bar with the time left. You can change it to an action bar or another message type, see
  [Messages](https://wiki.incredibleplugins.com/general/messages-and-config/messages).
* `teleportation.combat`: shown when a teleport is denied because of a combat tag.
* `combat-logout`: the death message of players killed by `quit-kill`.

# Placeholders and permissions

* PlaceholderAPI: `%lands_combat-tag%` and `%lands_combat-tag_bool%`, see
  [PlaceholderAPI Placeholders](PlaceholderAPI-Placeholders.md).
* LuckPerms context: `lands_combat_tag_bool`, for example to deny commands of other plugins during a fight, see
  [LuckPerms Context](../permissions/Luckperms-Context.md).

# Developers

`LandPlayer#getCombatTag()` returns the current tag of a player, with its opponents and the time left.
`LandsIntegration#canPvP(attacker, target, location, setCombatTag, sendMessage)` checks whether two players may fight
at a location, including combat tags, and can set a tag for them.

# Frequently asked questions

## Players can fight in a land, even though PvP is turned off there?

They are most likely in combat with each other: they started the fight somewhere PvP is allowed (for example in the
wilderness) and followed each other into the land. Set `tag_time` to `0s` to disable combat tags, or remove the world
from `tag-worlds_list`.
