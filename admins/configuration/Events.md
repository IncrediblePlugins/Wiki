# Lands Events

Lands can execute configured commands when Lands events happen.

Configuration file:

`events.yml`

Use this for server automation, rewards, announcements, punishments, logging, and integration hooks that do not require a custom plugin.

For the shared syntax rules, conditions, and command formatting, also read the general events guide:

[General Events Guide](https://wiki.incredibleplugins.com/general/messages-and-config/events)

# Event Structure

Each event has a section like this:

```yaml
LandCreateEvent:
  cancel: ''
  commands:
    condition: '!cancelled'
    groups:
      player_self:
        1:
          condition: ''
          commands: [ ]
```

Common fields:

| Field | What it does |
| --- | --- |
| `cancel` | Optional condition that cancels a cancellable event. |
| `commands.condition` | Condition required before command groups run. |
| `groups` | Recipients or related player groups that commands can run for. |
| `commands` | Commands executed for that group entry. |

# Common Event Groups

Groups depend on the event. Common groups include:

| Group | Meaning |
| --- | --- |
| `player_self` | The player who triggered the action. |
| `player_target` | The target player of the action. |
| `recipients` | Players receiving a broadcast or chat event. |
| `land_trusted` | Trusted players in the land. |
| `land_online` | Online trusted players in the land. |
| `area_trusted` | Trusted players in the affected area. |
| `area_online` | Online trusted players in the affected area. |
| `nation_trusted` | Trusted players in the nation. |
| `nation_online` | Online trusted players in the nation. |
| `war_attacker_online` | Online players on the attacking side. |
| `war_defender_online` | Online players on the defending side. |
| `war_winner_online` | Online players on the winning side. |
| `war_loser_online` | Online players on the losing side. |

# Cancellable Events

Some events include `cancel`.

Examples include:

* `ChunkPreClaimEvent`
* `LandCreateEvent`
* `LandDeleteEvent`
* `LandTrustPlayerEvent`
* `PlayerTaxEvent`
* `WarDeclareEvent`
* `MemberHolderUpkeepEvent`

Use cancellation carefully. A cancellation condition can block normal player actions.

# Claim and Unclaim Events

Use specific events when possible:

| Event | Use it for |
| --- | --- |
| `ChunkPreClaimEvent` | Before a single chunk claim is completed. Can be cancelled. |
| `ChunkPostClaimEvent` | After a chunk claim is completed. |
| `LandUnclaimSelectionEvent` | Selection unclaims. Can be cancelled. |
| `LandUnclaimAllEvent` | Full land unclaim actions. Can be cancelled. |
| `ChunkDeleteEvent` | Single chunk unclaims with type `DEFAULT`. |
| `LandDeleteEvent` | Land deletion. Can be cancelled. |

# War Events

War-related sections include:

* `WarDeclareEvent`
* `WarEndEvent`

Use these to announce wars, reward sides, run cleanup commands, or notify external systems.

# Testing

Recommended workflow:

1. Back up `events.yml`.
2. Add one event entry at a time.
3. Test on a staging server or with a staff-only action.
4. Check console output for condition or command errors.
5. Keep cancellation rules simple and documented.
