FROM mysql:8

# The base MySQL image will run all SQL files in this directory. For more
# information, see "Initializing a fresh instance" at
# https://hub.docker.com/_/mysql/
COPY sql/*.sql /docker-entrypoint-initdb.d/

# OPTIONAL: Loading from CSVs for data import
# If you wish to use data stored in CSV/TSV format to populate your database,
# you can tar each of your files together and use the Docker ADD command to add
# them to your image.
#
# Docker will unpack the archive due to the semantics of the ADD command.
# You can then use the MySQL LOAD command in a SQL script to load from a
# file into a table, such as:
#
# LOAD DATA INFILE # '/var/lib/mysql-files/events.tsv' INTO TABLE public.events;
#
# Also consider adding --secure-file-priv=/var/lib/mysql-files/ to your command
# arguments in your docker-compose file.
#
# ADD data/tsvs.tar.gz /var/lib/mysql-files/


# OPTIONAL: Additional Configuration
# If you want to have additional MySQL config, here's a good way to set it.
# COPY additional.cnf /etc/mysql/conf.d/additional.cnf
# RUN chmod 0444 /etc/mysql/conf.d/additional.cnf
