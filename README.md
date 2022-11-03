# ProyectoApache

## Imágenes necesarias

Para nuestro contenedor de un servidor **Apache** con soporte de **PHP** debemos acudir a la documentación de docker donde se nos ofrece dicho contenedor de [Servidor Apache + PHP](https://hub.docker.com/_/php/).

## Configuración Docker-compose

En este caso para levantar el servicio utilizaremos el fichero de [```docker-compose.yml```](https://github.com/ndiazdossantos/proyectoApache/blob/master/docker-compose.yml) donde en el indicaremos:

* **Services**

Donde indicamos el:

- Nombre de nuestro servicio:

```
services:
  apache:
```
- Añadimos el nombre de nuestro contenedor ```container_name```:

```
services:
  apache:
    container_name: apachePHP
```
- La imagen del contenedor a usar  ```image``` incluyendo su versión:

```
services:
  apache:
    container_name: apachePHP
    image: php:7.2-apache
```
- Los puertos en este caso TPC y UDP con el parámetro ```ports```:

```
services:
  apache:
    container_name: apachePHP
    image: php:7.2-apache
    ports:
      - 80:80/udp
      - 80:80/tcp
```

## Creación de sitios

Para levantar las diferentes páginas html/php debemos crear un nuevo o nuevos directorios para los sitios, para este primer sitio únicamente creamos uno denominado [**Sitio1**](https://github.com/ndiazdossantos/proyectoApache/tree/master/sitio1).

En dicho directorio añadimos un [**Hola Mundo**](https://github.com/ndiazdossantos/proyectoApache/blob/master/sitio1/index.php) en PHP para realizar la prueba.

## Mapeo directorio sitios

Para mapear nuestro sitio para utilizarlo en el servidor de Apache, debemos especificarlo en el [```docker-compose.yml```](https://github.com/ndiazdossantos/proyectoApache/blob/master/docker-compose.yml) en el apatardo de ```volumes: ```, indicando que nuestro directorio [**Sitio1**](https://github.com/ndiazdossantos/proyectoApache/tree/master/sitio1) se corresponde con el ```/var/www/html``` de Apache.

```
services:
  apache:
    container_name: apachePHP
    image: php:7.2-apache
    ports:
      - 80:80/udp
      - 80:80/tcp
    volumes:
      - /home/noe/proyectoApache/sitio1:/var/www/html
```

De esta manera si levantamos el servicio ejecutando en el terminal ```docker-compose up``` podremos visualizar desde nuestro buscador el  [**localhost**](http://localhost/) con el [**Hola Mundo**](https://github.com/ndiazdossantos/proyectoApache/blob/master/sitio1/index.php) que hemos indicado previamente.


_![GIF](https://github.com/ndiazdossantos/proyectoApache/blob/master/pictures/mOFSQJB.gif)_


[README.md](README.md) de Noé Díaz Dos Santos para el repositorio [Proyecto Apache](https://github.com/ndiazdossantos/proyectoApache)
