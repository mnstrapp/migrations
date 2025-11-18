# Migrations

A central repository for all database migrations for the backend of MNSTR.

## Requirements

- [PostgreSQL](https://www.postgresql.org/)
- [Direnv](https://direnv.net/)
- [SQLX CLI](https://crates.io/crates/sqlx-cli)

## Setting up the database locally

Create the role and a database for your Postgres instance. Here's the sql:

```
CREATE ROLE <db username> WITH LOGIN SUPERUSER PASSWORD <db password>;
CREATE DATABASE <db name>;
```
### Environment variables

Environment variables are controlled via Direnv. You can either:

- Copy the example file
- Create one from scratch

#### Copy example

Copy the `.envrc_example` like this:

```
cd <project directory>
cp .envrc_example .envrc
```

Edit the values to match the previous created values. For example:

```
export DATABASE_URL=postgresql://username:password@localhost:5432/mnstr
```

Allow direnv access to the file:

```
direnv allow .
```

#### Create one from scratch

Create a `.envrc` and add:

```
export DATABASE_URL=postgresql://<db username>:<db password>@<db host>:<db port>/<db name>
```

Edit the values to match the previous created values. For example:

```
export DATABASE_URL=postgresql://username:password@localhost:5432/mnstr
```

Allow direnv access to the file:

```
direnv allow .
```

## Migrating the database

In the terminal run:

```
cd <project directory>
sqlx migrate run
```