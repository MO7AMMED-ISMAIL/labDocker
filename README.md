##############################################################################################
# ITI - Docker Lab2 🐋

## Task 1:
Run a container using nginx image, and mount a directory from your host into the 
Docker container. example: /home/samy/nginx:/home/nginx (bind mount)
```bash
docker run -d -p 80:80 -v /usr/share/nginx/html nginx
```
---

## Task 2:
### Steps
#### 1. Create 2 docker network (net-1 & net-2)
```bash
    docker network create netone
    docker network create nettow
```
#### 2. Run 2 new containers using nginx:alpine image, and attach the net-1 to them
```bash
    docker run -d --name nginx1 --network=netone nginx:alpine
    docker run -d --name nginx2 --network=net-1 nginx:alpine
```
#### 3.  Run another 1 new containers using nginx:alpine image, and attach the net-2 to them
```bash
    docker run -d --name nginx3 --network=nettow nginx:alpine
```
#### 4. Inspect the 3 containers to know their IPs and write them aside
```bash
    docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nginx1
    docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nginx2
    docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nginx3

```
#### 5. Enter a container in the net-1 network and try to ping a container in the net-2 
network (What do you notice?)
```bash

```
#### 6. Enter a container in the net-1 network and try to ping the other container in the 
same network (What do you notice?)
```bash
    docker exec -it nginx1 sh
    ping 127.2.0.1
```
---
## Task 3: Explain the difference between Docker volumes and Bind Mount.
```bash
Docker Volumes:
    Volumes exist independently of the container's lifecycle. They persist even if the container is removed.
Bind Mounts:
    hey allow you to mount a directory or file from the host machine into the container
```

