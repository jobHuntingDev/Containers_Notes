# Working with containers

## Install Podman

```bash
sudo apt-get -y install podman
```

## Working with podman

**Download/Pull an image**

```
podman pull ghcr.io/rwxrob/ws-skilstak
```

**Create a podman machine:**

```
podman machine init
```

**Start the podman machine:**

```
podman machine start
```

**List podman machines:**

```
podman machine list
```

**View all your images:**

```
podman images
```

**Creating the container**

```
podman run -it --hostname host_name --name container_name -v shared://shared ws-skilstak
```

**Run the container:**

```
podman start -a container_name
```

## Building a postgress container

Creating a postgres container instance and connecting with a pgadmin instance

Pull images:

```bash
podman pull docker.io/library/postgres
podman pull docker.io/dpage/pgadmin4
```

Create and run postgres container

```bash
podman run -p <runningport>:5432 --name <container name> -e POSTGRES_PASSWORD=<password> postgres
```

```bash
podman run -p 8000:5432 --name pg -e POSTGRES_PASSWORD=pasword123 postgres
```

Create and run pgadmin container

```bash
podman run -p <runningport>:80 --name <container name> -e PGADMIN_DEFAULT_EMAIL=<email> -e PGADMIN_DEFAULT_PASSWORD=<password> dpage/pgadmin4
```

```bash
podman run -p 8001:80 --name pgadmin -e PGADMIN_DEFAULT_EMAIL="londa@gmail.com" -e PGADMIN_DEFAULT_PASSWORD=password123 dpage/pgadmin4
```

Then log onto pg admin by visiting: localhost:8001/, connect the database to check that everythin is fully operational
