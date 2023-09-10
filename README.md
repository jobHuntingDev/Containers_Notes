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
