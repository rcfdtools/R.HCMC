# 1.7. Análisis de la pendiente de diseño en cauce y valle
Keywords: `realigment` `river-slope` `valley-slope` `m01a07`

Utilizando el modelo de muestreo en HEC-RAS y a partir de la longitud del tramo natural a reemplazar y de las secciones existentes, determinar la pendiente de referencia para el diseño geométrico e hidráulico. Dentro de las consideraciones para el diseño de la sección del canal artificial, es importante evaluar la condición de equilibrio del cauce natural existente, expresada por la pendiente del cauce dominante y el equilibrio entre la erosión y agradación del lecho determinado por la edad del cauce.

<div align="center"><img src="graph/M01A07.png" alt="R.SIGE" width="60%" border="0" /></div>

En caso de que existan restricciones de trazado y sea necesario utilizar una pendiente mayor a la pendiente del cauce natural existente a reemplazar, será necesario considerar el diseño del fondo del canal de realineamiento en la sección dominante utilizando estructuras de caída con o sin contra escalón, permitiendo así replicar la pendiente natural.

> Para el diseño geométrico del canal artificial, se recomienda utilizar la pendiente obtenida del eje del diseño sinuoso del río entre las secciones de referencia de inicio y entrega, para replicar así la longitud del cauce natural sin alterar la longitud del tránsito y el tiempo de concentración de la cuenca.


## Objetivos

* Estimar la longitud del tramo de río natural a reemplazar o realinear.
* Estimar la pendiente general de referencia para el canal dominante.
* Estimar la pendiente ponderada a partir de la posición de las secciones transversales de muestreo.
* Definir la pendiente de diseño a utilizar para el cauce dominante.
* Evaluar la pendiente que regirá el tránsito de las crecientes por el valle.


## Requerimientos

Archivos, actividades previas, lecturas y herramientas requeridas para el desarrollo de esta actividad:

<div align="center">

| Requerimiento                                                                                                                                 | Descripción                                                                                 |
|:----------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------|
| [:toolbox:Herramienta](https://www.microsoft.com/es/microsoft-365/excel?market=bz)                                                            | Microsoft Excel 365.                                                                        |
| [:toolbox:Herramienta](https://www.hec.usace.army.mil/software/hec-ras/)                                                                      | HEC-RAS 6.6 o superior.                                                                     |
| [:open_file_folder:R.HydroTools.PendienteCauceValle.xlsx](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/PendienteCauceValle)       | Libro de cálculo para análisis de pendientes.                                               |
| [:open_file_folder:Modelo hidráulico HECRAS_v0](../../file/hec)                                                                               | Modelo hidráulico de muestreo HEC-RAS v0 creado en actividad [M01A05](../M01A05/Readme.md). |

</div>

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.


## 1. Pendiente cauce sinuoso natural

Utilizando como referencia las abscisas de inicio y entrega del modelo hidráulico evaluadas en la actividad anterior, correspondientes a 9944 m y 3253 m, la longitud del cauce natural a reemplazar o Delta X es de 6691 metros, la longitud vectorial del tramo a reemplazar corresponde a 6689.9 metros. A partir de las cotas de fondo de la sección de inicio y entrega correspondientes a 64.5 m y 70.5 m, el Delta Y del cauce natural es 6 metros. 

<div align="center">

S = ΔY / ΔX

</div>

En el libro de Microsoft Excel [R.HydroTools.PendienteCauceValle.xlsx](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/PendienteCauceValle), registre la longitud y diferencia de nivel obtenida.

<div align="center"><img src="graph/R.HydroTools.PendienteCauceValle.S1.jpg" alt="R.SIGE" width="80%" border="0" /></div>



## Actividades de proyecto :triangular_ruler:

Utilizando la [plantilla suministrada](../../file/report/R.HCMC.PlantillaSoporteDesarrollo.docx), cree un documento soporte mostrando las actividades desarrolladas en el orden presentado en esta actividad, junto con los análisis y recomendaciones realizadas, convierta a Adobe Acrobat (.pdf) y guarde en la carpeta _/activity_ del repositorio de datos del proyecto; nombre el archivo con el código de la actividad agregando al final la fecha de control documental en formato aaaammdd (p. ej. M01A00_20250531.pdf).

En la siguiente tabla se listan las actividades que deben ser desarrolladas y documentadas por cada estudiante o grupo de proyecto.

| Actividad | Alcance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| M01A07    | Descargar el archivo [R.HydroTools.DisenoCaucesParametros.xlsx](https://github.com/rcfdtools/R.HydroTools/blob/main/tool/DisenoCaucesParametros/R.HydroTools.DisenoCaucesParametros.xlsx) disponible en GitHub, e incluirlo en el repositorio.                                                                                                                                                                                                                                                                                                       | 
| M01A07    | Investigar, verificar y registrar en el libro de Excel, los parámetros técnicos, hidráulicos e hidrológicos indicados en esta actividad.<br><br>Para el grupo de parámetros normativos, ambientales / sociales y territoriales, revisar los parámetros actualmente reportados, investigar, registrar y actualizar.                                                                                                                                                                                                                                   | 
| M01A07    | Registrar los valores obtenidos en el [libro de parámetros generales](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoCaucesParametros) requeridos para el diseño y la modelación. Guardar en la carpeta _file/table_.                                                                                                                                                                                                                                                                                                                |
| M01A07    | Opcional: verificar la formulación correcta de los libros de cálculo suministrados. En las notas de la ficha de control documental indicar el método de verificación y si se requieren o no ajustes.                                                                                                                                                                                                                                                                                                                                                 |
| M01A07    | En una tabla y al final del informe de avance de esta entrega, indique el detalle de las actividades realizadas por cada integrante de su grupo; utilice las siguientes columnas: `Nombre del integrante`, `Actividades realizadas`, `Tiempo dedicado en horas` (si presenta la entrega individualmente, no es necesaria la presentación de esta tabla).<br><br>Para actividades que no requieren del desarrollo de elementos de avance, indicar si realizo la lectura de la guía de clase y las lecturas indicadas al inicio en los requerimientos. | 

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


| [:arrow_backward: Anterior](../M01A06/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.SIGE/discussions/99999) | [Siguiente :arrow_forward:](../M01A08/Readme.md) |
|--------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------|--------------------------------------------------|

[^1]: 