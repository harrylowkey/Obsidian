#Docker 

2 ways to persist volume:
- volume (it's most used. Currently esg projects use this way except lumen one)
- bind mounts

## Volumes

- **Functionality:** Volumes are managed by the container runtime and provide a way to store and share data between containers or between containers and the host machine. They are created and managed independently of the container's lifecycle.

- **Implementation:** Volumes are typically stored within a **container runtime-managed** directory on the **host machine**. They can be managed by the container orchestration platform and have a separate lifecycle from the container itself.

- **Persistence:** Volumes have a higher level of persistence as they continue to exist even if the container that created them stops or is removed. This makes them suitable for long-term storage needs.

- **Data Management:** Volumes can be easily managed and manipulated using container orchestration tools. They can be created, deleted, backed up, and restored independently of the container.

- **Use Cases:** Volumes are commonly used for storing application data, databases, configuration files, or any other data that needs to persist across container restarts or even when containers are recreated.

### How

1. Create a volume by using the `docker volume create` command.

```
$ docker volume create todo-db
```

2. Stop and remove the todo app container once again with `docker rm -f <id>`, as it is still running without using the persistent volume.

3. Start the todo app container, but add the `--mount` option to specify a volume mount. Give the volume a name, and mount it to `/etc/todos` in the container, which captures all files created at the path. In your Mac or Linux terminal, or in Windows Command Prompt or PowerShell, run the following command:

```bash
$ docker run -dp 127.0.0.1:3000:3000 --mount type=volume,src=todo-db,target=/etc/todos getting-started
```

```base
# docker-compose.yaml
volumes:
  - <volume_name>:
      <optional_configuration>

volumes:
  - my-volume:
      driver: local
```

## Bind mounts

- **Functionality:** Bind mounts allow you to directly mount a file or directory from the **host machine** into **the container**. They provide a way to share data between the host and container without the need for copying or managing it separately.

- **Implementation:** Bind mounts are essentially a reference to a file or directory on the host machine. They are mounted directly into the container's file system and are not managed by the container runtime.

- **Persistence:** Bind mounts rely on the underlying file system of the host machine. If the file or directory being mounted is modified or removed, those changes will be reflected within the container immediately.
- **Data Management:** Bind mounts do not have their own lifecycle management. Any management or manipulation of the data in bind mounts must be done externally, directly on the host machine.

- **Use Cases:** Bind mounts are often used for development or debugging purposes, where you want to access source code or log files from the container on the host machine. They are also useful when you need to provide configuration files or other resources to a container without modifying its image.

- Example:
```bash
volumes:
- <host_path>:<container_path>
  exp_1: /var/lib/docker/db-data:var/lib/docker
  exp_2 db-data:var/lib-docker # db-data is a volume name

- docker run -it --mount type=bind,src="$(pwd)",target=/src ubuntu bash

version: "3.3"
services:
  app:
    build: .
    volumes:
      - type: bind
        source: .
        target: /usr/app
    ports:
      - 2009:2009
    networks:
      - webnet
```


## Comparison

|               | Volume                                               | Bind mounts                                                                                                            |
| ------------- | ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| location      | on host                                              | on host                                                                                                                |
| stored        | within a container runtime-managed directory on host | reference to a file or directory on the host machine                                                                   |
| managed by    | container's life cycle                               | not managed by the container runtime, rely on underlying system on host                                                |
| accessibility | can not access                                       | if the file or directory being mounted is modified or removed, changes will be reflected within the container directly |