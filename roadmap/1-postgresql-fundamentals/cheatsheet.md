# PostgreSQL Fundamentals Cheatsheet

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