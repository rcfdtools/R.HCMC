# 1.17. Obras y estructuras hidráulicas - Caída y control de fondo
Keywords: `realigment`  `m01a17`

Diseño de estructura de caída con y sin contra-escalón en sección rectangular. 

<div align="center"><img src="graph/M01A17.jpg" alt="R.SIGE" width="60%" border="0" /></div>


## Objetivos

* Evaluar el requerimiento de estructuras de caída en el cauce principal o en cauces laterales.
* Obtener las especificaciones de desarrollo de la estructura para la protección del fondo.


## Requerimientos

Archivos, actividades previas, lecturas y herramientas requeridas para el desarrollo de esta actividad:

<div align="center">

| Requerimiento                                                                                                                                                                | Descripción                                                                                        |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------|
| [:toolbox:Herramienta](https://www.microsoft.com/es/microsoft-365/excel?market=bz)                                                                                           | Microsoft Excel 365.                                                                               |
| [:open_file_folder:R.HydroTools.DisenoEstructura CaidaSinContraescalon.xlsm](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoEstructuraCaidaSinContraescalon) | Libro de cálculo para el diseño de estructuras de caída sin contra-escalón en sección rectangular. |
| [:open_file_folder:R.HydroTools.DisenoEstructura CaidaSinContraescalon.xlsm](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoEstructuraCaidaConContraescalon) | Libro de cálculo para el diseño de estructuras de caída con contra-escalón en sección rectangular. |

</div>

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.


## 0. Conceptos generales

El diseño y construcción de canales hidráulicos requiere frecuentemente del diseño de estructuras de caída, especialmente en las siguientes situaciones: 

* Cuando se busca ajustar o mantener la pendiente de diseño.
* Cuando no se realiza diseño de cauce sinuoso confinado en valle suavizado.
* Cuando debido a procesos erosivos, el fondo del canal se degrada y es necesario que este se agrade para recuperar su condición inicial y restablecer su pendiente.

En la actividad [M01A08](../M01A08), realizamos el análisis del perfil de terreno del valle y evaluamos o no el requerimiento de estructuras de caída para el empalme o entrega de cauces laterales por encima o a fondo del nuevo valle de realineamiento, encontrando que por las condiciones geo-morfométricas, no es necesario ajustar el fondo Sin embargo, realizaremos el diseño suponiendo que en algún tramo del cauce dominante, podrán ser requeridas estas estructuras.

> Tenga en cuenta que la sección dominante diseña para el canal es trapezoidal y que los libros de diseño de estructuras de caída son aplicable a geometría en canales rectangulares.


## 1. Estructura de caída sin contra-escalón

1. En el libro de diseño [R.HydroTools.DisenoEstructuraCaidaSinContraescalon.xlsm](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoEstructuraCaidaSinContraescalon), ingrese los parámetros de diseño correspondientes a la sección del cauce dominante y la configuración del escalón.

Para este ejemplo, utilizaremos:

* Altura de escalón de 0.233 metros, que de acuerdo a los análisis previos realizados en la actividad [M01A08](../M01A08), corresponde a 6 caídas a lo largo del canal.
* Ancho superficial de la estructura de 40 metros, correspondiente al ancho del canal en la base del cauce dominante.
* Altura lámina en caída de 1.5 metros, suponiendo que el canal dominante se encuentra a flujo máximo para el periodo de diseño de 2.33 años.
* Pendiente del río correspondiente a 0.0008969 m/m.

Tabla de análisis actividad [M01A08](../M01A08).

<div align="center"><img src="graph/R.HydroTools.PerfilValleEstCaidaCorteRelleno.1.jpg" alt="R.SIGE" width="60%" border="0" /></div>

Parámetros de entrada en hoja de diseño de caída sin contra-escalón y resultados obtenidos.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraCaidaSinContraescalon.1.jpg" alt="R.SIGE" width="60%" border="0" /></div>

2. Para los parámetros de entrada, el análisis indica que la profundidad crítica Yc es igual a 1.025 metros, con profundidades hidráulicas en piscina de 0.619 metros, antes del resalto en 0.832 metros y después del resalto en 1.284 metros, requiriendo protección de fondo de 6.04 metros, como se muestra en la figura.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraCaidaSinContraescalon.2.jpg" alt="R.SIGE" width="60%" border="0" /></div>

3. Para crear en CAD las líneas correspondientes al perfil de fondo y lámina, seleccione las celdas en cursiva, copie y pegue en el Command de AutoCAD o Civil3D, primero lámina y luego fondo. En la selección incluir los espacios en blanco entre comandos y el espacio final. 

> Notación numérica requerida: separador decimal usando punto (.), separador de miles usando coma (,) y separador de listas usando coma (,).

Perfil de lámina esquemático

```
PLine
0,3.34812705803005
0.271338349198634,3.44837042139544
0.542676698397269,3.2841623060909
2.98472184118498,2.83193172409318
6.3111663690108,3.733
9.02454986099714,3.96043363365396

Pedit
M
All

Spline

```

Perfil de fondo

```
PLine
0,1.9997566366346
0.271338349198634,2
0.542676698397269,2
2.98472184118498,2
6.3111663690108,2
6.3111663690108,2.233
9.02454986099714,2.23543363365396

```

<div align="center"><img src="graph/Civil3D_CaidaSinContraEscalon.jpg" alt="R.SIGE" width="60%" border="0" /></div>

> Esta misma metodología puede ser aplicada a entrega de cauces laterales cuando no existe una gran diferencia en la altura de la caída.


## 2. Estructura de caída con contra-escalón












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

* Ven Te Chow, Hidráulica de canales abiertos, pág. 414 (pdf pág. 212) Vertedero de caída recta.


## Control de versiones

| Versión    | Descripción        | Autor                                      | Horas |
|------------|:-------------------|--------------------------------------------|:-----:|
| 2025.06.13 | Migración a GitHub | [rcfdtools](https://github.com/rcfdtools)  |   3   |


##

_R.HCMC es de uso libre para fines académicos, conoce nuestra licencia, cláusulas, condiciones de uso y como referenciar los contenidos publicados en este repositorio, dando [clic aquí](../../LICENSE.md)._

_¡Encontraste útil este repositorio!, apoya su difusión marcando este repositorio con una ⭐ o síguenos dando clic en el botón Follow de [rcfdtools](https://github.com/rcfdtools) en GitHub._


| [:arrow_backward: Anterior](../M01A00/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.SIGE/discussions/99999) | [Siguiente :arrow_forward:](../M01A02/Readme.md) |
|--------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------|--------------------------------------------------|

[^1]: 