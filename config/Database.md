# Database

ChestProtect stores protection data in SQLite by default. MySQL can be enabled in `config.yml`.

# SQLite

SQLite is used when `database.mysql.enabled` is `false`.

Use SQLite for smaller servers or simple single-server setups. The database files are stored in the
ChestProtect plugin folder.

# MySQL

Enable MySQL in `config.yml`:

```yaml
database:
  mysql:
    enabled_20: true
    ip-address: 'localhost'
    port: '3306'
    username: 'minecraft'
    password: 'password'
    database: 'chestprotect'
    table-prefix: 'chestprotect_'
```

Restart the server after changing database type or credentials.

Use a unique `table-prefix` if ChestProtect shares a database with other plugins or another
ChestProtect server.

# Backups

Make backups before:

1. Updating ChestProtect.
2. Changing the database type.
3. Importing data from LWC.
4. Running cleanup or player deletion commands.

Back up the full `plugins/ChestProtect` folder for SQLite. For MySQL, back up the configured
database tables and keep a copy of the plugin folder.

# Legacy JSON Migration

Older ChestProtect installations may have JSON world data. On startup, ChestProtect checks for old
world data and migrates it to the active SQL database. After the migration finishes, restart the
server.

ChestProtect creates a `MIGRATED` marker in the plugin folder after the migration completes.

# Inactive Player Cleanup

`config.yml` contains:

```yaml
database:
  inactive-player-deleter:
    enabled: true
    offline-days: 120
```

When enabled, ChestProtect can delete protections of players who have been offline for at least the
configured number of days. Set `offline-days` below `1` to prevent deletion by age.
