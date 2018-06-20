FROM bitnami/rails

USER root

RUN apt-get update -y

## Required for providing a javascript runtime, and selenium tests
RUN apt-get install -y vim wget libsqlite3-dev nodejs apt-transport-https libnss3 libxss1 libappindicator1 libindicator7

RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -

RUN sh -c 'echo "deb https://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'

RUN apt-get update -y && \
    apt-get install -y google-chrome-stable

# install the postgresql service + client libraries
RUN apt-get install -y postgresql libpq-dev

# allow access from any local client as `postgres` and `ispace_user` users
RUN echo  "local   all   postgres      trust\nlocal   all   ispace_user   trust" > /etc/postgresql/9.4/main/pg_hba.conf

# start the postgres service
RUN service postgresql restart && \
    psql -U postgres -c "CREATE ROLE ispace_user WITH LOGIN PASSWORD 'ispace_dev'" && \
    psql -U postgres -c "ALTER ROLE ispace_user CREATEDB" && \
    psql -U ispace_user -d postgres -c "CREATE DATABASE interstellar_space_dev"

