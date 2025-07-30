# 2.1. Modelo de terreno Civil 3D en estado natural (planicie)
Keywords: `contour` `dtm` `autodesk-civil-3d` `autodesk-autocad` `surface` `M02A01`

Generar a partir del modelo TIN o de curvas de nivel, un modelo de terreno en Civil 3D de la planicie natural como base para el trazado de perfiles, ejes, secciones, cálculo de volúmenes y trazado del modelo de terreno del canal sinuoso compuesto.

<div align="center"><img src="graph/M02A01.png" alt="R.SIGE" width="60%" border="0" /></div>


## Objetivos

* Importar información topográfica a Civil 3D.
* Depurar y generar la superficie en Civil 3D usando objetos independientes (líneas).
* Reconocer aspectos importantes en la generación de Modelos de Terreno en Civil 3D del tipo Surface (TIN) a partir de Objetos simples (Líneas). 


## Requerimientos

Archivos, actividades previas, lecturas y herramientas requeridas para el desarrollo de esta actividad:

<div align="center">

| Requerimiento                                                                            | Descripción                         |
|:-----------------------------------------------------------------------------------------|:------------------------------------|
| [:toolbox:Herramienta](https://qgis.org/)                                                | QGIS 3.42 o superior.               |
| [:toolbox:Herramienta](https://www.autodesk.com/products/autocad)                        | Autodesk Autocad 2026 o superior.   |
| [:toolbox:Herramienta](https://www.autodesk.com/products/civil-3d)                       | Autodesk Civil 3D 2026 o superior.  |
| [:round_pushpin:CGG_CurvaNivelLidar_v0.shp](../../file/shp/CGG_CurvaNivelLidar_v0.zip)   | Capa de curvas de nivel.            |
| [:round_pushpin:CGG_CurvaNivelLidar_v1.shp](../../file/shp/CGG_CurvaNivelLidar_v1.zip)   | Capa de curvas de nivel recortadas. |

</div>

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.


## Procedimiento general

R.HCMC se encuentra en proceso de actualización, consulte la versión anterior en el enlace [M02A01.pdf](M02A01.pdf).


## Actividades de proyecto :triangular_ruler:

Utilizando la [plantilla suministrada](../../file/report/R.HCMC.PlantillaSoporteDesarrollo.docx), cree un documento soporte mostrando las actividades desarrolladas en el orden presentado en esta actividad, junto con los análisis y recomendaciones realizadas, convierta a Adobe Acrobat (.pdf) y guarde en la carpeta _/report_ del repositorio de datos del proyecto; nombre el archivo con el código de la actividad agregando al final la fecha de control documental en formato aaaammdd (p. ej. M02A01_20250531.pdf).

En la siguiente tabla se listan las actividades que deben ser desarrolladas y documentadas por cada estudiante o grupo de proyecto.

| Actividad | Alcance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| M02A01    | Usando la herramienta de exportación de QGIS, exporte el contenido de la capa de curvas de nivel (completas o recortadas) a CAD, se recomienda guardar en .dxf o en .dwg versión 2007. Nombrar el archivo de salida con el mismo nombre de la capa de curvas del proyecto como /file/cad/acad/CGG_CurvaNivelLidar_v1.dwg. En el documento soporte incluya capturas de pantalla de las herramientas de exportación utilizadas.                                                                                                                                                 | 
| M02A01    | En Autodesk CIVIL 3D, crear el modelo o superficie de terreno, nombrar como _/file/cad/civil/Civil3D_MDT_Planicie_v1.dwg_. Puede crear la superficie utilizando todas las curvas de nivel o recortarlas hasta un corredor de aferencia al rededor de los drenajes a evaluar, p ej., un buffer de 2 km. En el documento soporte, incluya capturas de pantalla de las diferentes herramientas Autodesk Civil 3D utilizadas y la superficie obtenida en al menos 3 tipos de visualización (2D Wireframe, 3D Wireframe, Conceptual, Realistic, Shaded, Shaded with edges, X-Ray). | 
| M02A01    | En una tabla y al final del informe de avance de esta entrega, indique el detalle de las actividades realizadas por cada integrante de su grupo; utilice las siguientes columnas: `Nombre del integrante`, `Actividades realizadas`, `Tiempo dedicado en horas` (si presenta la entrega individualmente, no es necesaria la presentación de esta tabla).<br><br>Para actividades que no requieren del desarrollo de elementos de avance, indicar si realizo la lectura de la guía de clase y las lecturas indicadas al inicio en los requerimientos.                          | 

> Nota 1: para la revisión del proyecto final, guarde los libros cálculo de Microsoft Excel y los archivos generados en esta actividad, en las localizaciones indicadas en cada numeral.
>
> Nota 2: una vez el instructor realice la revisión y el estudiante presente las correcciones o ajustes solicitados, será necesario cargar una nueva versión de los archivos en el repositorio del proyecto, incluyendo o actualizando al final del nombre del archivo, la fecha de presentación en formato aaaammdd y manteniendo las versiones anteriores presentadas.
>


## Referencias

* https://www.autodesk.com/education/free-software/autocad
* https://www.autodesk.com/education/free-software/civil-3d


## Control de versiones

| Versión    | Descripción        | Autor                                      | Horas |
|------------|:-------------------|--------------------------------------------|:-----:|
| 2025.07.29 | Migración a GitHub | [rcfdtools](https://github.com/rcfdtools)  |   1   |
| 2014.01.12 | Versión inicial.   | [rcfdtools](https://github.com/rcfdtools)  |   6   |


##

_R.HCMC es de uso libre para fines académicos, conoce nuestra licencia, cláusulas, condiciones de uso y como referenciar los contenidos publicados en este repositorio, dando [clic aquí](../../LICENSE.md)._

_¡Encontraste útil este repositorio!, apoya su difusión marcando este repositorio con una ⭐ o síguenos dando clic en el botón Follow de [rcfdtools](https://github.com/rcfdtools) en GitHub._


| [:arrow_backward: Anterior](../M01A20/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.SIGE/discussions/99999) | [Siguiente :arrow_forward:](../M02A02/Readme.md) |
|--------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------|--------------------------------------------------|

[^1]: 