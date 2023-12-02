# Podman Notes

Podman is a daemon-less, open-source, Linux-native tool designed to make it easy to find, run, build, share, and deploy applications using OCI(Open Container Initiative) containers and container images.

## Installing podman

```
apt install podman
```

## Registry settings

## Image commands

### Search for a registry

```
podman search <containser_registry/image_name>
```

### Download an image from a registry

```
podman pull <image_name>
```

### List pulled images

```
podman images
```

## Container commands

### Create and run a new container from an image

-it: tells podman to allocate a virtual terminal session within the container.
--rm: To remove the container after use, considered best practice

```
podman run -it --rm <image_name>
```

### Show all container currently running

```
podman ps
``` 

## Show all containers

```
podman ps -a
```

### Start a container

```
podman start <container_name>
```

### Stop a container

```
podman stop <continer_name>
```

### Remove the container

```
podman rm <container_name>
```

### Remove the container image

```
podman rmi <container_image>
```

### Display low-level information

```
podman inspect <container_name>
```

### List all ports for the container

```
podman port <container_name>
```

## Example

### Building a postgress container

Creating a postgres container instance and connecting with a pgadmin instance

Pull images:

```
podman pull docker.io/library/postgres
podman pull docker.io/dpage/pgadmin4
```

Create and run postgres container

```
podman run -p <runningport>:5432 --name <container name> -e POSTGRES_PASSWORD=<password> -e POSTGRES_DB=<database name> postgres
```

```
podman run -p 8000:5432 --name pg -e POSTGRES_PASSWORD=pasword123 -e POSTGRES_DB=users postgres
```

Create and run pgadmin container

```
podman run -p <runningport>:80 --name <container name> -e PGADMIN_DEFAULT_EMAIL=<email> -e PGADMIN_DEFAULT_PASSWORD=<password> dpage/pgadmin4
```

```
podman run -p 8001:80 --name pgadmin -e PGADMIN_DEFAULT_EMAIL="londa@gmail.com" -e PGADMIN_DEFAULT_PASSWORD=password123 dpage/pgadmin4
```

Then log onto pg admin by visiting: localhost:8001/, connect the database to check that everythin is fully operational

## Building a Container Image

Images are made by creating a dockerfile.The DockerFile being a script that contain instructions on how to build a container image.

### Commands

Build a container image using the Dockerfile in the current working directory.
The '-t' flag specifies the name of the image.

```
podman build -t <image_name>
```

Run a container with the built image

```
podman run --name <container_name> -p 8080:8080 <image_name>:<tag>
```

### Example

Building a node script runner

...To be continued
