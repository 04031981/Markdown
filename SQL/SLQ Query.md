# <p align="center"><span style="color:blue">`Consultas SQL Más Usadas`</span></p>
# <p align="center"><span style="color:green">_Recopilación de Consultas SQL Frecuentes_</span></p>
#### <p align="center"><span style="color:red">_Fecha: [dd/mm/aaaa]_</span></p>

---

## **Tabla de contenido**



1. <span style="color:purple">[Crear una Base de Datos](#crear-base-de-datos)</span>

2. <span style="color:purple">[Usar una Base de Datos](#usar-una-base-de-datos)</span>

3. <span style="color:purple">[Crear una Tabla](#crear-una-tabla)</span>

4. <span style="color:purple">[Foreign Key](#foreign-key)</span>

5. <span style="color:purple">[Selección de Datos](#selección-de-datos)</span>

6. <span style="color:yellow">[Inserción de Datos](#inserción-de-datos)</span>

7. <span style="color:brown">[Actualización de Datos](#actualización-de-datos)</span>

8. <span style="color:teal">[Eliminación de Datos](#eliminación-de-datos)</span>

9. <span style="color:navy">[Funciones de Agregado](#funciones-de-agregado)</span>

10. <span style="color:maroon">[Joins](#joins)</span>

11. <span style="color:darkgreen">[Ordenamiento y Filtrado](#ordenamiento-y-filtrado)</span>

12. <span style="color:indigo">[Agrupación de Datos](#agrupación-de-datos)</span>

13. <span style="color:darkred">[Subconsultas](#subconsultas)</span>

14. <span style="color:darkblue">[Consultas Condicionales](#consultas-condicionales)</span>

15. <span style="color:darkorange">[Manipulación de Esquemas](#manipulación-de-esquemas)</span>

16. <span style="color:crimson">[Transacciones](#transacciones)</span>

17. <span style="color:crimson">[Logs](#logs)</span>

18. <span style="color:crimson">[PROCEDURE](#procedure)</span>

 <span style="color:purple">[Historial de Versiones](#historial-de-versiones)</span>
---


## Crear Base de Datos

 <span style="color:purple">[Inicio](#tabla-de-contenido)</span>

1. **Crear una Base de Datos**

   
```sql
   CREATE DATABASE NombreDeLaBaseDeDatos;
```
---

## Usar una Base de Datos
<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

2. **Usar una Base de Datos:**
Antes de ejecutar consultas en una base de datos específica, es importante seleccionarla con la sentencia USE.

```sql
   
   USE NombreDeLaBaseDeDatos;

```

---

## Crear una Tabla
<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

3. **Crear una Tabla:**

```sql
  CREATE TABLE NombreDeLaTabla (
    columna1 TIPO_DE_DATO,
    columna2 TIPO_DE_DATO,
    columna3 TIPO_DE_DATO,
    ...
);
  

```
---


## Foreign Key

<span style="color:purple">[Inicio](#tabla-de-contenido)</span> 


4. **Agregar una Clave Foránea (Foreign Key):**

```sql
 ALTER TABLE NombreDeLaTabla
ADD CONSTRAINT NombreDeLaClaveForanea FOREIGN KEY (NombreDeLaColumna)
REFERENCES OtraTabla (NombreDeLaColumnaReferenciada);

Ejemplo

ALTER TABLE Pedidos
ADD CONSTRAINT FK_ClienteID FOREIGN KEY (ClienteID)
REFERENCES Clientes (ClienteID);

 

```
---



## Selección de Datos

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

5. **Seleccionar todos los registros de una tabla:**

```sql
   SELECT * FROM nombre_tabla;
```
---
## Inserción de Datos

<span style="color:purple">[Inicio](#tabla-de-contenido)</span> 

6. **Insertar un nuevo registro en una tabla:**

```sql
   INSERT INTO nombre_tabla (columna1, columna2, columna3)

   VALUES (valor1, valor2, valor3);
```

#### Ejemplo: 

Supongamos que tenemos una tabla llamada Usuarios con las columnas ID, Nombre, Edad y queremos insertar un nuevo usuario:
```sql 
    INSERT INTO Usuarios (Nombre, Edad)
    VALUES ('Juan', 30); 
```

---

## Actualización de Datos

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

7. **Actualización de Datos:**

La actualización de datos en SQL Server se realiza utilizando la sentencia UPDATE. Aquí tienes un ejemplo:

```sql

UPDATE Empleados
SET Salario = Salario * 1.1
WHERE Departamento = 'Ventas';

```
En este ejemplo, la sentencia actualiza el salario de todos los empleados del departamento de ventas, incrementándolo en un 10%.

---
## Eliminación de Datos

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

8. **Eliminación de Datos:**

La eliminación de datos se realiza utilizando la sentencia DELETE. Por ejemplo:

```sql

DELETE FROM Empleados
WHERE Edad > 65;

```

Esta sentencia eliminará todos los registros de la tabla Empleados donde la edad sea mayor que 65.

---
## Funciones de Agregado

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

9. **Funciones de Agregado:**

Las funciones de agregado se utilizan para realizar cálculos en conjuntos de datos. Por ejemplo, la función SUM se utiliza para sumar los valores de una columna. Aquí tienes un ejemplo:

```sql
SELECT SUM(Monto) AS TotalVentas
FROM Ventas;
```
---
## Joins

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

10. **Joins:**

Los Joins se utilizan para combinar datos de dos o más tablas en función de una condición relacionada. Por ejemplo:

```sql
SELECT Empleados.Nombre, Departamentos.Nombre AS Departamento
FROM Empleados
INNER JOIN Departamentos ON Empleados.DepartamentoID = Departamentos.ID;
```
Esta consulta realizará una combinación interna entre las tablas Empleados y Departamentos basada en la coincidencia de DepartamentoID.

## Ordenamiento y Filtrado

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

11. **Ordenamiento y Filtrado:**

Para ordenar datos, se utiliza la cláusula ORDER BY. Por ejemplo:

```sql
SELECT Nombre, Apellido
FROM Empleados
ORDER BY Apellido ASC;
``` 
Esta consulta seleccionará los nombres y apellidos de los empleados y los ordenará alfabéticamente por apellido de forma ascendente.

## Agrupación de Datos

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

12. **Agrupación de Datos:**

La agrupación de datos se realiza utilizando la cláusula GROUP BY. Por ejemplo:

```sql
SELECT Departamento, COUNT(*) AS NumEmpleados
FROM Empleados
GROUP BY Departamento;
```
Esta consulta contará el número de empleados por departamento.

## Subconsultas

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

13. **Subconsultas:**

Las subconsultas se utilizan dentro de otras consultas para realizar operaciones más complejas. Por ejemplo:

```sql
SELECT Nombre
FROM Empleados
WHERE DepartamentoID IN (SELECT ID FROM Departamentos WHERE Nombre = 'Ventas');

```
## Consultas Condicionales

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

14. **Consultas Condicionales:**

Las consultas condicionales se realizan utilizando la cláusula CASE. Por ejemplo:

```sql
SELECT Nombre, 
       CASE 
           WHEN Edad < 30 THEN 'Joven'
           WHEN Edad BETWEEN 30 AND 50 THEN 'Adulto'
           ELSE 'Mayor'
       END AS GrupoEdad
FROM Empleados;
```

Esta consulta categorizará a los empleados según su edad en grupos: Joven, Adulto o Mayor.

## Manipulación de Esquemas

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

15. **Manipulación de Esquemas:**

La manipulación de esquemas se realiza utilizando sentencias como CREATE, ALTER y DROP. Por ejemplo:

```sql
ALTER TABLE Empleados
ADD Email NVARCHAR(100);

```

Esta sentencia agregará una columna llamada Email a la tabla Empleados.

##  Transacciones

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>

16. ** Transacciones:**

Las transacciones se utilizan para asegurar la consistencia de los datos en una base de datos. Por ejemplo:

```sql
BEGIN TRANSACTION;

UPDATE CuentaBancaria
SET Saldo = Saldo - 100
WHERE ClienteID = 123;

UPDATE CuentaBancaria
SET Saldo = Saldo + 100
WHERE ClienteID = 456;

COMMIT TRANSACTION;
```
Esto garantiza que las dos actualizaciones se realicen correctamente o ninguna de ellas se realice.

Espero que estos ejemplos te sean útiles para comprender cómo se utilizan estas sentencias en SQL Server. Si necesitas más ejemplos o explicaciones, no dudes en pedirlos.




##  Logs

<span style="color:purple">[Inicio](#tabla-de-contenido)</span>


17. **Logs:**


Para realizar la lectura de logs en Grafana, generalmente se utiliza Loki, que es un sistema de agregación y consulta de logs para entornos de nube. Loki está diseñado para ser utilizado junto con Grafana para proporcionar visualización y análisis de logs.

```C#
Registro de acceso a una aplicación dentro del contenedor:


2024-04-16T10:30:00.456789012Z [INFO] Acceso a la aplicación: GET /api/users - 200 OK





Registro de error estándar (stderr):

2024-04-16T10:25:15.345678901Z [ERROR] Ocurrió un error en el contenedor: Error de conexión a la base de datos.

```

```

1xx: Respuestas informativas (por ejemplo, 100 Continue).


2xx: Respuestas exitosas (por ejemplo, 200 OK, 201 Created).


3xx: Redirecciones (por ejemplo, 301 Moved Permanently, 302 Found).


4xx: Errores del cliente (por ejemplo, 400 Bad Request, 404 Not Found).


5xx: Errores del servidor (por ejemplo, 500 Internal Server Error, 503 Service Unavailable).


```


## 2024-04-16T10:30:00.456789012Z:
 Esta es la marca de tiempo del registro, que sigue el formato "Año-Mes-DíaTHora:Minuto:Segundo.MilisegundoNanosegundoZ". En este caso, el registro ocurrió el 16 de abril de 2024 a las 10:30:00, con 456789012 milisegundos y nanosegundos, en el huso horario UTC ('Z' indica Zulu, UTC).

## [INFO]:
 Indica el nivel de severidad del log. En este caso, es un mensaje de información (INFO), que generalmente se utiliza para registros informativos que no son ni errores ni advertencias, sino simplemente para proporcionar información sobre eventos en el sistema.

 ## Acceso a la aplicación:
  GET /api/users - 200 OK: Este es el contenido del mensaje de registro. Indica que se realizó una solicitud GET a la ruta "/api/users" en la aplicación, y el servidor respondió con un código de estado HTTP 200, que significa que la solicitud fue exitosa. Este tipo de registro es común en aplicaciones web y API, y es útil para rastrear el tráfico y el comportamiento de los usuarios en la aplicación.


---
##  PROCEDURE

18. **Procedimiento almacenado en SQL Server:**

Crear un procedimiento almacenado en SQL Server para interactuar con una tabla llamada "prestamos" en una base de datos llamada "banco". Aquí tienes un ejemplo básico de cómo podrías definir un procedimiento almacenado para insertar un préstamo en la tabla:

```sql
CREATE PROCEDURE InsertarPrestamo
    @ClienteID INT,
    @Monto DECIMAL(18, 2),
    @TasaInteres DECIMAL(5, 2),
    @PlazoMeses INT
AS
BEGIN
    SET NOCOUNT ON;

    -- Insertar el nuevo préstamo en la tabla
    INSERT INTO banco.dbo.prestamos (ClienteID, Monto, TasaInteres, PlazoMeses, FechaInicio)
    VALUES (@ClienteID, @Monto, @TasaInteres, @PlazoMeses, GETDATE());
END
```

Este procedimiento almacenado llamado InsertarPrestamo toma cuatro parámetros: @ClienteID (ID del cliente que solicita el préstamo), @Monto (monto del préstamo), @TasaInteres (tasa de interés del préstamo) y @PlazoMeses (plazo en meses para pagar el préstamo). La fecha de inicio del préstamo se establece automáticamente utilizando la función GETDATE().

Ejecutar este procedimiento almacenado con los valores adecuados para insertar un nuevo préstamo en la tabla. Por ejemplo:

```sql

EXEC InsertarPrestamo @ClienteID = 12345, @Monto = 10000.00, @TasaInteres = 5.5, @PlazoMeses = 12;

```
Este código ejecutará el procedimiento almacenado InsertarPrestamo con los valores proporcionados, insertando un nuevo préstamo en la tabla "prestamos". Asegúrate de ajustar los tipos de datos y las restricciones según sea necesario para tu caso de uso específico.





---
## Historial de Versiones


Fecha       | Versión | Autor       | Organización | Descripción
------------|---------|-------------|--------------|---------------------
14/02/2024  | 01      | Dario Cano  | Cliente      | Nueva funcionalidad