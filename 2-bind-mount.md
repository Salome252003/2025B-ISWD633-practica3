# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
# COMPLETAR CON EL COMANDO

docker run -d --name contenedor-nginx -p 8080:80 -v "C:\Users\prisc\OneDrive\Escritorio\nginx\html:/usr/share/nginx/html" nginx:alpine

### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

Al ingresar al servidor Nginx mediante el comando docker exec -it contenedor-nginx sh se accede al sistema de archivos interno del contenedor y también se puede navegar y comprobar si está sirviendo 

### ¿Qué pasa con el archivo index.html del contenedor?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

El bind-mount sobrescribe (oculta) el contenido por defecto del contenedor. El index.html queda oculto mientras el volumen está montado y Nginx sirve el index.html que está en la carpeta del host

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html

### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

Al navegar dentro del servidor nginx se observan los archivos del sitio montados desde el host

<img width="866" height="297" alt="image" src="https://github.com/user-attachments/assets/bb94a5b6-e4e5-4e7e-a36d-bebf81fe7fa0" />


### Eliminar el contenedor
# COMPLETAR CON EL COMANDO

docker rm -f contenedor-nginx

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

Al crear nuevamente un contenedor montado al mismo directorio se puede observar que todos los archivos del sitio web permanecen intactos dentro de la carpeta del host


