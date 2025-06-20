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

| Requerimiento                                                                                                                                                                 | Descripción                                                                                                                    |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------|
| [:toolbox:Herramienta](https://www.microsoft.com/es/microsoft-365/excel?market=bz)                                                                                            | Microsoft Excel 365.                                                                                                           |
| [:toolbox:Herramienta](https://qgis.org/)                                                                                                                                     | QGIS 3.42 o superior.                                                                                                          |
| [:toolbox:Herramienta](https://www.autodesk.com/products/civil-3d)                                                                                                            | Autodesk Civil 3D 2025 o superior.                                       |
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

2. En la hoja de diseño [R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.xlsm](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoEstructuraEscalonadaFlujoRasante), registre los siguientes parámetros de diseño de la estructura:

* Caudal de diseño, Qd: caudal del cauce lateral obtenido en la entrega [M01A02](../M01A02) para la cuenca W19610 del modelo hidrológico con factor de atenuación 1.0. 
* Altura del escalón o contrahuella, s: altura definida por el diseñador.
* Ancho superficial estructura, B: correspondiente al ancho geométrico de la sección obtenido en la entrega [M01A13](../M01A13).
* Diferencia de caída, Dh: diferencia entre el fondo del cauce lateral y el fondo del valle.

Una vez ingresados estos parámetros, de clic en los botones `0. Resolver θ < 19°, L huella` y `1. Resolver y1`, así obtendrá la longitud de la huella para un angulo tetta inferior a 19 grados y la profundidad hidráulica _y1_ al inicio de la estructura.

> El ancho superficial de la estructura podrá ser menor teniendo en cuenta que la geometría del canal es trapezoidal y la geometría de la estructura es rectangular. Este valor es utilizado para calcular las profundidades secuentes del resalto hidráulico en la zona inferior de la estructura.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.1.jpg" alt="R.SIGE" width="75%" border="0" /></div>

3. Verifique la altura de caída y que se cumplan los criterios de selección de altura de contrahuella.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.2.jpg" alt="R.SIGE" width="75%" border="0" /></div>

4. Verifique el cumplimiento del tipo de flujo rasante en la estructura y la altura de caída necesaria para alcanzar esta condición.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.3.jpg" alt="R.SIGE" width="75%" border="0" /></div>

5. Revise el cálculo de la profundidad y la velocidad de flujo, si se alcanza la condición de flujo quasi-uniforme.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.4.jpg" alt="R.SIGE" width="75%" border="0" /></div>

6. Revise el cálculo de la profundidad y la velocidad de flujo cuando no se alcanza la condición de flujo quasi-uniforme (de clic en el botón `2. Resolver dw`), la energía residual y la concentración media del aire.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.5.jpg" alt="R.SIGE" width="75%" border="0" /></div>

7. Revise y calcule la profundidad de flujo para una concentración de aire de 0.9 en zona de flujo quasi-uniforme, la altura de los muros del canal en zona de flujo quasi-uniforme y la profundidad de flujo y2 (profundidad secuente del resalto hidráulico) en zona inferior estructura, de clic en los botones `3. Resolver y2 con q-u` y `4. Resolver y2 sin q-u`.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.6.jpg" alt="R.SIGE" width="75%" border="0" /></div>

> Como observa, los resultados presentan valores si se alcanza o no la condición de flujo quasi-uniforme. Para este ejemplo utilizaremos los resultados cuando no se alcanza la condición q-u, suponiendo que la descarga no está controlada y que la estructura en su entrega está localizada dentro del valle del cauce principal de realineamiento garantizando el confinamiento del flujo.

8. Para la construcción de los esquemas geométricos, ingrese el valor de desplazamiento por coalineación que permitirá crear nodos con un pequeño desplazamiento lateral en las paredes, y la pendiente del cauce lateral evaluado en la entrega [M01A13](../M01A13).

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.7.jpg" alt="R.SIGE" width="75%" border="0" /></div>

> Para cambiar la longitud de los tramos de aproximación antes y después de la estructura, necesarios para desarrollar el flujo por la estructura, ajuste el valor del factor multiplicador que se encuentra en la tabla de parámetros de entrada.

9. Visualice y revise el esquema del perfil de la estructura.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.8.jpg" alt="R.SIGE" width="100%" border="0" /></div>


## 2. Creación de modelo digital de terreno

Para la ilustración del DTM, realizaremos un ajuste en el ancho de la sección de la estructura a 15 metros con factor de aproximación de 2.5 para obtener un corredor más largo y prevención de coalineación de nodos de 0.01 metros.

1. En el libro de diseño [R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.xlsm](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoEstructuraEscalonadaFlujoRasante), exporte el contenido de la hoja _GIS_ a un archivo de texto separado por comas como _/file/table/R.HCMC.DisenoEstructuraEscalonadaFlujoRasanteGIS.csv_.

> :bulb: En GIS y CAD, es obligatoria la definición de un valor de coalineación debido a que al crear las superficies TIN, estas requieren de un pequeño desplazamiento en la vertical para nodos en la misma localización. Se recomienda usar 0.01 metros para CAD en Civil 3D y 0.1 metros en GIS definiendo pixeles de 0.1 metros en la exportación inicial del ráster.

<div align="center"><img src="graph/R.HydroTools.DisenoEstructuraEscalonadaFlujoRasante.9.jpg" alt="R.SIGE" width="70%" border="0" /></div>

2. En QGIS, desde el menú _Layer / Add Layer / Add Delimited Text Layer..._ agregue la tabla de nodos y visualice como una capa temporal, utilice el archivo csv, la coordenada Z y asigne el CRS 3116.

<div align="center"><img src="graph/QGIS_AddDelimitedTextLayer.jpg" alt="R.SIGE" width="100%" border="0" /></div>

3. Ajuste la simbología de representación y rotule los nodos a partir de su cota. 

<div align="center"><img src="graph/QGIS_Label.jpg" alt="R.SIGE" width="100%" border="0" /></div>

4. Guarde la capa temporal como un archivo shapefile en _/file/shp/DisenoEstructuraEscalonadaFlujoRasanteGIS.shp_

<div align="center"><img src="graph/QGIS_SaveVectorLayerAs.jpg" alt="R.SIGE" width="65%" border="0" /></div>

5. Utilizando la herramienta _Processing Toolbox / Vector general / Delete duplícate geometries_, elimine los nodos duplicados y guarde como _/file/shp/DisenoEstructuraEscalonadaFlujoRasanteGISClean.shp_. De los 1812 puntos obtenidos, solo 144 son únicos.

<div align="center"><img src="graph/QGIS_DeleteDuplícateGeometries.jpg" alt="R.SIGE" width="70%" border="0" /></div>
<div align="center"><img src="graph/QGIS_DeleteDuplícateGeometries1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

6. Utilizando la herramienta _Processing Toolbox / Mesh / TIN Mesh Creation_, cree la malla del modelo digital de terreno de la estructura. Guarde como _/file/dem/DisenoEstructuraEscalonadaFlujoRasanteGIS.d2m_

<div align="center"><img src="graph/QGIS_TINMeshCreation.jpg" alt="R.SIGE" width="100%" border="0" /></div>

> :fire: Debido a la proximidad y extensión alargada de algunas caras trianguladas de la superficie del TIN, este procedimiento no se ejecuta correctamente en QGIS. En la ventana de ejecución podrá observar que el procedimiento no avanza más allá del 1% y que luego de unos segundo QGIS se cierra completamente.

<div align="center"><img src="graph/QGIS_TINMeshCreation1.jpg" alt="R.SIGE" width="70%" border="0" /></div>

7. Vuelva a abrir QGIS y exporte a formato DXF los 144 nodos que componen la estructura, guarde como _/file/cad/DisenoEstructuraEscalonadaFlujoRasanteGIS.dxf_.

<div align="center"><img src="graph/QGIS_SaveVectorLayerAsDxf.jpg" alt="R.SIGE" width="60%" border="0" /></div>

Agregue las entidades DXF al mapa y verifique su localización.

<div align="center"><img src="graph/QGIS_AddLayerDxf.jpg" alt="R.SIGE" width="65%" border="0" /></div>
<div align="center"><img src="graph/QGIS_AddLayerDxf1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

8. En Autodesk Civil 3D, abra el archivo DXF exportado, acérquese a la capa con el comando _Z E_ y con el comando _PTYPE_, cambie la representación de los nodos a círculos de 0.2 m de diámetro.

> You can change the size of points in AutoCAD using the _PTYPE_ command or the _PDSIZE_ system variable. 

<div align="center"><img src="graph/Civil3D_OpenDxf.jpg" alt="R.SIGE" width="100%" border="0" /></div>

9. Guarde el archivo DXF como un archivo de AutoCAD como /file/cad/DisenoEstructuraEscalonadaFlujoRasanteGIS.dwg.

<div align="center"><img src="graph/Civil3D_SaveAsDwg.jpg" alt="R.SIGE" width="70%" border="0" /></div>

10. En el panel lateral _TOOLSPACE_, de clic derecho en _Surfaces_ y seleccione _Create Surface_. 

<div align="center"><img src="graph/Civil3D_CreateSurface.jpg" alt="R.SIGE" width="100%" border="0" /></div>

11. En _Definition_, seleccione la opción _Drawing Object_, de clic derecho y seleccione _Add..._.

<div align="center"><img src="graph/Civil3D_CreateSurfaceDefinition.jpg" alt="R.SIGE" width="100%" border="0" /></div>

12. En el _Command_ observará que se están solicitando seleccionar los nodos, ingrese el comando _All_ y presione dos veces la tecla <kbd>Enter</kbd>.

<div align="center"><img src="graph/Civil3D_CreateSurfaceDefinitionAdd.jpg" alt="R.SIGE" width="100%" border="0" /></div>

Podrá observar un polígono de contorno que indica que la superficie ha sido creada.

<div align="center"><img src="graph/Civil3D_CreateSurfaceDefinitionAdd1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

13. En el menú _View_, active la vista _Conceptual_ y con el comando _3DORBIT_, rote la visualización 3D.

<div align="center"><img src="graph/Civil3D_3DOrbit.jpg" alt="R.SIGE" width="100%" border="0" /></div>

Acérquese y visualice los escalones de la estructura.

<div align="center"><img src="graph/Civil3D_3DOrbit1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

14. Dando clic derecho en el panel izquierdo en _Surfaces / Surface1_, seleccione la superficie. Observará que en la parte superior derecha se activa un panel específico para la superficie seleccionada.

<div align="center"><img src="graph/Civil3D_SurfaceSelect.jpg" alt="R.SIGE" width="100%" border="0" /></div>

15. En el panel _Tin Surface Surface1_, seleccione la herramienta _Extract from Surface / Extract Objects_ y marque la casilla _Triangles_. Guarde los cambios realizados.

<div align="center"><img src="graph/Civil3D_ExtractObjects.jpg" alt="R.SIGE" width="100%" border="0" /></div>

16. Desde el botón de menú Civil 3D, guarde el archivo en formato DXF versión 2007 como _/file/cad/DisenoEstructuraEscalonadaFlujoRasanteGISTriangle.dxf_

<div align="center"><img src="graph/Civil3D_SaveDrawingAsDxf.jpg" alt="R.SIGE" width="100%" border="0" /></div>

17. En QGIS, cargue solo las entidades del archivo de la superficie triangulada generada en Civil 3D.

<div align="center"><img src="graph/QGIS_AddLayerCivil3DEntities.jpg" alt="R.SIGE" width="100%" border="0" /></div>

18. Utilizando la herramienta _Processing Toolbox / Mesh / TIN Mesh Creation_, cree la malla del modelo digital de terreno _d2m_ de la estructura a partir de los triángulos de la superficie Civil 3D (entities). Guarde como _/file/dem/DisenoEstructuraEscalonadaFlujoRasanteGISCivil3D.d2m_

<div align="center"><img src="graph/QGIS_TINMeshCreation2.jpg" alt="R.SIGE" width="100%" border="0" /></div>

> Este procedimiento se ejecutará correctamente en QGIS, debido a que crearemos la superficie desde triangulos 3D.

<div align="center"><img src="graph/QGIS_TINMeshCreation3.jpg" alt="R.SIGE" width="100%" border="0" /></div>

19. Utilizando la herramienta _Processing Toolbox / Mesh / Rasterize mesh dataset_, cree la grilla TIFF del modelo digital de terreno a partir de la malla d2m. Guarde como _/file/dem/DisenoEstructuraEscalonadaFlujoRasanteGISCivil3D.tif_. En la entrada _Pixel size_ ingrese como resolución la mitad del valor utilizado en la coalineación (0.01 / 2) correspondiente a 0.05 metros.

> La definición del tamaño de pixel a partir de la mitad del valor de co-alineación, permitirá generar la grilla de la estructura con la precisión requerida para su posterior modelación

<div align="center"><img src="graph/QGIS_RasterizeMeshDataset.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/QGIS_RasterizeMeshDataset1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

20. Para verificar la correcta representación de la estructura, visualice el perfil longitudinal y algunas secciones transversales. En el menú _View_, seleccione la opción _Elevation Profile_, agregue las superficies y manualmente trace ejes de muestreo.

<div align="center"><img src="graph/QGIS_ElevationProfile.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/QGIS_ElevationProfile1.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/QGIS_ElevationProfile2.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/QGIS_ElevationProfile3.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/QGIS_ElevationProfile4.jpg" alt="R.SIGE" width="100%" border="0" /></div>


## Actividades de proyecto :triangular_ruler:

Utilizando la [plantilla suministrada](../../file/report/R.HCMC.PlantillaSoporteDesarrollo.docx), cree un documento soporte mostrando las actividades desarrolladas en el orden presentado en esta actividad, junto con los análisis y recomendaciones realizadas, convierta a Adobe Acrobat (.pdf) y guarde en la carpeta _/activity_ del repositorio de datos del proyecto; nombre el archivo con el código de la actividad agregando al final la fecha de control documental en formato aaaammdd (p. ej. M01A19_20250531.pdf).

En la siguiente tabla se listan las actividades que deben ser desarrolladas y documentadas por cada estudiante o grupo de proyecto.

| Actividad | Alcance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| M01A19    | Diseñar y modelar unidimensionalmente en HEC-RAS, la estructura de entrega escalonada a flujo rasante del cauce lateral. Crear un modelo prototipo en HEC-RAS y modelar a descarga libre y con descarga controlada, suponiendo que el canal principal está trasportando el caudal dominante. Nombrar los modelos como HECRAS_v0_EstructuraEscalonadaCauceLateral y cargar en formato .zip en la carpeta /file/hec/ del repositorio de datos (ver nota 3).                                                                                            | 
| M01A19    | Para cada prototipo digital funcional, crear un vídeo animando las láminas de agua obtenidas en la sección, el perfil y un gráfico animado con las variaciones en velocidad y cortante. Guardar en formato .mp4 como /file/report/M01A19_EstructuraEscalonadaCauceLateral.mp4.                                                                                                                                                                                                                                                                       | 
| M01A19    | En el informe incluir capturas de pantalla detalladas de las secciones transversales, perfiles, condiciones de control, planta, ventana de ejecución, tablas de resultados y vista 3D. Incluir notas descriptivas del funcionamiento del modelo y su relación con el diseño realizado.                                                                                                                                                                                                                                                               | 
| M01A19    | Opcional: verificar la formulación correcta de los libros de cálculo suministrados. En las notas de la ficha de control documental indicar el método de verificación y si se requieren o no ajustes.                                                                                                                                                                                                                                                                                                                                                 |
| M01A19    | En una tabla y al final del informe de avance de esta entrega, indique el detalle de las actividades realizadas por cada integrante de su grupo; utilice las siguientes columnas: `Nombre del integrante`, `Actividades realizadas`, `Tiempo dedicado en horas` (si presenta la entrega individualmente, no es necesaria la presentación de esta tabla).<br><br>Para actividades que no requieren del desarrollo de elementos de avance, indicar si realizo la lectura de la guía de clase y las lecturas indicadas al inicio en los requerimientos. | 

> Nota 1: para la revisión del proyecto final, guarde los libros cálculo de Microsoft Excel y los archivos generados en esta actividad, en las localizaciones indicadas en cada numeral.
>
> Nota 2: una vez el instructor realice la revisión y el estudiante presente las correcciones o ajustes solicitados, será necesario cargar una nueva versión de los archivos en el repositorio del proyecto, incluyendo o actualizando al final del nombre del archivo, la fecha de presentación en formato aaaammdd y manteniendo las versiones anteriores presentadas.
>
> Nota 3: en caso de que los cauces laterales puedan ser entregados a fondo y no requieran del diseño de estructuras escalonadas, para esta entrega será necesario diseñar y crear el prototipo solicitado diseñando por ejemplo con diferencia de cotas de 1.5 metros como mínimo y utilizando los parámetros hidráulicos del cauce.
>
> Nota 4: en los modelos unidimensionales HEC-RAS solo se tiene en cuenta el componente del vector direccional de la velocidad que es paralelo al sentido del flujo y se asume que el flujo es gradualmente variado a excepción de las estructuras hidráulicas propias que el programa puede modelar, tales como puentes, culverts y vertederos, en donde se resuelve mediante rápidamente variado o por la ecuación de momentum y otras ecuaciones empíricas. Para modelar con precisión este tipo de estructuras que estamos diseñando, se debería utilizar un modelo 3D (Como ANSYS FLUENT, Delft3D, OpenFoam) en el que se puede hacer la descomposición de los vectores en en sentido de cambio de dirección entre celdas y en la vertical. HEC-RAS 2D permite realizar el análisis de descomposición de transferencia entre celdas pero solo en planos horizontales correspondientes a la superficie de la lámina de agua. El objetivo de los prototipos es evaluar el alcance de los perfiles y líneas de energía que se obtienen usando modelos 1D para luego entender la necesidad de su modelación en 2D o 3D, por otra parte, para el diseño de ríos como el del ejercicio de clase, se busca obtener una abstracción y representación del tránsito hidráulico en grandes extensiones y superficies de inundación para evaluar las trazas en el plano XS y las zonas de flujo muerto, los circulantes y el cumplimiento de las condiciones de diseño.


## Referencias

* Ohtsu, Y. Yasuda & Takahashi M., "Flood Characteristics of Skimming Flows in Stepped Channels", Journal of Hydraulic Engineering, Vol. 130, No. 9, ASCE, September 2004.
* Esquemas INVIAS, Manual de Drenaje, Pág. 4-81.
* Formulación: [frankv13](https://github.com/frankv13), jagm, [rcfdtools](https://github.com/rcfdtools). Esquema y GIS: [rcfdtools](https://github.com/rcfdtools). Revisión y formato: [rcfdtools](https://github.com/rcfdtools)


## Control de versiones

| Versión    | Descripción        | Autor                                      | Horas |
|------------|:-------------------|--------------------------------------------|:-----:|
| 2025.06.16 | Migración a GitHub | [rcfdtools](https://github.com/rcfdtools)  |  18   |


##

_R.HCMC es de uso libre para fines académicos, conoce nuestra licencia, cláusulas, condiciones de uso y como referenciar los contenidos publicados en este repositorio, dando [clic aquí](../../LICENSE.md)._

_¡Encontraste útil este repositorio!, apoya su difusión marcando este repositorio con una ⭐ o síguenos dando clic en el botón Follow de [rcfdtools](https://github.com/rcfdtools) en GitHub._


| [:arrow_backward: Anterior](../M01A18/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.SIGE/discussions/99999) | [Siguiente :arrow_forward:](../M01A20/Readme.md) |
|--------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------|--------------------------------------------------|

[^1]: 