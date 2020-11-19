FROM postgres:12

# OPTIONAL: PostGIS Installation
# RUN apt-get update -y
# RUN apt-get install curl ca-certificates -y
# RUN curl https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
# RUN apt-get install postgis postgresql-12-postgis-scripts -y

# The base Postgres image will run all SQL files in this directory. For more
# information, see "Initialization scripts" at
# https://hub.docker.com/_/postgres/
COPY sql/*.sql /docker-entrypoint-initdb.d/

# OPTIONAL: Loading from CSVs for data import.
# If you wish to use data stored in CSV/TSV format to populate your database,
# you can tar each of your files together and use the Docker ADD command to add
# them to your image.
#
# Docker will unpack the archive due to the semantics of the ADD command.
# You can then use the Postgres COPY command in a SQL script to load from a
# file into a table, such as: COPY cohorts FROM '/standard_data/users.tsv';
#
# ADD data.tar.gz /standard_data
