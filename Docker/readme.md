# Docker

## Imagenes

Las imagenes son las plantillas donde definimos la configuracion que tendra nuestros contenedores.

Existen las imagenes oficiales, donde las podemos descargar desde el docker hub.

> docker pull mysql

### Dockerfile

Es el archivo donde definimos toda la configuración.

```
#Definimos la imagen o SO a utilizar

FROM centos:7

#Acciones a ejecutar en la consola

RUN yum install httpd -y

#Copia archivos desde nuestra maquina al contenedor

COPY . .

#Igual que COPY pero con la salvedad que con ADD podemos utilizar URL (Se recomienda en lo posible utilizar COPY)

ADD

#Definir variables de entorno

ENV key value

#Especifica el espacio de trabajo dentro del contenedor

WORKDIR /var/www/html

#Exponer los puertos del contenedor al host

EXPOSE 80

#Definir metadata al la Imagen

LABEL

#Agregar usuarios para ejecutar acciones

USER

#Prsistencia de la data a traves de los volumenes

VOLUME

#Ejecución de comando que mantiene activo el contrenedor

CMD

```

### Consideraciones Buenas Practicas

- **Efimeros** Facilmente de destruir y recrear
- Definir un solo servicio
- **Build context** Hacer uso el .dockerignore o en su defecto mantener siempre el contexto donde se construye la imagen solo los archivos necesarios
- Definir pocas capas
- Hacer uso del multi-liner \
- No instalar paquetes inecesarios
- En lo posible hacer uso de la metadata, para dar más información de la imagen.

### Algunos Comandos

- Construir imagen a partir del Dockerfile

  > docker build -t **[name:tag]**

- Enlista las imagenes por coincidencia

  > docker images | grep **[id or name]**

- Eliminar imagenes

  > docker rmi **[id or name]**

- Construir imagen sin Dockerfile default

  > docker build -t **[name:tag]** -f **[file]**

---

## Contenedores

Son instancias de ejecución de una imagen.

### Caracteristicas

- Son temporales
- La capa de ejecución es RW
- Se pueden crear multiples contenedores a partir de una misma imagen

### Algunos comandos

- Listar contenedores

  > docker ps

- Listar contenedores incluso terminados

  > docker ps -a

- Renombar contenedor

  > docker rename **[before_name]** **[new_name]**

- Detener un contenedor sin eliminarlo

  > docker stop **[id or name]**

- Iniciar un contenedor existente

  > docker start **[id or name]**

- Reiniciar un contenedor

  > docker restart **[id or name]**

- Entrar a un contenedor

  > docker exec -u root -it **[id or name]** bash | sh

- Ejecutar comando sin entrar al contenedor

  > docker exec **[id or name]** bash -c "cat /var"

- Eliminar contenedores

  ```
  > docker rm -f [id or name]

  > docker ps -aq | xargs docker rm -f

  > docker rm -f $(docker ps -aq)

  ```

- Definir variables de entorno

  > docker run -d -e "key=value" **[image_name]**

- Definir nombre al iniciar un contenedor

  > docker run -d --name **[container_name]** **[image_name]**

- Visualizar estadistica de contenedor

  > docker stats **[id or name]**

- Inspeccionar contenedor

  > docker inspet **[id or name]**

- Mostrar log de contenedor

  > docker logs **[id or name]**

- Definir memoria maxima de uso del contenedor

  > docker run -d -m "500mb" **[image_name]**

- Copiar archivos de host al contenedor y viseversa

  > docker cp file.txt **[id or name]:ruta**

- Convertir un contenedor a una imagen (No es buena practica)

  > docker commit **[id or name]** **[name_image_result]**

- Detener contenedor automaticamente

  > docker run --rm -it **[image_name]** bash

---

## Volumes

Nos permiten alamcenar la data de nuestros contenedores al host o nuestra maquina. Es decir la persitencia de los datos.

Existen tres tipos de volumenes

1. **Host:**

La data se persiste en la maquina ejemplo

> docker run -d --name db -p 3306:3306 **-v /opt/my-mysql/:/var/lib/mysql** mysql

2. Anonymus

Docker se encarga de definir el nombre del folder y la ubicacion. (Esta opción no es recomendable)

> docker run -d --name db -p 3306:3306 **-v /var/lib/mysql** mysql

3. Named Volumes

Son la combinacion de volumenes de host y anonymus. Permiten crear volumenes en una ruta especifica gestionado por docker.

> docker volume create **[name]** > \
> docker run -d --name db -p 3306:3306 **-v [name]:/var/lib/mysql** mysql

### Algunos Comandos

- Crear un volume

  > docker volume create **[name]**

- Eliminar volumenes dangling

  > docker volume ls -f dangling=true -q | xargs docker volume rm

- Eliminar Volume

  > docker volume rm **[name]**

---

## Redes

La red por default de los contenedores es la Bridge

### Tipos de redes

- **Bridge:** red por default de Docker
- **Host:** red de maquina local
- **None:** sin redes- Especifica que el contenedor no tiene red asignada
- **Overlay**

### Conectar contenedores

### Algunos comandos

- Crear un red

  > docker network create **[name]** \
  > docker network create -d bridge --subnet --gateway **[name]**

- Inspecionar red

  > docker network inspect **[name]**

- Listar redes

  > docker network ls

- Agregar un contenedor a una red distinta default

  > docker run --network **[name]** -d **[image_name]**

- Conectar y desconectar contenedores en distintas redes

  > docker network connect **[name]** **[container_name]**

  > docker network disconnect **[name]** **[container_name]**

- Eliminar redes

  > docker network rm **[name]**

- Conectar un contenedor a una IP especifica

  > docker run --network **[name]** --ip **0.0.0.0** --name **[container_name]** **[image_name]**

  IMPORTANTE: Para poder definir una ip se debe crear un red anteriormente y tener al menos una **subnet** y **gateway** para que pueda funcionar.
