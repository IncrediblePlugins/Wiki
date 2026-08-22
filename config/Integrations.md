# Integrations

ChestProtect supports several optional integrations. Install the other plugin normally, then review
the matching options in `config.yml`.

# Region Plugins

ChestProtect can work with region plugins such as Lands, WorldGuard, PlotSquared, BentoBox, and
SuperiorSkyblock2.

Region integrations can control where players may create protections and whether region members
can access or manage protections.

Important options:

| Option | What it does |
| --- | --- |
| `integration.lands.only-land` | Only allow protections inside claims. Protections in unclaimed wilderness are blocked. |
| `integration.lands.only-trusted` | If a location is claimed, only allow locking if the player is trusted there. |
| `integration.lands.untrust-remove` | Delete a player's protections in a region when they are untrusted from that region. |
| `integration.lands.allow-region-members` | Let region members be trusted through the region by default. Players can change this per protection in the menu. |
| `integration.lands.owner-unlock` | Allow region owners to unlock protections of other players. |
| `integration.flag.global-regions` | Apply the `chestprotect-lock` region flag to global regions in supported region managers. |
| `integration.flag.default-state` | Default state of the `chestprotect-lock` flag. |

For Lands, ChestProtect registers `chestprotect_lock` for creating protections in lands and
`chestprotect_open` for the war/opening checks.

# Economy

ChestProtect can use Vault, Levels, or item currency.

| Option | What it does |
| --- | --- |
| `integration.economy.Vault.enabled_9` | Uses a Vault economy plugin for lock costs, cashback, and teleport costs. |
| `integration.economy.Vault.server-bank` | Optional server bank account that receives player expenses. |
| `integration.economy.levels.enabled_10` | Uses Levels economy support if available. |
| `integration.economy.items.strict` | Requires item currency to match name, lore, and other metadata. |

Lock costs are configured in `protectables.yml`. Teleport costs are configured in `config.yml`.

# Holograms

Supported hologram providers include CMI, DecentHolograms, FancyHolograms, and HolographicDisplays.

Set `general.hologram-provider` if you want to force a specific provider. Leave it empty to let
ChestProtect choose an available provider.

# PlaceholderAPI

Enable PlaceholderAPI support with:

```yaml
integration:
  chat:
    PlaceholderAPI:
      enabled_6: true
```

See [PlaceholderAPI Placeholders](PlaceholderAPI-Placeholders.md).

# Dynmap

Dynmap support can mark protections on a web map.

```yaml
integration:
  web:
    Dynmap:
      enabled_8: true
      layer: 'ChestProtect'
      icon: 'Protections X: {x} Z: {z}'
```

# ChestSort

If ChestSort is installed, ChestProtect prevents players from sorting inventories that belong to
protections they cannot access.
