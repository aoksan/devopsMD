---
version:
  - v0.1gpt
---
### 1. **Move DB**
If you're moving a PostgreSQL database from one server to another, you can perform a dump of the database and restore it on the new server.

#### Commands:
1. **On the old server (Backup the DB):**
   ```bash
   pg_dump -U [username] -h [old_host] -F c -b -v -f /path/to/backup/file.dump [database_name]
   ```
   **Explanation:**

   - `pg_dump` creates a backup of the database.
   - `-U [username]` specifies the PostgreSQL username.
   - `-h [old_host]` is the host where the DB is located.
   - `-F c` specifies the custom format for the dump.
   - `-b` includes large objects in the dump.
   - `-v` enables verbose mode to show detailed information.
   - `-f /path/to/backup/file.dump` specifies the backup file's location.
   - `[database_name]` is the name of the database being backed up.

2. **On the new server (Restore the DB):**
   ```bash
   pg_restore -U [username] -h [new_host] -d [new_database_name] -v /path/to/backup/file.dump
   ```
   **Explanation:**
   - `pg_restore` restores the database from the dump file.
   - `-U [username]` specifies the PostgreSQL username.
   - `-h [new_host]` is the host where the DB will be restored.
   - `-d [new_database_name]` is the name of the new database.
   - `-v` enables verbose mode.
   - `/path/to/backup/file.dump` is the location of the backup file.

---

### 2. **Create DB User**
To create a new user in PostgreSQL:

#### Command:
```sql
CREATE USER [new_user_name] WITH PASSWORD '[password]';
```
**Explanation:**
- `CREATE USER [new_user_name]` creates a new user.
- `WITH PASSWORD '[password]'` assigns a password to the user.

---

### 3. **Grant DB's Permission to User**
Grant the necessary permissions to the newly created user for the database:

#### Command:
```sql
GRANT ALL PRIVILEGES ON DATABASE [database_name] TO [new_user_name];
```
**Explanation:**
- `GRANT ALL PRIVILEGES` gives full access to the database.
- `ON DATABASE [database_name]` specifies which database the user can access.
- `TO [new_user_name]` assigns the privileges to the newly created user.

If you want to be more specific and grant certain permissions (like read-only access), you can do something like:
```sql
GRANT SELECT ON ALL TABLES IN SCHEMA public TO [new_user_name];
```

---

### 4. **Re-config Client DB Connection**
On the client machine, update the database connection settings to point to the new database host and user credentials.

#### Example (Update connection string in configuration file):
```bash
DB_HOST=[new_host]
DB_USER=[new_user_name]
DB_PASSWORD=[password]
DB_NAME=[new_database_name]
```
**Explanation:**
- Update the connection string or configuration file with the new host, user, password, and database name.

---

These steps cover the migration of the database, creating a new user, granting permissions and updating client configurations. Let me know if you need further clarification or adjustments!