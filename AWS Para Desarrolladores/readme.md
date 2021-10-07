# Curso de AWS Para Desarrolladores

## IAM - Gestión de usuarios y grupos

Es el servicio que nos permite gestionar el acceso e idenidad de usuarios a AWS

### Grupos

Permite crear diferentes grupos de usuarios con las diferentes politicas o permisos asociados. Por Ejemplo

- Grupo de GroupAdministrador - Politica o Permisos - AdminstratorAccess.
- Grupo de GroupDDBB - Politica o Permisos - DatabaseAdministrator.
- Grupo de GroupS3 - Politica o Permisos - AmazonS3FullAccess

### Usuarios

Permite crear diferentes usuarios para acceder a la consolo de AWS o SSH.

Para crear un usuario se definen Información de usuairio > Permisos o Politicas(Grupos) > Etiquetas opcionales.

### Roles

Son los permisos que se le da a un servicio para que pueda utilizar otro servivio de AWS.

### Politicas

Son los permisos o politica personalizados.

### Contraseñas

Nos permite establecer la configuracion de las contraseña de los usuarios a traves del Servicio de IAM > Configuración de cuenta > Politica de contraseña

### Acceso multifactor

Nos permite activar MFA verificaciones en dos pasos

## AWS S3

Es el serivicio de almacenamiento simple. (Simple Storage Service).

**Caracteristicas importantes**

- Es el servicio de almacenamiento de objecto (ficheros de cualquier tipo)
- Maximo 5TB de peso
- Los ficheros de almacenan en Buckets (Carpetas) y estos Buckets deben ser unicos
- Permite encriptación de ficheros

**Información fichero**

- **Clave:** nombre del fichero
- **Valor:** datos del fichero
- **Versión ID:** número de versión
- **Metadatos:** Información extra
- **Control de acceso:** Especifica permisos de como se utiliza y quienes

**Tipos de almacenamiento** (Existen 4 tipos)

1. **S3 estandar:** Disponiblidad al 100% de los ficheros, se almacenan de forma redundante en multiples dispositivos e intancias.

2. **S3 IA (Acceso infrecuente):** Los datos no son accedidos de forma frecuente, pero se necesitan un rapido accesos cuando son necesarios. Es mas baratos que **S3 estandar**

3. **S3 On Zone IA:** Los ficheros con poca frecuencia y que solo se almacenan es una zona geografica. Es más barato que **S3 IA**

4. **Glacier:** Es el almacenamiento más barato y se utiliza para archivar datos de larga duración. Y el tiempo de recuperación puede llegar a pasar hasta 5 a 6 horas para obtenerlos.

### S3 - Encriptación

Hay 4 métodos de encriptación de objectos de S3.

1. **SSE-S3:** Son claves gestionadas por S3 mismo (AES-256)
2. **SSE-KMS:** Utiliza KMS (Servicio de gestión de claves)
3. **SSE-C:** El cliente maneja las claves de encriptación
4. **Encriptción del lado del cliente:** El cliente ya envia los datos encriptados a AWS S3
