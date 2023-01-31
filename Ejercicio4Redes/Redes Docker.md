# Redes Docker



> Carlota Menéndez Álvarez



[TOC]



## Trabajar con redes Docker

### Ejercicio 1

Vamos a crear dos redes de ese tipo (BRIDGE) con los siguientes datos:
**Red1**
Nombre: red1
Dirección de red: 172.28.0.0
Máscara de red: 255.255.0.0
Gateway: 172.28.0.1
**Red2**
Nombre: red2
Es resto de los datos será proporcionados automáticamente por Docker.



*Creación de red1*

![image-20230125102109587](Imagenes/image-20230125102109587.png)

*Creación de red2*

![image-20230125102302221](Imagenes/image-20230125102302221.png)



### Ejercicio 2

 Poner en ejecución un contenedor de la imagen ubuntu:20.04 que tenga como hostname
host1 , como IP 172.28.0.10 y que esté conectado a la red1. Lo llamaremos u1 .



Comando: 

```sh
docker run -it --name contenedor1 --network red1 --ip 172.28.0.10 --hostname host1 ubuntu:20.04
```



![image-20230125103401372](Imagenes/image-20230125103401372.png)

*Comprobaciones*

![image-20230125103526310](Imagenes/image-20230125103526310.png)



### Ejercicio 3

Entrar en ese contenedor e instalar la aplicación ping ( apt update && apt install
inetutils-ping ).

*Instalación*

![image-20230125103708710](Imagenes/image-20230125103708710.png)



![image-20230125103802182](Imagenes/image-20230125103802182.png)





### Ejercicio 4

Poner en ejecución un contenedor de la imagen ubuntu:20.04 que tenga como hostname
host2 y que esté conectado a la red2. En este caso será docker el que le de una IP correspondiente
a esa red. Lo llamaremos u2 .

```sh
docker run -it --name u2 --network red2 --hostname host2 ubuntu:20.04
```



![image-20230125104149979](Imagenes/image-20230125104149979.png)

*Comprobación*

![image-20230125104229187](Imagenes/image-20230125104229187.png)



### Ejercicio 5

 Entrar en ese contenedor e instalar la aplicación ping ( apt update && apt install
inetutils-ping ).

*Instalación:*

![image-20230125104329517](Imagenes/image-20230125104329517.png)

![image-20230125104411270](Imagenes/image-20230125104411270.png)



**Comprobaciones**



Contenedor 1:

![image-20230125105703140](Imagenes/image-20230125105703140.png)

Contenedor 2:

![image-20230125110844629](Imagenes/image-20230125110844629.png)



Ping entre contenedores:

![image-20230125110107925](Imagenes/image-20230125110107925.png)

![image-20230125110149244](Imagenes/image-20230125110149244.png)



Cambio la red del contenedor1:

![image-20230125110503875](Imagenes/image-20230125110503875.png)

Ahora mismo estan en la misma red los dos contenedores,  y hago ping :

![image-20230125110944683](Imagenes/image-20230125110944683.png)

Se ven, pruebo haciendo Ping con el nombre del host

![image-20230125111038990](Imagenes/image-20230125111038990.png)











## Despliegue de Nextcloud + mariadb

### Ejercicio 1

Crea una red de tipo bridge.

```sh
docker network create redNueva
```



![image-20230131182914570](Imagenes/image-20230131182914570.png)

### Ejercicio 2

Crea el contenedor de la base de datos conectado a la ed que has creado. La base de datos se debe
configurar para crear una base de dato y un usuario. Además el contenedor debe utilizar
almacenamiento (volúmenes o bind mount) para guardar la información. Puedes seguir la
documentación de mariadb o la de PostgreSQL .

```shell
docker run -d --name contenedorMaria --network redNueva -v /opt/mysql_base1:/var/lib/mysql -e MYSQL_DATEBASE=b1 -e MYSQL_USER=usu1 -e MYSQL_PASSWORD=123456 -e MYSQL_ROOT_PASSWORD=123456  mariadb:10.5
```



![image-20230131183315699](Imagenes/image-20230131183315699.png)



### Ejercicio 3

A continuación, siguiendo la documentación de la imagen nextcloud , crea un contenedor conectado a
la misma red, e indica las variables adecuadas para que se configure de forma adecuada y realice la
conexión a la base de datos. El contenedor también debe ser persistente usando almacenamiento.

```sh
docker run -d -p 8081:80 --name contenedorMaria2 --network redNueva --link contenedorMaria -v nextcloud:/var/www/html nextcloud
```





<img src="../../../AppData/Roaming/Typora/typora-user-images/image-20230131183535040.png" alt="image-20230131183535040" style="zoom:100%;" />





### Ejercicio 4

Accede a la aplicación usando un navegador web.

<img src="Imagenes/image-20230131184255724.png" alt="image-20230131184255724" style="zoom:67%;" />

![image-20230131184410053](Imagenes/image-20230131184410053.png)





A tener en cuenta:

Id de todos los contenedores q tenga `docker ps -a -q`

`docker rm -f $(docker ps -a -q)` - Borra todos los contenedores existentes.

`docker start -i contenedor`

