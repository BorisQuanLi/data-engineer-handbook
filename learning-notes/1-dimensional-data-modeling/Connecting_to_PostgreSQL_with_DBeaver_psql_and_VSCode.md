# Connecting to PostgreSQL with DBeaver, psql, and VS Code

## Introduction

This guide provides an overview of how to connect to and query a local PostgreSQL database using three different tools: DBeaver, psql, and VS Code with the PostgreSQL extension.

## DBeaver

### Installation

1. Download and install DBeaver from the [official website](https://dbeaver.io/download/).

### Connecting to PostgreSQL

1. Open DBeaver and click on the "New Database Connection" button.
2. Select "PostgreSQL" from the list of database types and click "Next".
3. Enter the connection details:
   - **Host**: `localhost`
   - **Port**: `5432`
   - **Database**: `your_database_name`
   - **Username**: `your_username`
   - **Password**: `your_password`
4. Click "Finish" to establish the connection.

### Querying the Database

1. Open the SQL Editor by right-clicking on the database connection and selecting "SQL Editor".
2. Write and execute your SQL queries in the editor.

## psql

### Installation

1. Install PostgreSQL, which includes the `psql` command-line tool. Follow the instructions on the [official PostgreSQL website](https://www.postgresql.org/download/).

### Connecting to PostgreSQL

1. Open a terminal and run the following command to connect to the PostgreSQL database:
   ```sh
   psql -h localhost -p 5432 -d your_database_name -U your_username
   ```
2. Enter your password when prompted.

### Querying the Database

1. Once connected, you can execute SQL queries directly in the `psql` command-line interface.
2. Use the `\q` command to exit the `psql` interface.

## VS Code with PostgreSQL Extension

### Installation

1. Download and install Visual Studio Code from the [official website](https://code.visualstudio.com/).
2. Install the PostgreSQL extension for VS Code from the [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ckolkman.vscode-postgres).

### Connecting to PostgreSQL

1. Open VS Code and click on the PostgreSQL extension icon in the Activity Bar.
2. Click on the "Add New Connection" button.
3. Enter the connection details:
   - **Host**: `localhost`
   - **Port**: `5432`
   - **Database**: `your_database_name`
   - **Username**: `your_username`
   - **Password**: `your_password`
4. Click "Connect" to establish the connection.

### Querying the Database

1. Open a new SQL file in VS Code.
2. Write and execute your SQL queries using the PostgreSQL extension.

## Troubleshooting

### Common Errors in DBeaver

#### Error: SQL SELECT statement not executing

If you encounter an error when running a SQL SELECT statement in DBeaver, try the following steps:

1. **Check Connection**: Ensure that your connection to the PostgreSQL database is active. You can do this by clicking on the connection in the Database Navigator and verifying that it is connected.
2. **Verify SQL Syntax**: Make sure that your SQL statement is correctly formatted and does not contain any syntax errors.
3. **Check Permissions**: Ensure that the user you are connecting with has the necessary permissions to execute the SQL statement.
4. **Review Error Message**: Look at the detailed error message provided by DBeaver. It often contains clues about what might be wrong.
5. **Restart DBeaver**: Sometimes, simply restarting DBeaver can resolve transient issues.

#### Error: Permission denied for table

If you receive a "permission denied" error for a table, follow these steps:

1. **Check User Permissions**: Ensure that the user you are connecting with has the necessary permissions to access the table. You can check and grant permissions using the following SQL commands:
   ```sql
   -- Check current permissions
   \dp player_seasons

   -- Grant SELECT permission to the user
   GRANT SELECT ON TABLE player_seasons TO your_username;
   ```
2. **Reconnect**: After updating permissions, reconnect to the database in DBeaver and try running the query again.

If the problem persists, consult the DBeaver [documentation](https://dbeaver.io/documentation/) or seek help from the community forums.

## Conclusion

By following this guide, you should be able to connect to and query a local PostgreSQL database using DBeaver, psql, and VS Code with the PostgreSQL extension. Each tool offers unique features and interfaces, allowing you to choose the one that best fits your workflow.
