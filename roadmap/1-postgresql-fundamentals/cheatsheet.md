# PostgreSQL Fundamentals Cheatsheet

## What is a Tablespace?
A tablespace in PostgreSQL is a storage location on disk where the actual data files for database objects (like tables and indexes) are stored. By default, all data is stored in the main PostgreSQL data directory, but you can create additional tablespaces to spread data across different disks or directories for performance, organization, or storage management.

**Key points:**
- Tablespaces allow you to control where your data physically resides.
- You can assign tables or indexes to a specific tablespace when creating them.
- Useful for managing large databases, optimizing I/O, or separating data for backup/restore.

**Example:**
```sql
CREATE TABLESPACE fastspace LOCATION '/mnt/fast_ssd';
CREATE TABLE mytable (
    id SERIAL PRIMARY KEY,
    data TEXT
) TABLESPACE fastspace;
```

To list tablespaces in psql: `\db`


## Connecting to PostgreSQL
```
psql -U username -d dbname -h host -p port
```

## Common Commands
| Action                | Command Example                      |
|-----------------------|--------------------------------------|
| List databases        | `\l`                                 |
| Connect to database   | `\c dbname`                          |
| List tables           | `\dt`                                |
| Describe table        | `\d tablename`                       |
| List users/roles      | `\du`                                |
| Show current database | `SELECT current_database();`         |
| Show tablespaces      | `\db`                                |
| Quit psql             | `\q`                                 |

## Table Operations
```
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name TEXT NOT NULL,
    email TEXT UNIQUE
);

INSERT INTO users (name, email) VALUES ('Alice', 'alice@mail.com');
SELECT * FROM users;
UPDATE users SET name = 'Bob' WHERE id = 1;
DELETE FROM users WHERE id = 1;
DROP TABLE users;
```

## Useful Meta-Commands
- `\?` — Show all psql commands
- `\h` — Get SQL syntax help (e.g., `\h SELECT`)
- `\timing` — Toggle query execution time

---
This cheatsheet covers the most common PostgreSQL basics for quick reference.