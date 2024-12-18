# Connecting to PostgreSQL and Running Queries

## Using psql

### Connect to PostgreSQL
1. Open a terminal.
2. Run the following command to connect to your PostgreSQL database:
   ```sh
   psql -h localhost -U your_username -d your_database
   ```

### Example Queries
1. **List all tables**:
   ```sql
   \dt
   ```

2. **Retrieve the first 5 rows from a table**:
   ```sql
   SELECT * FROM your_table LIMIT 5;
   ```

## Using DBeaver

### Connect to PostgreSQL
1. Open DBeaver.
2. Create a new connection:
   - Go to `Database` > `New Database Connection`.
   - Select `PostgreSQL` from the list of database types.
   - Enter the connection details (host, port, database, user, and password) and click `Finish`.

### Example Queries
1. **List all tables**:
   - Open the SQL Editor by right-clicking on the database or schema in the **Database Navigator** and selecting `SQL Editor` > `New SQL Script`.
   - Write and execute the following query:
     ```sql
     SELECT table_name FROM information_schema.tables WHERE table_schema = 'public';
     ```

2. **Retrieve the first 5 rows from a table**:
   - Write and execute the following query in the SQL Editor:
     ```sql
     SELECT * FROM your_table LIMIT 5;
     ```

## Using VS Code PostgreSQL Extension

### Connect to PostgreSQL
1. Install the PostgreSQL extension from the VS Code marketplace.
2. Open the PostgreSQL extension sidebar.
3. Add a new connection with your database details.

### Example Queries
1. **List all tables**:
   - Open a new query editor by right-clicking on the connection and selecting `New Query`.
   - Write and execute the following query:
     ```sql
     SELECT table_name FROM information_schema.tables WHERE table_schema = 'public';
     ```

2. **Retrieve the first 5 rows from a table**:
   - Write and execute the following query in the query editor:
     ```sql
     SELECT * FROM your_table LIMIT 5;
     ```

---

By using these commands and queries, you can connect to your local PostgreSQL server and retrieve data using psql, DBeaver, and the PostgreSQL extension of VS Code. Each tool provides a different interface and set of features, allowing you to choose the one that best fits your workflow and preferences.
