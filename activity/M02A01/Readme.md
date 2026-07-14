<div align="center"><img alt="rcfdtools" src="../../file/graph/R.HCMC.svg" height="46px"></div>

# :large_blue_circle:Módulo 2 – Diseño geométrico Civil 3D para trazado de ejes, construcción de corredores 3D y generación de planos de ingeniería de detalle

En este módulo se trazan en planta los ejes directrices del valle y río a partir del diseño geométrico realizado, para la posterior construcción e integración del modelo tridimensional triangulado requerido. Luego de realizar el diseño, se presentarán algunas indicaciones para la elaboración de planos de ingeniería de detalle, usando para ello las herramientas Autodesk AutoCAD y/o Autodesk Civil 3D.


# 2.1. Modelo de terreno Civil 3D en estado natural (planicie)
Keywords: `contour` `dtm` `autodesk-civil-3d` `autodesk-autocad` `surface` `m02a01`

Generar a partir del modelo TIN o de curvas de nivel, un modelo de terreno en Civil 3D de la planicie natural como base para el trazado de perfiles, ejes, secciones, cálculo de volúmenes y trazado del modelo de terreno del canal sinuoso compuesto.

<div align="center"><img src="graph/M02A01.png" alt="rcfdtools" width="60%" border="0" /></div>


## Objetivos

* Importar información topográfica a Civil 3D.
* Depurar y generar la superficie en Civil 3D usando objetos independientes (líneas).
* Reconocer aspectos importantes en la generación de Modelos de Terreno en Civil 3D del tipo Surface (TIN) a partir de Objetos simples (Líneas). 


## Requerimientos

Archivos, actividades previas, lecturas y herramientas requeridas para el desarrollo de esta actividad:

<div align="center">

| Requerimiento                                                                            | Descripción                                          |
|:-----------------------------------------------------------------------------------------|:-----------------------------------------------------|
| [🧰Herramienta](https://qgis.org/)                                                | QGIS 3.42 o superior.                                |
| [🧰Herramienta](https://www.autodesk.com/products/autocad)                        | Autodesk Autocad 2026 (english version) o superior.  |
| [🧰Herramienta](https://www.autodesk.com/products/civil-3d)                       | Autodesk Civil 3D 2026 (english version) o superior. |
| [📌CGG_CurvaNivelLidar_v0.shp](../../file/shp/CGG_CurvaNivelLidar_v0.zip)   | Capa geográfica de curvas de nivel.                  |
| [📌CGG_CurvaNivelLidar_v1.shp](../../file/shp/CGG_CurvaNivelLidar_v1.zip)   | Capa geográfica de curvas de nivel recortadas.       |

</div>

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.


## Procedimiento general

R.HCMC se encuentra en proceso de actualización, consulte la versión anterior en el enlace [M02A01.pdf](M02A01.pdf).

1. En QGIS, cargue, visualice y rotule las curvas de nivel contenidas en la capa [/shp/CGG_CurvaNivelLidar_v0.shp](../../file/shp/CGG_CurvaNivelLidar_v0.zip). Guarde el mapa de proyecto como _/map/m02a01.qgz_.

<div align="center"><img src="graph/QGIS_AddLayer.jpg" alt="rcfdtools" width="100%" border="0" /></div>

> Con la herramienta _QGIS / Processing Toolbox / Check Gometry / Self-Intersections_, verifique curvas de nivel con errores de intersección. Dependiendo del nivel de detalle de las curvas, este proceso puede tardar múltiples minutos (15 minutos en Intel Core i9, 32GB). Una vez terminado el proceso de identificación de errores, con la herramienta _Processing Toolbox / Fix Gometry / Split self-intersecting geometries_, divida las curvas en los puntos de intersección y elimine los extremos sobrantes en curvas o ajuste sus terminaciones.
>
> Con la herramienta _QGIS / Processing Toolbox / Vector general / Delete duplicate geometries_, verifique en una capa temporal si se han eliminado curvas duplicadas y en el evento que el número de curvas o registros de la capa original sea superior, guarde la capa como /shp/CGG_CurvaNivelLidar_v0a.shp.

En QGIS y con la herramienta _Vector Geometry / Explode Lines_, fraccione las curvas de nivel en líneas separadas por segmentos entre nodos, guardar como [/shp/CGG_CurvaNivelLidar_v0_Explode.shp](../../file/shp/CGG_CurvaNivelLidar_v0_Explode.zip)	

<div align="center"><img src="graph/QGIS_ExplodeLines.jpg" alt="rcfdtools" width="100%" border="0" /></div>

2. En Autodesk Civil 3D, cree un proyecto nuevo en blanco utilizando la plantilla métrica __Autodesk Civil 3D (Metric) NCS.dwt_. Guarde como _/cad/civil/Civil3D_MDT_Planicie_v1.dwg_

> Desde la barra de estado y con el botón _Workspace Switching_ (⚙️) o el comando **WSCURRENT**, establezca el entorno de trabajo como _Civil 3D_.

<div align="center"><img src="graph/AutodeskCivil3D_New.jpg" alt="rcfdtools" width="100%" border="0" /></div>

3. En Autodesk Civil 3D y con el Command **MAPCONNECT**, cree una conexión a la carpeta /HCMC/shp, nombre la conexión como HCMC/shp y de clic en el botón _Connect_.

<div align="center"><img src="graph/AutodeskCivil3D_MapConnectSHP.jpg" alt="rcfdtools" width="100%" border="0" /></div>

4. En la conexión, seleccione la capa _CGG_CurvaNivelLidar_v0.shp_ y agregue al proyecto. Con el comando **Z**OOM **E**xtents, acérquese al contenido de la capa cargada.

<div align="center"><img src="graph/AutodeskCivil3D_MapConnectSHP1.jpg" alt="rcfdtools" width="100%" border="0" /></div>

5. En _Civil 3D / Home / Palettes / Map Task Pane_ o con el comando **MAPWSPACE**, active el _TASK PANE_ que le permitirá activar o desactivar la visualización de las curvas de nivel y ajustar su simbología de representación.

<div align="center"><img src="graph/AutodeskCivil3D_MAPWSPACE.jpg" alt="rcfdtools" width="100%" border="0" /></div>

Desde el menú _Geolocation_, active la capa _Esri Imagery_ y verifique la localización correcta de las curvas de nivel a partir del mapa de fondo.

<div align="center"><img src="graph/AutodeskCivil3D_Geolocation.jpg" alt="rcfdtools" width="100%" border="0" /></div>

6. Desde el menú _Home / Create Ground Data / Surfaces / Create Surface from GIS Data_, cree la superficie de terreno a partir de las curvas _CGG_CurvaNivelLidar_v0_Explode.shp_ en formato shapefile.

<div align="center"><img src="graph/AutodeskCivil3D_CreateSurfaceFromGISData.jpg" alt="rcfdtools" width="100%" border="0" /></div>
<div align="center"><img src="graph/AutodeskCivil3D_CreateSurfaceFromGISData1.jpg" alt="rcfdtools" width="80%" border="0" /></div>
<div align="center"><img src="graph/AutodeskCivil3D_CreateSurfaceFromGISData2.jpg" alt="rcfdtools" width="80%" border="0" /></div>
<div align="center"><img src="graph/AutodeskCivil3D_CreateSurfaceFromGISData3.jpg" alt="rcfdtools" width="80%" border="0" /></div>

Defina el límite del modelo de terreno a partir del trazado manual de una ventana o recuadro que rodee todas las curvas de nivel.

<div align="center"><img src="graph/AutodeskCivil3D_CreateSurfaceFromGISData4.jpg" alt="rcfdtools" width="80%" border="0" /></div>

En la pestaña _Data Mapping_ establezca el atributo _Elevation_ a partir del campo _Elevation_ de la capa geográfica y de clic en el botón _Finish_. Espere hasta que el proceso sea completado y la superficie sea creada y se visualice en el espacio de trabajo. Desde el _TASK PANE_, desactive la capa shapefile de las curvas para observar las curvas de representación de la superficie para los intervalos de curvas predefinidos.

> Una vez creada la superficie, Autodesk Civil 3D podrá desplegar una ventana con errores identificados en las curvas de nivel origen tales como intersecciones, ángulos muy cerrados, nodos superpuestos, entre otros. El comando **SHOWEVENTVIEWER** permite reabrir esta ventana. 

<div align="center"><img src="graph/AutodeskCivil3D_CreateSurfaceFromGISData4a.jpg" alt="rcfdtools" width="80%" border="0" /></div>
<div align="center"><img src="graph/AutodeskCivil3D_CreateSurfaceFromGISData5.jpg" alt="rcfdtools" width="80%" border="0" /></div>
<div align="center"><img src="graph/AutodeskCivil3D_CreateSurfaceFromGISData6.jpg" alt="rcfdtools" width="100%" border="0" /></div>

7. En el panel _TOOLSPACE_ y la pestaña _Prospector_, ajuste las propiedades de visualización para contornos secundarios 0.5 metros y principales cada 2.5 metros.

<div align="center"><img src="graph/AutodeskCivil3D_PropertiesContours.jpg" alt="rcfdtools" width="100%" border="0" /></div>

8. Desde el espacio de trabajo y desde el _Visual Style Controls_, cambie el estilo de visualización a Shaded (fast).

<div align="center"><img src="graph/AutodeskCivil3D_VisualStyleShaded.jpg" alt="rcfdtools" width="100%" border="0" /></div>


## Actividades de proyecto (👥 grupal opcional no calificable, 👤individual requerido) :triangular_ruler:

Utilizando la [plantilla suministrada](../../file/report/HCMC_PlantillaInformeTecnico.docx), cree un informe técnico mostrando las actividades desarrolladas en el orden presentado en esta actividad, junto con los análisis y recomendaciones realizadas, convierta a Adobe Acrobat (.pdf) y guarde en la carpeta _/report_ del repositorio de datos del proyecto; nombre el archivo con el código de la actividad agregando al final la fecha de control documental en formato aaaammdd (p. ej. M02A01_20250531.pdf).

En la siguiente tabla se listan las actividades que deben ser desarrolladas y documentadas por cada estudiante o grupo de proyecto.

| Actividad | Alcance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| M02A01    | 👤👥 Usando la herramienta de exportación de QGIS, exporte el contenido de la capa de curvas de nivel (completas o recortadas) a CAD, se recomienda guardar en .dxf o en .dwg versión 2007. Nombrar el archivo de salida con el mismo nombre de la capa de curvas del proyecto como [/file/cad/acad/CGG_CurvaNivelLidar_v1.dwg](../../file/cad/acad/CGG_CurvaNivelLidar_v1.zip). En el informe técnico incluya capturas de pantalla de las herramientas de exportación utilizadas.                                                                                                                                                   | 
| M02A01    | 👤👥 En Autodesk Civil 3D, crear el modelo o superficie de terreno, nombrar como _[/file/cad/civil/Civil3D_MDT_Planicie_v1.dwg](../../file/cad/civil/Civil3D_MDT_Planicie_v1.zip)_. Puede crear la superficie utilizando todas las curvas de nivel o recortarlas hasta un corredor de aferencia al rededor de los drenajes a evaluar, p ej., un buffer de 2 km. En el informe técnico, incluya capturas de pantalla de las diferentes herramientas Autodesk Civil 3D utilizadas y la superficie obtenida en al menos 3 tipos de visualización (2D Wireframe, 3D Wireframe, Conceptual, Realistic, Shaded, Shaded with edges, X-Ray). | 
| M02A01    | 👥 En una tabla y al final del informe de avance de esta entrega, indique el detalle de las actividades realizadas por cada integrante de su grupo; utilice las siguientes columnas: `Nombre del integrante`, `Actividades realizadas`, `Tiempo dedicado en horas` (si presenta la entrega individualmente, no es necesaria la presentación de esta tabla).<br><br>👤 Para actividades que no requieren del desarrollo de elementos de avance, indicar si realizo la lectura de la guía de clase y las lecturas indicadas al inicio en los requerimientos.                                                                              | 

**_Nota 1_**: para la revisión del proyecto final, guarde los libros cálculo de Microsoft Excel y los archivos generados en esta actividad, en las localizaciones indicadas en cada numeral.

**_Nota 2_**: una vez el instructor realice la revisión y el estudiante presente las correcciones o ajustes solicitados, será necesario cargar una nueva versión de los archivos en el repositorio del proyecto, incluyendo o actualizando al final del nombre del archivo, la fecha de presentación en formato aaaammdd y manteniendo las versiones anteriores presentadas.


## Referencias

* https://www.autodesk.com/education/free-software/autocad
* https://www.autodesk.com/education/free-software/civil-3d
* [YouTube/ How to create a Civil 3D Surface from GIS contour shape files](https://www.youtube.com/watch?v=gwBrcZTPKkc&t=6s)


##

_R.HCMC es de uso libre para fines académicos, conoce nuestra licencia, cláusulas, condiciones de uso y como referenciar los contenidos publicados en este repositorio, dando [clic aquí](../../LICENSE.md)._

_¡Encontraste útil este repositorio!, apoya su difusión marcando este repositorio con una ⭐ o síguenos dando clic en el botón Follow de [rcfdtools](https://github.com/rcfdtools) en GitHub._


| [◄ Anterior](../M01A20/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.HCMC/discussions/1) | [Siguiente ►](../M02A02/Readme.md) |
|--------------------------------------------------|-----------------------------------|----------------------------------------------------------------------------------|--------------------------------------------------|

[^1]: 