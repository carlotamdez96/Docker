# Almacenamiento Docker

> Carlota Menéndez Álvarez   Despliegue 2º Evaluación



[TOC]



## Volúmenes docker



 ### Ejercicio 1

Crea un volumen docker que se llame miweb.

 `docker volume create miweb`

![image-20230120093911527](imagenes/image-20230120093911527.png)



### Ejercicio 2

Crea un contenedor desde la imagen php:7.4-apache donde montes en el directorio/var/www/html (que sabemos que es el DocumentRoot del servidor que nos ofrece esaimagen) el volumen docker que has creado.

 ![image-20230120094238365](imagenes/image-20230120094238365.png)

Este volumen que he creado tendrá el siguiente directorio:

![image-20230120094316511](imagenes/image-20230120094316511.png)



### Ejercicio 3

Utiliza el comando docker cp para copiar un fichero index.html en el directorio/var/www/html.

 ![image-20230120094925064](imagenes/image-20230120094925064.png)



### Ejercicio 4

Accede al contenedor desde el navegador para ver la información ofrecida por el ficheroindex.html.

Con el comando `docker inspect cVol` cojo la Ip de ese contenedor y desde el navegador accedo en esa ruta al index copiado.

![image-20230120095605602](imagenes/image-20230120095605602.png)



 

### Ejercicio 5

Borra el contenedor

 ![image-20230120095651192](imagenes/image-20230120095651192.png)



### Ejercicio 6

Crea un nuevo contenedor y monta el mismo volumen como en el ejercicio anterior.

 ![image-20230120095830319](imagenes/image-20230120095830319.png)



### Ejercicio 7

Accede al contenedor desde el navegador para ver la información ofrecida por el ficheroindex.html. ¿Seguía existiendo ese fichero?

 La información sigue existiendo por que es persistente:

![image-20230120095950290](imagenes/image-20230120095950290.png)







## Bind Mount

### Ejercicio 1

Crea un directorio en tu host y dentro crea un fichero index.html.

![image-20230120091145038](imagenes/image-20230120091145038.png)



![image-20230120091221860](imagenes/image-20230120091221860.png)

### Ejercicio 2

Crea un contenedor desde la imagen php:7.4-apache donde montes en el directorio/var/www/html el directorio que has creado por medio de bind mount.

![image-20230120092027245](imagenes/image-20230120092027245.png)



### Ejercicio 3

Accede al contenedor desde el navegador para ver la información ofrecida por el ficheroindex.html.

![image-20230120092719213](imagenes/image-20230120092719213.png)





### Ejercicio 4

Modifica el contenido del fichero index.html en tu host y comprueba que al refrescar la página ofrecida por el contenedor, el contenido ha cambiado.

Realizo los cambios:

![image-20230120092829060](imagenes/image-20230120092829060.png)

Compruebo que han cambiado:

![image-20230120092858677](imagenes/image-20230120092858677.png)



### Ejercicio 5 

Borra el contenedor

Primero hay que parar el contenedor, para luego borrarlo

![image-20230120093029076](imagenes/image-20230120093029076.png)



### Ejercicio 6

Crea un nuevo contenedor y monta el mismo directorio como en el ejercicio anterior.

![image-20230120093151839](imagenes/image-20230120093151839.png)



### Ejercicio 7

Accede al contenedor desde el navegador para ver la información ofrecida por el ficheroindex.html. ¿Se sigue viendo el mismo contenido?

![image-20230120093236658](imagenes/image-20230120093236658.png)

Sigue viéndose el mismo contenido.