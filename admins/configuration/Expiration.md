# Land Expiration and Cleanup

Lands can untrust inactive members, give the land of an inactive owner to an active member, put it up for sale, or delete it.

These settings are in `config.yml` under `land.expiration`.

Take a database backup before setting the status to `active`. A deleted land can't be restored without one.

# Status

`status` decides whether expiration runs:

| Value | Effect |
|---|---|
| `off` | Nothing expires, nothing is shown. |
| `preview` | The default. The checks only log what would happen, nothing is done. Members see in the land menu when their land would expire. |
| `active` | Lands and members expire. |

# Quick Start

1. Back up the database.
2. Keep `status: preview`. Check what would happen: `/lands admin expiration list` and `/lands admin expiration run`
   only show and log it.
3. Adjust the tiers until the list looks right, then set `status: active` and restart.

# How Players Count as Inactive

Last logins and playtimes are the ones of the whole network: they're read from the Lands database, so an owner who plays
on another server of the network isn't inactive. For players who weren't online since the update, the playerdata of
this server is used.

`owners.tiers_list` sets how long owners may be offline, by their playtime. Each entry is `'<playtime>: <offline time>'`:
from this much playtime on, owners may be offline this long. `never` means they never count as inactive. The tier with
the highest playtime the player reached applies.

```yaml
owners:
  tiers_list:
    - '0: 14d'     # everyone: 14 days
    - '5h: 30d'    # from 5 hours of playtime on: 30 days
    - '2d: 90d'    # from 2 days of playtime on: 90 days
    - '7d: never'  # from 7 days of playtime on: never
```

An empty list means owners don't expire.

Players whose playtime is unknown (0, e.g. their statistics file is missing) use the tier with the highest playtime, so
veterans without data don't expire early. Members without playtime data don't get a land as active members, though.
Players whose last login is unknown are decided by `unknown-players`, whatever their tier.

`members.member-tiers_list` works the same way for members. Inactive members are untrusted from the land and all its areas. It's
empty by default, so members don't expire.

If the playtime or last logins can't be read (e.g. the database is down), or some Lands data failed to load, the check
is skipped. Nothing is deleted then.

# What Happens to the Land

`owners.outcomes_list` decides what happens to the land of an inactive owner. The outcomes are tried in order, and the
first that's possible happens:

| Outcome | Effect |
|---|---|
| `transfer` | The land goes to the active member with the highest role (the one seen last first). Only members trusted in the whole land count, not tenants, temporary members or members of a sub area only. Only possible if one of them is active. |
| `sell` | The land is put up for sale for `sale.duration_time`. If nobody buys it in that time, the next outcome happens. Not while the land is at war. See [Selling Lands](#selling-lands). |
| `delete` | The land is deleted. Not while it's at war: then nothing happens until the war is over. Lands with rented or sold areas and lands with a KotH arena are deleted like others. |

```yaml
owners:
  outcomes_list:
    - transfer
    - sell
    - delete
```

The default is `transfer`, then `delete`. An empty list means nothing happens to the land, only members expire.

The old owner is untrusted after a transfer. A member who already owns as many lands as their limit allows is skipped.

A deleted land's bank goes to its owner.

## Selling Lands

With `sell` in `owners.outcomes_list`, the land of an inactive owner is put up for sale at the first check after the
owner became inactive. Players find these lands in `/lands rental list` (the type filter "Inactive owners" shows only
them) and buy one by clicking it, or with `/lands rental buy` while standing in it (permission
`lands.command.rental.buy`). The list says why the land is for sale and when it's deleted if nobody buys it.

Selling needs `land.rent.sell` to be enabled. Without it, `sell` is left out (the next outcome happens) and Lands logs a
warning at the start.

* The price is `sale.price` plus `sale.price-per-chunk` for each claimed chunk.
* The price and the land bank go to the old owner.
* The buyer becomes the owner. All members are untrusted, except tenants of rented or sold areas: they keep what they
  rented or bought. The land's inbox tells who bought it.
* A sold land leaves its nation. A sold capital passes the capital on first, like a deleted one (see below).
* The buyer needs the same as for buying a land with a sell sign: they must be able to own another land in its world,
  and the land's owner must not have changed too recently (`land.setowner.owner-change-cooldown`).
* A land at war when its sale ends stays for sale until someone buys it, since it can't be deleted then.
* `sale.duration_time` (default `14d`) is how long the land is for sale, from the check that put it up for sale. After
  that, the next outcome happens, e.g. `delete`. A land is always put up for sale first, also if its owner has been
  inactive for longer (e.g. expiration was turned on later). `0`, or `sell` as the last outcome, means it's for sale until someone buys it.
* The sale ends if the owner logs in, or if a member becomes active and `transfer` comes before `sell`.
* In preview, lands aren't for sale.

Players can only buy lands of the server they're on.

## Nation Capitals

If a capital is deleted or sold, another land of the nation with an active owner becomes the capital first (not a vassal, and
only lands that reached the capital level of `levels.yml`; the highest level first). The nation is only deleted with
its capital if none of its lands is active.

## Lands at War

A land at war isn't deleted, only logged: the war would end. It may still get a new owner. Admin lands and camps never
expire.

## Bypasses and Shields

* Owners with `lands.bypass.expiration` never count as inactive. For offline players, this needs LuckPerms. Members
  with it aren't untrusted.
* The natural flag `EXPIRATION_SHIELD` protects a land from expiration.

# When Lands Are Checked

`check.frequency` sets when lands are checked:

| Value | Checks |
|---|---|
| `daily` | Every day at `check.daily.time` (24h, server time zone, default `04:00`), or only on the weekdays in `check.daily.days_list` (e.g. `[ monday, thursday ]`). |
| `interval` | Every `check.interval_time` (e.g. `6h`) after the server started. The first check runs one interval after the start. |
| `manual` | Only with `/lands admin expiration run`. |

`daily` is the default: lands are deleted at a known time, the same for everyone, so nobody can wait for a land to
disappear to claim its area first. Changing `check.frequency` requires a restart.

A land that becomes due is acted on at the first check from then on.

# Warnings and Where Players See It

`warn-before_time` (default `3d`) is how long before a land is deleted, transferred or put up for sale its members are told. `0` turns
warnings off.

* The land gets an inbox message when the warning time begins.
* Members who may edit the land settings get a chat message when they join.
* No warnings are sent in preview.

The warning ends by itself once the owner logs in.

The land menu and the land info menu show an "Inactivity" item when something happens to the land soon: within
`warn-before` (3 days if that's `0`), or while it's for sale. It says when the land is deleted, transferred or put up
for sale. It isn't shown while the owner is online, since their offline time only starts once they log out. Members who
may edit the land settings and admins see it. With `show-to-untrusted: true`, every player sees it. It isn't shown to
others by default, since it tells when the owner was last online.

PlaceholderAPI: `%lands_land_expiration%`, `%lands_land_expiration_date%` and `%lands_land_expiration_action%`. See
[PlaceholderAPI Placeholders](PlaceholderAPI-Placeholders.md).

# Other Options

| Option | Description |
|---|---|
| `empty-lands_time` | Lands without any claims are deleted once they're this old, e.g. lands whose owner never claimed land after creating it. `0` = never. Lands of online owners aren't deleted. |
| `unknown-players` | Players whose last login is unknown (e.g. the playerdata folder was deleted): `ignore` (they never count as inactive) or `inactive`. With `inactive`, deleting the playerdata folder **may delete all affected lands**. |
| `show-to-untrusted` | Players who aren't trusted in a land see when it expires. Off by default. |

Players without any land who weren't online for 180 days are deleted from the Lands database too, if no tiers are set.

# Commands

| Command | Description | Permission |
|---|---|---|
| `/lands admin expiration list [duration]` | Lands that are deleted or transferred within the duration (default `7d`), the soonest first, and lands that are kept although they expired. | `lands.admin.command.expiration.list` |
| `/lands admin expiration run` | Checks the lands now, like a scheduled check. In preview, it only shows what would happen. | `lands.admin.command.expiration.run` |

`lands.admin.command.expiration` gives both `list` and `run`.

# Updating From the Old Options

The old options (before the rework) are converted when you update. If you used expiration (owner or member entries,
or `no-claims`), it **only runs in preview** until you set `status: active`, so you can review them. Otherwise it's
`off`, like before:

| Old | New |
|---|---|
| `owner_list` | `owners.tiers_list`, with the same behavior. `'15m:7d', '30m:14d'` ("up to 15m playtime: 7d, up to 30m: 14d, more: 14d") becomes `'0: 7d', '15m: 14d'`. |
| `member_list` | `members.member-tiers_list`, the same way. |
| `replace-owner` | `owners.outcomes_list`: `transfer`, `delete` (true) or `delete` (false). Empty if `owner_list` was empty. |
| `delete-invalid` | `unknown-players: inactive` (true) or `ignore` (false). |
| `no-claims` (days) | `empty-lands_time` (e.g. `7d`). Only if `land.creation.claim-radius` wasn't `-1`, where `no-claims` had no effect. |

Updated servers get `check.frequency: interval`, since lands were checked every 6 hours before. Consider `daily`.
