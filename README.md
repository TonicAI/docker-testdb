# Using Docker to Manage Your Test Database(s)

This repository contains a starter example for how to use Docker to create and package a test
environment for your team using PostgreSQL or MySQL. Using these scripts, it's as simple as dumping
a starter database using the below commands, and placing them in the respective sql/ directory for
each database. You'll see that we've done this with a fake database that contains two tables with a
single foreign key between them.

The general workflow is as follows:
1. Dump your database using the appropriate command for your database, and place the SQL files in
   the sql directory for your database.
2. Run `build.sh` to build your docker container.
3. Use `docker-compose up -d` to run your container.

By default the name of the image is testdb_postgres or testdb_mysql. If you want to change the name
of your image, edit the image name in both `build.sh` (for building it) and `docker-compose.yml`
(for starting, stopping, etc. the service that uses the image).

Once the build looks good to you, you can always use a `docker push` to push it to a remote
repository, and modify your `docker-compose.yml` file to use the repository's image so that you
always can pull the latest version. From there, it's just distributing the `docker-compose.yml`
file to your teammates and servers for distribution.

## Dumping Your Database

## PostgreSQL

* [PostgreSQL docs on pg_dump](https://www.postgresql.org/docs/12/app-pgdump.html)

```bash
# Copying your schema
pg_dump -U user -s -f 1_schema.sql test_data;

# Copying your data
pg_dump -U user -a -f 2_data.sql test_data;
```

## MySQL

* [MySQL docs on mysqldump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)

```bash
# Copying your schema
mysqldump -p -d -r 1_schema.sql -B test_data;

# Copying your data
mysqldump -p -nt -r 2_data.sql -B test_data;
```
