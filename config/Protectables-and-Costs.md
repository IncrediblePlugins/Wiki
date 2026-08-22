# Protectables and Costs

Protectable blocks and entities are configured in `protectables.yml`.

You can enable or disable whole categories and individual types, set lock costs, set cashback, and
choose whether supported containers show holograms.

# Global Costs

If `global-costs.enabled` is `true`, ChestProtect ignores individual type costs and uses the global
cost and cashback values.

```yaml
global-costs:
  enabled: false
  value: 25
  cashback: 50
```

# Per-Type Costs

Each protectable type can define:

| Option | What it does |
| --- | --- |
| `enabled` | Whether players can protect this type. |
| `hologram` | Whether supported containers start with holograms available. |
| `costs.value` | Cost to create the protection after free protections are used. |
| `costs.cashback` | Percentage of the lock cost returned when the protection is unlocked. |
| `icon` | Optional menu icon for types that need a custom item or skull texture. |

Example:

```yaml
protectables:
  blocks:
    types:
      chest:
        enabled: true
        hologram: true
        costs:
          value: 50
          cashback: 50
```

# Default Enabled Blocks

The default file enables common block protection types such as chests, barrels, furnaces, smokers,
doors, fence gates, trapdoors, lecterns, shulker boxes, shelves, and hoppers.

Other listed block types, such as crafting tables, beds, pressure plates, player heads, and signs,
are present but disabled by default.

# Default Enabled Entities

The default file enables armor stands, item frames, and several passive entities such as cows,
sheep, pigs, chickens, dolphins, donkeys, horses, foxes, llamas, mushroom cows, ocelots, pandas,
parrots, polar bears, wolves, rabbits, and turtles.

Many hostile or special entities are listed but disabled by default.

# Custom Types

You can add custom block or entity types by using Bukkit material or entity names. Only the default
types are fully tested.

After editing `protectables.yml`, run `/chestprotect admin reload` or restart the server.
