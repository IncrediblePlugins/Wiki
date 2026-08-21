# Wars

The war system is configured in two files under `Modules/Wars/`:

- **`wars.yml`** - the settings on this page: whether wars are enabled, declaration requirements,
  capture flags, what enemies may do in a land, shields, keep-inventory, and display.
- **`modes.yml`** - the **war modes and war goals**: scoring, points-to-win, timeouts, and what the
  winner gets (robbery, annexation, vassalage, raid, independence). See
  [War Modes and Goals](War-Modes-and-Goals.md).

> **What moved to `modes.yml`.** In older versions, `wars.yml` held the point values, points-to-win,
> the war timeout, the surrender **tribute**, and the war-end commands/robbery/shields. These are now
> per-mode and per-goal in `modes.yml`, because they only make sense per mode/goal. There is **no
> tribute setting anymore** - surrendering simply applies the chosen goal's (usually milder) outcome.

For player-facing gameplay, see the player wiki's [Wars](../../players/general/Wars.md) page.

> The option tables below list the settings that matter most. They are not a full copy of `wars.yml` -
> check your generated file for every option and its inline comments. Some leaf keys carry a numeric
> suffix (e.g. `defender_3`, `enabled_3`, `min_2`); the suffix is stripped on load and only keeps
> otherwise-identical key names textually distinct so the duplicate-key check doesn't warn.

# Enable or Restrict Wars

| Option | What it does |
| --- | --- |
| `enabled` | Enables or disables wars. Requires reload or restart. |
| `only-nations` | If `true`, wars can only happen between nations; single lands can't fight alone. |

# Declaration Requirements

Requirements that gate whether a war may be declared at all live under `declaration.requirements`. If
any isn't met, the declaration is refused.

| Option | What it controls |
| --- | --- |
| `min-players.attacker_3` | Minimum trusted players the attacker needs. |
| `min-players.defender_3` | Minimum trusted players the defender needs before being declared against. |
| `min-chunks.attacker` / `min-chunks.defender` | Minimum claimed chunks. `0` = no minimum. |
| `min-balance.attacker_2` / `min-balance.defender_2` | Minimum land/nation bank balance. |
| `min-age.attacker_time` / `min-age.defender_time` | Minimum age of the land/nation. |
| `max-level-difference` | Anti-grief level gate: only allow a war between holders within this many **levels** of each other (symmetric). `-1` disables it, `0` = same level only, `1` = one level up or down, etc. Independence wars and admin-editor staff are exempt. |
| `online` | Requires at least one defender player online to receive a declaration. |
| `send-time.days_range` | Days of the week declarations may be sent. `1` = Monday, `7` = Sunday (e.g. `1-7`). |
| `send-time.hours_range` | Hours declarations may be sent, 24-hour (e.g. `0-23`, or `20-23;0-4`). |

# Declaration Flow

These live directly under `declaration`.

| Option | What it controls |
| --- | --- |
| `preparation_time` | Time between declaration and war start. Use `0s` to start immediately. |
| `broadcast` | Broadcast declarations to the whole server. |
| `mutual.enabled_2` | Requires the defender to accept the declaration before preparation begins. Requires reload/restart. |
| `mutual.declaration-timeout_time` | Deletes an unaccepted mutual declaration after this time. `0` disables the timeout. |

> When a war is declared, the attacker also picks a **war mode** and **war goal** in a menu. What each
> one costs the loser is configured in [`modes.yml`](War-Modes-and-Goals.md), not here.

# Capture Flags

Capture flags are the block-based capture mechanic of the **Skirmish** mode (and the player-land King
of the Hill points reuse the same capture area). Settings live under `capture`.

| Option | What it controls |
| --- | --- |
| `enabled_3` | Enables capture flags. Disabled on MultiPaper by source checks. |
| `recipe_list` | Crafting recipe for the capture flag item (shown in `/land <land> war info captureflag`). |
| `max` | Maximum active capture flags per team. |
| `place-cooldown_time` | Cooldown between placing capture flags. |
| `restrict-placement` | If `true`, only players with the `WAR_MANAGE` role flag may place flags. |
| `radius` | Chunk radius affected by a flag. Keep within view distance. |
| `unclaim` | Captured chunks become unclaimed. |
| `claim` | Captured chunks become claimed by the enemy. |
| `hold_time` | How long invaders must hold the area to capture it. |
| `firework_time` | Firework interval while players are in the capture area. |
| `drop` | Drop the capture flag item when the flag is removed. |
| `invaders-break` | Allow the team that placed the flag to break it too. |
| `recapture` | If `true`, defenders holding the point reverse capture progress; if `false`, they only pause it (progress is sticky). Applies to the normal flag and player-land KotH points. |
| `y.min` / `y.max_2` | Height range where flags can be placed. |
| `y-limit` | Vertical size of the capture area (blocks up/down from the flag). `0` = whole column. Applies to the normal flag and player-land KotH points; admin arenas use their sub-area's own height. |

Capture flag **durability** is configured under `capture.durability` - give the flag health, damage from
block breaks or explosions, and optional point rewards at health thresholds.

**Point values** for capturing, breaking, or exploding a flag are **not** here - they belong to each
mode in [`modes.yml`](War-Modes-and-Goals.md) (e.g. `modes.skirmish.points.capture-flag`).

Give capture flag items with `/lands admin player <player> give captureflag <amount> [silent]`
(permission `lands.admin.command.give.captureflag`).

# What Enemies May Do In a Land

Settings live under `in-land`. This is the **in-war** action set; the separate **post-war raid** action
set lives under `goals.raid.actions` in `modes.yml`.

| Option | What it controls |
| --- | --- |
| `restrictions.min-players` | Online defenders required before enemies may interact in that land (and before capture flags work). `0` allows pillaging with no defenders online. Requires reload/restart. |
| `restrictions.cooldown_logging_time` | Grace time enemies can still interact after the last defender logs out. |
| `allies-war-field` | Allow fighting in allied lands of both sides, not only the direct participants. |
| `actions.role-flags_list` | Role flags granted to enemies in the land during war (e.g. `ATTACK_PLAYER`, `LAND_ENTER`). |
| `actions.block-place_list` | Specific blocks enemies may place if `BLOCK_PLACE` isn't granted. |
| `actions.block-break_list` | Specific blocks enemies may break if `BLOCK_BREAK` isn't granted. |

> Adding `BLOCK_PLACE` or `BLOCK_BREAK` to `role-flags_list` lets enemies place/break **all** blocks. To
> limit them, leave those flags out and use the block lists instead. During war, enemies also get the
> flags of the invaded area's untrusted role. See [Roles and Role Flags](Roles-and-their-Flags.md).

# War Natural Flags

`land-flags_list` enables natural flags during war, for example:

```yaml
land-flags_list:
  - TNT_GRIEFING
```

To allow TNT in wars you usually also need `BLOCK_IGNITE` in `in-land.actions.role-flags_list`. See
[Natural Flags](Natural-Flags.md).

# Shields

A war shield protects a land or nation from being attacked.

| Option | What it controls |
| --- | --- |
| `shield.activation.creation_time` | Shield granted to a newly created land or nation. `0` disables it. |

> Shields granted **after a war ends or a surrender** are configured per goal in
> [`modes.yml`](War-Modes-and-Goals.md) (`goals.<goal>.<state>.shield.winner` / `.loser`), not here.

Admins can set or modify shields manually:

| Command | Permission |
| --- | --- |
| `/lands admin land <land or *> shield set <time>` | `lands.admin.command.land.shield.set` |
| `/lands admin land <land or *> shield modify <time>` | `lands.admin.command.land.shield.modify` |

# Keep Inventory

`keep-inventory.enabled_4` enables Lands' war keep-inventory handling. `keep-inventory.mode` controls
whether drops are kept. If another plugin controls keep-inventory, test this carefully.

# Combat, Display, and Sounds

| Option | What it controls |
| --- | --- |
| `combat.friendly_fire.default_2` | Default for friendly fire (players can change it in-game with permission). Friendly-fire kills don't count toward war kill stats. |
| `status-interval_time` | How often active war status messages are sent. |
| `start.broadcast_2` | Broadcast a message when a war starts. |
| `hide-player` | Hide players in war from Dynmap (not BlueMap). |
| `nametag` | Show enemy/ally nametags for players in the same war. |
| `cmd-blacklist_list` | Commands blocked while a player is in war. Bypass with `lands.bypass.cmd.war`. |
| `sounds.capture.place_sound` | Sound played when a capture flag is placed (`sound,volume,pitch`; empty to disable). |

# Admin War Commands

There is no standalone `/wars` command; war commands live under the land and nation trees
(`/land <land> war ...` / `/nation <nation> war ...`, see the player wiki). Wars are now **started
through the normal `declare` command** - which admins can run too, using the
`lands.admin.command.edit` bypass to act on a land or nation they aren't a member of.

Admin-only war actions live under `/lands admin war`:

| Command | What it does | Permission |
| --- | --- | --- |
| `/lands admin war end <land or nation>` | Force-ends an upcoming or active war cleanly, without applying the goal or winner rewards. | `lands.admin.command.war.end` |

King of the Hill **arena** management lives under `/lands admin war koth` - see the KoTH arena section
of [War Modes and Goals](War-Modes-and-Goals.md#king-of-the-hill-server-arenas).
