# Podman CMD
## _lista de comandos para podman_
### list of commands for podman

## First container

corre un contenedor y abre una conexion interactiva con proceso.

runs a container and opens an interactive connection with the process.
```sh
podman run -it --name myfedora fedora /bin/sh
```

con esta secuencia, volveremos a nuestro indicador de shell mientras el contenedor sigue ejecutándose.

with this sequence, we will return to our shell prompt while the container continues to run.
```sh
CTRL + p  y CTRL + q
```

vuelve a adjuntar el contenedor en ejecucion a -tty "emulador de terminal".

re-attach the running container to -tty "terminal emulator".
```sh
podman attach 685a339917e7
```

podemos ver el mapeo de puertos del contenedor por su id.

we can see the port mapping of the container by its id.
```sh
podman port 685a339917e7
```
---

## Gestión imágenes de contenedores
### Managing container images

lista solo imagenes oficiales de nginx.

list only official nginx images.
```sh
podman search nginx --filter=is-official
```

lista las imagenes oficiales de nginx en formato tabla.

lists official nginx images in table format.
```sh
podman search nginx --filter=is-official \
--format "table {{.Index}} {{.Name}} {{.Description}} {{.Official}}"
```

lista todas la imagenes de postgres con sus etiquetas.

list all postgres images with their tags.
```sh
podman search postgres --list-tags
```

extraemos una imagen oficial con una version especifica.

we extract an official image with a specific version.
```sh
podman pull docker.io/library/alpine:2.7
```

retorna un JSON con la informacion de la imagen

returns a JSON with the image information
```sh
podman image inspect name-img:tag | jq
```

elimina todas las imagenes por su id

deletes all images by their id
```sh
podman rmi $(podman images -qa)
```

elimina todas las images que estan sin uso

deletes all images that are not in use
```sh
podman image prune -af
```

---
## Operaciones con contenedores en funcionamiento
### Operations with running containers

ejecutamos un contenedor de nginx.

we run a nginx container.
```sh
podman run -d --name server -p 8080:80 nginx:1-alpine
```

hacemos un request al puerto 8080 donde el contenedor escucha 

we make a request to port 8080 where the container listens
```sh
curl localhost:8080
```

detenemos la ejecucion del proceso por su ID o Nombre

stop the process execution by its ID or Name
```sh
podman stop server
```

lista los contenedores en ejecucion.

list the running containers.
```sh
podman ps
```

lista todos los contenedores en ejecucion y detenidos

list all running and stopped containers.
```sh
podman ps -a
```

reanuda la ejecucion del contenedor detenido por su ID o nombre

restart the execution of the stopped container by its ID or Name

```sh
podman start server
```

reinicia un contenedor en ejecucion con un nuevo ID de proceso (Pid)

restart a running container with a new process ID (Pid)
```sh
podman restart dd8c532ab377
```

elimina todos los contenedores sin ejecucion

deletes all containers without execution
```sh
podman container prune
```

detalles sobre los namespace clonados de los contenedores en ejecución

details about the cloned namespaces of the running containers
```sh
podman ps --namespace
```

---
```sh
```
**Free Software, Hell Yeah!**

