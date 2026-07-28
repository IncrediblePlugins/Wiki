# Wars

Wars are configured in `wars.yml`. This page explains the settings that matter for server owners.

For player-facing war gameplay, use the player wiki page. This page is for admins configuring the system.

Note: The option tables on this page list the most important config options. They are not a complete copy of `wars.yml`; check your generated config file for every available option.

# Enable or Restrict Wars

| Option | What it does |
| --- | --- |
| `enabled` | Enables or disables wars. Requires reload or restart. |
| `only-nations` | If `true`, wars can only happen between nations. Single lands cannot fight alone. |

# Declaration Rules

Declaration settings live under `declaration`.

| Option | What it controls |
| --- | --- |
| `min-players.attacker` | Minimum trusted players the attacker needs. |
| `min-players.defender_3` | Minimum trusted players the defender needs before they can be declared against. |
| `send-time.days_range` | Days of the week when declarations can be sent. `1` is Monday, `7` is Sunday. |
| `send-time.hours_range` | Hours when declarations can be sent, using 24-hour time. |
| `preparation_time` | Time between declaration and war start. Use `0s` to start immediately. |
| `online` | Requires at least one defender player to be online. |
| `broadcast` | Broadcasts declarations to the server. |
| `mutual.enabled_2` | Requires the defender to accept the declaration. |
| `mutual.declaration-timeout_time` | Deletes unaccepted mutual declarations after this time. Use `0` to disable timeout. |
| `min-balance.attacker_2` | Minimum attacker land or nation balance. |
| `min-balance.defender_2` | Minimum defender land or nation balance. |
| `min-age.attacker_time` | Minimum age of the attacker land or nation. |
| `min-age.defender_time` | Minimum age of the defender land or nation. |

The source also checks `declaration.min-chunks.attacker` and `declaration.min-chunks.defender` if those paths exist in your `wars.yml`. They can be used to require a minimum claimed chunk amount.

# Points and Winning

Settings live under `points`.

| Option | What it controls |
| --- | --- |
| `kill` | Points per kill. |
| `capture-block.capture` | Points for capturing a capture flag. |
| `capture-block.break` | Points for breaking an enemy capture flag. |
| `capture-block.explode` | Points for exploding an enemy capture flag. |
| `towin.per-player` | Required points are based on the smaller team size multiplied by this value. |
| `towin.min_2` | Minimum required points even if the per-player calculation is lower. |

If the war timeout is reached, the team with the most points wins. Equal points end in a draw.

# Capture Flags

Settings live under `capture`.

| Option | What it controls |
| --- | --- |
| `enabled_3` | Enables capture flags. Capture flags are disabled on MultiPaper by source checks. |
| `recipe_list` | Crafting recipe for capture flag items. |
| `max` | Maximum active capture flags per team. |
| `place-cooldown_time` | Cooldown between placing capture flags. |
| `restrict-placement` | If `true`, only players with the `WAR_MANAGE` role flag can place capture flags. |
| `radius` | Chunk radius affected by the capture flag. Keep this within view distance. |
| `unclaim` | Captured chunks become unclaimed. |
| `claim` | Captured chunks become claimed by the enemy. |
| `hold_time` | Time invaders must hold the flag area. |
| `firework_time` | Firework interval while players are in the capture area. |
| `drop` | Drops the capture flag item when removed. |
| `invaders-break` | Allows the team that placed the flag to break it too. |
| `y.min` and `y.max_2` | Height range where capture flags can be placed. |

Capture flag durability is configured under `capture.durability`. It can give the flag health, damage from block breaks or explosions, and optional point rewards based on health thresholds.

Server admins can give capture flag items with `/lands admin player <player> give captureflag <amount> [silent]`.

Permission: `lands.admin.command.give.captureflag`

# War Status and Display

| Option | What it controls |
| --- | --- |
| `status-interval_time` | How often active war status messages are sent. |
| `war-timeout_time` | Maximum war length. |
| `hide-player` | Hides players in war from Dynmap. This does not apply to BlueMap. |
| `nametag` | Shows enemy or ally nametags for players in the same war. |
| `cmd-blacklist_list` | Commands blocked while a player is in war. Bypass with `lands.bypass.cmd.war`. |

# Surrender, Shields, and Rewards

| Option | What it controls |
| --- | --- |
| `surrender.tribute.force` | Requires tribute before the opposite team can surrender. |
| `surrender.tribute.max.defender` | Maximum tribute attackers can set for defender surrender. Supports fixed money or `%`. |
| `surrender.tribute.max.attacker` | Money attackers pay if they surrender. Supports fixed money or `%`. |
| `shield.activation.shield_creation_time` | Shield for new lands or nations. |
| `shield.activation.shield_surrender_time` | Shield after surrender. |
| `shield.activation.declaration.min-tribute` | Minimum tribute needed for declaration surrender shield. |
| `shield.activation.declaration.shield_declaration_time` | Shield after surrendering before the war starts. |
| `shield.activation.shield_end_time` | Shield after a war ends. |
| `end.winner.winner-cmds_list` | Commands executed for the winner. |
| `end.loser.loser-cmds_list` | Commands executed for the loser. |
| `end.robbery` | Money the loser pays at war end. Supports fixed money or `%`. |

Admins can set or modify shields with:

| Command | Permission |
| --- | --- |
| `/lands admin land <land or *> shield set <time>` | `lands.admin.command.land.shield.set` |
| `/lands admin land <land or *> shield modify <time>` | `lands.admin.command.land.shield.modify` |

# War Settings Players Can Change

`settings.friendly_fire.default_2` sets the default for friendly fire. Friendly fire kills do not count toward war kill stats.

# War Natural Flags

`land-flags_list` enables natural flags during war.

Example:

```yaml
land-flags_list:
  - TNT_GRIEFING
```

If you want TNT to be used in wars, you usually also need to allow `BLOCK_IGNITE` in `invading.flags.role-flags_list`.

See [Natural Flags](Natural-Flags.md) for all natural flags.

# Keep Inventory

`keep-inventory.enabled_4` enables Lands war keep-inventory handling.

`keep-inventory.mode` controls whether drops are kept. If another plugin controls keep inventory, test this carefully.

# Invading Rules

Settings live under `invading`.

| Option | What it controls |
| --- | --- |
| `restrictions.min-players` | Required online defender players before enemies can interact in that land. Use `0` to allow pillaging without defenders online. |
| `restrictions.cooldown_logging_time` | Time enemies can still interact after the last defender logs out. |
| `allies-war-field` | Allows fighting in allied lands of both sides, not only the direct war participants. |
| `flags.role-flags_list` | Role flags granted to invaders during war. |
| `flags.block-place_list` | Specific blocks invaders may place if `BLOCK_PLACE` is not granted. |
| `flags.block-break_list` | Specific blocks invaders may break if `BLOCK_BREAK` is not granted. |

See [Roles and Role Flags](Roles-and-their-Flags.md) for all role flags.

# Admin War Commands

There is no standalone `/wars` command; war commands live under the land and nation command trees
(`/land <land> war ...` / `/nation <nation> war ...`, see the player wiki). Forcing a war is an
admin-only extension of that, reached through `/lands admin land`:

| Command | What it does | Permission |
| --- | --- | --- |
| `/lands admin land <land> war start <attacker> <defender> <tribute> <preparation_time>` | Forcefully declares or starts a war. | `lands.admin.command.land.war.start` |
| `/lands admin land <land> war end` | Ends an upcoming or active war without winner rewards. | `lands.admin.command.land.war.end` |

`preparation_time` accepts time values such as `0s`, `10m`, `1h`, or `1d`.
