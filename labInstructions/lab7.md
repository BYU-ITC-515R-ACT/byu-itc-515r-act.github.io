# Lab 7: Database Servers

## Introduction

In this lab, you will configure and secure a PostgreSQL database. Your goal is to set up the database, implement access controls, enforce security policies, and manage backups while ensuring the system remains functional and protected.  

### Configuration Instructions

#### Virtual Machines and Operating Systems
You will be working with:  
  - 1 Ubuntu 20.04 Machine

#### Network Configuration
Since your machines do not currently have internet access, you will need to configure the network as follows:  

1. **`Lab-7-database` Machine**:  
    - WAN (`ens18` interface):  
        - IP: `172.18.<ID>.14/16`  
        - Gateway: `172.18.0.1`  
        - DNS: `172.18.0.1`  

#### **Accessing the Virtual Machines**  
- The VMs can be accessed through your **Proxmox** instance.  
- To monitor your progress, visit: <a href="http://172.18.0.3/lab/7" target="_blank">scoreboard</a>.

#### Scoreboard Key
- **Green arrows** indicate that everything is working as intended.
- **Orange exclamation marks** indicate that something is partially working.
- **Red down arrows** indicate that something is not working.

You can hover over each specific arrow, and a tooltip will appear with a hint on what is wrong or not working.

#### **Credentials**  
- All VMs have the same login credentials:  
  - **Username**: `blueteam`  
  - **Password**: `abc123`  

#### **File Creation and Content**  
- If a referenced file does not exist, you must create it.  
- For any questions requiring files to contain specific content, use the `Lab-7-database` machine.  

## Pass Criteria

### P1: Database Installation and Setup

1. Log into postgres using the `postgres` account. Enter the line `login:<command>` into `/home/blueteam/P1/P1.txt`
1. Set the password for the `postgres` user to be `unwell-easter-broadly` in the db.
1. Create a database called `etechacademy`
1. Switch to use the `etechacademy` database
1. Import the file `/home/blueteam/database.sql` into the `etechacademy` database.
1. Exit the database.

### P2: Database User Management 

1. Create a backup user with the `superuser` role, name the user `admin` and set the password to `stream-regroup-childhood`.
1. Create another user called `website` with the password `labored-contend-probation` and allow it to only `SELECT`, `UPDATE`, `DELETE` and `INSERT` permissions on the `etechacademy` database.
 - In order for this step to score, these users must be able to log in to the database
 - *Additional Note*: you don't need this to score this step, but you will need to grant usage and insert on sequences to score on P4 (you can test it with and without in trying to insert into the table and you'll see why). We'll leave the implementation of this to you.

### P3: Database Security

1. Force all local users except the `blackteam` user to use their password when logging into the database from the machine
  - You do not need to add or remove any lines from the config file. Modify the existing lines.
1. Stop the `postgres` user from logging into the database by locking/disabling the account.
1. Make sure you restart the service to have the changes take effect
1. Remove any unnecessary or malicious users and databases.
1. Allow remote connections to the database.

### P4: Database Hardening

1. Restrict the `website` user to only login from `172.18.0.3`.
1. No other user should be able to login remotely.

## Merit Criteria

### M1: Database Security

To complete `M1` `P1-P4` must have a green arrow before starting.

1. The database currently uses MD5 for it's password hashing. Change it to use `scram-sha-256`.
  - Make the change permanent
1. You will need to also change all the user's passwords to use the new hashing algorithm.
  - Use the same passwords for the accounts when changing them.
  - The accounts to update are `admin`, `postgres` and `website`

### M2: Database Backup and Recovery

- Backup the `etechacademy` database to the directory `/backups/`
  - Call the file `backup.sql`
  - Don't use any special formatting or include blobs
  - When you look at the file you should see a list of SQL queries.
- Enter the command you would use to restore the backup into the file `/home/blueteam/M2/M2.txt` as `restore:<command>`
  - Use the `admin` user
  - Use an a full apsolute filepath

### M3: Database Monitoring and Logging 

1. Enable logging for Postgres with the following specifications
  - Logging should be enabled
  - Connections and disconnections should be logged
  - Log all SQL statements executed by clients
  - Minimum error should be set to error
  - Log all SQL queries that take more than 200ms

### M4 Troubleshooting
To complete `M4` `P1-P4` and `M1-M3` must have a green arrow before starting.
 
- The database is having issues, find and fix them.
- The criteria for a working database are:
  - The Postgres service is running
  - You can connect locally with DB users and remotely with any users that need it
  - The database should maintain its integrity
  - Database users have the correct permissions


### Distinction Criteria

### D1: Database Hardening

- Using UFW and the system logs block any malicious traffic to the machine.
  - Ensure that all of your deny rules are first
  - Traffic should be blocked from the IP(s) to anywhere and for both TCP and UDP in one rule per IP
  - After all the deny rules you should have a default allow for `SSH` and `Postgres` 

## Submission

You don't need to submit anything for this lab. All of the above criteria will be auto-graded unless stated otherwise. Once you have finished the lab you will have to do a verbal pass off with a TA.

## Pass Off Questions

You will be asked two of these questions at random during your verbal pass-off. 

1. What is a relational database?  
1. What does SQL stand for, and what is it used for?
1. How do you create a new database in PostgreSQL?  
1. What is the purpose of a primary key in a table?  
1. How do you list all databases in PostgreSQL using the `psql` command-line tool?  
1. What is a foreign key, and why is it important?  
1. What command would you use to update a user’s password in a PostgreSQL table?  
1. How do you create a new user in PostgreSQL with a password?  
1. How can you back up a PostgreSQL database? Provide the command.  
1. Why is role-based access control important in PostgreSQL security?  
1. What is the purpose of the `listen_addresses` directive?

### Grading

- **Pass**: All Pass criteria and verbal pass-off has been completed.
- **Merit:** All **Pass** and **Merit** criteria completed.
- **Distinction:** All **Pass**, **Merit**, and **Distinction** criteria completed.


