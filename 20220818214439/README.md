# PosgreSQL cheatsheet

## Installing PostgreSQL via docker

```bash
$ docker run --name psqldatabase -p 5432:5432 \
    -e POSTGRES_USER=postgres \
    -e POSTGRES_PASSWORD=postgresPW \
    -e POSTGRES_DB=postgresDB \
    -d \
    postgres:latest
```

## PSQL cheatsheet

```bash
# General information/configuration about PQSL
$ ps -ef | grep postgres # verify the db is running
$ sudo find /tmp/ -name .s.PGSQL.5432 # find if the service is running
$ vi /var/lib/postgresql/data/postgresql.conf # configuration files
$ vi /var/lib/postgresql/data/pg_hba.conf # configuration files
$ /usr/lib/postgresql/11/bin/pg_ctl reload # to reload
# If error appears change to postgres user
$ su postgres -c "/usr/lib/postgresql/11/bin/pg_ctl -D /var/lib/postgresql/11/main reload"

# Connect to PSQL
$ psql postgresql://postgresUser:postgresPW@localhost:5455/postgresDB # connect to db remotely
$ psql -U postgresUser -d postgresDB # connect to db locally
$ psql -h localhost -p 5432 -U postgresUser -d postgresDB # connect to db locally

# Inside PSQL
psql$ \password "<user>" # change the password
psql$ \l # information
psql$ \q # quit
psql$ select pg_reload_config(); # reload configuration
psql$ SHOW password_encryption; # show type of encryption

```
