# <p align="center"><span style="color:blue">`"Empresa"`</span></p>
# <p align="center"><span style="color:green">_Requerimientos de software_</span></p>
#### <p align="center"><span style="color:red">_[Nombre del Proyecto] Fecha: [dd/mm/aaaa]_</span></p>

---

### <span style="color:orange">Tabla de contenido</span>

1. <span style="color:purple">[Historial de Versiones](#historial-de-versiones)</span>

2. <span style="color:yellow">[Información del Proyecto](#información-del-proyecto)</span>

3. <span style="color:brown">[Aprobaciones](#aprobaciones)</span>

4. <span style="color:teal">[Propósito](#propósito)</span>

5. <span style="color:navy">[Alcance del producto / Software](#alcance-del-producto--software)</span>

6. <span style="color:maroon">[Funcionalidades del producto](#funcionalidades-del-producto)</span>

7. <span style="color:darkgreen">[Clases y características de usuarios](#clases-y-características-de-usuarios)</span>

8. <span style="color:indigo">[Entorno operativo](#entorno-operativo)</span>

9. <span style="color:darkred">[Requerimientos funcionales](#requerimientos-funcionales)</span>

    - <span style="color:darkblue">[9.1 Nombre de la funcionalidad 1](#nombre-de-la-funcionalidad-1)</span>

    - <span style="color:darkorange">[9.2 Nombre de la funcionalidad 2](#nombre-de-la-funcionalidad-2)</span>

10. <span style="color:crimson">[Reglas de negocio](#reglas-de-negocio)</span>

11. <span style="color:darkviolet">[Requerimientos de interfaces externas](#requerimientos-de-interfaces-externas)</span>

12. <span style="color:olive">[Interfaces de usuario y Prototipado](#interfaces-de-usuario-y-prototipado)</span>

13. <span style="color:royalblue">[Interfaces de hardware](#interfaces-de-hardware)</span>

14. <span style="color:darkgoldenrod">[Interfaces de software](#interfaces-de-software)</span>

15. <span style="color:forestgreen">[Interfaces de comunicación](#interfaces-de-comunicación)</span>

16. <span style="color:mediumvioletred">[Requerimientos no funcionales](#requerimientos-no-funcionales)</span>

17. <span style="color:darkslategray">[Otros requerimientos](#otros-requerimientos)</span>

18. <span style="color:sienna">[Glosario](#glosario)</span>

## Historial de Versiones


Fecha       | Versión | Autor       | Organización | Descripción
------------|---------|-------------|--------------|---------------------
14/02/2024  | 01      | Dario Cano  | Cliente      | Nueva funcionalidad





## Información del Proyecto
```
Empresa / Organización | Proyecto | Fecha de preparación | Cliente | Patrocinador principal | Gerente / Líder de Proyecto | Gerente / Líder de Análisis de negocio y requerimientos
```

## Aprobaciones

Nombre y Apellido | Cargo | Departamento u Organización | Fecha | Firma


## Propósito 

En esta sección se define el nombre o título del software que se está especificado en el documento, incluyendo su número de versión. Luego se describe cuales componentes o partes del alcance del producto están incluidas en el documento, estableciendo si este documento cubre la totalidad del software, sólo una parte del sistema, subsistema o subgrupo de procesos.


## Alcance del producto / Software 

Se incluye una corta descripción del alcance del software que se está especificando, incluyendo: 

- Su propósito u objetivo general. 

- Beneficios que brinda al área de negocio y organización. 

- Objetivos y metas. 


## Funcionalidades del producto 

Lista de las funcionalidades del software que se están especificando en el documento de requerimientos.


## Clases y características de usuarios 

En esta sección se clasifican los usuarios que utilizarán el producto.


## Entorno operativo 

En esta sección se describe el entorno operativo en el que se desenvolverá el sistema.


## Requerimientos funcionales 

Los requerimientos funcionales de un sistema son aquellos que describen cualquier actividad que este deba realizar.


### Nombre de la funcionalidad 1 
```



En el título de la funcionalidad, se recomienda utilizar nombres lo más descriptivo posible para cada funcionalidad. No limitarse a nombrarlas “Funcionalidad 1”. Un buen ejemplo podría ser “Autorización de pedido de compra”. 



```
**Descripción:** Descripción corta de la funcionalidad. 

**Prioridad:** Nivel bajo, medio o alto de prioridad. Esta debe ser establecida por el área funcional. 

**Acciones iniciadoras y comportamiento esperado:** Secuencia de acciones de usuario y respuestas esperadas del sistema para esta funcionalidad. 

**Requerimientos funcionales:** Lista detallada de los requerimientos funcionales asociados a esta funcionalidad. Para cada requerimiento funcional se establece como debe mostrarse el software y cuales comportamientos debe desempeñar para que el usuario pueda realizar la función que necesita. Es recomendable incluir como el software debe responder a condiciones de error y entradas de datos inválidas.


```



Cada requerimiento debe ser identificado unívocamente, para lo cual se recomienda usar un número de secuencia, que tenga algún significado y de formato común a toda la organización. Por ejemplo: REQ-1: REQ-2: REQ-3: 

Para ver algunos ejemplos de cómo se redactan los requerimientos funcionales, te recomendamos el siguiente enlace:




```

### Nombre de la funcionalidad 2 
```
Seguir los mismos lineamientos de la funcionalidad 1 para tantas funcionalidades tenga el sistema.
```


## Reglas de negocio 

Listado de reglas y principios que aplican a todo el conjunto de requerimientos de software contenidos en el documento.


## Requerimientos de interfaces externas


## Interfaces de usuario y Prototipado

Aquí se describen las características de cada interfaz con el usuario.

Prototipado del producto [Enlace al prototipo ](https://www.figma.com/file/MzTkMPIG6WsWLkMwXraIQQ/Atomic-Desing-%2F-Ui-Kit?type=design&node-id=4%3A163&mode=design&t=f3OFiAJ0uvND3XNH-1).



## Interfaces de hardware 

Información sobre cuales tipos de dispositivos soporta el sistema.


## Interfaces de software 

Aquí se describen las interacciones entre el software y otros componentes.


## Interfaces de comunicación 

Requerimientos de las funciones de comunicación que requiere el producto.


## Requerimientos no funcionales 

Los requerimientos no funcionales son los que especifican criterios para evaluar la operación de un servicio de tecnología de información.


## Otros Requerimientos 

Requerimientos no cubiertos en ninguna otra sección del documento de requerimientos de software.


## Glosario





## Codigo

```C#
using System;
using System.Collections.Generic;
using System.Text;

namespace REDi.Models
{
    public class UserAuthentication
    {
        public string email { get; set; }
        public string password { get; set; }
        public bool returnSecureToken { get; set; }
    }
}
```


```SQL
USE [SEGUROS]
GO

/****** Object:  Table [dbo].[Auditoria]    Script Date: 14/2/2024 18:59:59 ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [dbo].[Auditoria](
	[IDAuditoria] [int] NOT NULL,
	[CertificadoID] [int] NULL,
	[ClienteID] [int] NULL,
	[PaqueteID] [int] NULL,
	[Fecha] [datetime] NULL,
PRIMARY KEY CLUSTERED 
(
	[IDAuditoria] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO

ALTER TABLE [dbo].[Auditoria]  WITH CHECK ADD FOREIGN KEY([CertificadoID])
REFERENCES [dbo].[Certificado] ([IDCertificado])
GO

ALTER TABLE [dbo].[Auditoria]  WITH CHECK ADD FOREIGN KEY([ClienteID])
REFERENCES [dbo].[Cliente] ([IDCliente])
GO

ALTER TABLE [dbo].[Auditoria]  WITH CHECK ADD FOREIGN KEY([PaqueteID])
REFERENCES [dbo].[Paquete] ([IDPaquete])
GO

```