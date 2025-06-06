# 1.5. Modelo topológico de muestreo en HEC-RAS para el estudio de secciones y perfiles
Keywords: `topological-model` `sample-model` `ras-mapper`  `m01a05`

A partir del modelo de terreno triangulado - TIN, la red de drenaje natural foto restituida y el eje suavizado del valle; construir un modelo HEC-RAS que permita evaluar las secciones de referencia, el canal natural actual y el perfil de terreno del eje de valle trazado.

<div align="center"><img src="graph/M01A05.PNG" alt="R.SIGE" width="60%" border="0" /></div>


## Objetivos

* Importar y editar los drenajes, secciones transversales, bancas y líneas de flujo de la zona de estudio.
* Configurar las capas del proyecto hidráulico para su exportación.
* Validar las líneas de drenaje y secciones transversales.
* Visualizar el perfil del cauce natural a reemplazar, el perfil del eje del valle suavizado y las secciones transversales de inicio y entrega.


## Requerimientos

Archivos, actividades previas, lecturas y herramientas requeridas para el desarrollo de esta actividad:

<div align="center">

| Requerimiento                                                                                           | Descripción                                                    |
|:--------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------|
| [:toolbox:Herramienta](https://www.hec.usace.army.mil/software/hec-ras/)                                | HEC-RAS 6.7 Beta 3 o superior.                                 |
| [:toolbox:Herramienta](https://qgis.org/)                                          | QGIS 3.42 o superior.                                                    |
| [:round_pushpin:RASMapper_SampleModelShapefile](../../file/shp/RASMapper_SampleModelShapefile.zip)      | Capas geográficas vectoriales para modelo de muestreo HEC-RAS. |

</div>

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.


## 1. Creación y verificación de vectores en QGIS

1. En QGIS, cargue desde la ruta _/file/shp_ las capas [RASMapper_BanksAnthropic.shp](../../file/shp/RASMapper_BanksAnthropic.zip), [RASMapper_BanksNatural.shp](../../file/shp/RASMapper_BanksNatural.zip), [RASMapper_RiverAnthropic.shp](../../file/shp/RASMapper_RiverAnthropic.zip), [RASMapper_RiverNatural.shp](../../file/shp/RASMapper_RiverNatural.zip), [RASMapper_XSCutlinesAnthropic.shp](../../file/shp/RASMapper_XSCutlinesAnthropic.zip) y [RASMapper_XSCutlinesNatural.shp](../../file/shp/RASMapper_XSCutlinesNatural.zip).

<div align="center"><img src="graph/QGIS_RASMapperLayers.jpg" alt="R.SIGE" width="100%" border="0" /></div>

2. Active solo los elementos de muestreo de la red natural, ajuste la simbología de representación con colores similares a los mostrados en la ilustración y rotule los drenajes con `"RiverCode"  || ' / ' ||  "ReachCode"`. Para facilitar la comprensión del modelo de muestreo, agregue desde _/file/shp_ el eje suavizado del realineamiento del valle _RD_EjeValleSuavizado_AutodeskCivil3DClotoide.shp_ y el modelo digital de elevación _/file/dem/TIN_TerrenoNaturalQGIS_v0.tif_.

> :fire: Tenga en cuenta que para la correcta asociación de las abscisas del modelo hidráulico de muestreo, los drenajes así como las líneas de banca deberán ser digitalizadas en el sentido del flujo y las secciones transversales de izquierda a derecha en el sentido del flujo. Verifique la dirección vectorial por medio de simbología por flechas hacia el final.

Como observa en la ilustración, la red de muestreo de cauces naturales únicamente contiene elementos próximos a la zona del futuro cauce de realineamiento y hasta el límite del modelo digital de terreno generado previamente.

<div align="center"><img src="graph/QGIS_RASMapperNaturalSymbology.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/QGIS_RASMapperNaturalSymbology1.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/QGIS_RASMapperNaturalSymbology2.jpg" alt="R.SIGE" width="70%" border="0" /></div>

Para la construcción de las líneas de muestreo de cauces naturales de su proyecto, utilice las siguientes directrices:

| Tipo línea                      | Directriz                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:--------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| RASMapper_RiverNatural.shp      | Crear la red de muestreo a partir de los vectores contenidos en la capa de [drenajes naturales](../../file/shp/CGG_DrenajeNatural_v0.zip), incluya aguas arriba y aguas abajo de los nodos inicio y entrega del eje del valle suavizado, tramos naturales entre 1 y 5 km y los ejes de los cauces naturales hasta el límite del modelo digital de elevación. Para el nombramiento de los tramos, en el campo `RiverCode` identifique el cauce principal con un nombre único y los demás tramos laterales con nombres como Lateral1 / Lateral2 en el sentido del flujo, en el campo `ReachCode` asigne nombres en función de los sub-tramos identificados. |
| RASMapper_BanksNatural.shp      | A partir de la red de drenaje, generar paralelas de 30 metros a cada lado. Herramienta _QGIS / Processing Toolbox / Vector geometry / Offset lines_.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| RASMapper_XSCutlinesNatural.shp | En RAS Mapper, generar líneas de muestreo en intervalos cada 200 metros y anchos iniciales de 500 metros, luego editar y ajustar manualmente la localización muestreando ondas sinuosas, meandros, pasos de vía, cambios de pendiente y resuelva secciones generadas entre cruzadas o por fuera del límite del DTM. Agregue secciones transversales complementarias en zonas de inicio y entrega del realineamiento proyectado de valle (a no más de 10 cm del nodo) y en localizaciones estratégicas del modelo como nodos de unión, zonas con bajos y estructuras existentes.                                                                      |

<div align="center"><sub>Ejemplo de creación de líneas paralelas de bancas usando QGIS.</sub><br><img src="graph/QGIS_OffsetLines.jpg" alt="R.SIGE" width="100%" border="0" /></div>

> Las bancas definen la localización de la zona central del canal o zona de cauce dominante en la que se asume constante el valor de la rugosidad, de las bancas hacia afuera se considera la zona de llanura. 
> 
> Tenga en cuenta que los valores de rugosidad pueden variar discretamente en toda la sección transversal de acuerdo a las coberturas de usos actuales del suelo disponibles en la zona.

3. Edite manualmente las líneas de secciones transversales para:

* Evitar que en las secciones transversales las bancas de un mismo lado crucen dos o más veces la misma sección.
* Cada sección transversal debe ser cruzada solo una vez por la banca izquierda y solo una vez por la banca derecha.
* Las secciones transversales siempre deben ser intersecadas por cada una de las bancas.
* Las líneas de banca no pueden intersecar los ríos (River) o las líneas de dirección de flujo (Flowpaths).
* La sección más aguas abajo al final del último tramo de drenaje debe localizarse en el extremo del río para garantizar que el absicado de las secciones inicie en cero.

> Nota: en caso de que las secciones transversales editadas hayan sido copiadas desde un proyecto anterior, será necesario eliminar el campo de atributos de los identificadores hidráulicos denominado _HydroID_.

4. Repita el procedimiento anterior para la creación y verificación de las líneas de muestreo del modelo antrópico, utilice las directrices generales del modelo natural presentadas anteriormente y las siguientes directrices complementarias:

| Tipo línea                        | Directriz                                                                                                                                                                                    |
|:----------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| RASMapper_RiverAnthropic.shp      | Elimine los tramos naturales remanentes que serán removidos en la operación minera y conserve solo los elementos conectores al nuevo eje de realineamiento de valle.                         |
| RASMapper_BanksAnthropic.shp      | En la zona del eje del valle suavizado de realineamiento, generar paralelas de 150 metros a cada lado para el muestreo completo del corredor de confinamiento hidráulico.                    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| RASMapper_XSCutlinesAnthropic.shp | En la zona natural utilizar el mismo trazado de secciones naturales y en la zona del valle generar líneas de muestreo en intervalos cada 200 metros y anchos iniciales de 500 a 1000 metros. |

<div align="center"><img src="graph/QGIS_RASMapperAnthropicSymbology.jpg" alt="R.SIGE" width="100%" border="0" /></div>


## 2. Creación de proyecto HEC-RAS y topología RAS Mapper red natural

1. Abra HEC-RAS y en el menú _Options_, seleccione la opción _Units System (US Customary / SI)_ y establezca como sistema por defecto el sistema de unidades internacional.

<div align="center"><img src="graph/HECRAS_UnitSystem.jpg" alt="R.SIGE" width="80%" border="0" /></div>

2. En el menú _File_, seleccione la opción _New Project_ creando primero la carpeta de proyecto _/file/hec/HECRAS_v0/_ y nombre el proyecto como _HECRAS_v0.prj_.

<div align="center"><img src="graph/HECRAS_CreateProject.jpg" alt="R.SIGE" width="80%" border="0" /></div>
<div align="center"><img src="graph/HECRAS_CreateProject1.jpg" alt="R.SIGE" width="50%" border="0" /></div>

3. En el menú _GIS Tools_, de clic en _RAS Mapper..._ o en de clic en el ícono RAS Mapper de la ventana principal de HEC-RAS. En RAS Mapper, de clic en el menú _Project_ y seleccione la opción _Set Projection_, busque y establezca el CRS [GAUSS_BTA_MAGNA.prj](../../file/projectionfile).

<div align="center"><img src="graph/HECRAS_RASMapperSetProjection.jpg" alt="R.SIGE" width="100%" border="0" /></div>

4. En el panel lateral izquierdo seleccione el grupo Terrains y de clic derecho y seleccione la opción _Create a New RAS Terrain_, busque el DTM [/file/dem/TIN_TerrenoNaturalQGIS_v0.tif](../../file/dem) y de clic en _Create_.

> En la opción _Rounding (Precision)_ puede utilizar 1/128 de precisión con respecto a las elevaciones registradas en la grilla de terreno. 

<div align="center"><img src="graph/HECRAS_RASMapperCreateNewRASTerrain.jpg" alt="R.SIGE" width="100%" border="0" /></div>

Renombre el modelo de terreno como TIN_TerrenoNaturalQGIS y ajuste las propiedades de visualización utilizando un factor de sombreado de 10 y rampa ajustada a 24 clases en escala de grises.

<div align="center"><img src="graph/HECRAS_RASMapperTerrainRename.jpg" alt="R.SIGE" width="90%" border="0" /></div>
<div align="center"><img src="graph/HECRAS_RASMapperTerrainStretched.jpg" alt="R.SIGE" width="100%" border="0" /></div>

5. En el panel lateral izquierdo seleccione el grupo _Geometries_, de clic derecho y seleccione la opción _Create New Geometry_, nombre como _GeometryNatural_ y asocie el DTM.

<div align="center"><img src="graph/HECRAS_RASMapperCreateNewGeometry.jpg" alt="R.SIGE" width="70%" border="0" /></div>
<div align="center"><img src="graph/HECRAS_RASMapperCreateNewGeometry1.jpg" alt="R.SIGE" width="90%" border="0" /></div>

6. Seleccione la nueva geometría creada y de clic en el botón de edición (lápiz amarillo), seleccione la capa _Rivers_ y dando clic derecho seleccione la opción _Import Features_. Busque y seleccione la capa [/file/shp/RASMapper_RiverNatural.shp](../../file/shp/RASMapper_RiverNatural.zip) y asocie los códigos `River = RiverCode` y `Reach = ReachCode`.

<div align="center"><img src="graph/HECRAS_RASMapperEditRivers.jpg" alt="R.SIGE" width="100%" border="0" /></div>

Detenga la edición y guarde los cambios realizados en la geometría.

<div align="center"><img src="graph/HECRAS_RASMapperEditRivers1.jpg" alt="R.SIGE" width="35%" border="0" /></div>

Dando clic derecho en la capa _Rivers_, seleccione la opción _Layer Properties_ y en _Additional Options_ active las casillas de visualización de flechas direccionales y abscisado. Acérquese a la zona de unión del cauce lateral y verifique que exista el nodo de unión o Junction y que las flechas direccionales estén en el sentido del flujo.

<div align="center"><img src="graph/HECRAS_RASMapperEditRivers2.jpg" alt="R.SIGE" width="100%" border="0" /></div>

7. Edite la geometría e importe los _Bank Lines_ desde [/file/shp/RASMapper_BanksNatural.shp](../../file/shp/RASMapper_BanksNatural.zip), guarde, visualice y verifique las flechas direccionales.

<div align="center"><img src="graph/HECRAS_RASMapperEditBankLines.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/HECRAS_RASMapperEditBankLines1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

8. Edite la geometría e importe las _Cross Sections_ desde [/file/shp/RASMapper_XSCutlinesNatural.shp](../../file/shp/RASMapper_XSCutlinesNatural.zip), guarde, visualice y verifique las flechas direccionales y los nodos de posición de banca.

<div align="center"><img src="graph/HECRAS_RASMapperEditCrossSections.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/HECRAS_RASMapperEditCrossSections1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

9. Visualice toda la geometría y revise en detalle las diferentes localizaciones. Como referencia de visualización, en _Map Layers_ agregue desde _Reference Layers_ la capa del eje del valle suavizado [/file/shp/RD_EjeValleSuavizado_AutodeskCivil3DClotoide.shp](../../file/shp/RD_EjeValleSuavizado_AutodeskCivil3DClotoide.zip).

<div align="center"><img src="graph/HECRAS_RASMapperReferenceLayers.jpg" alt="R.SIGE" width="100%" border="0" /></div>

<div align="center">Sección inicio realineamiento<br><img src="graph/HECRAS_RASMapperReferenceLayers1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

<div align="center">Sección entrega realineamiento<br><img src="graph/HECRAS_RASMapperReferenceLayers2.jpg" alt="R.SIGE" width="100%" border="0" /></div>

10. Edite la geometría de Cross Sections y en el menú contextual seleccione las opciones _Update Cross Sections / Elevation Profiles from Terrain_ y _All XS Attributes (Except Terrain)_, que calculara las elevaciones respecto al terreno en cada sección transversal y guarde las actualizaciones. En _Cross Sections_ active la casilla de visualización _Edge Lines_ que le permitirá conocer el límite externo de la envolvente que rodea las secciones transversales.

<div align="center"><img src="graph/HECRAS_RASMapperCrossSectionsElevationProfilesFromTerrain.jpg" alt="R.SIGE" width="100%" border="0" /></div>

Selecione uno de los tramos de drenaje contenidos en Rivers y desde el menú contextual, visualice el perfil de terreno. La línea roja representa las elevaciones de la grilla del DTM y la línea verde, las elevaciones asociadas en cada sección transversal de muestreo en la intersección con el río.

<div align="center">Cauce principal aguas abajo de la entrada Lateral 1<br><img src="graph/HECRAS_RASMapperEditRiversProfile.jpg" alt="R.SIGE" width="100%" border="0" /></div>

<div align="center">Cauce Lateral 1<br><img src="graph/HECRAS_RASMapperEditRiversProfile1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

> Para su proyecto, visualice en RAS Mapper, cada uno de los tramos de drenaje.


## 3. Visualización y ajuste de geometría 1D red natural en HEC-RAS

1. Cierre RAS Mapper, y en la ventana principal de HEC-RAS, de clic en el editor de geometría 1D.

> Se recomienda mantener cerrado el editor RAS Mapper cuando esté utilizando el editor de geometría 1D de HEC-RAS, así evitará perdidas de datos o corrupción de los archivos del proyecto.

<div align="center"><img src="graph/HECRAS_GeometricData.jpg" alt="R.SIGE" width="100%" border="0" /></div>

2. En la ventana _Geometric Data_ y desde el menú _File_, seleccione la opción _Open Geometry Data_, seleccione el archivo _GeometryNatural_.

<div align="center"><img src="graph/HECRAS_GeometricDataOpen.jpg" alt="R.SIGE" width="100%" border="0" /></div>

3. Consulte y verifique los siguientes elementos:

* Perfil de cada tramo de drenaje con abscisado correcto
* Perfil de cada río incluyendo sus tramos
* Secciones transversales con distancias positivas en bancas y entre secciones
* Posición de bancas en las secciones

4. Perfil del cauce natural principal y cauce lateral

<div align="center">Cauce principal<br><img src="graph/HECRAS_GeometricDataProfile1.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center">Cauce lateral<br><img src="graph/HECRAS_GeometricDataProfile2.jpg" alt="R.SIGE" width="100%" border="0" /></div>

5. Sección de inicio y entrega realineamiento.

<div align="center">Sección de inicio, abscisa 9944 m<br><img src="graph/HECRAS_GeometricDataCrossSection1.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center">Sección de entrega, abscisa 3253 m<br><img src="graph/HECRAS_GeometricDataCrossSection2.jpg" alt="R.SIGE" width="100%" border="0" /></div>

6. Utilizando el _Graphical Cross Section Editor..._, ajuste las posiciones de banca hasta la corona de confinamiento.

> Visualmente, verifique que la posición de las bancas sobre el modelo de terreno sea consistente con la localización del cauce.

<div align="center">Ejemplo en sección, abscisa 10800 m<br><img src="graph/HECRAS_GeometricDataGraphicXSEditor1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

<div align="center">Cauce principal con ajuste de bancas<br><img src="graph/HECRAS_GeometricDataProfile3.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center">Cauce lateral con ajuste de bancas<br><img src="graph/HECRAS_GeometricDataProfile4.jpg" alt="R.SIGE" width="100%" border="0" /></div>

7. Imprima las secciones transversales en un archivo de Adobe Acrobat (.pdf) mostrando 9 secciones por hoja en formato horizontal. En la ventana del editor de geometría o _Geometric Data_, de clic en una de las secciones y seleccione la herramienta _Plot Cross Section_. En el menú File seleccione Print Multiple, ajuste el tamaño de hoja, número de secciones y guarde como [/file/report/M01A05_CrossSectionNatural.pdf](../../file/report/M01A05_CrossSectionNatural.pdf).

<div align="center"><img src="graph/HECRAS_GeometricDataCrossSectionPrintMultiple.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/HECRAS_GeometricDataCrossSectionPrintMultiple1.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/HECRAS_GeometricDataCrossSectionPrintMultiple2.jpg" alt="R.SIGE" width="100%" border="0" /></div>


## 4. Topología RAS Mapper red antrópica

Utilizando las capas geográficas [RASMapper_BanksAnthropic.shp](../../file/shp/RASMapper_BanksAnthropic.zip), [RASMapper_RiverAnthropic.shp](../../file/shp/RASMapper_RiverAnthropic.zip) y [RASMapper_XSCutlinesAnthropic.shp](../../file/shp/RASMapper_XSCutlinesAnthropic.zip) y siguiendo el procedimiento presentado en los numerales anteriores, cree el modelo de muestreo en estado antrópico ajustando también las posiciones de las bancas. Nombre la geometría como _GeometryAnthropic_.

> Para la correcta asociación de las secciones transversales es preciso unir con la herramienta _Editor / Tools / Merge_ de RAS Mapper, los dos tramos de drenaje aguas arriba del cauce lateral y luego los dos tramos aguas abajo, ajustar los nombres del río y tramos.

<div align="center">Geometría red antrópica en RAS Mapper<br><img src="graph/HECRAS_RASMapperCrossSectionsElevationProfilesFromTerrain1.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center">Cauce principal aguas abajo de la entrada Lateral 1<br><img src="graph/HECRAS_RASMapperEditRiversProfile2.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center">Cauce Lateral 1<br><img src="graph/HECRAS_RASMapperEditRiversProfile3.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center">Geometría red antrópica en Geometryc Data<br><img src="graph/HECRAS_GeometricDataOpen1.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center">Cauce principal con ajuste de bancas<br><img src="graph/HECRAS_GeometricDataProfile5.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center">Cauce lateral con ajuste de bancas<br><img src="graph/HECRAS_GeometricDataProfile6.jpg" alt="R.SIGE" width="100%" border="0" /></div>

Imprima las secciones transversales en un archivo de Adobe Acrobat (.pdf) mostrando 9 secciones por hoja en formato horizontal y guarde como [/file/report/M01A05_CrossSectionAnthropic.pdf](../../file/report/M01A05_CrossSectionAnthropic.pdf).

<div align="center"><img src="graph/HECRAS_GeometricDataCrossSectionPrintMultiple3.jpg" alt="R.SIGE" width="100%" border="0" /></div>


## 5. Generación automáticas de secciones transversales en RAS Mapper

1. Cree una nueva geometría, nombre como _CrossSectionSample_ y asocie el DTM. En Rivers importe las líneas de drenaje de la red antrópica asociando los nombres de ríos y tramos, y con la herramienta _Merge_ una los tramos de drenaje aguas abajo del cauce lateral y aguas arriba del cauce lateral, y ajuste los nombres.

<div align="center"><img src="graph/HECRAS_RASMapperCreateNewGeometry2.jpg" alt="R.SIGE" width="100%" border="0" /></div>

2. Con el modo de edición activo, seleccione, de clic derecho y ejecute la herramienta _Auto Generate Cross Section_; en espaciamiento defina 200 metros y en ancho 500 metros.

<div align="center"><img src="graph/HECRAS_RASMapperAutoGenerateCrossSection.jpg" alt="R.SIGE" width="100%" border="0" /></div>

3. Repita el procedimiento anterior para los otros dos drenajes.

<div align="center"><img src="graph/HECRAS_RASMapperAutoGenerateCrossSection1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

4. Utilizando el editor de entidades y agregando nodos (doble clic sobre la sección), ajuste las secciones no perpendiculares y/o con cruces sobre otras secciones.

<div align="center"><img src="graph/HECRAS_RASMapperEditFeature.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/HECRAS_RASMapperEditFeature1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

Una vez finalizados los ajustes, detenga el modo de edición y guarde los cambios.


## Actividades de proyecto :triangular_ruler:

Utilizando la [plantilla suministrada](../../file/report/R.HCMC.PlantillaSoporteDesarrollo.docx), cree un documento soporte mostrando las actividades desarrolladas en el orden presentado en esta actividad, junto con los análisis y recomendaciones realizadas, convierta a Adobe Acrobat (.pdf) y guarde en la carpeta _/activity_ del repositorio de datos del proyecto; nombre el archivo con el código de la actividad agregando al final la fecha de control documental en formato aaaammdd (p. ej. M01A00_20250531.pdf).

En la siguiente tabla se listan las actividades que deben ser desarrolladas y documentadas por cada estudiante o grupo de proyecto.

| Actividad | Alcance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| M01A05    | Crear dos modelos topológicos independientes en RAS Mapper, uno para el estudio de los cauces naturales y otro para el estudio del valle suavizado con los cauces naturales remanentes que se conservarán luego de su implantación.                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | 
| M01A05    | Para el modelo topológico del nuevo valle, definir y trazar la localización preliminar del paso de vía para el proyecto.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | 
| M01A05    | En HEC-RAS, ajustar la localización correcta de las bancas para la obtención de los Thalweg sobre los diferentes drenajes a evaluar y verificar en planta.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | 
| M01A05    | Cargar en la carpeta _/file/hec_ del repositorio de datos, el archivo comprimido del modelo RAS como [HECRAS_v0.zip](../../file/hec).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | 
| M01A05    | Utilizando la plantilla Microsoft Word suministrada, crear reportes de desarrollo detallados de los modelos topológicos en RAS Mapper, hidráulicos de muestreo en HEC-RAS, incluyendo capturas de pantalla de cada capa generada con visualización de la dirección vectorial de las líneas y tablas de atributos. Para cada modelo HEC-RAS (natural y con realineamiento de valle), crear un archivo .pdf con 9 secciones transversales por hoja en formato horizontal presentando todas las secciones del modelo (utilizar la herramienta Plot Cross Section y Print Múltiple). Nombrar como M01A05_CrossSectionNatural.pdf y M01A05_CrossSectionAnthropic.pdf y guardar en la carpeta _/file/report_. | 
| M01A05    | Crear un único reporte en Adobe Acrobat que integre todos los modelos y reportes (utilizar separadores con títulos que indiquen el contenido de cada modelo), cargar en la carpeta _/file/report_ del repositorio de datos como M01A05.pdf.                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 
| M01A05    | En una tabla y al final del informe de avance de esta entrega, indique el detalle de las actividades realizadas por cada integrante de su grupo; utilice las siguientes columnas: `Nombre del integrante`, `Actividades realizadas`, `Tiempo dedicado en horas` (si presenta la entrega individualmente, no es necesaria la presentación de esta tabla).<br><br>Para actividades que no requieren del desarrollo de elementos de avance, indicar si realizo la lectura de la guía de clase y las lecturas indicadas al inicio en los requerimientos.                                                                                                                                                    | 

> Nota 1: para la revisión del proyecto final, guarde los libros cálculo de Microsoft Excel y los archivos generados en esta actividad, en las localizaciones indicadas en cada numeral.
>
> Nota 2: una vez el instructor realice la revisión y el estudiante presente las correcciones o ajustes solicitados, será necesario cargar una nueva versión de los archivos en el repositorio del proyecto, incluyendo o actualizando al final del nombre del archivo, la fecha de presentación en formato aaaammdd y manteniendo las versiones anteriores presentadas.
>
> Nota 3: para facilitar el estudio del terreno natural y los cauces, se deben crear dos modelos de muestreo: el primer modelo tendrá solo los cauces naturales y el segundo modelo el eje trazado de valle suavizado sin los cruces, pero con los tramos naturales aguas arriba, aguas abajo y cauces laterales. Al inicio y entrega del canal a construir, se recomienda extender el tramo natural seleccionado e incluir los cauces que confluyen antes del punto de inicio (tramo en cuenca W19600, W19450, W19440, W20010), debido a que son necesarios para el estudio de los taludes y las pendientes. Recordar que el punto de inicio del proyecto final fue localizado en una zona con alta depositación de sedimentos, para lo cual, será necesario definir una condición de rectificación del fondo de la sección natural que entregará al canal diseñado. Para el modelo de muestreo de tramos naturales, mantener los cauces laterales completos hasta el límite del DTM y para el modelo de muestreo con el nuevo eje de valle, eliminar los tramos remanentes desde el eje del valle hasta la antigua entrega al canal natural.
>
> Nota 4: para los dos modelos de muestreo no es necesario subdividir el cauce principal y el valle en los puntos definidos de inicio y entrega. En el punto de inicio o punto aguas arriba, se debe incluir una sección transversal a máximo 10 cm aguas abajo de este punto y en el punto de entrega se debe incluir una sección transversal a máximo 10 cm aguas arriba del punto.
>
> Nota 5: las secciones transversales dibujadas deben ser lo suficientemente anchas para llegar hasta la cota de confinamiento hidráulico del valle o de la llanura de inundación, especialmente en aquellos tramos donde se encuentra la zona de inicio y entrega.
> 
> Nota 6: en el modelo de muestreo que incluye el valle suavizado, las líneas de banca paralelas solo al eje de los tramos de nuevo valle, deben ser localizadas a 150m a cada lado, esto permitirá evaluar los cortes y rellenos a analizar en entregas posteriores.
> 
> Nota 7: para garantizar la obtención correcta de los perfiles de terreno, especialmente en el cauce principal, en los dos modelos hidráulicos de muestreo se deben nombrar los ríos (river) del cauce principal con el mismo nombre, p. ej., ArroyoElZorro; de esta forma, el abscisado de las secciones transversales será continuo desde la última sección hasta la sección más aguas arriba en el tramo natural remanente inicial. Esta indicación aplica para tanto para el modelo de muestreo natural como para el que contiene el eje del valle suavizado.


## Referencias

* https://www.hec.usace.army.mil/confluence/rasdocs/r2dum/6.6/developing-a-terrain-model-and-geospatial-layers/opening-ras-mapper
* https://www.hec.usace.army.mil/confluence/rasdocs/r2dum/6.6/developing-a-terrain-model-and-geospatial-layers/setting-the-spatial-reference-projection
* https://www.hec.usace.army.mil/confluence/rasdocs/r2dum/6.6/ras-mapper-supported-file-formats


## Control de versiones

| Versión    | Descripción        | Autor                                      | Horas |
|------------|:-------------------|--------------------------------------------|:-----:|
| 2025.06.03 | Migración a GitHub | [rcfdtools](https://github.com/rcfdtools)  |  12   |


##

_R.HCMC es de uso libre para fines académicos, conoce nuestra licencia, cláusulas, condiciones de uso y como referenciar los contenidos publicados en este repositorio, dando [clic aquí](../../LICENSE.md)._

_¡Encontraste útil este repositorio!, apoya su difusión marcando este repositorio con una ⭐ o síguenos dando clic en el botón Follow de [rcfdtools](https://github.com/rcfdtools) en GitHub._


| [:arrow_backward: Anterior](../M01A04/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.SIGE/discussions/99999) | [Siguiente :arrow_forward:](../M01A06/Readme.md) |
|--------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------|--------------------------------------------------|

[^1]: 