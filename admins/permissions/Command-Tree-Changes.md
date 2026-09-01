# Command Tree Changes

This page summarizes a major command restructure. If you're upgrading from an older version and
manage permissions by hand, read this before assuming your old permission setup still works.

# What Changed

- Commands now take the land or nation directly: `/land <land> ...` / `/lands land <land> ...` and
  `/nation <nation> ...` / `/nations nation <nation> ...` - see
  [`/lands edit` and `cmd-land-argument`](#lands-edit-and-cmd-land-argument) below for when the
  `<land>`/`<nation>` argument is actually required.
- There is no standalone `/wars` command or `wars.*` permission tree anymore. War commands live
  under `/land <land> war ...` and `/nation <nation> war ...`. Wars are started through the normal
  `declare` command (admins use the `lands.admin.command.edit` bypass); admin-only actions are
  `/lands admin war end <land or nation>` and the `/lands admin war koth ...` arena commands.
- Staff who need to manage lands/nations they're not a member of use the
  `lands.admin.command.edit` bypass permission - this is unrelated to `/lands edit <land>` (below),
  which only lets *members* pick which of their own lands a command without an argument applies to.

# `/lands edit` and `cmd-land-argument`

Whether `/land`/`/nation` commands need an explicit `<land>`/`<nation>` argument is controlled by
`general.cmd-land-argument` in `config.yml`:

- **`false`** (the default, and what existing servers get migrated to) - the argument is optional.
  Left out, the target is resolved from the player's *edit land* instead, falling back to their only
  land if they're only a member of one. `/lands edit <land>` is registered so players with multiple
  lands can pick which one those commands should apply to.
- **`true`** - `/land`/`/nation` always require an explicit `<land>`/`<nation>` argument, and
  `/lands edit` isn't registered at all, since there's nothing to select.

This also affects placeholders - see
[PlaceholderAPI Placeholders](../configuration/PlaceholderAPI-Placeholders.md#which-land-is-used-without-_here).

# Permissions Changed Too

Because commands moved, most of their permission nodes moved with them - old nodes tied to the
removed command tree no longer exist, and new commands have new nodes (`lands.command.land.*`,
`nations.command.nation.*`, and so on). Don't assume a pre-upgrade permission config still grants
the right access - review it against the current command list.

# Where to Look Next

| Page | Use it for |
| --- | --- |
| [Player Commands](Player-Commands.md) | Full player-facing command-to-permission reference. |
| [Admin Commands](../Commands.md) | Full `/lands admin` command-to-permission reference. |
| [Permissions](Permissions.md) | Wildcards, flag permissions, and other non-command permissions. |
| [Recommendation](Recommended-Permission-Setup.md) | Suggested permission setup to rebuild from. |
