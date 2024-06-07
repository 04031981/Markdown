<div align="center">
    <img src="https://logopng.com.br/logos/docker-27.png" alt="Texto alternativo" style="width: 200px;"/>
</div>



#### <p align="center"><span style="color:purple">Fecha: 07/06/2024</span></p>


## **Tabla de contenido**


[Historial de Versiones](#historial-de-versiones)

[Conceptos Básicos de Docker](#conceptos-básicos-de-docker)



1. <span>[docker version](#docker-version)</span>
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




---



## Conceptos Básicos de Docker
 <span style="color:purple">[Inicio](#tabla-de-contenido)</span>

1- Contenedores: Los contenedores son unidades ligeras y portátiles que incluyen todo lo necesario para ejecutar una aplicación, como el código, las bibliotecas y las dependencias. Son más eficientes que las máquinas virtuales (VM) porque comparten el mismo sistema operativo host y solo contienen los archivos y configuraciones necesarios para ejecutarse.

2- Imágenes: Una imagen de Docker es una plantilla inmutable que contiene el sistema de archivos y las aplicaciones necesarias para ejecutar un contenedor. Las imágenes se construyen a partir de un archivo llamado Dockerfile, que especifica las instrucciones para crear la imagen.

3- Dockerfile: Es un archivo de texto que contiene una serie de comandos que Docker usa para ensamblar una imagen. En el caso de aplicaciones .NET, se suelen usar imágenes base proporcionadas por Microsoft, como mcr.microsoft.com/dotnet/aspnet para aplicaciones ASP.NET Core.

4- Registries: Son repositorios donde se almacenan y distribuyen las imágenes de Docker. Docker Hub es el registry público más conocido, pero también existen registries privados.

5- Beneficios de Docker en el Desarrollo de Software
Consistencia: Docker asegura que la aplicación se ejecute de manera idéntica en diferentes entornos (desarrollo, pruebas, producción), eliminando problemas de "funciona en mi máquina".

6- Portabilidad: Los contenedores se pueden ejecutar en cualquier lugar donde Docker esté instalado, ya sea en un entorno local, en servidores on-premises o en la nube.

7- Aislamiento: Cada contenedor tiene su propio entorno aislado, lo que permite ejecutar múltiples aplicaciones en el mismo host sin conflictos.

8- Escalabilidad: Docker facilita la escalabilidad horizontal, permitiendo ejecutar múltiples instancias de una aplicación de manera sencilla.

## Docker en el Entorno de .NET
Desarrollo y Pruebas: Docker permite a los desarrolladores .NET crear entornos de desarrollo consistentes y reproducibles. Utilizando Docker Compose, se pueden definir y administrar aplicaciones multi-contenedor (por ejemplo, una aplicación web .NET Core, una base de datos SQL Server, y un servicio de caching).

Integración Continua/Entrega Continua (CI/CD): Docker se integra perfectamente con sistemas de CI/CD como Azure DevOps, Jenkins, y GitHub Actions. Las imágenes de Docker se pueden construir y probar como parte del pipeline de CI/CD, asegurando que la aplicación esté lista para ser desplegada en cualquier entorno.

Microservicios: Docker es ideal para arquitecturas de microservicios, donde cada servicio puede ser empaquetado y desplegado independientemente. .NET Core y .NET 6/7/8 son altamente compatibles con este enfoque debido a su naturaleza multiplataforma y ligera.

Azure Kubernetes Service (AKS): Docker se utiliza comúnmente junto con Kubernetes, un orquestador de contenedores, para gestionar despliegues a gran escala. AKS facilita la gestión y escalabilidad de aplicaciones .NET contenedorizadas en la nube de Azure.


## Dockerfile
El Dockerfile es un archivo de texto que contiene una serie de instrucciones que Docker utiliza para construir una imagen de contenedor. Cada instrucción en el Dockerfile crea una capa en la imagen, permitiendo construir el entorno necesario para ejecutar una aplicación
```C#

 # https://hub.docker.com/_/microsoft-dotnet
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base

USER app
WORKDIR /app
EXPOSE 5080
EXPOSE 5081

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
ARG BUILD_CONFIGURATION=Release

WORKDIR /src

# Copiar todos los archivos de la solución
COPY . .

# Restaurar dependencias
RUN dotnet restore

# Compilar la aplicación
RUN dotnet build -c $BUILD_CONFIGURATION -o /app/build

FROM build AS publish
ARG BUILD_CONFIGURATION=Release

# Publicar la aplicación
RUN dotnet publish -c $BUILD_CONFIGURATION -o /app/publish --no-restore

FROM base AS final
WORKDIR /app

# Copiar los archivos publicados
COPY --from=publish /app/publish .

ENTRYPOINT ["dotnet", "Application.dll"]

```

## .dockerignore
El archivo .dockerignore es similar a un archivo .gitignore y se utiliza para especificar qué archivos o directorios deben ser excluidos durante el proceso de construcción de una imagen de Docker. Esto es útil para evitar copiar archivos innecesarios, como archivos temporales, directorios de compilación, archivos de configuración específicos del entorno, etc., en la imagen del contenedor, lo que puede reducir el tamaño de la imagen y mejorar los tiempos de construcción.

```C#
**/.classpath
**/.dockerignore
**/.env
**/.git
**/.gitignore
**/.project
**/.settings
**/.toolstarget
**/.vs
**/.vscode
**/*.*proj.user
**/*.dbmdl
**/*.jfm
**/azds.yaml
**/bin
**/charts
**/docker-compose*
**/Dockerfile*
**/node_modules
**/npm-debug.log
**/obj
**/secrets.dev.yaml
**/values.dev.yaml
LICENSE
README.md
!**/.gitignore
!.git/HEAD
!.git/config
!.git/packed-refs
!.git/refs/heads/**

 
```
---
# <p align="center"><span style="color:purple">_Recopilación de Comandos para Docker_</span></p>
---






---
## Docker version

 <span style="color:purple">[Inicio](#tabla-de-contenido)</span>

1. **docker version:**
Muestra la versión de Docker instalada en tu máquina.

   
```powershell
   docker version
```
## Docker Info

 <span style="color:purple">[Inicio](#tabla-de-contenido)</span>

2. **docker info:**
Proporciona información detallada sobre la instalación de Docker, incluyendo datos sobre contenedores, imágenes, volúmenes, red y configuración del sistema. Es útil para obtener una visión general del estado y la configuración de Docker en tu sistema..

   
```powershell

   docker info

```
---
## Docker pull

 <span style="color:purple">[Inicio](#tabla-de-contenido)</span>

3. **docker pull:**
Descarga una imagen desde un repositorio (normalmente Docker Hub). Este comando se utiliza para obtener la última versión de una imagen de contenedor.

   
```spowershell

   docker pull

```
---

## Docker images

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

4. **docker images:**
Lista todas las imágenes descargadas en tu sistema. Proporciona información sobre las imágenes disponibles localmente, como el nombre, la etiqueta, el ID de la imagen, la fecha de creación y el tamaño.


```powershell

docker images

```


---


## Docker run

<span style="color:purple">[Inicio](#tabla-de-contenido)</span> 


5. **docker run:**
Crea y ejecuta un contenedor a partir de una imagen. Puedes especificar parámetros como el mapeo de puertos, variables de entorno, volúmenes, entre otros. La opción -d ejecuta el contenedor en segundo plano (detached mode).


```powershell

docker run -d -p 80:80 nombre_imagen

```
---



## Docker ps

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

6. **docker ps:**
Lista los contenedores en ejecución. Proporciona información sobre los contenedores activos, como el ID, la imagen, el comando, el tiempo de ejecución, los puertos expuestos y el nombre del contenedor.
```powershell

   docker ps

```
---
## Docker ps -a

<span style="color:purple">[Inicio](#tabla-de-contenido)</span> 

7. **docker ps -a:**
Lista todos los contenedores, incluyendo los que no están en ejecución. Es útil para ver el historial de todos los contenedores creados en tu sistema.

```powershell

   docker ps -a

```



---

## Docker stop

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

8. **docker stop:**

Detiene un contenedor en ejecución de manera ordenada. Envía una señal SIGTERM al contenedor y espera un tiempo predeterminado antes de forzar su detención con SIGKILL si no se ha detenido.

```powershell

docker stop id_contenedor

```
En este ejemplo, se debe agregar el id del contenedor el cual se debe detener.

---
## Docker start

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

9. **docker start:**

Inicia un contenedor detenido. Este comando es útil para reanudar la ejecución de contenedores que han sido detenidos anteriormente.

```powershell

docker start id_contenedor

```

En este ejemplo, se debe agregar el id del contenedor el cual se debe inicializar.

---
## Docker restart

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

10. **docker restart:**

Reinicia un contenedor. Primero detiene el contenedor y luego lo inicia nuevamente. Es útil para aplicar cambios de configuración o solucionar problemas sin crear un nuevo contenedor.  Ejemplo:

```powershell

docker restart id_contenedor

```
---
## Docker kill

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

11. **docker kill:**

Detiene un contenedor de forma inmediata (forzada) enviando una señal SIGKILL, lo que no permite al contenedor realizar una parada ordenada. Por ejemplo:

```powershell

docker kill id_contenedor

```
---

## Docker rm

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

12. **docker rm:**

Elimina un contenedor detenido. Este comando se utiliza para liberar recursos y limpiar contenedores no deseados. Por ejemplo:

```spowershell

docker rm id_contenedor

``` 
---

## Docker rmi

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

13. **docker rmi:**

Elimina una imagen de Docker de tu sistema. Es útil para liberar espacio y gestionar imágenes no deseadas.

```powershell

docker rmi nombre_imagen:tag

```
---

## Docker build

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

14. **docker build:**

Construye una imagen a partir de un Dockerfile. Puedes especificar un nombre y una etiqueta para la imagen utilizando la opción -t . es muy importante el punto al final

```powershell

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

```powershell

docker exec -it nombre_contenedor comando

```


## docker logs

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

16. **docker logs:**

Explicación: Muestra los registros (logs) de un contenedor en tiempo real. Por ejemplo:

```powershell

docker logs nombre_contenedor

```

nombre_contenedor: El nombre o ID del contenedor del que se desean ver los registros.

##   Docker inspect

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

17. **docker inspect:**

Proporciona información detallada sobre un contenedor, imagen, red o volumen de Docker. Por ejemplo:

nombre_objeto: El nombre o ID del contenedor, imagen, red o volumen del que se desea obtener información detallada.

```powershell

docker inspect nombre_objeto

```
Esto garantiza que las dos actualizaciones se realicen correctamente o ninguna de ellas se realice.


## Docker commit

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


18. **docker commit:**
    Explicación: Crea una nueva imagen a partir de un contenedor en ejecución.

```powershell

docker commit nombre_contenedor nombre_imagen

```
nombre_contenedor: El nombre o ID del contenedor del que se desea crear una nueva imagen.

nombre_imagen: El nombre y la etiqueta de la nueva imagen que se creará.

## Docker tag

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


19. **docker tag:**
 Asigna una etiqueta a una imagen de Docker existente.

```powershell

docker tag nombre_imagen nombre_nueva_etiqueta

```

nombre_imagen: El nombre de la imagen a la que se desea asignar una etiqueta.

nombre_nueva_etiqueta: La nueva etiqueta que se asignará a la imagen.

## Docker push

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


20. **docker push:**
 Asigna una etiqueta a una imagen de Docker existente.

```powershell

docker push nombre_imagen

```
nombre_imagen: El nombre de la imagen que se desea subir al repositorio remoto.







## Docker network ls

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


21. **docker network ls:**
Proporciona información detallada sobre una red de Docker específica.

```powershell

docker network ls

```



## Docker network inspect

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


22. **docker network inspect:**
Proporciona información detallada sobre una red de Docker específica.

```powershell

docker network inspect nombre_red

```






## Docker network create

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


23. **docker network create:**
Crea una nueva red de Docker.

```powershell

docker network rm nombre_red

```








## docker network rm

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


24. **docker network rm:**
Elimina una red de Docker existente.

```powershell

docker network rm nombre_red

```






## Docker volume ls

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


25. **docker volume ls:**
Lista todos los volúmenes de Docker disponibles en el sistema.

```powershell

docker volume ls

```





## Docker volume inspect

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


26. **docker volume inspect:**
Proporciona información detallada sobre un volumen de Docker específico.

```shpowershell

docker volume inspect nombre_volumen

```



## Docker volume create

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


27. **docker volume create:**
Crea un nuevo volumen de Docker.

```powershell

docker volume create nombre_volumen

```

## Docker volume rm

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


28. **docker volume rm:**
Elimina un volumen de Docker existente.

```powershell

docker volume rm nombre_volumen

```


## Docker-compose up

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


29. **docker-compose up:**
Crea y arranca servicios definidos en un archivo docker-compose.yml.

```powershell

docker-compose up -d

```



## Docker-compose down

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


30. **docker-compose down:**
Detiene y elimina los contenedores creados por docker-compose up.

```powershell

docker-compose down


```




## Docker-compose ps

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


31. **docker-compose ps:**
Explicación: Lista los servicios definidos en el archivo docker-compose.yml.

```powershell

docker-compose ps

```


## docker-compose logs

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


32. **docker-compose logs:**
Muestra los logs de los servicios definidos en el archivo docker-compose.yml.

```powershell

docker-compose logs nombre_servicio

```





## Docker-compose build

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


33. **docker-compose build:**
Construye los servicios definidos en el archivo docker-compose.yml.

```powershell

docker-compose build

```

## Docker-compose exec

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


34. **docker-compose exec:**
Ejecuta un comando en un servicio definido en el archivo docker-compose.yml.

```powershell

docker-compose exec nombre_servicio comando

```
nombre_servicio: El nombre del servicio en el que se desea ejecutar el comando.

comando: El comando que se desea ejecutar dentro del servicio.



---
## Historial de Versiones


Fecha       | Versión | Autor       | Organización | Descripción
------------|---------|-------------|--------------|---------------------
07/06/2024  | 01      | Dario Cano  | Cliente      | Docker