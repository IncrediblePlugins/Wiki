# Protection Flags

Protection flags are toggled in a protection's menu. They change the behavior of one protection and
do not change role permissions.

Players need role access to `EDIT_FLAGS` to edit these flags.

| Flag | What it does |
| --- | --- |
| `REDSTONE` | Allows redstone signals to affect the protection. Useful for doors, trapdoors, buttons, levers, repeaters, comparators, and similar mechanisms. |
| `PUBLIC_TAKE` | Allows everyone to take or use the protection without being trusted. |
| `PUBLIC_INSERT` | Allows everyone to insert items without being trusted. |
| `HOLOGRAM` | Shows a hologram above supported containers with information such as the name and storage space. |

# Availability

Not every flag appears for every protection type.

| Protection type | Common available flags |
| --- | --- |
| Containers | `PUBLIC_TAKE`, `PUBLIC_INSERT`, and sometimes `HOLOGRAM` |
| Doors and trapdoors | `REDSTONE`, `PUBLIC_TAKE` |
| Buttons, levers, repeaters, comparators | `REDSTONE`, `PUBLIC_TAKE` |
| Pressure plates | `REDSTONE`, `PUBLIC_TAKE` |

# Defaults

New protections use the default flags configured in `config.yml`. The default file shows this as
`protection.default_flags_list`.

The default file enables `REDSTONE` and `HOLOGRAM`.
