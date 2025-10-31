# Notes

## Network Connections

> Creating a new network

```bash
docker network create <network_name_here>
```

> Running a container with a network

```bash
docker run -d --name <container_name_here> --network <network_name_here> <image_name_here>
```

## Commands

> Listing all networks

```bash
docker network ls
```

> Listing all networks with their IDs

docker network ls -q

> Listing all networks with their names

docker network ls -q --filter name=<name_here>

> Listing all networks with their IDs and names

docker network ls -q --filter name=<name_here>

> Listing all networks with their IDs and names

docker network ls --filter name=<name_here>

````

## Containers

> Listing all containers

```bash
docker container ls
```

> Listing all containers with their IDs

```bash
docker container ls -q
```

> Listing all containers with their names

```bash
docker container ls -q --filter name=<name_here>
```

> Listing all containers with their IDs and names

```bash
docker container ls -q --filter name=<name_here>
```

> Listing all containers with their IDs and names

```bash
docker container ls --filter name=<name_here>
```
````
