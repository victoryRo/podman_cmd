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

---
```sh
```
**Free Software, Hell Yeah!**

