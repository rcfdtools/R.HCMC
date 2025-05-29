# 1.2. Modelación hidrológica para obtención de caudales de diseño e hidrogramas para tránsito de crecientess
Keywords: `hydrologic-model` `basin` `subbasin` `hec-hms` `hec-dssvue` `m01a02`

Obtención en función del área de aportación hasta los puntos de inicio, entrega, descarga de cauces laterales y para diferentes periodos de retorno, los caudales requeridos para el diseño hidráulico y geométrico, así como los hidrogramas para el tránsito hidráulico de crecientes por el canal artificial.

<div align="center"><img src="graph/M01A02.png" alt="R.SIGE" width="60%" border="0" /></div>


## Objetivos

* Explorar el modelo hidrológico e Identificar los puntos de estudio.
* Evaluar el área de aportación hasta cada punto de estudio.
* Estimar el factor de atenuación por área simultánea para cada punto.
* Importar a HEC-DSS, los hietogramas por sub-cuenca del modelo hidrológico.
* Estimar caudales pico en diferentes puntos de estudio y para diferentes periodos de retorno.
* Obtener y analizar los hidrogramas obtenidos para el tránsito de crecientes por el tramo de cauce diseñado. 


## Requerimientos

| Requerimiento                                                                                                                                                    | Descripción                                                                                                                                                                                                                                                                                     |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [:toolbox:Herramienta](https://www.microsoft.com/es/microsoft-365/excel?market=bz)                                                                               | Microsoft Excel 365                                                                                                                                                                                                                                                                             |
| [:toolbox:Herramienta](https://notepad-plus-plus.org/)                                                                                                           | Notepad++                                                                                                                                                                                                                                                                                       |
| [:toolbox:Herramienta](https://www.hec.usace.army.mil/software/hec-hms/)                                                                                         | HEC-HMS 4.13 Beta 6 o superior                                                                                                                                                                                                                                                                  |
| [:toolbox:Herramienta](https://www.hec.usace.army.mil/software/hec-dssvue/)                                                                                      | HEC-DSSVue 3.2.3 (versión funcional para cargue masivo de hietogramas)                                                                                                                                                                                                                          |
| [:notebook:Lectura](https://github.com/rcfdtools/R.HydroTools/blob/main/tool/FactorAtenuacionPrecipitacionFa/R.HydroTools.FactorAtenuacionPrecipitacionFa.pdf)   | Factor de atenuación de la precipitación por área simultánea                                                                                                                                                                                                                                    |
| [:open_file_folder:R.HydroTools.FactorAtenuacion PrecipitacionFa.xlsx](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/FactorAtenuacionPrecipitacionFa) | Libro de cálculo para la estimación del Fa - Factor de atenuación de la precipitación máxima por área simultánea en una cuenca                                                                                                                                                                  |
| [:open_file_folder:HECHMS_v0.zip](../../file/hec/HECHMS_v0.zip)                                                                                                  | Modelo hidrológico HEC-HMS con topología de áreas de drenaje de aproximadamente 4 km² o superior, compuesto por 44 subcuencas, 41 tramos de drenaje de 151.6 km (21 corresponden a tramos con tránsito hidrológico), área total de la cuenca en estudio: 247.1 km².                             |
| [:open_file_folder:Hietogramas.zip](Hietogramas.zip)                                                                                                             | Archivos con series de hietogramas para diferentes periodos de retorno y factores de atenuación (0.62, 0.63, 0.64, 1) en función de las áreas acumuladas hasta los puntos de inicio, entrega y cauces menores. Incluye hietogramas para periodos de retorno de 2.33, 5, 10, 25, 50 y 100 años.  |
| [:open_file_folder:R.HydroTools.Hidrograma RegVal.xlsm](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/HidrogramaRegVal)                               | Libro de cálculo para el registro y validación de hidrogramas obtenidos a partir de modelación hidrológica en HEC-HMS                                                                                                                                                                           |

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.
>
> Nota: los datos hidroclimatológicos suministrados corresponden a información tomada y procesada a partir de datos del IDEAM  y los archivos de formas vectoriales han sido descargados del IGAC y de otras fuentes alternas.


## Procedimiento general

> Geográficamente, se muestran las sub-cuencas localizadas al sur del eje del valle, pero para el tránsito hidrológico no se considerará la escorrentía producida por estas áreas debido a que el análisis hidrológico corresponde al tránsito hasta el punto de entrega del canal a diseñar y este se encuentra arriba del punto de confluencia de estos drenajes. Total área geográfica incluyendo las cuencas al sur: 262.3 km².


## Actividades de proyecto :triangular_ruler:

En la siguiente tabla se listan las actividades que deben ser desarrolladas y documentadas por cada estudiante o grupo de proyecto.

| Actividad | Alcance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| M01A01    | Descargar el archivo [R.HydroTools.DisenoCaucesParametros.xlsx](https://github.com/rcfdtools/R.HydroTools/blob/main/tool/DisenoCaucesParametros/R.HydroTools.DisenoCaucesParametros.xlsx) disponible en GitHub, e incluirlo en el repositorio.                                                                                                                                                                                                                                                                                                       | 
| M01A01    | Investigar, verificar y registrar en el libro de Excel, los parámetros técnicos, hidráulicos e hidrológicos indicados en esta actividad.<br><br>Para el grupo de parámetros normativos, ambientales / sociales y territoriales, revisar los parámetros actualmente reportados, investigar, registrar y actualizar.                                                                                                                                                                                                                                   | 
| M01A01    | En una tabla y al final del informe de avance de esta entrega, indique el detalle de las actividades realizadas por cada integrante de su grupo; utilice las siguientes columnas: `Nombre del integrante`, `Actividades realizadas`, `Tiempo dedicado en horas` (si presenta la entrega individualmente, no es necesaria la presentación de esta tabla).<br><br>Para actividades que no requieren del desarrollo de elementos de avance, indicar si realizo la lectura de la guía de clase y las lecturas indicadas al inicio en los requerimientos. | 

> :blue_heart: Una vez el instructor realice la revisión y el estudiante presente las correcciones o ajustes solicitados, será necesario cargar una nueva versión de los archivos en el repositorio del proyecto, incluyendo o actualizando al final del nombre del archivo, la fecha de presentación en formato aaaammdd y manteniendo las versiones anteriores presentadas.


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