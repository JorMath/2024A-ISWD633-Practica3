# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### Crear un volumen tipo host con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host: directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html esta ruta se obtiene al revisar la documentación
![Volúmenes](imagenes/volumen-host.PNG)
# docker run -d --name nginx -P -v C:\Users\jorma\OneDrive\Documentos\GitHub\2024A-ISWD633-Practica3\nginx\html:/usr/share/nginx/html nginx:alpine

### ¿Qué sucede al ingresar al servidor de nginx?
# El cliente no encuentra el recurso, tenemos un error 404

### ¿Qué pasa con el archivo index.html del contenedor?
# Al no haber un archivo index.html no lo encuentra por lo que no encuentra el recurso de inicio al iniciar un servidor web

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de nginx/html
### ¿Qué sucede al ingresar al servidor de nginx?
# El resultado sigue siendo el mismo puesto que el volumen anterior ya ha sido cargado al contenedor

### Eliminar el contenedor
# docker rm nginx

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
# Ahora si se ha pasado el template como volumen al nuevo contenedor, y se puede visualizar

### ¿Qué hace el comando pwd?
# Es un comando que lista los contenidos de un directorio específico, es parecido al comando ls en Linux
Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

