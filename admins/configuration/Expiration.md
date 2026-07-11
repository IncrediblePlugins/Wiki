# Land Expiration and Cleanup

Lands can remove inactive members, replace inactive owners, or delete inactive lands.

These settings are in `config.yml` under `land.expiration`.

Take a database backup before changing expiration settings. A bad expiration setup can delete lands permanently.

# Task Timing

The expiration task runs automatically about every 6 hours.

You can run the configured cleanup manually with:

`/lands admin deleteinactive`

Permission:

`lands.admin.command.deleteinactive`

Expiration setting changes require a server reload or restart.

# Owner Inactivity

`land.expiration.owner_list` controls when land owners count as inactive.

Entry format:

`playtime:offline-time`

Example:

```yaml
owner_list:
  - '15m:7d'
  - '30m:14d'
  - '12h:30d'
  - '30d:never'
```

This means newer players can expire sooner, while players with more playtime get a longer offline period. `never` prevents expiration for players in that playtime range.

An empty list disables owner expiration.

# Member Inactivity

`land.expiration.member_list` uses the same format as `owner_list`.

Inactive members are untrusted from lands.

An empty list disables member expiration.

# Replacing Owners

`land.expiration.replace-owner` decides what happens when an owner expires.

If enabled, Lands tries to transfer ownership to the member with the highest role.

If no member can become owner, the land is deleted.

If disabled, inactive owner expiration can delete the land directly.

# Invalid Player Data

`land.expiration.delete-invalid` deletes Lands data for players whose Minecraft playerdata no longer exists.

Keep this disabled unless you fully understand the risk. If the server playerdata folder is removed or damaged, enabling this may delete many affected lands.

# Lands Without Claims

`land.expiration.no-claims` deletes lands that have no claims and are old enough.

Use `0` to disable it.

This option only applies when `land.creation.claim-radius` is larger than `-1`.

# Bypasses and Shields

Players with `lands.bypass.expiration` can bypass land expiration when LuckPerms support is available.

The natural flag `EXPIRATION_SHIELD` can protect a land from expiration if you expose or manage that flag.

# Safe Rollout

Recommended rollout for live servers:

1. Back up the database.
2. Start with empty lists or generous times.
3. Reload or restart.
4. Run `/lands admin deleteinactive` during a maintenance window.
5. Check logs and player reports before tightening the values.
