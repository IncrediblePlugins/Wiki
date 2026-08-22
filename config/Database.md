# Database

FasterFurnaces stores placed furnaces and player data in a database.

## SQLite

SQLite is used by default and works without additional setup. It is the simplest option for a single server.

## MySQL

Enable MySQL in `config.yml` if you want FasterFurnaces to use an external database.

```yaml
database:
  mysql:
    enabled: true
    address: 'localhost'
    port: '3306'
    username: 'minecraft'
    password: 'password'
    database: 'fasterfurnaces'
    table-prefix: 'furnaces_'
```

Use a unique `table-prefix` if the database is shared with other plugins or another FasterFurnaces installation.

Do not connect multiple FasterFurnaces instances to the same database tables unless your setup has been designed for it. The default configuration is intended for one plugin instance per table prefix.

## Backups and Migration

Stop the server before changing database type, connection details, or table prefixes.

Always back up the existing database before migrating data or installing updates.
