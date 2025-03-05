# Database.learn

![database managements system architecture](/assets/images/database-management-architecture.png)

[installation](https://www.postgresql.org/download/macosx/)
[official documentation](https://www.postgresql.org/docs/current/index.html)

SQL = Structured Query Language

## Postgresql basics

https://www.postgresql.org/docs/current/tutorial-start.html
### architectural fundamental
PostgreSQL uses a client/server model. A PostgreSQL session consists of the following cooperating processes (programs):

A server process, which manages the database files, accepts connections to the database from client applications, and performs database actions on behalf of the clients. The database server program is called postgres.

The user's client (frontend) application that wants to perform database operations. Client applications can be very diverse in nature: a client could be a text-oriented tool, a graphical application, a web server that accesses the database to display web pages, or a specialized database maintenance tool. Some client applications are supplied with the PostgreSQL distribution; most are developed by users.
The PostgreSQL server can handle multiple concurrent connections from clients. To achieve this it starts (“forks”) a new process for each connection. From that point on, the client and the new server process communicate without intervention by the original postgres process. Thus, the supervisor server process is always running, waiting for client connections, whereas client and associated server processes come and go.

### Basic commands
1. find location of the server directory
for brew installed default:- /opt/homebrew/var/postgresql@14
```sh
brew info postgresql
```
if postgres is running
```sh
psql -c "SHOW data_directory;"

```
2. start the server
brew installed 
```sh 
brew services start postgresql
```
use pg_ctl
```sh
pg_ctl -D /opt/homebrew/var/postgresql@14 start
```
3. checking status of the server
```sh
brew services list 
```
```sh
pg_ctl -D  /opt/homebrew/var/postgresql@14 status
```
3. create and drop db
```sh
createdb name_of_db
```
```sh
drop name_of_db
```
4. connecting to the server using psql
```sh
psql mydb
```
if you see the  'mydb=#' # means you are super user and 'mysql=>' means other user.
5. version
In postgres interactive shell
```sh
SELECT version();
```
6. The psql program has a number of internal commands that are not SQL commands. They begin with the backslash character, “\”. For example, you can get help on the syntax of various PostgreSQL SQL commands by typing:
```sh
\h
```
To get out of psql, type:
```sh
\q
```
about internal commands
```sh
\? 
```

### starting the tutorial
1. get the tutorial directory from the source folder of postgres /src/tutorial cd to tutorial
```sh
make
```
2. create my db and connect to postgres server using postgres interactive console
```sh
createdb mydb
psql -s mydb
```
3. start interactive setion
```sh
mydb=> \i basics.sql
```
The \i command reads in commands from the specified file. psql's -s option puts you in single step mode which pauses before sending each statement to the server. The commands used in this section are in the file basics.sql.

## SQL Command Types

### DDL: Data Definition Language

Define admissible database content (schema)

- Define relations with their schemata
- What columns and column types?
- Define constraints restricting admissible content
- Constraints on single relations
- Constraints linking multiple relations

### DML: Data Manipulation Language

### Change and retrieve database content

### TCL: Transaction Control Language

### Groups SQL commands (transactions)

### DCL: Data Control Language

### Assign data access rights```
