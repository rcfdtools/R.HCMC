# 3. Trazado del eje de valle y estimación de radios de curvatura para suavizado
Keywords: `realigment` `curvature-ratio` `clothoid` `m01a03`

Establecer los puntos para el trazado del eje de valle y estimar los radios de curvatura que permitan trazar el corredor del alineamiento del valle suavizado requerido para el diseño sinuoso.

Existen diversas metodologías para estimar la curvatura de suavizado del eje recto del valle. El suavizado tiene como propósito garantizar un adecuado cambio de dirección en el río que permita el flujo o tránsito de las crecientes de forma segura y evitando en lo posible, turbulencias, oleaje y zonas susceptibles a procesos erosivos y/o de depositación de sedimentos, buscando de mantener velocidad constante en el flujo.

<div align="center"><img src="graph/M01A03.png" alt="R.SIGE" width="80%" border="0" /></div>


## Objetivos

* Localizar los puntos fijos de inicio, entrega o cambio de dirección que definirán el trazado del eje recto del valle.
* Trazar el eje recto del valle.
* Estimar el radio de curvatura para el suavizado del valle.
* Trazar el eje curvo suavizado o clotoide de valle utilizando diferentes métodos y herramientas.
* Comparar los ejes suavizados obtenidos.
* Estudiar los elementos que componen una clotoide.


## Requerimientos

Archivos, actividades previas, lecturas y herramientas requeridas para el desarrollo de esta actividad:

<div align="center">

| Requerimiento                                                                                                                            | Descripción                                                                                            |
|:-----------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------|
| [:toolbox:Herramienta](https://www.microsoft.com/es/microsoft-365/excel?market=bz)                                                       | Microsoft Excel 365.                                                                                   |
| [:toolbox:Herramienta](https://qgis.org/)                                                                                                | QGIS 3.42 o superior.                                                    |
| [:toolbox:Herramienta](https://www.autodesk.com/products/civil-3d)                                                                       | Autodesk Civil 3D 2025 o superior.                                       |
| [:open_file_folder:R.HydroTools. RadioCurvaturaValle.xlsx](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/RadioCurvaturaValle) | Libro de cálculo para la Estimación del radio de curvatura para el suavizado del valle en canales, Rc. |
| [:round_pushpin:R.HCMC.NodoValle.shp](../../file/shp/R.HCMC.NodoValle.zip)                                                               | Capa de nodos eje valle recto (creada en actividad anterior).                                          |

</div>

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.


## Conceptos generales

### Consideraciones generales para el trazado del eje de valle

Generalmente, el alineamiento, ancho y suavizado del valle está condicionado por múltiples restricciones.

| Condición o restricción   | Descripción                                                                                                                                                                                                                                                               |
|:--------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Topográfica               | Zonas con bajos que impiden que el canal se trace en corte o zonas que hidráulicamente drenan hacia otras cuencas.                                                                                                                                                        |
| Geotécnica                | Fallas, afloramientos rocosos, acuíferos.                                                                                                                                                                                                                                 |
| Eco-ambiental             | Fauna y flora nativa en suelos de protección. Corredor para el transito de especies endémicas protegidas.                                                                                                                                                                 |
| Infraestructura existente | Instalaciones, vías, canales, tanques, bocatomas, asentamientos humanos.                                                                                                                                                                                                  |
| Territorial               | Incompatibilidad con los usos del suelo definidos en los POT, rondas de protección, zonas declararas de interés histórico. Resguardos indígenas y asentamientos de comunidades protegidas. Zonas agropecuarias productivas con puntos de agua superficial concesionada. |


### Métodos incluidos

| Método                                                                                          | Descripción                                                                                                                                                                                                                                                                                                                                                   |
|:------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1. Manual de procedimientos de pequeños sistemas de riego                                       | Estimación del radio de curvatura del valle para el diseño de canales a caudal máximo. Ref: Manual de procedimientos de pequeños sistemas de riego. Rango de caudales entre 0.5 y 20 m³/s.                                                                                                                                                                    |                                                                                                                                                                    
| 2. Universidad Utah State. Diseño Básico de Canales                                             | Estimación del radio de curvatura del valle para el diseño de canales a caudal máximo. Ref: Universidad Utah State. Diseño Básico de Canales. Rango de caudales entre 15 y 225 m³/s.                                                                                                                                                                          |                                                                                                                                                                          
| 3. En función del tipo de régimen. Subcrítico y Supercrítico                                    | Esta metodología no tiene en cuenta directamente el total caudal transportado por el valle y cauce dominante sino parámetros en función del régimen de flujo. Parámetros de entrada, profundidad del flujo y, velocidad V, ancho superficial T.                                                                                                               |                                                                                                               
| 4. Por factor multiplicador en función del caudal y la base (Wageningen, The Netherlands. 1978) | Estimación del radio de curvatura del valle para el diseño de canales a caudal máximo. Ref: "International Institute For Land Reclamation And Improvement" ILRI, Principios y Aplicaciones del Drenaje, Tomo IV, Wageningen The Netherlands 1978. Rango de caudales mínimos entre 0 y 17 m³/s. Rango de caudales máximos entre 10 y hasta mayores de 20 m³/s. | 
| 5. Por factor multiplicador en función del ancho (Urban Storm Drainage Criteria Manual )        | Estimación del radio de curvatura del valle para el diseño de canales. Ref:  Urban Drainage and Flood Control District. Urban Storm Drainage Criteria Manual Volume 1. Chapter 08 Open Channels, numeral 5.4, el radio de curvatura debe estar entre 3 o 4 veces el ancho superior del canal. Se estima en función del ancho superficial T.                   |                   
| 6. En función del tipo de canal. Salzitegger                                                    | Salzitegger Consult GMBH, Planificación de canales, Zona Piloto Ferreñafe, Tomo II/1. Proyecto Tinajones - Chiclayo 1984. En función del ancho superficial T y el tipo de drenaje o canal.                                                                                                                                                                    |

## 1. Estimación de radios de curvatura

1. En los parámetros de entrada del Método 1 correspondiente al Manual de procedimientos de pequeños sistemas de riego, ingrese el caudal de diseño para la estimación del radio de curvatura del valle, tenga en cuenca que el caudal ingresado deberá corresponder al mayor valor obtenido para el periodo de retorno del valle en cada uno los puntos de estudio localizados a lo largo del valle. Para el caso de estudio, utilizaremos un caudal de diseño de 522.1 m³/s correspondiente al periodo de retorno de 100 años, obtendrá un radio estimado de 2500 metros. 

> Debido a que esta metodología es aplicable a caudales en rangos entre 5 y 100 m³/s, no se recomienda utilizar el radio estimado.

<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.Metodo1a.jpg" alt="R.SIGE" width="40%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.Metodo1b.jpg" alt="R.SIGE" width="40%" border="0" /></div>

2. El método 2, correspondiente al Diseño Básico de Canales de la Universidad Utah State, calcula automáticamente el radio de curvatura en función del caudal ingresado previamente, obtendra un radio estimado de 1825 metros.

<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.Metodo2a.jpg" alt="R.SIGE" width="45%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.Metodo2b.jpg" alt="R.SIGE" width="35%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.Metodo2c.jpg" alt="R.SIGE" width="35%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.Metodo2d.jpg" alt="R.SIGE" width="70%" border="0" /></div>

3. En los parámetros de entrada del Método 3 correspondiente al cálculo de curvatura en función del régimen del flujo, ingrese los valores correspondientes a la profundidad del flujo, velocidad media en el canal y ancho superficial inundable del valle. Para el caso de estudio utilizaremos como referencia un canal de sección compuesta con altura de sección de 3 metros (menos 0.4 metros de borde libre), velocidad máxima de diseño en valle de 3 m/s y ancho superficial de 300 metros en el valle, obteniendo para régimen subcrítico un radio de 900 metros y para supercrítico de 424 metros.

<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.Metodo3.jpg" alt="R.SIGE" width="60%" border="0" /></div>

4. En los parámetros de entrada del Método 4 por factor multiplicador en función del caudal y la base (Wageningen, The Netherlands. 1978), ingresar el ancho en la base de la sección del canal en valle, para el caso de estudio utilizaremos como referencia un valle de 240 metros que combinado con el caudal ingresado de diseño, permite establecer un radio de 1680 metros.

<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.Metodo4.jpg" alt="R.SIGE" width="60%" border="0" /></div>

5. El método 5 por factor multiplicador en función del ancho (Urban Storm Drainage Criteria Manual), calcula automáticamente el radio de curvatura en función del caudal ingresado previamente, obtendra un radio estimado de 1200 metros.

<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.Metodo5.jpg" alt="R.SIGE" width="45%" border="0" /></div>

6. En los parámetros de entrada del Método 6 en función del tipo de canal (Salzitegger), seleccione el tipo de canal a diseñar, para el caso de estudio utilizaremos _Drenaje - Colector principal_, obteniendo un radio de curvatura de 1500 metros.

<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.Metodo6.jpg" alt="R.SIGE" width="45%" border="0" /></div>

7. Compare los resultados obtenidos, defina y justifique textualmente el radio de curvatura a utilizar en su proyecto.

<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.MetodosA.jpg" alt="R.SIGE" width="75%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.MetodosB.jpg" alt="R.SIGE" width="95%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.MetodosC.jpg" alt="R.SIGE" width="75%" border="0" /></div>

Para el caso de estudio, se selecciona el Método 2. Universidad Utah State / Diseño Básico de Canales, con un radio redondeado a 1800 metros debido a que tiene en cuenta un amplio rango de caudales que al ser ajustados a una curva logarítmica ofrecen un ajuste adecuado para su estimación.


## 2. Nodos del eje recto y trazado del alineamiento recto central del valle

1. En QGIS, cargue los archivos shapefile _HMS_Subbasin_v0_, _HMS_River_v0_, _CGG_Vial_v0_ contenidos dentro del modelo hidrológico en la ruta _file/hec/HECHMS_v0_ y la capa de nodos [:round_pushpin:file/shp/R.HCMC.NodoValle.shp](../../file/shp/R.HCMC.NodoValle.zip) generada en la actividad anterior.

<div align="center"><img src="graph/QGIS_AddLayer.jpg" alt="R.SIGE" width="100%" border="0" /></div>

2. Utilizando la herramienta _Vector creation / Points to path_, cree el eje del valle con el nombre de capa _file/shp/RD_EjeValle_v0.shp_. Rotule los nodos a partir del código del eje.

<div align="center"><img src="graph/QGIS_PointsToPath.jpg" alt="R.SIGE" width="60%" border="0" /></div>
<div align="center"><img src="graph/QGIS_PointsToPath1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

3. Desde Layer _Properties / Source / Query Builder_, filtre los nodos y el eje de su proyecto.

<div align="center"><img src="graph/QGIS_QueryBuilder.jpg" alt="R.SIGE" width="100%" border="0" /></div>
<div align="center"><img src="graph/QGIS_QueryBuilder1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

> :fire: Atención: los nodos y ejes mostrados en la ilustración no son los mismos nodos a utilizar en el proyecto final, consulte con el instructor los nodos a utilizar.


## 3. Curva clotoide con QGIS

QGIS dispone de herramientas de digitalización básica y avanzada CAD, sin embargo, la creación de curvas es generada a partir de segmentos rectos sin inclusión de nodos complementarios en intersecciones. Para el desarrollo de este ejemplo utilizaremos el procedimiento genérico de construcción de clotoides, correspondiente a la creación de arcos circulares y segmentos rectos de entre tangencia.

1. Desde el panel lateral _Browser_, cree en la carpeta _file/shp/_ una capa geográfica de líneas en formato shapefile y guarde como _RD_EjeValleSuavizado_QGIS.shp_, utilize el CRS 3116 y cree un campo de atributos numérico doble con el nombre `CurvRatio` y agregue al mapa.

<div align="center"><img src="graph/QGIS_NewShapefileLayer.jpg" alt="R.SIGE" width="100%" border="0" /></div>

> Para facilitar la edición y visualización de la clotoide, agregue el mapa base de Google Satellite desde el conector https://mt1.google.com/vt/lyrs=s&x={x}&y={y}&z={z}.

2. En el panel Layers, seleccione la capa _RD_EjeValleSuavizado_QGIS_ y de clic en el botón de edición de capa, luego seleccione la opción _Add Line Feature_ y _Digitize Shape_; podrá observar que se han activado diferentes herramientas asociadas a formas geométricas.

<div align="center"><img src="graph/QGIS_Digitize1.jpg" alt="R.SIGE" width="100%" border="0" /></div>

3. En la barra _Shape Digitizing Toolbar_, seleccione la herramienta de creación de círculos _Circle from 2 tangents and a point_, luego en la barra de encajado o _Snapping Toolbar_, defina ajuste por segmento y tolerancias en 5 pixeles.

<div align="center"><img src="graph/QGIS_Digitize2.jpg" alt="R.SIGE" width="70%" border="0" /></div>

3. Digitalice dos circunferencias tangentes con radio de curvatura 1800m entre los nodos 1-2-3 y 2-3-4.

> Para terminar la creación de cada círculo tangente de clic derecho en cualquier lugar del mapa y complete el atributo _CurvRatio_.

<div align="center"><img src="graph/QGIS_Digitize3.jpg" alt="R.SIGE" width="70%" border="0" /></div>

4. Utilizando la herramienta _Split_, fraccione las circunferencias creadas y conserve solo los arcos circulares próximos al eje. Primero, seleccione una de las circunferencias, luego la herramienta _Split Features_ y el nodo central o más próximo a la tangencia del valle.

> Recuerde que QGIS crea subtramos rectos de dibujo y no arcos circulares.

<div align="center"><img src="graph/QGIS_Digitize4.jpg" alt="R.SIGE" width="70%" border="0" /></div>
<div align="center"><img src="graph/QGIS_Digitize5.jpg" alt="R.SIGE" width="70%" border="0" /></div>

5. Utilizando las herramientas de dibujo y el encajado por nodos y vertices, complete la digitalización de tramos rectos y entre tangencias y combine las 5 partes en una única polilínea utilizando la herramienta _Merge Selected Features_.

<div align="center"><img src="graph/QGIS_Digitize6.jpg" alt="R.SIGE" width="70%" border="0" /></div>

7. 




## 4. Curva clotoide con Autodesk Autocad






## 5. Curva clotoide con Autodesk Civil 3D




## Actividades de proyecto :triangular_ruler:

Utilizando la [plantilla suministrada](../../file/report/R.HCMC.PlantillaSoporteDesarrollo.docx), cree un documento soporte mostrando las actividades desarrolladas en el orden presentado en esta actividad, junto con los análisis y recomendaciones realizadas, convierta a Adobe Acrobat (.pdf) y guarde en la carpeta /activity/ del repositorio de datos del proyecto; nombre el archivo con el código de la actividad agregando al final la fecha de control documental en formato aaaammdd (p. ej. M01A00_20250531.pdf).

En la siguiente tabla se listan las actividades que deben ser desarrolladas y documentadas por cada estudiante o grupo de proyecto.

| Actividad | Alcance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| M01A01    | Descargar el archivo [R.HydroTools.DisenoCaucesParametros.xlsx](https://github.com/rcfdtools/R.HydroTools/blob/main/tool/DisenoCaucesParametros/R.HydroTools.DisenoCaucesParametros.xlsx) disponible en GitHub, e incluirlo en el repositorio.                                                                                                                                                                                                                                                                                                       | 
| M01A01    | Investigar, verificar y registrar en el libro de Excel, los parámetros técnicos, hidráulicos e hidrológicos indicados en esta actividad.<br><br>Para el grupo de parámetros normativos, ambientales / sociales y territoriales, revisar los parámetros actualmente reportados, investigar, registrar y actualizar.                                                                                                                                                                                                                                   | 
| M01A01    | En una tabla y al final del informe de avance de esta entrega, indique el detalle de las actividades realizadas por cada integrante de su grupo; utilice las siguientes columnas: `Nombre del integrante`, `Actividades realizadas`, `Tiempo dedicado en horas` (si presenta la entrega individualmente, no es necesaria la presentación de esta tabla).<br><br>Para actividades que no requieren del desarrollo de elementos de avance, indicar si realizo la lectura de la guía de clase y las lecturas indicadas al inicio en los requerimientos. | 

> :blue_heart: Una vez el instructor realice la revisión y el estudiante presente las correcciones o ajustes solicitados, será necesario cargar una nueva versión de los archivos en el repositorio del proyecto, incluyendo o actualizando al final del nombre del archivo, la fecha de presentación en formato aaaammdd y manteniendo las versiones anteriores presentadas.


## Referencias

* http://www.fao.org/3/a-at787s.pdf
* Manual de procedimientos de pequeños sistemas de riego.
* Universidad Utah State, Diseño Básico de Canales.
* International Institute For Land Reclamation And Improvement" ILRI, Principios y Aplicaciones del Drenaje, Tomo IV, Wageningen, The Netherlands. 1978.
* Urban Drainage and Flood Control District. Urban Storm Drainage Criteria Manual Volume 1. Chapter 08 Open Channels, numeral 5.4
* http://cybertesis.uach.cl/tesis/uach/2011/bmfcim722p/doc/bmfcim722p.pdf
* Salzitegger Consult GMBH, Planificación de canales, Zona Piloto Ferreñafe, Tomo II/1. Proyecto Tinajones - Chiclayo 1984.
* https://www.u-cursos.cl/ Facultad de ingeniería


## Control de versiones

| Versión    | Descripción                                                                                                                                                                    | Autor                                      | Horas |
|------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------|:-----:|
| 2024.02.31  | Migración a GitHub                                                                                                                                                             | [rcfdtools](https://github.com/rcfdtools)  |   8   |
| 2022.07.25 | Actualización general de documentación.                                                                                                                                        | [rcfdtools](https://github.com/rcfdtools)  |  0.5  |
| 2021.10.14 | Actualización general de formato.                                                                                                                                              | [rcfdtools](https://github.com/rcfdtools)  |   2   |
| 2020.10.11 | Inclusión de Método 5. Por factor multiplicador en función del ancho (Urban Storm Drainage Criteria Manual). Inclusión de Método 6. En función del tipo de canal. Salzitegger. | [rcfdtools](https://github.com/rcfdtools)  |   2   |
| 2016.05.19 | Versión inicial.                                                                                                                                                               | [rcfdtools](https://github.com/rcfdtools)  |   8   |



##

_R.HCMC es de uso libre para fines académicos, conoce nuestra licencia, cláusulas, condiciones de uso y como referenciar los contenidos publicados en este repositorio, dando [clic aquí](../../LICENSE.md)._

_¡Encontraste útil este repositorio!, apoya su difusión marcando este repositorio con una ⭐ o síguenos dando clic en el botón Follow de [rcfdtools](https://github.com/rcfdtools) en GitHub._


| [:arrow_backward: Anterior](../M01A02/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.SIGE/discussions/99999) | [Siguiente :arrow_forward:](../M01A04/Readme.md) |
|--------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------|--------------------------------------------------|

[^1]: 