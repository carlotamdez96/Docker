# Docker

> Carlota Menéndez Álvarez    2º Evaluación Despliegue

[TOC]

## Ejercicios de Repaso

#### Ejercicio 1



Instala Docker en una máquina y configúralo para que se pueda usar con un usuario sin privilegios.

La máquina virtual inicialmente ya disponia de Docker. En el caso de no tener Docker instalado sería:

```sh 
apt install docker.io
```

Y el comando para utilizar Docker sin privilegios:

```sh
usermod -aG docker user
```



#### Ejercicio 2

Ejecuta un contenedor a partir de la imagen `hello-word`. Comprueba que nos devuelve la salida adecuada. Comprueba que no se está ejecutando. Lista los contenedores que están parado. Borra el contenedor.

Ejecuto el contenedor:

![image-20230118095945365](imagenes/image-20230118095945365.png)



Compruebo que no se esta ejecutando:

![image-20230118100027668](imagenes/image-20230118100027668.png)

Listo los contenedores que están parado:

![image-20230118100042234](imagenes/image-20230118100042234.png)

Borrar contenedor:

`docker rm mi_prueba`

![image-20230118100059041](imagenes/image-20230118100059041.png)





#### Ejercicio 3

 Crea un contenedor interactivo desde una imagen debian. Instala un paquete (por ejemplo `nano`). Sal de la terminal, ¿sigue el contenedor corriendo? ¿Por qué?. Vuelve a iniciar el contenedor y accede de nuevo a él de forma interactiva. ¿Sigue instalado el `nano`?. Sal del contenedor, y bórralo. Crea un nuevo contenedor interactivo desde la misma imagen. ¿Tiene el `nano` instalado?



a) Creación del contenedor Interactivo:

![image-20230118100113183](imagenes/image-20230118100113183.png)



b) Instalación de un paquete

Para realizar la instalación de un paquete como nano, será necesario hacer un `apt update` y una vez hecho esto, nos dejará instalar el paquete con el comando:

`apt install nano`

![image-20230118100124866](imagenes/image-20230118100124866.png)



c) Sal de la terminal, ¿sigue el contenedor corriendo? ¿Por qué?.

![image-20230118100135892](imagenes/image-20230118100135892.png)

No sigue corriendo el contenedor, porque se cerró y no está en segundo plano



d) Vuelve a iniciar el contenedor y accede de nuevo a él de forma interactiva. ¿Sigue instalado el `nano`?

Utilizo el comando `docker start -i debian1` , para iniciar el contenedor

![image-20230118100147504](imagenes/image-20230118100147504.png)

Como se ve en la imagen anterior, sigue estando instalado el paquete nano.



e) Sal del contenedor, y bórralo. Crea un nuevo contenedor interactivo desde la misma imagen. ¿Tiene el `nano` instalado?

![image-20230118100159878](imagenes/image-20230118100159878.png)

No tiene instalado el paquete nano.

#### Ejercicio 4

Crea un contenedor demonio con un servidor nginx, usando la imagen oficial de nginx. Al crear el contenedor, ¿has tenido que indicar algún comando para que lo ejecute? Accede al navegador web y comprueba que el servidor esta funcionando. Muestra los logs del contenedor.



Es importante saber que para correr un contenedor en segundo plano osea demonio, debe tener **-d**  a continuación de run.

![image-20230118100211387](imagenes/image-20230118100211387.png)



Comprobación:

![image-20230118100223281](imagenes/image-20230118100223281.png)

Con el comando `docker logs nginx1` podré ver los logs de ese contenedor

![image-20230118100235058](imagenes/image-20230118100235058.png)

#### Ejercicio 5

Crea un contenedor con la aplicación Nextcloud, mirando la documentación en docker Hub,para personalizar el nombre de la base de datos sqlite que va a utilizar.

El comando a utilizar será: 

```sh
docker run -d -p 8080:80 --name nextCloud -e SQLITE_DATABASE=myBase nextcloud
```

![image-20230118100249229](imagenes/image-20230118100249229.png)

### Referencias

https://hub.docker.com/_/nextcloud

https://www.digitalocean.com/community/tutorials