# Docker-Notes
Easy place to keep my docker notes.

## Secrets

From command line:

    Note: Don't forget the dash at end of command.  It tells docker to read in from standard input.

`echo "blah..." | docker secret create psql-pw -`

    For file based secrets in development:

```
docker-compose up -d
docker-compose exec psql cat /run/secrets/psql_user
```

```
Example of docker-compose for Postgres using secrets:

version: "3.1"

services:
  psql:
    image: postgres
    secrets:
      - psql_user
      - psql_password
    environment:
      POSTGRES_PASSWORD_FILE: /run/secrets/psql_password
      POSTGRES_USER_FILE: /run/secrets/psql_user

secrets:
  psql_user:
    file: ./psql_user.txt
  psql_password:
    file: ./psql_password.txt
```





