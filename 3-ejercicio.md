## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker create network net-wp -d bridge
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/

Para la db 
Ruta carpeta host: .../ejercicio3/db

```
docker run -d --name mysql_wordpress --network net-wp -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=wordpressdb -e MYSQL_USER=alexis -e MYSQL_PASSWORD=password --mount type=bind,source=C:\Users\alexi\OneDrive\Documents\docker\mysql\ejercicio3\db,target=/var/lib/mysql mysql:8
```


### ¿Qué contiene la carpeta db del host?
Sin la configuracion del volumen complementado, no contiene nada. Sin embargo con el volumen ya configurado contiene lo que se presenta en la imagen que contiene en la carpeta del host que se encontraba vacia inicialment 

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Se presentan los siguientes archivos complementados en la siguiente imagen:

<img width="911" height="800" alt="image" src="https://github.com/user-attachments/assets/19cb9065-91cd-4c6c-9de3-763496296fd1" />

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)

```
docker run -d --name some-wordpress --network net-wp -p 9500:80 -e WORDPRESS_DB_HOST=mysql_wordpress:3306 -e WORDPRESS_DB_USER=alexis -e WORDPRESS_DB_PASSWORD=password -e WORDPRESS_DB_NAME=wordpressdb --mount type=bind,source=C:\Users\alexi\OneDrive\Documents\docker\wordpress\ejercicio3\www,target=/var/www/html wordpress
```

Dentro de la carpeta del host se presenta los siguientes ficheros de la imagen
<img width="780" height="804" alt="image" src="https://github.com/user-attachments/assets/548fb3e4-1792-4b1e-9b9c-2a6ee236a882" />


### Personalizar la apariencia de wordpress y agregar una entrada

Se previsualiza de esta manera dentro de wordpress
<img width="1830" height="865" alt="image" src="https://github.com/user-attachments/assets/c1570460-a323-493c-8697-b65f0a5e8829" />


### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Cargo el contenedor donde estaba, no se ha borrado informacion, siguio persistiendo a pesar de haber eliminado el contenedor con los mismos parametros configurados.

<img width="1836" height="844" alt="image" src="https://github.com/user-attachments/assets/e61b6546-e84f-4505-8e01-73e250ccda85" />


