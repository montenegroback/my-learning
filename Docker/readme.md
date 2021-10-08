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
