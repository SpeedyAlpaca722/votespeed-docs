# Database (MySQL / SQLite)

VoteSpeed stores all player vote data in a database. Two backends are supported.

## SQLite (Default)

SQLite is the default database. It requires no setup — a single file is created in the plugin folder.

```yaml
# config.yml
storage:
  type: sqlite
  sqlite:
    file: "votes.db"
```

| Option | Description | Default |
|---|---|---|
| `file` | Database filename (relative to plugin folder) | `votes.db` |

**Best for:** Single servers, small to medium player counts, simple setups.

## MySQL

MySQL is recommended for larger servers or proxy networks where multiple servers need to access the same data.

```yaml
# config.yml
storage:
  type: mysql
  mysql:
    host: "localhost"
    port: 3306
    database: "votespeed"
    username: "root"
    password: "your_password"
```

| Option | Description | Default |
|---|---|---|
| `host` | MySQL server hostname or IP | `localhost` |
| `port` | MySQL server port | `3306` |
| `database` | Database name (must exist) | `votespeed` |
| `username` | MySQL username | `root` |
| `password` | MySQL password | — |

### MySQL Setup

1. Create the database:

```sql
CREATE DATABASE votespeed;
```

2. Create a user (optional but recommended):

```sql
CREATE USER 'votespeed'@'localhost' IDENTIFIED BY 'your_secure_password';
GRANT ALL PRIVILEGES ON votespeed.* TO 'votespeed'@'localhost';
FLUSH PRIVILEGES;
```

3. Update `config.yml` with your credentials
4. Restart the server

VoteSpeed automatically creates all required tables on first connection.

### Remote MySQL

For proxy networks, use a remote MySQL server accessible from all backend servers:

```yaml
mysql:
  host: "mysql.yourserver.com"
  port: 3306
  database: "votespeed"
  username: "votespeed"
  password: "your_secure_password"
```

Make sure all backend servers use the **same** MySQL credentials so they share vote data.

## Migrating from SQLite to MySQL

1. Stop the server
2. Change `storage.type` to `mysql` in `config.yml`
3. Configure MySQL credentials
4. Start the server — VoteSpeed creates fresh tables
5. Manually migrate data if needed (export from SQLite, import to MySQL)

> **Note:** There is no automatic migration tool. For a fresh start, simply switch the type and let the database start empty.

## Performance

### Caching

VoteSpeed includes a built-in cache to reduce database queries:

```yaml
cache:
  enabled: true
  expiry-seconds: 60
```

With caching enabled, player data is kept in memory for the configured duration, reducing database load significantly.

### Connection Pooling

For MySQL, VoteSpeed uses connection pooling internally to manage database connections efficiently.
