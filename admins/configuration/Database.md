# Available Database Types
* SQLite-v2: Doesn't require any database server and works without setting anything up.
* MySQL: Use MySQL-v2 instead. This database mode is deprecated.
* MySQL-v2: We recommend using MySQL, if you need to connect your database to an external system, or you use a backup system that requires it. If you want to use MySQL: Make sure that your MySQL server is set up correctly (up-to-date MySQL server version, connection limits, utf8mb4_0900_as_cs as table encoding, etc.). This also supports [synchronizing claim data across multiple servers](https://wiki.incredibleplugins.com/lands/configuration/database#synchronizing-claims-across-servers) in combination with Redis.\
Please make sure to configure the table-prefix correctly:
  ````yaml
    # It is highly recommended to set a unique table prefix if the plugin
    # shares a database with other plugins or Lands instances.
    table-prefix_2: 'lands_'
    ````

We recommend using MySQL-v2 over SQLite, if possible.

# Backups
Lands can back up and restore its own database, on both SQLite and MySQL-v2, without any external
tooling:

* `/lands admin database backup` runs an on-demand backup immediately.
* `/lands admin database restore <backup> confirm` restores from a backup file - tab-complete
  `<backup>` to see the available files. This is destructive: it replaces your current data with
  the backup, and the server restarts automatically right after to avoid continuing to run on
  stale, already-loaded data.

Backups can also run on a schedule, configured in `config.yml`:
````yaml
database:
  backup:
    schedule:
      # Daily backup time, 24h HH:mm, server-local time zone. Leave blank to disable.
      time: '04:00'
      # Which weekdays to run on - leave empty for every day.
      days: []
    # How many backups to keep - the oldest are deleted once this limit is exceeded.
    max_backups: 14
````
Backup files are stored under `Data/Backups/` in your plugin's data folder.

You can still additionally use MySQL-v2 with your own external backup service or script if you
prefer - the two approaches aren't exclusive.

# Migrate your Database to MySQL-v2, SQLite-v2
1. If you use MySQL, please create a new database that you want to new database to be saved to.
2. Also, if you want to migrate to MySQL, make sure the credentials and database name is set up correctly in your Lands config.
3. Make sure to take a backup of your current database (see [Backups](#backups) above).
After you have followed these steps, execute one of these commands:

* `/lands admin database migrate sqlite-v2 confirm`
* `/lands admin database migrate mysql-v2 confirm`

# Synchronizing Claims across Servers
A MySQL database and Redis instance is required. It won't work properly without Redis! Also each connected server must have the same time zone configured for your Minecraft server.
If you want to synchronize claim data between servers, make sure to configure the following sections in config.yml.

> **Note:** The `/lands storage` command (shared land storage) is **disabled when Redis is enabled**. A shared item container can't be reliably synchronized across servers, so land storage is not available in a multi-server (Redis) setup — regardless of the `land.storage` setting.

# MySQL:
If you're currently using the old SQL schema, please make sure to migrate to the new one using `/lands admin database migrate mysql-v2`.
Before migration, make sure to use a different `table-prefix` for `mysql-v2`, if you're currently using `mysql`. In case it's the same, adjust it and then reload the configuration before migration.

````yaml
  mysql-v2:
    enabled_19: true
    address_2: 'localhost'
    port_2: '3306'
    username_2: 'minecraft'
    password_2: 'password'
    database_2: 'lands'

    # It is highly recommended to set a unique table prefix if the plugin shares a database with other plugins.
    table-prefix_2: 'lands_'
````

#### Redis:
It is very important to properly configure the `server-name` and `master` option properly.
````yaml
  redis:
    enabled_6: true
    address_3: "redis://127.0.0.1"
    port_3: 6379
    username_3: "default"
    password_3: "password"
    # This should be the name that you configured for this server in your BungeeCord or Velocity config.
    server-name: "server-1"
    # This option should only be enabled on ONE of the servers that are connected to the same Lands database and Redis.
    # If true: This server will execute tasks, such as upkeep, taxes etc. for all lands across all servers that are
    # connected to the same Lands database and Redis.
    master: true
````

# Schema Migration
You might have gotten a warning in console that you should migrate to the new SQL schema.

## SQLite
To migrate to the new SQL schema with SQLite, follow these instructions:
1. Make sure that sqlite-v2 is **disabled** in config.yml and you currently still use the old database.
2. Execute `/lands admin database migrate sqlite-v2`
3. **Enable** `sqlite-v2` in config.yml:
````yaml
  # Use SQLite for the database. Doesn't require a database server.
  sqlite-v2: true
````
4. Restart the server.

## MySQL
To migrate to the new SQL schema with MySQL, follow these instructions:
1. Configure the mysql-v2 section in config.yml. **Make sure that mysql-v2 is disabled, and you currently still use the old database. Also, make sure to use a different table prefix or database than your current MySQL config!**
````yaml
  # MySQL database
  # To use this without issues, your connection limits etc. need to be configured properly in your MySQL server configuration.
  # If you want to synchronize lands and claims across servers, please read the setup instructions: https://wiki.incredibleplugins.com/lands/configuration/database#synchronizing-claims-across-servers
  mysql-v2:
    enabled_19: false
    address_2: 'localhost'
    port_2: '3306'
    username_2: 'minecraft'
    password_2: 'password'
    database_2: 'lands'

    # It is highly recommended to set a unique table prefix if the plugin shares a database with other plugins.
    table-prefix_2: 'lands_'
````
2. Execute `/lands admin database migrate mysql-v2` and check for any error messages, in case you provided the wrong credentials etc.
3. Enable mysql-v2 in config.yml.
4. Restart the server.
