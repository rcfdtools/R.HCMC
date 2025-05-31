# 3. Trazado del eje de valle y estimación de radios de curvatura para suavizado
Keywords: `realigment` `curvature-ratio` `m01a03`

Establecer los puntos para el trazado del eje de valle y estimar los radios de curvatura que permitan trazar el corredor del alineamiento del valle suavizado requerido para el diseño sinuoso.

Existen diversas metodologías para estimar la curvatura de suavizado del eje recto del valle. El suavizado tiene como propósito garantizar un adecuado cambio de dirección en el río que permita el flujo o tránsito de las crecientes de forma segura y evitando en lo posible, turbulencias, oleaje y zonas susceptibles a procesos erosivos y/o de depositación de sedimentos, buscando de mantener velocidad constante en el flujo.

<div align="center"><img src="graph/M01A03.png" alt="R.SIGE" width="100%" border="0" /></div>


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

| Requerimiento                                                                                           | Descripción                                                                                            |
|:--------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------|
| [:toolbox:Herramienta](https://www.microsoft.com/es/microsoft-365/excel?market=bz)                      | Microsoft Excel 365.                                                                                   |
| [:open_file_folder:R.HydroTools.RadioCurvaturaValle.xlsx](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/RadioCurvaturaValle) | Libro de cálculo para la Estimación del radio de curvatura para el suavizado del valle en canales, Rc. |

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

## Procedimiento general

1. En los parámetros de entrada del Método 1, ingrese el caudal de diseño para la estimación del radio de curvatura del valle, tenga en cuenca que el caudal ingresado deberá corresponder al mayor valor obtenido para el periodo de retorno del valle en cada uno los puntos de estudio localizados a lo largo del valle. Para el caso de estudio, utilizaremos un caudal de diseño de 522.1 m³/s correspondiente al periodo de retorno de 100 años, obtendrá un radio estimado de 2500 metros. 

> Debido a que esta metodología es aplicable a caudales en rangos entre 5 y 100 m³/s, no se recomienda utilizar el radio estimado.

<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.Metodo1a.jpg" alt="R.SIGE" width="50%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.RadioCurvaturaValle.Metodo1b.jpg" alt="R.SIGE" width="50%" border="0" /></div>





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


| [:arrow_backward: Anterior](../M01A00/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.SIGE/discussions/99999) | [Siguiente :arrow_forward:](../M01A02/Readme.md) |
|--------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------|--------------------------------------------------|

[^1]: 