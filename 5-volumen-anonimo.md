## VOLUMEN ANÓNIMO
Un volumen anónimo es un volumen gestionado por Docker, el volumen se crea automáticamente sin un nombre específico cuando ejecutas un contenedor. Son útiles cuando deseas almacenar datos temporalmente sin preocuparte por el nombre del volumen. Docker asigna un identificador único en lugar de un nombre. Se utilizan principalmente para almacenamiento temporal. 
**Considerar**
Los datos persisten mientras el contenedor exista, pero son más difíciles de gestionar y referenciar después.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta contenedor> <nombre imagen>
```
ó
```
docker run -d --name <nombre contenedor> --mount type=volume,target=<ruta carpeta contenedor> <nombre_imagen>
```
destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.

Para el ejemplo con gninx

```
docker run -d --name server-nginx --mount type=volume,target=/var/cache/nginx nginx:alpine
```

### Para eliminar el contenedor y el volumen
```
docker rm -fv server-nginx
```
_esta instrucción elimina el volumen si éste es de tipo anónimo_
<img width="599" height="49" alt="image" src="https://github.com/user-attachments/assets/4bc832f2-5749-4fc1-a66c-2df05f29e365" />


# Eliminar todos los volúmenes anónimos (dangling volumes) no utilizados
Los dangling volumes son volúmenes en Docker que no están asociados a ningún contenedor en ejecución. Estos volúmenes se crean cuando se monta un volumen en un contenedor y luego se elimina ese contenedor sin eliminar explícitamente el volumen.
```
docker volume prune
```
<img width="971" height="120" alt="image" src="https://github.com/user-attachments/assets/2b297813-c6f8-400e-8d69-7521905eaafe" />

