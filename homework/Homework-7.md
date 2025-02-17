# Homework 7 – Database Servers

1. **Question:** (True/False) A relational database organizes data into tables with rows and columns.
   - **Answer:** `True`

1. **Question:** (True/False) SQL stands for Structured Query Language.
   - **Answer:** `True`

1. **Question:** (True/False) All databases use SQL as their query language.
   - **Answer:** `False`

1. **Question:** What command is used to retrieve data from a SQL database?
   - **Answer:** `SELECT`

1. **Question:** What command is used to add new data to a SQL database table?
   - **Answer:** `INSERT`

1. **Question:** What command is used to modify existing data in a SQL database table?
   - **Answer:** `UPDATE`

1. **Question:** What command is used to remove data from a SQL database table?
   - **Answer:** `DELETE`

1. **Question:** A foreign key is used to link two ____ together.
   - **Answer:** `tables`

1. **Question:** (True/False) A database index improves data retrieval speed.
   - **Answer:** `True`

1. **Question:** What command is used to grant permissions to a SQL database user?
   - **Answer:** `GRANT`

1. **Question:** What command is used to revoke permissions from a SQL database user?
   - **Answer:** `REVOKE`

1. **Question:** (True/False) PostgreSQL is an open-source relational database management system.
   - **Answer:** `True`

1. **Question:** (True/False) PostgreSQL uses `MySQL` as its default query language.
   - **Answer:** `False`

1. **Question:** (True/False) PostgreSQL can handle both SQL and JSON queries.
   - **Answer:** `True`

1. **Question:** What command is used to connect to a PostgreSQL database from the command line?
   - **Answer:** `psql`

1. **Question:** What flag allows you to specify the database name when connecting using `psql`?
   - **Answer:** `-d`

1. **Question:** What command lists all databases in PostgreSQL?
   - **Answer:** `\l` or `\list`

1. **Question:** What command lists all tables in the current PostgreSQL database?
   - **Answer:** `\dt`

1. **Question:** How do you create a new database named `testdb` in PostgreSQL?
   - **Answer:** `CREATE DATABASE testdb;`

1. **Question:** How do you delete a database named `testdb` in PostgreSQL?
   - **Answer:** `DROP DATABASE testdb;`

1. **Question:** What command creates a new user named `dbuser` with a password `password123`?
   - **Answer:** `CREATE USER dbuser WITH PASSWORD 'password123';`

1. **Question:** What command grants all privileges on a database named `testdb` to user `dbuser`?
   - **Answer:** `GRANT ALL PRIVILEGES ON DATABASE testdb TO dbuser;`

1. **Question:** What command revokes all privileges on `testdb` from `dbuser`?
   - **Answer:** `REVOKE ALL PRIVILEGES ON DATABASE testdb FROM dbuser;`

1. **Question:** What command starts the PostgreSQL service on a Linux system? Assume you are not the root user.
   - **Answer:** `sudo systemctl start postgresql`

1. **Question:** What command stops the PostgreSQL service? Assume you are not the root user.
   - **Answer:** `sudo systemctl stop postgresql`

1. **Question:** What command checks the status of the PostgreSQL service? Assume you are not the root user.
   - **Answer:** `sudo systemctl status postgresql`
