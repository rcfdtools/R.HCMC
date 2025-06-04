# 1.6. Evaluación de secciones transversales de referencia y cotas de fondo de inicio y entrega
Keywords: `realigment` `cross-section` `hydraulic-depth` `m01a06`

A partir de las secciones existentes en los ríos naturales a intervenir, definir las cotas de inicio y entrega del canal artificial a diseñar, la cota máxima de almacenamiento o cota de desbordamiento, la altura máxima de la sección y el ancho promedio existente del cauce dominante y/o de la llanura.

<div align="center"><img src="graph/M01A06.png" alt="R.SIGE" width="50%" border="0" /></div>


## Objetivos

* Identificar las secciones transversales de inicio y entrega del canal a diseñar.
* Evaluar las cotas de fondo de inicio y entrega.
* Estimar el delta Y o diferencia de elevación entre secciones de inicio y entrega.
* Comparar los anchos superficiales de las secciones naturales.


## Requerimientos

Archivos, actividades previas, lecturas y herramientas requeridas para el desarrollo de esta actividad:

<div align="center">

| Requerimiento                                                                                           | Descripción                                                                     |
|:--------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------|
| [:toolbox:Herramienta](https://www.microsoft.com/es/microsoft-365/excel?market=bz)                      | Microsoft Excel 365.                                                            |
| [:toolbox:Herramienta](https://www.microsoft.com/es/microsoft-365/word?market=bz)                       | Microsoft Word 365.                                                             |
| [:toolbox:Herramienta](https://notepad-plus-plus.org/)                                                  | Notepad++.                                                                      |
| [:toolbox:Herramienta](https://www.hec.usace.army.mil/software/hec-hms/)                                | HEC-HMS 4.13 Beta 6 o superior.                                                 |
| [:toolbox:Herramienta](https://www.hec.usace.army.mil/software/hec-dssvue/)                             | HEC-DSSVue 3.2.3 (versión funcional para cargue masivo de hietogramas).         |
| [:notebook:Lectura](R.HydroTools.FactorAtenuacionPrecipitacionFa.pdf)                                   | Factor de atenuación de la precipitación por área simultánea.                   |
| [:open_file_folder:R.HydroTools.SeccionTransvInicioEntrega.xlsx](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/SeccionTransvInicioEntrega) | Libro de cálculo para la evaluación de secciones naturales de inicio y entrega. |
| [:round_pushpin:R.HCMC.NodoValle.shp](../../file/shp/R.HCMC.NodoValle.zip)                                                               | Capa de nodos eje valle recto (creada en actividad anterior).                   |

</div>

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.


## 0. Consideraciones generales

* Los datos de estación / elevación son extraídos del modelo de muestreo HEC-RAS, construido a partir del modelo digital de terreno de puntos o curvas topográficas y líneas de secciones transversales.
* Las cotas de inicio y entrega para el diseño y modelación pueden ser más altas o bajas dependiendo si se considera rellenar, dragar o rectificar el cauce natural antes de su intervención.
* Se puede considerar que el canal artificial a diseñar deberá tener una profundidad similar a la del cauce natural a reemplazar, sin embargo, cuando se plantea realizar dragado o rectificación de fondo para rehabilitación o realce de los taludes de protección, las profundidades pueden variar y será necesario realizar un nuevo levantamiento topo-batimétrico de las zonas de inicio y entrega para realizar un nuevo análisis.
* Para el correcto cálculo del área hidráulica y perímetro mojado, la línea que describe el ancho superficial a partir de la selección de estaciones, no debe cruzar la línea de terreno. Tenga en cuenca que cuando existen bancos de arena o sobre elevaciones por encima de la lámina de agua dentro del ancho superficial, la hoja de cálculo sobre estima o sub estima el valor del área y perímetro hidráulico calculado.


## 1. Obtención de valores estación / elevación y localización geográfica 

1. Abra el [modelo hidráulico de muestreo HEC-RAS](../../file/hec) creado en la actividad anterior, y en _Geometry Data_ cargue la geometría _GeomertyNatural_ e identifique la sección natural de inicio y entrega del eje del valle correspondientes a las abscisas 9944 m al inicio y 3253 m en la entrega.

<div align="center">Sección inicio - Abscisa 9944 m<br><img src="graph/HECRAS_GeometricDataXSStart.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center">Sección entrega - Abscisa 3253 m<br><img src="graph/HECRAS_GeometricDataXSEnd.jpg" alt="R.SIGE" width="100%" border="0" /></div>

2. En el libro de Microsoft Excel [R.HydroTools.SeccionTransvInicioEntrega.xlsx](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/SeccionTransvInicioEntrega), registre los valores de estación y elevación copiando y pegando los valores desde el visor de secciones de HEC-RAS.

<div align="center"><img src="graph/R.HydroTools.SeccionTransvInicioEntrega.Values.jpg" alt="R.SIGE" width="100%" border="0" /></div>

3. En QGIS, agregue las capas de ríos, secciones transversales naturales y eje del valle suavizado, obtenga las coordenadas de localización del centroide de las secciones de inicio y entrega, registre en el libro de Excel.

Para la localización de centroides, cree y calcule en la capa de secciones transversales naturales, las siguientes propiedades geométricas:

| Campo  | Tipo       | Descripción                                  | Propiedad geométrica                                                 |
|:-------|:-----------|:---------------------------------------------|:---------------------------------------------------------------------|
| CXm    | Real (10)  | Coordenada X de centroide en metros          | x(@geometry)                                                         |
| CYm    | Real (10)  | Coordenada Y de centroide en metros          | y(@geometry)                                                         |
| Latdd  | Real (10)  | Latitud de centroide en grados geodésicos    | x(transform($geometry, layer_property(@layer, 'crs'),'EPSG:4326'))   |
| Londd  | Real (10)  | Longitud de centroide en grados geodésicos   | y(transform($geometry, layer_property(@layer, 'crs'),'EPSG:4326'))   |

<div align="center"><img src="graph/QGIS_FieldCalculator.jpg" alt="R.SIGE" width="100%" border="0" /></div>

> Para el cálculo correcto del centroide geográfico se debe exportar y reproyectar la capa _RASMapper_XSCutlinesNatural.shp_ al CRS 3116, guardar como _RASMapper_XSCutlinesNatural3116.shp_

<div align="center"><img src="graph/QGIS_FieldCalculator1.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/QGIS_XSCutlineStartEndCoordinate.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.SeccionTransvInicioEntrega.Coordinates.jpg" alt="R.SIGE" width="100%" border="0" /></div>

4. Dando clic en el enlace _Ver Localización de Google Maps_ del libro de Excel, visualice la localización de las secciones.

<div align="center"><img src="graph/GoogleChrome_GoogleMapsXSStart.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/GoogleChrome_GoogleMapsXSSEnd.jpg" alt="R.SIGE" width="100%" border="0" /></div>


## 2. Estimación de anchos superficiales







## Actividades de proyecto :triangular_ruler:

Utilizando la [plantilla suministrada](../../file/report/R.HCMC.PlantillaSoporteDesarrollo.docx), cree un documento soporte mostrando las actividades desarrolladas en el orden presentado en esta actividad, junto con los análisis y recomendaciones realizadas, convierta a Adobe Acrobat (.pdf) y guarde en la carpeta _/activity_ del repositorio de datos del proyecto; nombre el archivo con el código de la actividad agregando al final la fecha de control documental en formato aaaammdd (p. ej. M01A00_20250531.pdf).

En la siguiente tabla se listan las actividades que deben ser desarrolladas y documentadas por cada estudiante o grupo de proyecto.

| Actividad | Alcance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| M01A01    | Descargar el archivo [R.HydroTools.DisenoCaucesParametros.xlsx](https://github.com/rcfdtools/R.HydroTools/blob/main/tool/DisenoCaucesParametros/R.HydroTools.DisenoCaucesParametros.xlsx) disponible en GitHub, e incluirlo en el repositorio.                                                                                                                                                                                                                                                                                                       | 
| M01A01    | Investigar, verificar y registrar en el libro de Excel, los parámetros técnicos, hidráulicos e hidrológicos indicados en esta actividad.<br><br>Para el grupo de parámetros normativos, ambientales / sociales y territoriales, revisar los parámetros actualmente reportados, investigar, registrar y actualizar.                                                                                                                                                                                                                                   | 
| M01A02    | Registrar los valores obtenidos en el [libro de parámetros generales](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoCaucesParametros) requeridos para el diseño y la modelación. Guardar en la carpeta _file/table_.                                                                                                                                                                                                                                                                                                                |
| M01A02    | Opcional: verificar la formulación correcta de los libros de cálculo suministrados. En las notas de la ficha de control documental indicar el método de verificación y si se requieren o no ajustes.                                                                                                                                                                                                                                                                                                                                                 |
| M01A01    | En una tabla y al final del informe de avance de esta entrega, indique el detalle de las actividades realizadas por cada integrante de su grupo; utilice las siguientes columnas: `Nombre del integrante`, `Actividades realizadas`, `Tiempo dedicado en horas` (si presenta la entrega individualmente, no es necesaria la presentación de esta tabla).<br><br>Para actividades que no requieren del desarrollo de elementos de avance, indicar si realizo la lectura de la guía de clase y las lecturas indicadas al inicio en los requerimientos. | 

> Nota 1: para la revisión del proyecto final, guarde los libros cálculo de Microsoft Excel y los archivos generados en esta actividad, en las localizaciones indicadas en cada numeral.
>
> Nota 2: una vez el instructor realice la revisión y el estudiante presente las correcciones o ajustes solicitados, será necesario cargar una nueva versión de los archivos en el repositorio del proyecto, incluyendo o actualizando al final del nombre del archivo, la fecha de presentación en formato aaaammdd y manteniendo las versiones anteriores presentadas.
>


## Referencias

* 


## Control de versiones

| Versión    | Descripción        | Autor                                      | Horas |
|------------|:-------------------|--------------------------------------------|:-----:|
| 2024.02.24 | Migración a GitHub | [rcfdtools](https://github.com/rcfdtools)  |   8   |
| 2014.01.11 | Versión inicial.   | [rcfdtools](https://github.com/rcfdtools)  |  18   |


##

_R.HCMC es de uso libre para fines académicos, conoce nuestra licencia, cláusulas, condiciones de uso y como referenciar los contenidos publicados en este repositorio, dando [clic aquí](../../LICENSE.md)._

_¡Encontraste útil este repositorio!, apoya su difusión marcando este repositorio con una ⭐ o síguenos dando clic en el botón Follow de [rcfdtools](https://github.com/rcfdtools) en GitHub._


| [:arrow_backward: Anterior](../M01A00/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.SIGE/discussions/99999) | [Siguiente :arrow_forward:](../M01A02/Readme.md) |
|--------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------|--------------------------------------------------|

[^1]: 