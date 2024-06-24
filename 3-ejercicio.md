## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio3.PNG)

### Crear red net-wp
# docker network create net-wp

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (a) es (/var/lib/mysql)
Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# Inicialmente está vacía, pero una vez que se ejecuta el contenedor de MySQL, esta carpeta se llenará con los archivos de datos de MySQL

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
docker run -d --name mysql-container --network net-wp -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=mydatabase -e MYSQL_USER=jrmth -e MYSQL_PASSWORD=root -v /path/to/ejercicio3/db:/var/lib/mysql mysql:8

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# Ahora contiene los archivos de la base de datos MySQL

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta contenedor (b) es (/var/www/html)
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# docker run -d --name wordpress-container --network net-wp -e WORDPRESS_DB_HOST=mysql-container:3306 -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=root -e WORDPRESS_DB_NAME=mydatabase -v C:\Users\jorma\OneDrive\Documentos\GitHub\2024A-ISWD633-Practica3\ejercicio3\www:/var/www/html -p 9500:80 wordpress:latest

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# La personalización anterior se ha guardado, puesto que se guarda en host la parte del contenedor que se ha guardado como parte de volumen 



