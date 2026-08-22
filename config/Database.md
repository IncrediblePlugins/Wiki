# Database

UpgradeableSpawners stores placed spawners and player data in a database.

By default, it uses SQLite. You can enable MySQL in `config.yml` if you want a shared external
database.

# SQLite

SQLite is the default file-based database. It is the simplest option for single-server setups.

Before updating or migrating, stop the server and back up the plugin folder.

# MySQL

To use MySQL:

1. Stop the server.
2. Configure the `database.mysql` section in `config.yml`.
3. Set MySQL to enabled.
4. Start the server.

Make sure the database, username, password, host, and port are correct before starting the server.

# Migrating Data

Use `/spawners admin migratedb mysql` to copy the current data to MySQL.

Use `/spawners admin migratedb sqlite` to copy the current data back to SQLite.

After migration, enable the target database type in `config.yml` and restart the server.

Always make a backup before migrating.
