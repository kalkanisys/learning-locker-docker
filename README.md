# Learning Locker v2

Start learning locker v2 project with docker and docker-compose.

## Prerequisites

- Docker <https://docs.docker.com/engine/install/>
- Taskfile <https://taskfile.dev/>

## Development

### Setup

Setup is first time process when you are configuring project first time.

- If you are asked to change any think in default.env then create new .env file and
  add those new env variables to override from default.env. Else start with next steps

- Create .env.learninglocker and .env.xapi file

```bash
cp .env.learninglocker.example .env.learninglocker
cp .env.xapi.example .env.xapi
```

- Build project containers

```bash
task dev:build
```

- Start containers

```bash
task dev:up
```

- Run database migrations

```bash
task run -- yarn migrate
```

- Create site admin user

```bash
task run -- node cli/dist/server createSiteAdmin <email> <organisation> <password>
# Example:
task run -- node cli/dist/server createSiteAdmin admin@example.org admin Admin@123456
```

- Stop containers

```bash
task dev:down
```

### Start project

- Start project

```bash
# If you want to build containers again and then start project
task dev:up -- --build

# Or else don't want to build new since there are no new changes in containers
# docker files
task dev:up
# OR
task dev:start

# Both are same commands start is just alias for up here
```

### Stop project

- Stop project

```bash
task dev:down
# OR
task dev:stop
# Both are same commands stop is just alias for down here
```

- Stop project and delete database

```bash
# Beware this delete all database files
task clean
```

### Restart project

```bash
task restart
```
