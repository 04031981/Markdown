# <p align="center"><span style="color:blue">`DOCKER`</span></p>
**Resumen:**
Proporciona información detallada sobre la instalación de Docker, incluyendo datos sobre contenedores, imágenes, volúmenes, red y configuración del sistema. Es útil para obtener una visión general del estado y la configuración de Docker en tu sistema..

   
```sql
   docker info
```
---
# <p align="center"><span style="color:green">_Recopilación de Comandos para Docker_</span></p>
#### <p align="center"><span style="color:red">_Fecha: [07/06/2024]_</span></p>

---


## **Tabla de contenido**



1. <span style="color:purple">[docker version](#docker-version)</span>
2. <span style="color:purple">[docker info](#docker-info)</span>
3. <span style="color:purple">[docker pull](#docker-pull)</span>
4. <span style="color:purple">[docker images](#docker-images)</span>
5. <span style="color:purple">[docker run](#docker-run)</span>
6. <span style="color:purple">[docker ps](#docker-ps)</span>
7. <span style="color:purple">[docker ps -a](#docker-ps--a)</span>
8. <span style="color:purple">[docker stop](#docker-stop)</span>
9. <span style="color:purple">[docker start](#docker-start)</span>
10. <span style="color:purple">[docker restart](#docker-restart)</span>
11. <span style="color:purple">[docker kill](#docker-kill)</span>
12. <span style="color:purple">[docker rm](#docker-rm)</span>
13. <span style="color:purple">[docker rmi](#docker-rmi)</span>
14. <span style="color:purple">[docker build](#docker-build)</span>
15. <span style="color:purple">[docker exec](#docker-exec)</span>
16. <span style="color:purple">[docker logs](#docker-logs)</span>
17. <span style="color:purple">[docker inspect](#docker-inspect)</span>
18. <span style="color:purple">[docker commit](#docker-commit)</span>
19. <span style="color:purple">[docker tag](#docker-tag)</span>
20. <span style="color:purple">[docker push](#docker-push)</span>
21. <span style="color:purple">[docker network ls](#docker-network-ls)</span>
22. <span style="color:purple">[docker network inspect](#docker-network-inspect)</span>
23. <span style="color:purple">[docker network create](#docker-network-create)</span>
24. <span style="color:purple">[docker network rm](#docker-network-rm)</span>
25. <span style="color:purple">[docker volume ls](#docker-volume-ls)</span>
26. <span style="color:purple">[docker volume inspect](#docker-volume-inspect)</span>
27. <span style="color:purple">[docker volume create](#docker-volume-create)</span>
28. <span style="color:purple">[docker volume rm](#docker-volume-rm)</span>
29. <span style="color:purple">[docker-compose up](#docker-compose-up)</span>
30. <span style="color:purple">[docker-compose down](#docker-compose-down)</span>
31. <span style="color:purple">[docker-compose ps](#docker-compose-ps)</span>
32. <span style="color:purple">[docker-compose logs](#docker-compose-logs)</span>
33. <span style="color:purple">[docker-compose build](#docker-compose-build)</span>
34. <span style="color:purple">[docker-compose exec](#docker-compose-exec)</span>

 <span style="color:purple">[Historial de Versiones](#historial-de-versiones)</span>
---



---
## Docker version

 <span style="color:purple">[Inicio](#tabla-de-contenido)</span>

1. **docker version:**
Muestra la versión de Docker instalada en tu máquina.

   
```sh
   docker version
```
## Docker Info

 <span style="color:purple">[Inicio](#tabla-de-contenido)</span>

2. **docker info:**
Proporciona información detallada sobre la instalación de Docker, incluyendo datos sobre contenedores, imágenes, volúmenes, red y configuración del sistema. Es útil para obtener una visión general del estado y la configuración de Docker en tu sistema..

   
```sql
   docker info
```
---
## Docker pull

 <span style="color:purple">[Inicio](#tabla-de-contenido)</span>

3. **docker pull:**
Descarga una imagen desde un repositorio (normalmente Docker Hub). Este comando se utiliza para obtener la última versión de una imagen de contenedor.

   
```sql
   docker pull
```
---

## Docker images

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

4. **docker images:**
Lista todas las imágenes descargadas en tu sistema. Proporciona información sobre las imágenes disponibles localmente, como el nombre, la etiqueta, el ID de la imagen, la fecha de creación y el tamaño.


```sql
docker images
```


---


## Docker run

<span style="color:purple">[Inicio](#tabla-de-contenido)</span> 


5. **docker run:**
Crea y ejecuta un contenedor a partir de una imagen. Puedes especificar parámetros como el mapeo de puertos, variables de entorno, volúmenes, entre otros. La opción -d ejecuta el contenedor en segundo plano (detached mode).


```sh
docker run -d -p 80:80 nombre_imagen

```
---



## Docker ps

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

6. **docker ps:**
Lista los contenedores en ejecución. Proporciona información sobre los contenedores activos, como el ID, la imagen, el comando, el tiempo de ejecución, los puertos expuestos y el nombre del contenedor.
```sh
   docker ps

```
---
## Docker ps -a

<span style="color:purple">[Inicio](#tabla-de-contenido)</span> 

7. **docker ps -a:**
Lista todos los contenedores, incluyendo los que no están en ejecución. Es útil para ver el historial de todos los contenedores creados en tu sistema.
```sh

   docker ps -a
```



---

## Docker stop

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

8. **docker stop:**

Detiene un contenedor en ejecución de manera ordenada. Envía una señal SIGTERM al contenedor y espera un tiempo predeterminado antes de forzar su detención con SIGKILL si no se ha detenido.

```sh
docker stop id_contenedor

```
En este ejemplo, se debe agregar el id del contenedor el cual se debe detener.

---
## Docker start

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

9. **docker start:**

Inicia un contenedor detenido. Este comando es útil para reanudar la ejecución de contenedores que han sido detenidos anteriormente.

```sql

docker start id_contenedor

```

En este ejemplo, se debe agregar el id del contenedor el cual se debe inicializar.

---
## Docker restart

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

10. **docker restart:**

Reinicia un contenedor. Primero detiene el contenedor y luego lo inicia nuevamente. Es útil para aplicar cambios de configuración o solucionar problemas sin crear un nuevo contenedor.  Ejemplo:

```sh
docker restart id_contenedor

```
---
## Docker kill

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

11. **docker kill:**

Detiene un contenedor de forma inmediata (forzada) enviando una señal SIGKILL, lo que no permite al contenedor realizar una parada ordenada. Por ejemplo:

```sh
docker kill id_contenedor

```
---

## Docker rm

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

12. **docker rm:**

Elimina un contenedor detenido. Este comando se utiliza para liberar recursos y limpiar contenedores no deseados. Por ejemplo:

```sh
docker rm id_contenedor

``` 
---

## Docker rmi

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

13. **docker rmi:**

Elimina una imagen de Docker de tu sistema. Es útil para liberar espacio y gestionar imágenes no deseadas.

```sh
docker rmi nombre_imagen:tag
```
---

## Docker build

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

14. **docker build:**

Construye una imagen a partir de un Dockerfile. Puedes especificar un nombre y una etiqueta para la imagen utilizando la opción -t . es muy importante el punto al final

```sh
docker build -t nombre_imagen .


```
-t nombre_imagen: Especifica el nombre y la etiqueta de la imagen que se va a construir.

.  : Especifica el contexto de compilación actual, donde se encuentra el Dockerfile y otros archivos necesarios.

## docker exec

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

15. **docker exec:**

Explicación: Permite ejecutar un comando dentro de un contenedor en ejecución. Por ejemplo:

-it: Permite interactuar con el contenedor mediante la entrada estándar.

nombre_contenedor: El nombre o ID del contenedor en el que se ejecutará el comando.

comando: El comando que se ejecutará dentro del contenedor.

```sh
docker exec -it nombre_contenedor comando

```


## docker logs

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

16. **docker logs:**

Explicación: Muestra los registros (logs) de un contenedor en tiempo real. Por ejemplo:

```sh
docker logs nombre_contenedor

```

nombre_contenedor: El nombre o ID del contenedor del que se desean ver los registros.

##   Docker inspect

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

17. **docker inspect:**

Proporciona información detallada sobre un contenedor, imagen, red o volumen de Docker. Por ejemplo:

nombre_objeto: El nombre o ID del contenedor, imagen, red o volumen del que se desea obtener información detallada.

```sh
docker inspect nombre_objeto
```
Esto garantiza que las dos actualizaciones se realicen correctamente o ninguna de ellas se realice.


## Docker commit

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


18. **docker commit:**
    Explicación: Crea una nueva imagen a partir de un contenedor en ejecución.
```sh
docker commit nombre_contenedor nombre_imagen

```
nombre_contenedor: El nombre o ID del contenedor del que se desea crear una nueva imagen.

nombre_imagen: El nombre y la etiqueta de la nueva imagen que se creará.

## Docker tag

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


19. **docker tag:**
 Asigna una etiqueta a una imagen de Docker existente.
```sh

docker tag nombre_imagen nombre_nueva_etiqueta

```
nombre_imagen: El nombre de la imagen a la que se desea asignar una etiqueta.

nombre_nueva_etiqueta: La nueva etiqueta que se asignará a la imagen.

## Docker push

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


20. **docker push:**
 Asigna una etiqueta a una imagen de Docker existente.
```sh

docker push nombre_imagen


```
nombre_imagen: El nombre de la imagen que se desea subir al repositorio remoto.







## Docker network ls

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


21. **docker network ls:**
Proporciona información detallada sobre una red de Docker específica.
```sh

docker network ls
```



## Docker network inspect

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


22. **docker network inspect:**
Proporciona información detallada sobre una red de Docker específica..
```sh

docker network inspect nombre_red

```






## Docker network create

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


23. **docker network create:**
Crea una nueva red de Docker.
```sh
docker network rm nombre_red
```








## docker network rm

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


24. **docker network rm:**
Elimina una red de Docker existente.
```sh

docker network rm nombre_red

```






## Docker volume ls

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


25. **docker volume ls:**
Lista todos los volúmenes de Docker disponibles en el sistema.

```sh

docker volume ls


```





## Docker volume inspect

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


26. **docker volume inspect:**
Proporciona información detallada sobre un volumen de Docker específico.

```sh

docker volume inspect nombre_volumen


```



## Docker volume create

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


27. **docker volume create:**
Crea un nuevo volumen de Docker.

```sh

docker volume create nombre_volumen


```

## Docker volume rm

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


28. **docker volume rm:**
Elimina un volumen de Docker existente.

```sh

docker volume rm nombre_volumen


```


## Docker-compose up

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


29. **docker-compose up:**
Crea y arranca servicios definidos en un archivo docker-compose.yml.

```sh

docker-compose up -d

```



## Docker-compose down

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


30. **docker-compose down:**
Detiene y elimina los contenedores creados por docker-compose up.

```sh

docker-compose down


```




## Docker-compose ps

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


31. **docker-compose ps:**
Explicación: Lista los servicios definidos en el archivo docker-compose.yml.

```sh

docker-compose ps

```


## docker-compose logs

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


32. **docker-compose logs:**
Muestra los logs de los servicios definidos en el archivo docker-compose.yml.

```sh

docker-compose logs nombre_servicio

```





## Docker-compose build

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


33. **docker-compose build:**
Construye los servicios definidos en el archivo docker-compose.yml.

```sh

docker-compose build


```

## Docker-compose exec

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


34. **docker-compose exec:**
Ejecuta un comando en un servicio definido en el archivo docker-compose.yml.

```sh

docker-compose exec nombre_servicio comando

```
nombre_servicio: El nombre del servicio en el que se desea ejecutar el comando.

comando: El comando que se desea ejecutar dentro del servicio.



---
## Historial de Versiones


Fecha       | Versión | Autor       | Organización | Descripción
------------|---------|-------------|--------------|---------------------
14/02/2024  | 01      | Dario Cano  | Cliente      | Nueva funcionalidad