# Use the official MySQL image as the base image
FROM mysql:8.0.33
LABEL "Project"="vprofile"
LABEL "Author"="Nisal"

# These values can be taken from the application.properties file in the application codebase. We are setting these values as environment variables in the Dockerfile so that they can be used by the MySQL server when it starts up. The MYSQL_ROOT_PASSWORD variable sets the password for the root user, and the MYSQL_DATABASE variable specifies the name of the database to be created when the container is initialized.
ENV MYSQL_ROOT_PASSWORD="vprodbpass"
ENV MYSQL_DATABASE="accounts"

# Adding the sql file that needs to be run at the startup into the initialization directory (docker-entrypoint-initdb.d/) as mentioned in the documentation
ADD db_backup.sql docker-entrypoint-initdb.d/db_backup.sql


