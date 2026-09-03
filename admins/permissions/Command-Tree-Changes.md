# Command Tree Changes

This page summarizes a major command restructure. If you're upgrading from an older version and
manage permissions by hand, read this before assuming your old permission setup still works.

# What Changed

- `/land` and `/nation` no longer exist as separate commands. Every land subcommand that used to be
  reached through `/land <land> ...` (or `/lands land <land> ...`) is now a direct child of
  `/lands` - e.g. `/land <land> claim` is now `/lands claim`. The same applies to nations:
  `/nation <nation> chat` is now `/nations chat`. There's no `<land>`/`<nation>` argument anymore -
  every command acts on the player's *edit land*/its nation (see
  [`/lands edit`](#lands-edit) below), the same target resolution that used to only apply when
  `cmd-land-argument` was `false`.
- The `general.cmd-land-argument` config option is gone entirely - there's no mode where a
  `<land>`/`<nation>` argument is required, since there's no longer anywhere in the flattened
  command tree to put one.
- `/lands claim`/`/lands unclaim` absorbed the old `/claim`/`/lands claim` shortcut and the
  land-scoped `claim`/`unclaim` subtree into one command each. `/lands claim` with zero lands
  auto-creates one named after you, same as the old `/claim` shortcut did.
- `/lands area <area> resize` was renamed to `/lands area <area> assign` (a plain `/assign <area>`
  top-level shortcut exists too), and gained a sibling `/lands area <name> create` for making an
  empty area without also assigning a selection to it in the same step.
- Member commands were renamed from `add`/`remove` to `trust`/`untrust` to match the terminology
  already used everywhere else (message keys, events): `/lands member trust <player>` (also
  `/trust <player>`), `/lands member untrust <player>` (also `/untrust <player>`), and the nation
  equivalents `/nations member trust`/`untrust <land>` (also `/nations trust`/`untrust <land>`).
- `/lands spawn`/`/nations spawn` split: the browse-any-land/nation version stayed at
  `/lands spawn [land]` / `/nations spawn [nation]` (now with the argument optional - omit it to
  teleport to your own edit land's/nation's spawn), and a new `/lands setspawn` was added for
  setting your own edit land's spawn (previously `/land <land> spawn set`).
- There is no standalone `/wars` command or `wars.*` permission tree. War commands live directly
  under `/lands war ...` and `/nations war ...`. Wars are started through the normal `declare`
  command (admins use the `lands.admin.command.edit` bypass); admin-only actions are
  `/lands admin war end <land or nation>` and the `/lands admin war koth ...` arena commands.
- Staff who need to manage lands/nations they're not a member of use the
  `lands.admin.command.edit` bypass permission - this is unrelated to `/lands edit <land>` (below),
  which only lets *members* pick which of their own lands a command without an argument applies to.

# `/lands edit`

`/lands edit <land>` picks which of your own lands a bare command (`/lands claim`,
`/lands chat`, `/lands member trust`, ...) applies to, when you're trusted in more than one land -
there's no `<land>` argument on those commands anymore for you to specify it directly. If you're
only a member of one land, everything already applies to it automatically and `/lands edit` isn't
needed (the command replies "unavailable" if you try it with fewer than two lands, unless you have
the `lands.admin.command.edit` bypass). There's no equivalent for nations - a land's nation is
always resolved from the land, not selected separately.

This also affects placeholders - see
[PlaceholderAPI Placeholders](../configuration/PlaceholderAPI-Placeholders.md#which-land-is-used-without-_here).

# Permissions Changed Too

Because commands moved, most of their permission nodes moved with them - old nodes tied to the
removed `/land`/`/nation` tree no longer exist (`lands.command.land.*` and
`nations.command.nation.*` are both gone), and the promoted commands sit directly under
`lands.command.*`/`nations.command.*` instead (e.g. `lands.command.land.claim` is now just
`lands.command.claim`). Don't assume a pre-upgrade permission config still grants the right access -
review it against the current command list.

# Where to Look Next

| Page | Use it for |
| --- | --- |
| [Player Commands](Player-Commands.md) | Full player-facing command-to-permission reference. |
| [Admin Commands](../Commands.md) | Full `/lands admin` command-to-permission reference. |
| [Permissions](Permissions.md) | Wildcards, flag permissions, and other non-command permissions. |
| [Recommendation](Recommended-Permission-Setup.md) | Suggested permission setup to rebuild from. |
