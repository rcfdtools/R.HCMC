# 2.8. Planos - Cálculo de volúmenes corte y relleno
Keywords: `volume-cut-fill` `engineering-sketch` `cross-section` `autodesk-civil-3d` `autodesk-autocad` `surface` `m02a07`

A partir de los modelos de terreno para la planicie y para el canal combinado, determinar los volúmenes de corte y relleno para el canal. Generar las tablas de volúmenes.

<div align="center"><img src="graph/M02A08.jpg" alt="R.HCMC" width="60%" border="0" /></div>


## Objetivos

* Generar el modelo de terreno del canal combinado (valle y cauce sinuoso).
* Importar las líneas de secciones transversales de muestreo.
* Crear materiales de corte y relleno.
* Crear tablas de reporte.


## Requerimientos

Archivos, actividades previas, lecturas y herramientas requeridas para el desarrollo de esta actividad:

<div align="center">

| Requerimiento                                                                                                                        | Descripción                                                                                                                                                                                                                                                                      |
|:-------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [:toolbox:Herramienta](https://qgis.org/)                                                                                            | QGIS 3.42 o superior.                                                                                                                                                                                                                                                            |
| [:toolbox:Herramienta](https://www.autodesk.com/products/civil-3d)                                                                   | Autodesk Civil 3D 2026 (english version) o superior.                                                                                                                                                                                                                             |
| [:round_pushpin:Civil3D_MDT_Planicie_v1.dwg](../../file/cad/civil/Civil3D_MDT_Planicie_v1.zip)                                       | Archivo Autodesk Civil 3D con: modelo digital de terreno de la planicie a partir de curvas de nivel.                                                                                                                                                                             |
| [:round_pushpin:Civil3D_MDT_ValleRio_v0.dwg](../../file/cad/acad/Civil3D_MDT_ValleRio_v0.zip)                                        | Archivo Autodesk AutoCAD con: líneas CAD del modelo digital de terreno que integra el valle curvo y el río sinuoso.                                                                                                                                                              |
| [:mortar_board:Actividad 1.5. Modelo topológico de muestreo en HEC-RAS para el estudio de secciones y perfiles](../M01A05/Readme.md) | A partir del modelo de terreno triangulado - TIN, la red de drenaje natural foto restituida y el eje suavizado del valle; construir un modelo HEC-RAS que permita evaluar las secciones de referencia, el canal natural actual y el perfil de terreno del eje de valle trazado.  |

</div>

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.


## Procedimiento general

R.HCMC se encuentra en proceso de actualización, consulte la versión anterior en el enlace [M02A05.pdf](M02A05.pdf).


## Actividades de proyecto :triangular_ruler:

Utilizando la [plantilla suministrada](../../file/report/R.HCMC.PlantillaSoporteDesarrollo.docx), cree un documento soporte mostrando las actividades desarrolladas en el orden presentado en esta actividad, junto con los análisis y recomendaciones realizadas, convierta a Adobe Acrobat (.pdf) y guarde en la carpeta _/report_ del repositorio de datos del proyecto; nombre el archivo con el código de la actividad agregando al final la fecha de control documental en formato aaaammdd (p. ej. M02A01_20250531.pdf).

En la siguiente tabla se listan las actividades que deben ser desarrolladas y documentadas por cada estudiante o grupo de proyecto.

| Actividad | Alcance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| M02A08    | A partir del archivo /cad/civil/Civil3D_MDT_Planicie_v1.dwg en el cual se generó el MDT para la planicie, importar desde /cad/acad/Civil3D_MDT_ValleRio_v0.dwg, los elementos 3D que componen el canal que fueron generados al momento de trazar los respectivos corredores para el valle y cauce sinuoso. Guardar como /cad/civil/Civil3D_MDT_PlanicieCanal_v1.dwg.<br><br>Trazar las secciones transversales de muestreo y calcular los volúmenes de corte y relleno de la sección compuesta.<br><br>En el documento soporte, incluya capturas de pantalla de detalle con las diferentes herramientas Autodek Civil 3D utilizadas.  |  
| M02A08    | En una tabla y al final del informe de avance de esta entrega, indique el detalle de las actividades realizadas por cada integrante de su grupo; utilice las siguientes columnas: `Nombre del integrante`, `Actividades realizadas`, `Tiempo dedicado en horas` (si presenta la entrega individualmente, no es necesaria la presentación de esta tabla).<br><br>Para actividades que no requieren del desarrollo de elementos de avance, indicar si realizo la lectura de la guía de clase y las lecturas indicadas al inicio en los requerimientos.                                                                                  | 

> Nota 1: para la revisión del proyecto final, guarde los libros cálculo de Microsoft Excel y los archivos generados en esta actividad, en las localizaciones indicadas en cada numeral.
>
> Nota 2: una vez el instructor realice la revisión y el estudiante presente las correcciones o ajustes solicitados, será necesario cargar una nueva versión de los archivos en el repositorio del proyecto, incluyendo o actualizando al final del nombre del archivo, la fecha de presentación en formato aaaammdd y manteniendo las versiones anteriores presentadas.


## Referencias

* https://www.autodesk.com/education/free-software/autocad
* https://www.autodesk.com/education/free-software/civil-3d


## Control de versiones

| Versión    | Descripción        | Autor                                     | Horas |
|------------|:-------------------|-------------------------------------------|:-----:|
| 2025.07.31 | Migración a GitHub | [rcfdtools](https://github.com/rcfdtools) |   2   |
| 2014.01.23 | Versión inicial.   | [frankv13](https://github.com/frankv13)   |   8   |


##

_R.HCMC es de uso libre para fines académicos, conoce nuestra licencia, cláusulas, condiciones de uso y como referenciar los contenidos publicados en este repositorio, dando [clic aquí](../../LICENSE.md)._

_¡Encontraste útil este repositorio!, apoya su difusión marcando este repositorio con una ⭐ o síguenos dando clic en el botón Follow de [rcfdtools](https://github.com/rcfdtools) en GitHub._


| [:arrow_backward: Anterior](../M02A07/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.HCMC/discussions/99999) | [Siguiente :arrow_forward:](../M02A09/Readme.md) |
|---------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------|---------------------------------------------------|

[^1]: 