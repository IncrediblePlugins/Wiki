# War Modes and Goals

War **modes** and **goals** are configured in `Modules/Wars/modes.yml`. The rest of the war system
(declaration rules, capture flags, in-war permissions, shields) is in `wars.yml` - see
[Wars](Wars.md).

- A **war mode** decides how a war is *scored and won* (points sources, points-to-win, timeout).
- A **war goal** decides what the winner/loser *get* when the war resolves.

When declaring, the attacker picks one mode and one goal in a menu. Every mode and goal is built into
the plugin; `modes.yml` only holds each one's settings and marks which are enabled and which is the
default.

> **Two toggles per entry.** `enabled: true/false` turns an entry on or off entirely (a disabled entry
> is never offered and is never chosen as the default). `default: true` marks the single mode/goal used
> for a war where the player didn't (or couldn't) pick one. Make sure the entry you mark `default` is
> also `enabled`, and don't mark more than one default per section - the first enabled default wins,
> and if none is usable the plugin falls back to its built-in default.

You may add extra properties to any entry; they're ignored unless that mode/goal reads them.

---

# War Modes

## `skirmish` - the classic war

Score from **kills and capture flags**; first to `points.towin` wins, or the higher score at timeout
(a draw if tied).

```yaml
modes:
  skirmish:
    enabled: true
    default: true
    add-goals: []        # extra goals applied on top of the chosen goal (e.g. [raid])
    timeout: 36h         # 0 = no time limit
    points:
      kill: 1
      capture-flag:      # points for the wars.yml capture-flag mechanic
        capture: 5
        break: 3
        explode: 5
      towin:
        per-player: 5    # (smallest team's player count) * per-player ...
        min: 100         # ... but never less than this
```

`add-goals` applies extra goals to **every** war of this mode, on top of the war's chosen primary goal -
e.g. add `raid` so the winner can also raid the loser afterwards.

## `koth` - King of the Hill (server arena)

Fought over a neutral, admin-built **arena** (see below). Kills score nothing; instead, whichever team
**controls the arena point** earns `hold-reward.amount` points every `hold-reward.interval`. First to
`points.towin` wins, or the leader at timeout.

```yaml
  koth:
    enabled: true
    default: false
    timeout: 30m
    hold-reward:
      interval: 20s
      amount: 5          # 0 disables hold scoring
    points:
      kill: 0
      towin:
        per-player: 5
        min: 100
      timeout-draw-margin: 20   # at timeout, a lead this small or smaller is a draw; 0 = any lead wins
```

> Only offered when at least **one fully set-up arena exists**. Tune `hold-reward` against `towin` so a
> war lasts a reasonable number of holds rather than ending in one.

## `koth_land` - King of the Hill (player lands)

A two-front variant that needs no admin arena. During preparation each team places one re-arming point
in its **own** land (`/land <land> war koth set`), and scores by holding the **enemy's** point. Both
lands become battlegrounds. Same scoring keys as `koth`.

```yaml
  koth_land:
    enabled: true
    default: false
    timeout: 30m
    hold-reward:
      interval: 20s
      amount: 5
    points:
      kill: 0
      towin:
        per-player: 5
        min: 100
      timeout-draw-margin: 20
```

Caveats worth knowing:

- A team **only scores by holding the enemy's point**, never its own - camping your own point only
  denies the enemy, it earns nothing. (This is why two passive teams end 0-0.)
- Attackers get limited block-break/place in the contested lands so they can reach the enemy point;
  which blocks come from `wars.yml` (`in-land.actions`).
- If both points aren't placed by war start, the war **falls back** to a free server arena; if arenas
  exist but all are busy it waits for one; if no arena exists at all, the side that placed wins (a draw
  if neither placed).
- The player-land points reuse the `capture.radius` / `capture.y-limit` / `capture.recapture` settings
  from `wars.yml`.

---

# King of the Hill Server Arenas

An **arena** is a designated sub-area of any land (player or server) that a `koth` war is fought in.
Manage arenas with `/lands admin war koth ...` (permission base `lands.admin.command.war.koth`):

| Command | What it does | Permission |
| --- | --- | --- |
| `/lands admin war koth create` | Designate the sub-area you're standing in as a KoTH arena. | `lands.admin.command.war.koth.create` |
| `/lands admin war koth setflag` | Place the arena's control point at your position. | `lands.admin.command.war.koth.setflag` |
| `/lands admin war koth setspawn <attacker\|defender>` | Set a team's spawn point at your position. | `lands.admin.command.war.koth.setspawn` |
| `/lands admin war koth remove` | Remove the arena you're standing in. | `lands.admin.command.war.koth.remove` |
| `/lands admin war koth list` | List existing arenas. | `lands.admin.command.war.koth.list` |

**Setting up an arena:**

1. Create the sub-area you want to use (a normal Lands sub-area), stand in it, and run
   `/lands admin war koth create`.
2. Stand where the control point should be and run `/lands admin war koth setflag`. The flag is placed
   instantly and you're teleported on top of it.
3. Set both team spawns with `/lands admin war koth setspawn attacker` and
   `/lands admin war koth setspawn defender`, standing where each team should spawn.

**Caveats:**

- An arena is **complete** (and only then selectable for a war) once its control-point block exists
  **and both spawns are set**. Steps 2 and 3 can be done in any order.
- The control point is a normal land block. If it's later broken or the area removed, the arena becomes
  **incomplete** and won't be offered until you place it again.
- **One war per arena.** A `koth` war reserves a random free arena; while it's in use no other war can
  take it. If all arenas are busy, a new `koth` war waits (both teams are notified) until one frees.
- A designated arena's land/area is **protected from player deletion** - a player can't `unclaim` or
  delete a land or sub-area covering an arena. Internal removal (inactivity, upkeep, admin deletion)
  still removes it and cleans up the arena.

---

# War Goals

Every goal configures its outcome **per war-state**, so a conceded war can be milder than a fought one:

- `end` - a fought win/loss.
- `surrender` - a side conceded (during preparation or an active war). Usually less punishing.
- `draw` - no decisive winner. A draw has no winner/loser, so commands and shields do nothing and
  aren't listed by default; add them if you want a draw to still grant a shield or run a command.

Every state takes the same options:

| Option | What it does |
| --- | --- |
| `cmds.winner` / `cmds.loser` | Console commands run once per winner/loser land when the war resolves. Placeholders: `{winner}`/`{loser}` (parameter-safe name), `{winner_name}`/`{loser_name}` (display name), `{winner_owner}`/`{loser_owner}` (owner). `[]` = none. |
| `shield.winner` / `shield.loser` | War shield granted to the winner/loser afterwards (`0` = none). |

Individual goals add their own options on top, described below.

## `skirmish` - rob money (low stakes)

The winner robs money from the loser's bank; no one loses claims. `robbery` accepts a trailing `%` (a
percentage of the loser's balance) or a plain number (a flat amount, capped at what the loser has).

```yaml
goals:
  skirmish:
    enabled: true
    end:
      robbery: 75%
      shield: { winner: 7d, loser: 7d }
      cmds:   { winner: [], loser: [] }
    surrender:
      robbery: 40%
      shield: { winner: 7d, loser: 7d }
      cmds:   { winner: [], loser: [] }
```

## `annex` - unclaim the loser's lands

The winner unclaims all of the loser's war lands (the loser gets the usual unclaim cash-back). No
ownership transfer.

```yaml
  annex:
    enabled: true
    default: false
    end:       { shield: { winner: 0, loser: 3d }, cmds: { winner: [], loser: [] } }
    surrender: { shield: { winner: 0, loser: 3d }, cmds: { winner: [], loser: [] } }
```

## `vassal` - subjugate the loser (nations only)

The winning **nation** absorbs the loser as restricted `VASSAL` members. Only usable when the attacker
is a nation. `seize-treasury: true` also transfers the loser's bank balance to the winner's nation bank.

```yaml
  vassal:
    enabled: true
    default: false
    seize-treasury: false
    end:       { shield: { winner: 0, loser: 0 }, cmds: { winner: [], loser: [] } }
    surrender: { shield: { winner: 0, loser: 0 }, cmds: { winner: [], loser: [] } }
```

## `independence` - a vassal secedes

Applied only via `/land <vassal> war independence` - a vassal wages war to leave its overlord. If the
vassal wins it stays free; if the overlord wins or the war draws, the vassal is re-subjugated and can't
declare independence again until `cooldown` passes.

```yaml
  independence:
    enabled: true
    default: false
    cooldown: 7d
    end:       { shield: { winner: 7d, loser: 0 }, cmds: { winner: [], loser: [] } }
    surrender: { shield: { winner: 7d, loser: 0 }, cmds: { winner: [], loser: [] } }
```

> `independence` is never shown in the declaration goal picker - it's chosen automatically by the
> independence command. Its `enabled` toggle gates that command directly.

## `raid` - post-war raid window

The winner's members may act on the loser's lands for `duration` after the war, limited to the actions
in `actions`. Can also be added on top of another goal via `modes.<mode>.add-goals`.

```yaml
  raid:
    enabled: true
    default: true
    duration: 1h
    end:       { shield: { winner: 0, loser: 0 }, cmds: { winner: [], loser: [] } }
    surrender: { shield: { winner: 0, loser: 0 }, cmds: { winner: [], loser: [] } }
    actions:
      role-flags:      # flags granted outright (loot, open doors, pick up drops)
        - INTERACT_CONTAINER
        - INTERACT_DOOR
        - INTERACT_TRAPDOOR
        - INTERACT_MECHANISM
        - ITEM_PICKUP
      block-break:     # only these materials may be broken (breach walls without levelling everything)
        - COBBLESTONE
        - OAK_PLANKS
        # ... see the generated file for the full curated list
      block-place:     # only these may be placed (to bridge/climb in)
        - LADDER
        - SCAFFOLDING
```

> **`raid.actions` vs `wars.yml`'s `in-land.actions`.** `in-land.actions` governs what enemies may do
> **during** the war; `raid.actions` governs the **post-war** raid window. They're separate lists.
> `role-flags` grants a flag outright; `block-break` / `block-place` allow only the listed materials
> when the corresponding flag isn't granted, so raiders can breach and loot without destroying the whole
> base. Materials your server version doesn't have are ignored. Flag names: see
> [Roles and Role Flags](Roles-and-their-Flags.md).
