# 1.15. Diseño geométrico horizontal o diseño sinuoso
Keywords: `realigment`  `hydraulics` `hydraulic-design` `sinusoidal-river-design ``m01a015`

A partir de la estimación de los radios de curvatura característicos de los meandros o las ondas existentes en el cauce natural a reemplazar, el índice de sinuosidad y los anchos de sección diseñados hidráulicamente para el transporte del caudal dominante y creciente, determinar los atributos geométricos requeridos para el trazado del cauce sinuoso.

<div align="center"><img src="graph/M01A15.jpg" alt="R.SIGE" width="60%" border="0" /></div>


## Objetivos

* Entender conceptos aplicables al diseño geométrico horizontal de cauces sinuosos.
* Realizar diferentes diseños sinuosos a partir de diferentes criterios y valores de sinuosidad. (3 diseños)


## Requerimientos

Archivos, actividades previas, lecturas y herramientas requeridas para el desarrollo de esta actividad:

<div align="center">

| Requerimiento                                                                                                                          | Descripción                                                                |
|:---------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------|
| [:toolbox:Herramienta](https://www.microsoft.com/es/microsoft-365/excel?market=bz)                                                     | Microsoft Excel 365.                                                       |
| [:open_file_folder:R.HydroTools.DisenoSinuosoCanal.xlsm](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoSinuosoCanal)  | Libro de cálculo para el diseño geométrico horizontal sinuoso de canales.  |

</div>

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.


## 0. Conceptos generales

Para el diseño sinuoso son requeridos los parámetros geométricos obtenidos en las actividades anteriores, a partir de estos valores obtendremos con el libro de diseño los siguientes valores:

* Ángulo de deflexión de la onda, α.
* Longitud sinuosa del río, Lr.
* Número de ondas sinuosas, n.
* Longitud hidráulica de cada onda, Lb.
* Longitud de aproximación entre ondas o entre-tangencia, La.
* Número de subdivisiones en el eje del valle suavizado, Lc * (Lm/4).

> Estos valores serán utilizados para el trazado de ejes en Autodesk Civil 3D.

<div align="center"><img src="graph/SeccionCompuestaDiseño.jpg" alt="R.SIGE" width="60%" border="0" /></div>

Geometría de las ondas sinuosas

* Lm: Longitud de onda.
* Lb: Longitud hidráulica de la onda. Incluida la longitud de aproximación.
* α: Ángulo de deflexión de la onda.
* La: Longitud de aproximación entre ondas.
* B: Amplitud de onda. Definida hasta la línea de bancas.
* B’: Amplitud de onda para el trazado.
* ϴ: Radio de apertura.
* Lc: Longitud del valle suavizado.

Solución trigonométrica de una onda sinuosa.

<div align="center"><img src="graph/TrigonometriaOndaSinuosa.jpg" alt="R.SIGE" width="60%" border="0" /></div>
<div align="center"><img src="graph/TrigonometriaOndaSinuosa1.jpg" alt="R.SIGE" width="60%" border="0" /></div>

Procedimiento general:

* (1): Decidir el factor de sinuosidad a aplicar para: a. Mantener la pendiente original del cauce natural, b. Disminuir la pendiente del cauce con un factor de sinuosidad mayor ó c. Aumentar la pendiente del cauce con un factor de sinuosidad menor.
* (2A, 2B, 2C, 2D): Ingresar un radio de curvatura Rc (m) menor o igual al medido. Puede ingresar un valor de 10 m para que solver estime el máximo permisible para que la Longitud de Aproximación La (m) sea cero, o para que una onda se empalme con otra sin aproximación. Para Solver establecer una _alphasemilla_ cercana a cero y positiva, o ingresar 1. Nota: Este valor no puede ser una raíz negativa obtenida por Solver.
* (3A, 3B): Ingresar el valor calculado de ancho de la base del canal para caudal dominante de Tr: 2.33yr y el ancho del valle máximo. Al ancho de la base del valle disponible se le debe descontar un ancho de separación entre la curva externa de cada onda al borde de talud de la base del valle para evitar que el talud del cauce dominante y del valle sea contínuo y asi prevener la erosión del talud. Se recomiendan 5 m a cada lado. Ejemplo: Si el ancho disponible para valle es de 160m se debe realizar el diseño sinuoso con 150m. En el trazado de ejes usando CIVIL 3D se dibuja el corredor de 160 m, un offset de 5 m a cada lado y las curvas externas se trazan dentro del corredor efectivo libre para garantizar la separación de taludes.
* (4): Para trazar el eje de la clotoide en CIVIL3D, se toma la longitud hidraulica de cada onda y se divide en 4 partes (Lm/4), se multiplica por el número de ondas requeridas y se divide el eje del valle en este numero. Luego se traza con una línea espiral o una clotoide de radio Rc característico calculado por el eje sinuoso por los puntos extremos de intersección de cada subtramo con el borde externo de la onda. Para las sample lines dividir B' entre 2 y utilizar este valor para su construcción.









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