# Command Tree Changes

This page summarizes a major command restructure. If you're upgrading from an older version and
manage permissions by hand, read this before assuming your old permission setup still works.

# What Changed

- `/lands edit <land>` is gone. Commands now take the land or nation directly:
  `/land <land> ...` / `/lands land <land> ...` and `/nation <nation> ...` / `/nations nation <nation> ...`.
- There is no standalone `/wars` command or `wars.*` permission tree anymore. War commands live
  under `/land <land> war ...` and `/nation <nation> war ...`. Admin force-start/force-end moved to
  `/lands admin land <land> war start`/`end`.
- Staff who need to manage lands/nations they're not a member of now use the
  `lands.admin.command.edit` bypass permission instead of a separate edit command.

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
