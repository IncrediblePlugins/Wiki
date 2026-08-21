# Custom Wars

The war system is built around two pluggable pieces you can extend from your own plugin:

- A **war mode** decides how a war is *scored* and *won* (e.g. Skirmish, King of the Hill).
- A **war goal** decides the *terminal consequence* for the winner and loser (e.g. robbery,
  annexation, vassalage).

Modes and goals are orthogonal: a war has one mode and one primary goal, chosen when it is declared.
The old `WarHandler` / `api.setWarHandler(...)` API and the standalone `/war` command no longer exist
— register modes and goals against the registries below instead.

## Getting the registries

Both registries are reached through the war module of your `LandsIntegration` instance:

```java
LandsIntegration api = LandsIntegration.of(plugin);
WarModule warModule = api.getWarModule();
WarModeRegistry modeRegistry = warModule.getModeRegistry();
WarGoalRegistry goalRegistry = warModule.getGoalRegistry();
```

## Registering before Lands loads

Modes and goals **must be registered before Lands loads its data** (before Lands is enabled).
Registering after that throws `IllegalStateException`. Registering an id that already exists throws
`IllegalArgumentException`. Use `LandsIntegration#onLoad(Runnable)` so your registration runs at the
right time:

```java
LandsIntegration api = LandsIntegration.of(plugin);

api.onLoad(() -> {
    api.getWarModule().getModeRegistry().register(new MyWarMode());
    api.getWarModule().getGoalRegistry().register(new MyWarGoal());
});
```

Each mode and goal has a unique `getId()` used for persistence and lookup, so keep ids stable across
restarts and updates.

## Implementing a war mode

Implement `me.angeschossen.lands.api.war.mode.WarMode`. A mode owns the scoring of both teams and the
decision of when the war ends and who wins. The key methods:

| Method | Purpose |
| --- | --- |
| `getId()` | Unique, stable id used for persistence and lookup. |
| `getName()` | Internal English name, used for logs and as a fallback. |
| `getDisplayName(viewer)` | Localized name for the UI. Defaults to `getName()`. |
| `getDescription(context, viewer)` | Required. Adventure component describing how the mode is scored and won, shown in the declaration UI and war info. |
| `isApplicable(attacker, defender)` | Whether the mode may be used for these two parties. The declaration UI lists every mode but rejects a click on a non-applicable one. Defaults to `true`. |
| `getScore(war, team)` | The team's current score. Higher means closer to winning. |
| `checkConclusion(war)` | Called periodically. Return `null` while the war continues, or a `WarConclusion` naming the winner (or a draw) when it should end. |

Useful optional hooks (all have sensible defaults):

- `describeScore(war, team, viewer)` — extra per-source breakdown lore in the war-info UI (e.g. kills
  vs. captures). Defaults to empty.
- `getLeader(war)` — the currently leading party; defaults to comparing `getScore` for both teams.
- `tick(war)` — called every war tick, for modes with their own scoring sources.
- `onPreparationStart(declaration)` / `onWarStart(war)` / `onEnd(war)` — lifecycle hooks to tell
  participants what to do or to release external resources (e.g. a reserved arena). These are **not**
  re-fired when a running war is reloaded on restart.
- `allowsPassiveDefenderDraw()` — return `false` if a defending winner can legitimately win without
  kills (e.g. by holding an objective). Defaults to `true` (a defender that merely out-camps is
  downgraded to a draw).
- `createState(war)` / `deserializeState(war, data)` — return a `WarModeState` if your mode needs to
  persist extra state beyond the shared war stats. Return `null` (the default) for a stateless mode
  that derives its score purely from the shared stats.

## Implementing a war goal

Implement `me.angeschossen.lands.api.war.goal.WarGoal`. A goal owns everything specific to the
outcome: applying the effect, the win/loss announcement (broadcast + inbox), and the war shield. The
framework only keeps goal-agnostic concerns (win/loss counters, `WarEndEvent`, capture-flag cleanup,
and the draw broadcast). The key methods:

| Method | Purpose |
| --- | --- |
| `getId()` | Unique, stable id used for persistence and lookup. |
| `getName()` / `getDisplayName(viewer)` | Internal name and localized UI name. |
| `describeOutcome(context, winner, viewer, result)` | Required. Adventure component describing what happens to the winning team, shown in the declaration UI and war info. Called for both a fought win (`WarResult.END`) and a surrender (`WarResult.SURRENDERED`). |
| `isApplicable(attacker, defender)` | Whether the goal may be used for these two parties. Defaults to `true`. |
| `applyOutcome(war, winner, loser, result)` | Apply the terminal consequence and announce it once when the war ends with a clear winner. |

Optional:

- `applyOutcome(declaration, winner, loser, result)` — apply a surrender that happens **during
  preparation**, before a `War` exists (only a `WarDeclaration`). Defaults to a no-op.
- `onDraw(war)` — react to a stalemate. Draws apply no goal outcome by default; override only if a
  draw needs handling (e.g. the independence goal re-subjugates the rebel on a draw).
- `isAddOn()` — return `true` to make this an add-on goal that runs its outcome *after* a war's
  primary goal, rather than being selectable as a primary goal in the declaration.

## Player-facing configuration

Built-in modes and goals are configured in `Modules/Wars/modes.yml`. For how the built-in modes and
goals behave and are configured, see [War Modes and Goals](../configuration/War-Modes-and-Goals.md).
Your custom mode or goal is responsible for its own configuration and localized text (built-in ones
resolve their text from Lands' locale; third-party ones may build their own, e.g. localized via
`viewer.getPlayer().locale()`).

Read the JavaDocs on `WarMode`, `WarGoal`, `WarModeState`, and `WarConclusion` for the full contract
of each method.
