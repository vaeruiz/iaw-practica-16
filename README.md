# Dockerizando un contenedor

Instalando una aplicación LAMP para dockerizar.

## Instalando docker y docker-compose

Para instalar ambas utilidades tenemos que ejecutar el siguiente comando:

>apt install docker docker-compose

Cuando se descargue, cada vez que las queramos utilizar deberá de ser con el comando sudo, para evitar esto, tenemos que meter al usuario en el grupo de usuarios de Docker, esto se hace con la siguiente instrucción:

>sudo usermod -aG docker $USER

Después de esto, tenemos que habilitar el servicio docker para que se arranque cada vez que iniciemos el sistema, para ello ejecutamos este comando:

>sudo systemctl enable docker

Ahora reiniciamos la máquina haciendo un reboot y podremos empezar a utilizar docker con total normalidad.

# Preparando archivos

Empezaremos creando el dockerfile, este archivo es el que define como será nuestro contenedor, en el repositorio se encontrará el dockerfile que he utilizado, cabe destacar que para que funcione deberemos meterlo dentro de una carpeta, en mi caso, he creado un directorio llamado apache en el que dentro he colocado el dockerfile.

Después crearemos el archivo yml para docker-compose, este archivo también se encontrará en el repositorio.

Hay que tener en cuenta que en la imagen mysql del yml deberemos de crear un volumen llamado ./sql:/docker-entrypoint-initdb.d ya que este volumen nos va a permitir hacer uso del sql creado para la aplicación web y guardar sus datos.

Como paso final, crearemos el archivo env que tendrá todas las variables del contenedor MySQL.

Después de esto podremos levantar nuestra infraestructura con:

>docker-compose up -d

# Retocando la aplicación web

Si entramos a la aplicación web y le pasamos datos, no se añadirán en la base de datos, en el repositorio dejaré el archivo sql que se deberá ejecutar en la base de datos para que la aplicación sea 100% funcional.
