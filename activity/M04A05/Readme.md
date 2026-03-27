<div align="center"><img alt="rcfdtools" src="../../file/graph/R.HCMC.svg" height="46px"></div>

# 4.5. Localización espacial de las condiciones de frontera y datos de entrada para flujo no permanente
Keywords: `manning` `2d-modeling` `hec-ras` `ras-mapper` `hydraulic-model` `hydraulic-simulation` `cross-section` `boundary-condition` `m04a05`

La localización espacial de dos diferentes condiciones de frontera (BC – Boundary Condition Line), No debe ser definida sobre una misma celda de la grilla. Múltiples condiciones de frontera pueden ser agregadas a la malla compuesta y se pueden asociar múltiples hidrogramas de entrada, por ejemplo, en el cauce principal y los cauces laterales, al menos se debe ingresar una línea de condición de frontera aguas arriba y una aguas abajo. Existen 5 diferentes tipos de condiciones de frontera que pueden ser utilizados para modelación 2D y en modelos mixtos 1D a 2D.

<div align="center"><img src="graph/M04A05.png" alt="R.HCMC" width="60%" border="0" /></div>


## Objetivos

* Trazar la condición de frontera aguas arriba y aguas abajo usando RAS Mapper.
* Establecer las definiciones aguas arriba. Hidrogramas para diferentes periodos de retorno.
* Establecer las definiciones aguas abajo. Profundidad normal y pendiente de diseño utilizada.
* Considerar la inclusión de precipitación directa simultánea sobre el área de drenaje.


## Requerimientos

Archivos, actividades previas, lecturas y herramientas requeridas para el desarrollo de esta actividad:

<div align="center">

| Requerimiento                                                                                      | Descripción                                                                                                                                                                                               |
|:---------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [:toolbox:Herramienta](https://qgis.org/)                                                          | QGIS 3.42 o superior.                                                                                                                                                                                     |
| [:toolbox:Herramienta](https://www.hec.usace.army.mil/software/hec-ras/)                           | HEC-RAS 6.7 Beta 3 o superior.                                                                                                                                                                            |

</div>

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.


## Procedimiento general

R.HCMC se encuentra en proceso de actualización, consulte la versión anterior en el enlace [M04A05.pdf](M04A05.pdf).

Consideraciones para la localización de las condiciones de frontera:

* La localización espacial de dos diferentes condiciones de frontera (BC – Boundary Condition Line), No debe ser definida sobre una misma celda de la grilla.
* Múltiples condiciones de frontera pueden ser agregadas a la malla compuesta. Se pueden asociar múltiples hidrogramas de entrada, por ejemplo, en el cauce principal y los cauces laterales.
* Al menos se debe ingresar una línea de condición de frontera aguas arriba y una aguas abajo.
* Las líneas de condición de frontera pueden ser trazadas interna o externamente. Por ejemplo, el flujo base o flujo subterráneo puede ser definido en cualquier zona interna del modelo.
* Las líneas BC podrán ser dibujadas o importadas usando un archivo de formas shapefile. Se recomienda importar estas líneas cuando se trate de elementos no rectos como vertederos circulares o curvos.

Existen 5 diferentes tipos de condiciones de frontera que pueden ser utilizados para modelación 2D y en modelos mixtos 1D a 2D:

* Flow Hydrograph: Hidrograma de flujo.
* Stage Hydrograph: Hidrograma de almacenamiento.
* Normal Depth: Profundidad normal.
* Rating Curve: Curva de variación del almacenamiento vs flujo.
* Precipitation: Precipitación.


## Actividades de proyecto :triangular_ruler:

Utilizando la [plantilla suministrada](../../file/report/R.HCMC.PlantillaInformeTecnico.docx), cree un informe técnico mostrando las actividades desarrolladas en el orden presentado en esta actividad, junto con los análisis y recomendaciones realizadas, convierta a Adobe Acrobat (.pdf) y guarde en la carpeta _/report_ del repositorio de datos del proyecto; nombre el archivo con el código de la actividad agregando al final la fecha de control documental en formato aaaammdd (p. ej. M02A01_20250531.pdf).

En la siguiente tabla se listan las actividades que deben ser desarrolladas y documentadas por cada estudiante o grupo de proyecto.

| Actividad | Alcance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| 
| M04A05    | No requeridas para esta actividad.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |  
| M04A05    | En una tabla y al final del informe de avance de esta entrega, indique el detalle de las actividades realizadas por cada integrante de su grupo; utilice las siguientes columnas: `Nombre del integrante`, `Actividades realizadas`, `Tiempo dedicado en horas` (si presenta la entrega individualmente, no es necesaria la presentación de esta tabla).<br><br>Para actividades que no requieren del desarrollo de elementos de avance, indicar si realizo la lectura de la guía de clase y las lecturas indicadas al inicio en los requerimientos. | 

**_Nota 1_**: para la revisión del proyecto final, guarde los libros cálculo de Microsoft Excel y los archivos generados en esta actividad, en las localizaciones indicadas en cada numeral.

**_Nota 2_**: una vez el instructor realice la revisión y el estudiante presente las correcciones o ajustes solicitados, será necesario cargar una nueva versión de los archivos en el repositorio del proyecto, incluyendo o actualizando al final del nombre del archivo, la fecha de presentación en formato aaaammdd y manteniendo las versiones anteriores presentadas.


## Referencias

* https://www.hec.usace.army.mil/confluence/rasdocs 
* https://www.hec.usace.army.mil/confluence/rasdocs/r2dum/6.6/developing-a-terrain-model-and-geospatial-layers/opening-ras-mapper
* https://www.hec.usace.army.mil/confluence/rasdocs/r2dum/6.6/developing-a-terrain-model-and-geospatial-layers/setting-the-spatial-reference-projection
* https://www.hec.usace.army.mil/confluence/rasdocs/r2dum/6.6/ras-mapper-supported-file-formats
* https://www.fsl.orst.edu/geowater/FX3/help/8_Hydraulic_Reference/Flow_Profiles.htm 


##

_R.HCMC es de uso libre para fines académicos, conoce nuestra licencia, cláusulas, condiciones de uso y como referenciar los contenidos publicados en este repositorio, dando [clic aquí](../../LICENSE.md)._

_¡Encontraste útil este repositorio!, apoya su difusión marcando este repositorio con una ⭐ o síguenos dando clic en el botón Follow de [rcfdtools](https://github.com/rcfdtools) en GitHub._


| [:arrow_backward: Anterior](../M04A04/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.HCMC/discussions/1) | [Siguiente :arrow_forward:](../M04A06/Readme.md) |
|---------------------------------------------------|-----------------------------------|----------------------------------------------------------------------------------|--------------------------------------------------|

[^1]: 