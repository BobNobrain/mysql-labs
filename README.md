# sqlabs

Environment for doing sql labs. Includes:
- script to initialize a container with mysql;
- script to run a command promt in this container;
- scripts for filling database with data (creating tables and records).

## Creating Container

_NB: you need [docker](http://docker.com) for using this environment_

_NB: don't forget to `chmod +x` for scripts_

```bash
. create
```

This command will create a docker container named `sqlab` with latest mysql server inside.

## Running SQL Promt

```bash
. run
```

This will run a SQL command promt in your terminal. It assumes that `sqlab` container was already created before.
This container is stopped and started automatically inside the script.

## Filling Database

`./files` directory containes needed scripts and is mounted into container as `/files`.
To test that all is mounted correctly, type:

```sql
source /files/test.sql
```

It should print that 2*2 == 4.

To create database, then tables and then records type:

```sql
create database lab;
use lab;
source /files/tables.sql
source /files/dump.sql
# test that everything is ok:
select * from P;
```

Type `exit` to exit sql command promt, stop `sqlab` container and than exit the `run` script.
