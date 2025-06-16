# 1.19. Obras y estructuras hidráulicas - Escalonada
Keywords: `hydraulics` `hydraulic-structure` `hydraulic-stepped-structure` `m01a19`

El diseño y construcción de canales hidráulicos, requiere frecuentemente del diseño de estructuras escalonadas cuando existen diferencias importantes de nivel entre el fondo del cauce lateral intervenido y el cauce o canal receptor.

<div align="center"><img src="graph/M01A19.jpg" alt="R.SIGE" width="60%" border="0" /></div>


## Objetivos

* Evaluar la diferencia entre la cota de fondo del cauce lateral y el fondo del realineamiento.
* Diseñar una estructura escalonada para la entrega de un cauce lateral.
* Modelar y validar el funcionamiento de la estructura para las condiciones de diseño.


## Requerimientos

Archivos, actividades previas, lecturas y herramientas requeridas para el desarrollo de esta actividad:

<div align="center">

| Requerimiento                                                                                                          | Descripción                                                                                                                    |
|:-----------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------|
| [:toolbox:Herramienta](https://www.microsoft.com/es/microsoft-365/excel?market=bz)                                     | Microsoft Excel 365.                                                                                                           |
| [:toolbox:Herramienta](https://qgis.org/)                                                                              | QGIS 3.42 o superior.                                                                                                          |
| [:toolbox:Herramienta](https://www.hec.usace.army.mil/software/hec-ras/)                                               | HEC-RAS 6.6 o superior.                                                                                                        |
| [:open_file_folder:R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.xlsm](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoEstructuraEscalonadaFlujoRasante) | Libro de cálculo para el análisis y diseño de estructura escalonada en sección rectangular a flujo rasante, método Iwao Ohtsu. |

</div>

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.


## 0. Conceptos generales

Casos en los que se requiere del uso de estructuras escalonadas:

* Entrega de cauces laterales a cauces o a canales principales.
* Entrega de cuencas remanentes en cortes de vías a cunetas, canales perimetrales o ríos.
* Canales realineados en los que existe una diferencia considerable de altura entre el fondo de inicio realineado y el fondo del canal de entrega.


## 1. Procedimiento general

1. Utilizando el perfil del realineamiento del valle suavizado y el fondo del canal proyectado en la actividad [M01A08](../M01A08), determine la diferencia de nivel que existe en la entrega del cauce lateral. 

<div align="center"><img src="graph/R.HydroTools.PerfilValleEstCaidaCorteRelleno.Transicion1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

Para el caso de estudio, esta diferencia es tan solo de 0.25 metros, lo que indica que la entrega lateral podrá ser realizada por empalme de fondos y sin una estructura escalonada.

> Para el desarrollo de este ejercicio, realizaremos el diseño de una estructura escalonada con diferencia de caída de 1.5 metros.

2. En la hoja de diseño, registre los siguientes parámetros de diseño de la estructura:

* Caudal de diseño, Qd: caudal del cauce lateral obtenido en la entrega [M01A02](../M01A02) para la cuenca W19610 del modelo hidrológico con factor de atenuación 1.0. 
* Altura del escalón o contrahuella, s: altura definida por el diseñador.
* Ancho superficial estructura, B: correspondiente al ancho geométrico de la sección obtenido en la entrega [M01A13](../M01A13).
* Diferencia de caída, Dh: diferencia entre el fondo del cauce lateral y el fondo del valle.

Una vez ingresados estos parámetros, de clic en los botones `0. Resolver θ < 19°, L huella` y `1. Resolver y1`, así obtendrá la longitud de la huella para un angulo tetta inferior a 19 grados y la profundidad hidráulica _y1_ al inicio de la estructura.

> El ancho superficial de la estructura podrá ser menor teniendo en cuenta que la geometría del canal es trapezoidal y la geometría de la estructura es rectangular. Este valor es utilizado para calcular las profundidades secuentes del resalto hidráulico en la zona inferior de la estrtuctura.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

3. Verifique la altura de caída y que se cumplan los criterios de selección de altura de contrahuella.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.2.jpg" alt="R.SIGE" width="100%" border="0" /></div>

4. Verifique el cumplimiento del tipo de flujo rasante en la estructura y la altura de caída necesaria para alcanzar esta condición.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.3.jpg" alt="R.SIGE" width="100%" border="0" /></div>

5. Revise el cálculo de la profundidad y la velocidad de flujo, si se alcanza la condición de flujo quasi-uniforme.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.4.jpg" alt="R.SIGE" width="100%" border="0" /></div>

6. Revise el cálculo de la profundidad y la velocidad de flujo cuando no se alcanza la condición de flujo quasi-uniforme (de clic en el botón `2. Resolver dw`), la energía residual y la concentración media del aire.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.5.jpg" alt="R.SIGE" width="100%" border="0" /></div>

7. Revise y calcule la profundidad de flujo para una concentración de aire de 0.9 en zona de flujo quasi-uniforme, la altura de los muros del canal en zona de flujo quasi-uniforme y la profundidad de flujo y2 (profundidad secuente del salto hidráulico) en zona inferior estructura, de clic en los botones `3. Resolver y2 con q-u` y `4. Resolver y2 sin q-u`.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.6.jpg" alt="R.SIGE" width="100%" border="0" /></div>

> Como observa, los resultados presentan valores si se alcanza o no la condición de flujo quasi-uniforme. Para este ejemplo utilizaremos los resultados cuando no se alcanza la condicón q-u.

8. 







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
| 2025.06.12 | Migración a GitHub | [rcfdtools](https://github.com/rcfdtools)  |   8   |
| 2014.01.11 | Versión inicial.   | [rcfdtools](https://github.com/rcfdtools)  |  18   |


##

_R.HCMC es de uso libre para fines académicos, conoce nuestra licencia, cláusulas, condiciones de uso y como referenciar los contenidos publicados en este repositorio, dando [clic aquí](../../LICENSE.md)._

_¡Encontraste útil este repositorio!, apoya su difusión marcando este repositorio con una ⭐ o síguenos dando clic en el botón Follow de [rcfdtools](https://github.com/rcfdtools) en GitHub._


| [:arrow_backward: Anterior](../M01A00/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.SIGE/discussions/99999) | [Siguiente :arrow_forward:](../M01A02/Readme.md) |
|--------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------|--------------------------------------------------|

[^1]: 