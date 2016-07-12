# docker-keycloak-sqlserver

[![Build Status](https://secure.travis-ci.org/stocksoftware/docker-keycloak-sqlserver.png?branch=master)](http://travis-ci.org/stocksoftware/docker-keycloak-sqlserver)

Extends the Keycloak docker image to use SQL Server.

## Creating admin account

By default there is no admin user created so you won't be able to login to the admin console. You can create an
account on an already running container by running:

    docker exec <CONTAINER> keycloak/bin/add-user-keycloak.sh -u <USERNAME> -p <PASSWORD>

Then restarting the container:

    docker restart <CONTAINER>

## Usage

### Environment variables

When starting the Keycloak instance you can pass a number of environment variables to configure how it connects to SQL Server. For example:

    docker run --name keycloak -e KEYCLOAK_LOGLEVEL=DEBUG -e MSSQL_DATABASE=keycloak -e MSSQL_USER=keycloak -e MSSQL_PASSWORD=password jboss/keycloak-postgres


#### KEYCLOAK_LOGLEVEL

The keycloak log level. Use `DEBUG` to get detailed logging.

#### MSSQL_HOST

Specify name of SQL Server host. (Required, no default).

#### MSSQL_PORT

Specify name of SQL Server host. (optional, default is `1433`).

#### MSSQL_DATABASE

Specify name of SQL Server database (optional, default is `keycloak`).

#### MSSQL_USER

Specify user for SQL Server database (optional, default is `keycloak`).

#### MSSQL_PASSWORD

Specify password for SQL Server database (optional, default is `keycloak`).
