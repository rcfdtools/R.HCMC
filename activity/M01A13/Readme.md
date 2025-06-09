# 1.13. Diseño geométrico e hidráulico vertical del cauce principal de desviación y cauces laterales menores
Keywords: `hydraulic-desgn` `tractive-force`  `m01a13`

Dimensionar la sección hidráulica dominante (1) y de creciente (2) del cauce principal y de los cauces laterales menores, verificando a flujo uniforme la capacidad hidráulica de la sección compuesta (3) y el borde libre requerido.

<div align="center"><img src="graph/M01A13.png" alt="R.SIGE" width="60%" border="0" /></div>


## Objetivos

* Diseñar la sección dominante por los métodos Copeland, Régimen de Flujo y Fuerza tractiva.
* Diseñar la sección de creciente por los métodos Copeland, Régimen de Flujo y Fuerza tractiva.
* Verificar la sección compuesta por flujo uniforme.
* Diseñar la geometría de los pasos de vía usando alcantarillas por área equivalente a descarga libre.
* Crear un prototipo digital del diseño realizado y modelar a flujo permanente y no permanente.

<div align="center"><img src="graph/SeccionCompuesta.jpg" alt="R.SIGE" width="60%" border="0" /></div>


## Requerimientos

Archivos, actividades previas, lecturas y herramientas requeridas para el desarrollo de esta actividad:

<div align="center">

| Requerimiento                                                                                                                                                            | Descripción                                                                                     |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------|
| [:toolbox:Herramienta](https://www.microsoft.com/es/microsoft-365/excel?market=bz)                                                                                       | Microsoft Excel 365.                                                                            |
| [:toolbox:Herramienta](https://www.hec.usace.army.mil/software/hec-ras/)                                                                                                 | HEC-RAS 6.6 o superior.                                                                         |
| [:round_pushpin:R.HCMC.NodoValle.shp](../../file/shp/R.HCMC.NodoValle.zip)                                                                                               | Capa de nodos eje valle recto (creada en actividad anterior).                                   |
| [:open_file_folder:R.HydroTools.DisenoGeometricoHidraulicoVertical.xlsm](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoGeometricoHidraulicoVertical)    | Libro de cálculo para el diseño geométrico e hidráulico vertical de canales a superficie libre. |
| [:open_file_folder:Modelo hidráulico HECRAS_v0](../../file/hec)                                                                                                          | Modelo hidráulico de muestreo HEC-RAS v0 creado en actividad [M01A05](../M01A05/Readme.md).     |

</div>

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.


## 1. Diseño hidráulico para el cauce dominante principal

1. En HEC-RAS cree un proyecto nuevo y nombre como _/file/hec/HECRAS_v0_HD/HECRAS_v0_HD.prj_. 

> En actividades anteriores, establecimos por defecto el sistema internacional de unidades, sin embargo, es indispensable verificar que el proyecto sea creadoo en este sistema. 

<div align="center"><img src="graph/SeccionCompuesta.jpg" alt="R.SIGE" width="60%" border="0" /></div>

2. Ingrese al Módulo de Diseño, menú _Run / Hydraulic Design Functions…_ o clic en el botón _Perform Hydraulic Design Computations_.  

En la ventana de diseño hidráulico y en _Type / Stable Channel Design…_, observará que HEC-RAS dispone de 3 métodos diferentes para el diseño de sección estable (secciones que hidráulicamente se encuentran en el límite entre la agradación o degradación del lecho).

* Copeland
* Regime
* Tractive Force

<div align="center"><img src="graph/HECRAS_NewProject.jpg" alt="R.SIGE" width="60%" border="0" /></div>























## Actividades de proyecto :triangular_ruler:

Utilizando la [plantilla suministrada](../../file/report/R.HCMC.PlantillaSoporteDesarrollo.docx), cree un documento soporte mostrando las actividades desarrolladas en el orden presentado en esta actividad, junto con los análisis y recomendaciones realizadas, convierta a Adobe Acrobat (.pdf) y guarde en la carpeta _/activity_ del repositorio de datos del proyecto; nombre el archivo con el código de la actividad agregando al final la fecha de control documental en formato aaaammdd (p. ej. M01A00_20250531.pdf).

En la siguiente tabla se listan las actividades que deben ser desarrolladas y documentadas por cada estudiante o grupo de proyecto.

| Actividad | Alcance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| M01A00    | Descargar el archivo [R.HydroTools.DisenoCaucesParametros.xlsx](https://github.com/rcfdtools/R.HydroTools/blob/main/tool/DisenoCaucesParametros/R.HydroTools.DisenoCaucesParametros.xlsx) disponible en GitHub, e incluirlo en el repositorio.                                                                                                                                                                                                                                                                                                       | 
| M01A00    | Investigar, verificar y registrar en el libro de Excel, los parámetros técnicos, hidráulicos e hidrológicos indicados en esta actividad.<br><br>Para el grupo de parámetros normativos, ambientales / sociales y territoriales, revisar los parámetros actualmente reportados, investigar, registrar y actualizar.                                                                                                                                                                                                                                   | 
| M01A00    | Registrar los valores obtenidos en el [libro de parámetros generales](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoCaucesParametros) requeridos para el diseño y la modelación. Guardar en la carpeta _/file/table_.                                                                                                                                                                                                                                                                                                               |
| M01A00    | Opcional: verificar la formulación correcta de los libros de cálculo suministrados. En las notas de la ficha de control documental indicar el método de verificación y si se requieren o no ajustes.                                                                                                                                                                                                                                                                                                                                                 |
| M01A00    | En una tabla y al final del informe de avance de esta entrega, indique el detalle de las actividades realizadas por cada integrante de su grupo; utilice las siguientes columnas: `Nombre del integrante`, `Actividades realizadas`, `Tiempo dedicado en horas` (si presenta la entrega individualmente, no es necesaria la presentación de esta tabla).<br><br>Para actividades que no requieren del desarrollo de elementos de avance, indicar si realizo la lectura de la guía de clase y las lecturas indicadas al inicio en los requerimientos. | 

> Nota 1: para la revisión del proyecto final, guarde los libros cálculo de Microsoft Excel y los archivos generados en esta actividad, en las localizaciones indicadas en cada numeral.
>
> Nota 2: una vez el instructor realice la revisión y el estudiante presente las correcciones o ajustes solicitados, será necesario cargar una nueva versión de los archivos en el repositorio del proyecto, incluyendo o actualizando al final del nombre del archivo, la fecha de presentación en formato aaaammdd y manteniendo las versiones anteriores presentadas.
>


## Referencias

* Book: Julian Aguirre
* Ven Te Chow. Hidráulica de canales (Ejemplo 7.4 Ven Te Chow)


## Control de versiones

| Versión    | Descripción        | Autor                                      | Horas |
|------------|:-------------------|--------------------------------------------|:-----:|
| 2025.06.09 | Migración a GitHub | [rcfdtools](https://github.com/rcfdtools)  |   8   |



##

_R.HCMC es de uso libre para fines académicos, conoce nuestra licencia, cláusulas, condiciones de uso y como referenciar los contenidos publicados en este repositorio, dando [clic aquí](../../LICENSE.md)._

_¡Encontraste útil este repositorio!, apoya su difusión marcando este repositorio con una ⭐ o síguenos dando clic en el botón Follow de [rcfdtools](https://github.com/rcfdtools) en GitHub._


| [:arrow_backward: Anterior](../M01A12/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.SIGE/discussions/99999) | [Siguiente :arrow_forward:](../M01A0214/Readme.md) |
|--------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------|----------------------------------------------------|

[^1]: 