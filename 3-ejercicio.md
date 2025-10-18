## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO

docker network create --driver bridge --subnet 172.21.0.0/16 net-wp

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es **(/var/lib/mysql)**

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

La carpeta db se encuentra vacía

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO

docker run -d --name contenedor-mysql --network net-wp -e MYSQL_ROOT_PASSWORD=admin123 -e MYSQL_DATABASE=info -e MYSQL_USER=priscila -e MYSQL_PASSWORD=salome123 -v ./ejercicio3/db:/var/lib/mysql mysql:8

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

Los archivos de datos, el catálogo interno de MySQL y los logs internos y archivos de configuración del motor de almacenamiento 

<img width="882" height="772" alt="image" src="https://github.com/user-attachments/assets/fb3ffa0d-e39b-4593-9e4f-72367a2f3272" />


### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es **(/var/www/html)**

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO

docker run -d --name contenedor-wordpress --network net-wp -e WORDPRESS_DB_HOST=contenedor-mysql -e WORDPRESS_DB_USER=priscila -e WORDPRESS_DB_PASSWORD=salome123 -e WORDPRESS_DB_NAME=info -v ./ejercicio3/www:/var/www/html -p 9500:80 wordpress


### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA 

Al eliminar y volver a crear el contenedor WordPress y volver a iniciar en la página web se conserva la información y la configuración
