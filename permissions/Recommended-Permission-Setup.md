# Recommended Permission Setup

This page gives a simple starting point for a normal survival server.

Adjust it to your server's economy, rank system, and disabled features.

# Normal Players

Give players the commands and limits they need:

```text
uspawners.command.get
uspawners.command.list
uspawners.command.confirmtp
uspawners.spawners.5
uspawners.upgrade
uspawners.drop-item
uspawners.teleport.spawner
```

If Silk Touch pickup is enabled, also give:

```text
uspawners.silktouch
```

Give mob permissions for the entity types players may buy:

```text
uspawners.mob.pig
uspawners.mob.cow
uspawners.mob.zombie
```

Use your own limit number in `uspawners.spawners.<number>`.

# Staff

Give trusted staff the admin command permissions they actually need:

```text
uspawners.admin.command
uspawners.admin.command.player
uspawners.admin.command.teleport
uspawners.admin.command.list
uspawners.admin.command.listperms
```

# Administrators

Reserve destructive or configuration-changing permissions for administrators:

```text
uspawners.admin.command.give
uspawners.admin.command.reload
uspawners.admin.command.migratedb
uspawners.admin.command.killall
uspawners.bypass.delete
uspawners.bypass.edit
uspawner.bypass.ownership
uspawners.bypass.only-land
uspawners.bypass.vanilla.place
```

Players with operator status usually have all permissions.
