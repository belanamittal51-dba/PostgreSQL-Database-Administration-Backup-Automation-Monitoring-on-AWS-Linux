# PostgreSQL Database Administration, Backup Automation & Monitoring on AWS Linux

## Project Overview

This project demonstrates practical PostgreSQL Database Administration (DBA) skills in an AWS Linux environment. It focuses on database installation, configuration, security, user and role management, backup and recovery, performance monitoring, and automated database backups using Linux shell scripting.

The project uses AWS EC2 to host PostgreSQL and AWS S3 for secure backup storage.

## Project Objectives

- Install and configure PostgreSQL on an AWS EC2 Linux server.
- Create and manage databases, tables, users, and roles.
- Implement database security and access control.
- Perform manual database backups using pg_dump.
- Restore databases using pg_restore.
- Automate database backups using Bash scripts and cron jobs.
- Upload PostgreSQL backups to AWS S3.
- Monitor database connections, locks, and performance.
- Practice database troubleshooting and recovery procedures.

## Technologies Used

**Database:** PostgreSQL, SQL  
**Operating System:** Linux  
**Cloud Platform:** AWS EC2, AWS S3  
**Scripting:** Bash Shell Scripting  
**Automation:** Cron Jobs  
**Database Tools:** psql, pg_dump, pg_restore, DBeaver  
**Version Control:** Git and GitHub

## Project Workflow

1. Configure an AWS EC2 Linux server.
2. Install and configure PostgreSQL.
3. Create an employee management database.
4. Configure database users, roles, and permissions.
5. Perform manual database backups.
6. Develop an automated backup shell script.
7. Schedule backups using cron.
8. Upload backup files to AWS S3.
9. Monitor database activity and performance.
10. Test database restoration and verify data integrity.

## Expected Outcomes

This project aims to demonstrate foundational PostgreSQL DBA skills, Linux server administration, database backup automation, AWS cloud integration, database monitoring, and troubleshooting.

## Career Relevance

This hands-on project is designed for freshers preparing for PostgreSQL DBA, Junior Database Administrator, Linux Administrator, and Database Support Engineer roles.


## Questions That I Have Solved In This Project:-
# PostgreSQL DBA Fresher Project – 20 Interview Questions and Answers

**Project Name:** PostgreSQL Database Administration, Backup Automation & Monitoring on AWS Linux

These 20 questions are based on your project and will help you prepare for **PostgreSQL DBA fresher interviews, project presentations, and practical exams**.

## Part 1: Project and PostgreSQL Basics

### 1. What is the objective of your PostgreSQL DBA project?
**Answer:** The main objective is to install, configure, manage, secure, monitor, and back up a PostgreSQL database on a Linux server using AWS EC2.

### 2. Which technologies are used in your project?
**Answer:** PostgreSQL, Linux, SQL, AWS EC2, AWS S3, Bash scripting, cron, DBeaver, pg_dump, and pg_restore.

### 3. What is PostgreSQL?
**Answer:** PostgreSQL is an open-source relational database management system (RDBMS) used to store, manage, and retrieve data securely.

### 4. How do you check the PostgreSQL version?
**Answer:**

```bash
psql --version
```

To check the PostgreSQL server version:

```sql
SELECT version();
```

### 5. How do you check whether PostgreSQL is running on Linux?
**Answer:**

```bash
sudo systemctl status postgresql
```

The service name may differ depending on the PostgreSQL installation.

---

## Part 2: Database Management

### 6. How do you create a database in PostgreSQL?
**Answer:**

```sql
CREATE DATABASE companydb;
```

### 7. How do you list all databases?
**Answer:**

```sql
\l
```

### 8. How do you connect to a particular database?
**Answer:**

```sql
\c companydb
```

### 9. How do you create a table in PostgreSQL?
**Answer:**

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(100),
    salary NUMERIC(10,2)
);
```

### 10. How do you check the size of a PostgreSQL database?
**Answer:**

```sql
SELECT pg_size_pretty(
    pg_database_size('companydb')
);
```

---

## Part 3: User and Role Management

### 11. What is the difference between a user and a role in PostgreSQL?
**Answer:** PostgreSQL uses roles for access management. A user is essentially a role with the `LOGIN` privilege, while roles without `LOGIN` can be used to group permissions.

### 12. How do you create a PostgreSQL user?
**Answer:**

```sql
CREATE USER developer WITH PASSWORD 'StrongPassword123!';
```

Use a unique, securely managed password in real environments.

### 13. How do you grant database access to a user?
**Answer:**

```sql
GRANT CONNECT ON DATABASE companydb TO developer;
```

This allows the user to connect, but additional schema and table permissions may be required.

### 14. How do you list PostgreSQL users and roles?
**Answer:**

```sql
\du
```

---

## Part 4: Backup and Recovery

### 15. What is the difference between pg_dump and pg_restore?
**Answer:**

- **pg_dump:** Creates a logical backup of a PostgreSQL database.
- **pg_restore:** Restores backups created in formats such as custom, directory, or tar.

### 16. How do you take a manual PostgreSQL backup?
**Answer:**

```bash
pg_dump -U postgres -d companydb -Fc -f companydb.dump
```

This creates a custom-format backup.

### 17. How do you restore a PostgreSQL database?
**Answer:**

First, create a new database:

```bash
createdb -U postgres companydb_restore
```

Restore the backup:

```bash
pg_restore -U postgres -d companydb_restore companydb.dump
```

---

## Part 5: Linux, AWS and Automation

### 18. What is the purpose of AWS EC2 and S3 in your project?
**Answer:**

**AWS EC2:** Hosts the Linux server and PostgreSQL database.

**AWS S3:** Stores database backup files outside the EC2 instance for improved data protection.

### 19. What is a cron job, and how is it used in PostgreSQL backup automation?
**Answer:** Cron is a Linux scheduling service that executes commands or scripts automatically at specified times.

Example:

```bash
*/5 * * * * /home/ec2-user/backup.sh
```

This runs the backup script every five minutes.

### 20. How do you monitor active PostgreSQL connections?
**Answer:**

```sql
SELECT
    pid,
    usename,
    datname,
    state,
    query
FROM pg_stat_activity;
```

This query helps a DBA monitor database sessions and troubleshoot activity.

