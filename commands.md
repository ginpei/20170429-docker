# Docker Commands and References

Don't forget to check official documents. :)

## Docker Compose

### General

You have to run these commands in a directory in which your `docker-compose.yml` is.

### `docker-compose up`

Starts containers. `C-c` to stop. Since it sometimes fails, you may need to run `docker-compose stop` by yourself.

### `docker-compose up -d`

Starts containers in background. `docker-compose stop` to stop.

### `docker-compose stop`

Stop containers.

### `docker-compose logs`

Show logs when docker is running in background.

## Docker Container

### `docker ps`

Show running container information.

### `docker stop <container_name_or_id>`

Stop container(s).

### `docker ps -a`

Show all container information.

### `docker rm \`docker ps -aq\``

Remove all stopped containers.

## Docker Volume

### `docker volume ls`

Show volume information.

### `docker volume prune`

Remove volumes which are not linked to any containers. You may run this after `docker rm`.

## `docker-compose.yml`

### `version`

Version. It should be `"3"` or `"2.1"` now.

### `services`

Define containers.

### `build`

Specify `Dockerfils` directory. (Not file itsself.)

### `command`

Command which runs when

### `volumes`

Volumes.

### `ports`

Posts to expose to outside.

### `export`

Posts to expose to inside docker network.

### `depends_on`

Wait for the other containers.

## Reverse Lookup

### When you modified Dockerfile but container doesn't change

```bash
$ docker-compose build
$ docker-compose up
```

Or

```bash
$ docker-compose up --build
```

### Complained something about port

When you see an error message like following;

```
ERROR: for www  Cannot start service www: driver failed programming external connectivity on endpoint xxx_www_1 (xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx): Bind for 0.0.0.0:80 failed: port is already allocated
ERROR: Encountered errors while bringing up the project.
```

It means there is a container which is using the port. You needs to stop it before start the new one.

### Stop All Containers

```bash
$ docker stop `docker ps -q`
```

### Remove All Containers

```bash
$ docker stop `docker ps -q`
$ docker rm `docker ps -qa`
```

### Remove All Docker Volumes

After removing all containers;

```bash
$ docker volume prune
```
