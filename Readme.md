## 💻 Getting started

### Requirements

- [Node.js](https://nodejs.org/en/)
- [Yarn](https://classic.yarnpkg.com/) or [npm](https://www.npmjs.com/)
- One instance of [PostgreSQL](https://www.postgresql.org/)

> Obs.: I recommend use docker

**Clone the project and access the folder**

```bash
$ git clone https://github.com/luiscostalafc/test-matrix-server.git && cd test-matrix-server
```

**Follow the steps below**

```bash
# Install the dependencies
$ yarn

# Make a copy of '.env.example' to '.env'
# and set with YOUR environment variables.
# The aws variables do not need to be filled for dev environment
$ cp .env.example .env

# Create the instance of postgreSQL using docker
$ docker run --name matrix-postgres -e POSTGRES_USER=matrix \
              -e POSTGRES_DB=matrix -e POSTGRES_PASSWORD=matrix \
              -p 5432:5432 -d postgres

# Create the instance of mongoDB using docker
$ docker run --name matrix-mongodb -p 27017:27017 -d -t mongo

# Create the instance of redis using docker
$ docker run --name matrix-redis -p 6379:6379 -d -t redis:alpine

# Once the services are running, run the migrations
$ yarn typeorm migration:run

# To finish, run the api service
$ yarn dev:server

# Well done, project is started!
