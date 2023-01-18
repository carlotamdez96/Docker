# Docker Imágenes

> Carlota Menéndez Álvarez





## Ejercicio 1

Descarga las siguientes imágenes: `ubuntu 18.04`, `httpd`,` tomcat 9.0.39-jdk11` ,` jenkins/jenkins:lts, php 7.4-apache`

Comando: 

```sh
docker pull ubuntu:tag
```





Ubuntu:

![image-20230118102907398](imagenes/image-20230118102907398.png)



Apache:

![image-20230118103037451](imagenes/image-20230118103037451.png)

Tomcat:

![image-20230118103255816](imagenes/image-20230118103255816.png)

Jenkins:

![image-20230118135117868](imagenes/image-20230118135117868.png)

Php:

![image-20230118105539281](imagenes/image-20230118105539281.png)







## Ejercicio 2

Muestra todas las imágenes que tienes descargadas:

![image-20230118105630161](imagenes/image-20230118105630161.png)



## Ejercicio 3

Crea un contenedor demonio con la imagen php:7.4-apache

Comando: 

```sh
docker run -d --name contenedor1 php:7.4-apache
```



![image-20230118105914660](imagenes/image-20230118105914660.png)



## Ejercicio 4

Comprueba el tamaño del contenedor en el disco duro

```sh
docker ps -a -s
```



![image-20230118110221548](imagenes/image-20230118110221548.png)



## Ejercicio 5

Con la instrucción `docker cp` podemos copiar ficheros desde un contenedor. Crea un fichero en tu ordenador con el siguiente contenido:

```sh
<?php
	echo phpinfo();
?>
```

Copia un fichero `info.php` al directorio `var/www/html`del contenedor con docker cp.



Primero creo el documento:

![image-20230118110706225](imagenes/image-20230118110706225.png)

A continuación copio ese fichero al contenedor dentro de la ruta especificada anteriormente:

![image-20230118110925055](imagenes/image-20230118110925055.png)

## Ejercicio 6

Vuelve a comprobar el espacio ocupado por el contenedor

![image-20230118111133859](../../../AppData/Roaming/Typora/typora-user-images/image-20230118111133859.png)

Ha aumentado.



## Ejercicio 7



![image-20230118121945839](imagenes/image-20230118121945839.png)

