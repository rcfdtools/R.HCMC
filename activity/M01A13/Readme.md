# 1.13. Diseño geométrico e hidráulico vertical del cauce principal de desviación y cauces laterales menores
Keywords: `hydraulics` `hydraulic-design` `critical-depth` `normal-depth` `yn` `yc` `hec-ras-hydraulic-design` `trapezoidal` `circular` `rectangular` `triangular` `tractive-force` `river` `valley` `confined-valley` `m01a13`

Dimensionar la sección hidráulica dominante (1) y de creciente (2) del cauce principal y de los cauces laterales menores, verificando a flujo uniforme la capacidad hidráulica de la sección compuesta (3) y el borde libre requerido.

<div align="center"><img src="graph/M01A13.png" alt="R.SIGE" width="60%" border="0" /></div>


## Objetivos

* Diseñar la sección dominante por los métodos Copeland, Régimen de Flujo y Fuerza tractiva.
* Diseñar la sección de creciente por los métodos Copeland, Régimen de Flujo y Fuerza tractiva.
* Verificar la sección compuesta por flujo uniforme.
* Crear un prototipo digital del diseño realizado y modelar a flujo permanente y no permanente.

<div align="center"><img src="graph/SeccionCompuesta.jpg" alt="R.SIGE" width="60%" border="0" /></div>


## Requerimientos

Archivos, actividades previas, lecturas y herramientas requeridas para el desarrollo de esta actividad:

<div align="center">

| Requerimiento                                                                                                                                                          | Descripción                                                                                     |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------|
| [:toolbox:Herramienta](https://www.microsoft.com/es/microsoft-365/excel?market=bz)                                                                                     | Microsoft Excel 365.                                                                            |
| [:toolbox:Herramienta](https://www.hec.usace.army.mil/software/hec-ras/)                                                                                               | HEC-RAS 6.6 o superior.                                                                         |
| [:open_file_folder:R.HydroTools.Diseno GeometricoHidraulicoVertical.xlsm](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoGeometricoHidraulicoVertical) | Libro de cálculo para el diseño geométrico e hidráulico vertical de canales a superficie libre. |
| [:open_file_folder:Modelo hidráulico HECRAS_v0](../../file/hec)                                                                                                        | Modelo hidráulico de muestreo HEC-RAS v0 creado en actividad [M01A05](../M01A05/Readme.md).     |
| [:chart_with_upwards_trend:M01A13.pptx](M01A13.pptx)                                                                                                                   | Plantilla para presentación de esquemas sección compuesta.                                      |

</div>

> Para los diferentes avances de proyecto, es necesario guardar y publicar las diferentes versiones generadas del (los) libro (s) de Microsoft Excel y reportes o informes, agregando al final la fecha de control documental en formato aaaammdd, p. ej. _R.HydroTools.DisenoCaucesParametros.20250528.xlsx_.


## 0. Creación de proyecto HEC-RAS

1. En HEC-RAS cree un proyecto nuevo y nombre como _/file/hec/HECRAS_v0_HD/HECRAS_v0_HD.prj_. 

> En actividades anteriores, establecimos por defecto el sistema internacional de unidades, sin embargo, es indispensable verificar que el proyecto sea creadoo en este sistema. 

<div align="center"><img src="graph/HECRAS_NewProject.jpg" alt="R.SIGE" width="80%" border="0" /></div>

2. Ingrese al Módulo de Diseño, menú _Run / Hydraulic Design Functions…_ o clic en el botón _Perform Hydraulic Design Computations_.  

En la ventana de diseño hidráulico y en _Type / Stable Channel Design…_, observará que HEC-RAS dispone de 3 métodos diferentes para el diseño de sección estable (secciones que hidráulicamente se encuentran en el límite entre la agradación o degradación del lecho).

* Copeland
* Regime
* Tractive Force

<div align="center"><img src="graph/HECRAS_HD.jpg" alt="R.SIGE" width="80%" border="0" /></div>


## 1. Diseño por Método de Copeland en HEC-RAS


### 1.1. Sección dominante (river)

Para el diseño geométrico e hidráulico vertical utilizaremos los siguientes parámetros registrados en el libro global de diseño en Excel:

* Caudal de diseño Tr 2.33yr (m³/s) = 130.
* Temperatura Agua (ºC) = 15.
* Gradación de los materiales del lecho: D84 = 0.18 mm, D50 = 0.146 mm, D16 = 0.032 mm.
* Taludes = 14H : 1V.
* Rugosidad canal dominante = 0.018.

1. En la ventana del módulo de diseño, ingrese los parámetros de la sección dominante en la pestaña del método de Copelad.

> Concentración de sedimentos: calculados por HEC-RAS en función de la geometría de la sección suponiendo que el cauce natural tiene un ancho en la base del canal dominante de 20 m, altura máxima de 3 m y la pendiente de la línea de energía es paralela a la del fondo del cauce sinuoso S = 0.000897, sedimentos totales = 2605.57 ppm.

<div align="center"><img src="graph/HECRAS_HDRiverCopeland.jpg" alt="R.SIGE" width="90%" border="0" /></div>
<div align="center"><img src="graph/HECRAS_HDRiverCopeland1.jpg" alt="R.SIGE" width="20%" border="0" /></div>

Una vez ingresados los valores, de clic en el botón _Apply_.

2. De clic en el botón _Compute_, aparecerá entonces una ventana con diferentes geometrías propuestas que cumplen con el diseño de sección estable para los parámetros ingresados.

<div align="center"><img src="graph/HECRAS_HDRiverCopeland2.jpg" alt="R.SIGE" width="80%" border="0" /></div>

Para la selección de la sección de diseño, es necesario tener en cuenta que existe una restricción preestablecida respecto al alto máximo de 3 metros disponible la sección natural compuesta y al borde libre de 0.4 metros, por tanto, seleccionar por ejemplo la sección diseñada que utiliza 1.5 metros de la altura total para el tránsito del caudal dominante.

La sección seleccionada de 1.5 m de altura además de cumplir con los criterios de sección estable, cumple con los criterios de velocidad (1.7 m/s < 2 m/s) y cortante (11.44 N/m² ≈ 10 N/m²).

> Para la sección correspondiente al tránsito del caudal dominante, NO es necesario disponer de borde libre debido a que se considera válido que la llanura de inundación confinada pueda ser parcialmente inundada.

3. Verifique las curvas de estabilidad 1 y 2 trazadas para la sección diseñada a partir de los parámetros ingresados.

> Atención: las gráficas presentan una inconsistencia en las unidades refiriéndose al Sistema Inglés, los valores mostrados corresponden a las unidades del Sistema Internacional. El caudal utilizado es 130 m³/s.

<div align="center"><img src="graph/HECRAS_HDRiverCopeland3.jpg" alt="R.SIGE" width="60%" border="0" /></div>

Por tratarse de una sección ancha (28.96 m) el lecho podría sufrir algún nivel de degradación y para la altura seleccionada de 1.5 metros. Entonces, el canal diseñado podrá presentar algunos fenómenos de erosión de sedimentos provenientes de su propio lecho cuando esté recién excavado y sin vegetación acuática o hierbas en las zonas de talud.

<div align="center"><img src="graph/HECRAS_HDRiverCopeland4.jpg" alt="R.SIGE" width="60%" border="0" /></div>
<div align="center"><img src="graph/HECRAS_HDRiverCopeland6.jpg" alt="R.SIGE" width="90%" border="0" /></div>

4. En _File / Save Hydraulic Design Data_, guarde el diseño como _RiverCopeland_.

<div align="center"><img src="graph/HECRAS_HDRiverCopeland5.jpg" alt="R.SIGE" width="65%" border="0" /></div>


### 1.2. Sección creciente (valley)

Para el diseño geométrico e hidráulico vertical utilizaremos los siguientes parámetros registrados en el libro global de diseño en Excel:

* Caudal de diseño Tr 100yr (m³/s) = 392 (Tr 100yr = 522 – Tr 2.33yr = 130).
* Temperatura Agua (ºC) = 15.
* Gradación de los materiales del lecho: D84 = 0.18 mm, D50 = 0.146 mm, D16 = 0.032 mm.
* Taludes = 14H : 1V.
* Rugosidad canal dominante = 0.035.

> Concentración de sedimentos = Calculados por HEC-RAS en función de la geometría de la sección suponiendo que el cauce natural tiene un ancho de llanura en la base de 230 m, altura máxima de 3 m y la pendiente de la línea de energía es paralela a la del fondo del cauce sinuoso S = 0.000897. Sedimentos totales = 4414.83 ppm.

1. En el menú _File / New Hydraulic Design Data_, guarde como _ValleyCopeland_ e ingrese los parámetros requeridos.

<div align="center"><img src="graph/HECRAS_HDValleyCopeland.jpg" alt="R.SIGE" width="90%" border="0" /></div>

2. Clic en _Apply_ y _Compute_, aparecerá entonces una ventana con diferentes geometrías propuestas que cumplen con el diseño de sección estable para los parámetros ingresados.

Para la selección de la sección de diseño, es necesario tener en cuenta que existe una restricción preestablecida respecto al alto máximo de 3 m disponible la sección natural compuesta, el borde libre de 0.4 m y la altura de sección seleccionada de 1.5 m para la zona del cauce dominante. (para el ejercicio de clase seleccionar la sección con menor elevación)

<div align="center"><img src="graph/HECRAS_HDValleyCopeland1.jpg" alt="R.SIGE" width="80%" border="0" /></div>

La sección seleccionada de 1.39 m de altura además de cumplir con los criterios de sección estable, cumple con los criterios de velocidad (1.72 m/s < 3 m/s) y cortante (11.93 N/m² ≈ 20 N/m²). Tener en cuenta que el borde libre disponible para este diseño es de 0.11 m (3 m – 1.5 m – 1.39 m) inferior al estimado de 0.4 m. 

<div align="center"><img src="graph/HECRAS_HDValleyCopeland2.jpg" alt="R.SIGE" width="90%" border="0" /></div>


### 1.3. Sección compuesta (composite)

* Corona cauce dominante 70.96 m = 2 * (14 * 1.5 ) + 28.96
* T Ancho Superficial 183.48 m = 2 * (14 * 1.39) + 144.56
* Corona Valle 186.56 m = 2 * (14 * 1.5) + 144.56
* Huella para mecanización = (300 – 186.56) / 2 = 56.72 m

<div align="center"><img src="graph/HECRAS_HDCompositeCopeland.jpg" alt="R.SIGE" width="70%" border="0" /></div>

> Posteriormente, verificaremos por flujo uniforme la altura del borde libre de la sección compuesta.


## 2. Diseño por Método del Régimen de Flujo en HEC-RAS

Para el diseño geométrico e hidráulico vertical utilizaremos los siguientes parámetros registrados en el libro global de diseño en Excel:

* Caudal de diseño Tr 100yr (m³/s) = 392 (Tr 100yr = 522 – Tr 2.33yr = 130).
* Gradación de los materiales del lecho D50 = 0.146 mm.
* Concentración de sedimentos: 2605.57 ppm + 4414.83 ppm = 7020.4 ppm. Corresponde a los sedimentos calculados por el método de Copeland para la sección de dominante y de creciente
* Temperatura Agua (ºC) = 15.
* Factor lateral = 0.1 suponiendo que las bancas son desmoronables.

En el menú _File / New Hydraulic Design Data_, guarde como _ValleyRegime_ e ingrese los parámetros requeridos.

<div align="center"><img src="graph/HECRAS_HDValleyRegime.jpg" alt="R.SIGE" width="80%" border="0" /></div>

La sección obtenida es de 892.49 metros de ancho, altura de lámina de agua en 0.22 metros, pendiente de 0.000663 y rugosidad del lecho de 0.0046.

> Como observa, en este método no se ingresan las inclinaciones de los taludes laterales y pendiente, la sección es resuelta en función de la estabilidad.


## 3. Diseño por Método de la Fuerza Tractiva (Lane) en HEC-RAS


### 3.1. Sección dominante (river)

Para el diseño geométrico e hidráulico vertical utilizaremos los siguientes parámetros registrados en el libro global de diseño en Excel:

* Caudal de diseño Tr 2.33yr (m³/s) = 130
* Temperatura Agua (ºC) = 15
* Gradación de los materiales del lecho d75 = 0.172 mm.
* Ángulo de reposo de los materiales (º): 35
* Talud lateral = 14H:1V.
* n rugosidad de Manning : 0.018
* Pendiente de diseño del cauce sinuoso (m/m): 0.000897.
* Altura estimada = 1.5m.

1. En el menú _File / New Hydraulic Design Data_, guarde como _RiverTractiveForceLane_ e ingrese los parámetros requeridos.

> Para establecer las variables a resolver (texto en **negrilla**), usar doble clic. Resolver **d50** zona central y ancho de base en la sección **W**.

<div align="center"><img src="graph/HECRAS_HDRiverTractiveForceLane.jpg" alt="R.SIGE" width="90%" border="0" /></div>

Resultados:

* Ancho en la base = 38.69 metros.
* Ancho en la corona = 80.64 metros.
* Tamaño de partículas requeridas para lecho estable = 16.2 mm.


### 3.2. Sección creciente (valley)

Para el diseño geométrico e hidráulico vertical utilizaremos los siguientes parámetros registrados en el libro global de diseño en Excel:

* Caudal de diseño Tr 100yr (m³/s) = 392 (Tr 100yr = 522 – Tr 2.33yr = 130).
* Temperatura Agua (ºC) = 15.
* Gradación de los materiales del lecho d75 = 0.172 mm.
* Ángulo de reposo de los materiales (º): 35
* Talud lateral = 14H:1V.
* n rugosidad de Manning: 0.035 en bancas y 0.018 en el lecho central
* Pendiente de diseño del cauce sinuoso (m/m): 0.000897.
* Altura estimada = 1.1 m.

> La altura total de la sección deberá ser máximo de 3 metros correspondientes a 1.5m para el caudal dominante, 1.1m para crecientes y 0.4m para borde libre.

1. En el menú _File / New Hydraulic Design Data_, guarde como _ValleyTractiveForceLane_ e ingrese los parámetros requeridos.

<div align="center"><img src="graph/HECRAS_HDValleyTractiveForceLane.jpg" alt="R.SIGE" width="90%" border="0" /></div>

Resultados:

* Ancho en la base = 200.24 metros.
* Ancho en la corona = 231.04 metros.
* Tamaño de partículas requeridas para lecho estable = 12.7 mm.

La diferencia en los resultados con respecto al Método de Shields corresponde a un mayor tamaño de material para la protección del lecho.


### 3.3. Sección compuesta (composite)

Geometría ajustada de la Sección a utilizar en el caso de estudio: al corredor disponible de 300 metros se le descontó una huella de mecanización de 24.4 metros. A la base del valle se le sumó aproximadamente 4.5 metros a cada lado para prevenir co-alineación de taludes.

div align="center"><img src="graph/HECRAS_HDCompositeTractiveForceLane.jpg" alt="R.SIGE" width="70%" border="0" /></div>

> Para regularizar el diseño y facilitar el replanteo en terreno se recomienda ajustar los anchos calculados a valores enteros por encima del valor obtenido.


## 4. Diseño por Método de la Fuerza Tractiva (Shields) en HEC-RAS


### 4.1. Sección dominante (river)

Para el diseño geométrico e hidráulico vertical utilizaremos los siguientes parámetros registrados en el libro global de diseño en Excel:

* Caudal de diseño Tr 2.33yr (m³/s) = 130
* Temperatura Agua (ºC) = 15
* Gradación de los materiales del lecho d50 = 0.146 mm.
* Ángulo de reposo de los materiales (º): 35
* Talud lateral = 14H:1V.
* n rugosidad de Manning : 0.018
* Pendiente de diseño del cauce sinuoso (m/m): 0.000897.
* Altura estimada = 1.5m.

1. En el menú _File / New Hydraulic Design Data_, guarde como _RiverTractiveForceShields_ e ingrese los parámetros requeridos.

> Para establecer las variables a resolver (texto en **negrilla**), usar doble clic. Resolver **d50** zona central y ancho de base en la sección **W**.

<div align="center"><img src="graph/HECRAS_HDRiverTractiveForceShields.jpg" alt="R.SIGE" width="90%" border="0" /></div>

Resultados:

* Ancho en la base = 38.68 metros.
* Ancho en la corona = 80.68 metros.
* Tamaño de partículas requeridas para lecho estable = 13.8 mm.


### 4.2. Sección creciente (valley)

Para el diseño geométrico e hidráulico vertical utilizaremos los siguientes parámetros registrados en el libro global de diseño en Excel:

* Caudal de diseño Tr 100yr (m³/s) = 392 (Tr 100yr = 522 – Tr 2.33yr = 130).
* Temperatura Agua (ºC) = 15.
* Gradación de los materiales del lecho D50 = 0.146 mm.
* Ángulo de reposo de los materiales (º): 35
* Talud lateral = 14H:1V.
* n rugosidad de Manning: 0.035 en bancas y 0.018 en el lecho central
* Pendiente de diseño del cauce sinuoso (m/m): 0.000897.
* Altura estimada = 1.1 m.

> La altura total de la sección deberá ser máximo de 3 metros correspondientes a 1.5m para el caudal dominante, 1.1m para crecientes y 0.4m para borde libre.

1. En el menú _File / New Hydraulic Design Data_, guarde como _ValleyTractiveForceShields_ e ingrese los parámetros requeridos.

<div align="center"><img src="graph/HECRAS_HDValleyTractiveForceShields.jpg" alt="R.SIGE" width="90%" border="0" /></div>

Resultados:

* Ancho en la base = 200.24 metros.
* Ancho en la corona = 231.04 metros.
* Tamaño de partículas requeridas para lecho estable = 10.8 mm.


### 4.3. Sección compuesta (composite)

Geometría ajustada de la Sección a utilizar en el caso de estudio: al corredor disponible de 300 metros se le descontó una huella de mecanización de 24.4 metros. A la base del valle se le sumó aproximadamente 4.5 metros a cada lado para prevenir co-alineación de taludes.

> Atención: los datos de este esquema se utilizarán para el diseño sinuoso

<div align="center"><img src="graph/HECRAS_HDCompositeTractiveForceShields1.jpg" alt="R.SIGE" width="80%" border="0" /></div>

> Para regularizar el diseño y facilitar el replanteo en terreno se recomienda ajustar los anchos calculados a valores enteros por encima del valor obtenido.


## 5. Verificación sección compuesta por Flujo Uniforme en HEC-RAS

Luego del diseño hidráulico, es necesario comprobar que la sección compuesta es capaz de drenar el caudal de la creciente de diseño de acuerdo a los parámetros y restricciones establecidas:

* Ancho base canal dominante desde el eje (m) = 20. (40 m / 2)
* Ancho base canal creciente desde el eje (m) = 104.6. (209.2 m / 2)
* Taludes = 14H:1V.
* Altura sección dominante (m) = 1.5.
* Altura sección creciente (m) = 1.5. (1.1 m + 0.4 m). Sumar el alto estimado más el borde libre.
* s pendiente (m/m) = 0.000897.

1. En el módulo de diseño ir al menú _Type / NewHydraulic Design Data…._ y nombrar como _CompositeTractiveForceShieldUniformFlow_.

<div align="center"><img src="graph/HECRAS_HDCompositeTractiveForceShieldsUniformFlow.jpg" alt="R.SIGE" width="80%" border="0" /></div>

2. En el módulo de diseño ir al menú _Type / Uniform Flow…._ e ingresar en la pestaña _Width_ los parámetros y geometría obtenida del diseño hidráulico:

> Para la elevación inversa o cota de fondo, puede utilizar 0 cómo valor de referencia o la cota real del fondo en el inicio del nuevo realineamiento, correspondiente a 70.5 metros.
> 
> Cota máxima lámina de agua = 2.6 m, considerando el borde libre de diseño definido en actividades anteriores.

<div align="center"><img src="graph/HECRAS_HDCompositeTractiveForceShieldsUniformFlow1.jpg" alt="R.SIGE" width="80%" border="0" /></div>

3. Seleccionar _Compute Widths_ usando _OverBank_, oprimir en _Apply_ y _Compute_.

<div align="center"><img src="graph/HECRAS_HDCompositeTractiveForceShieldsUniformFlow2.jpg" alt="R.SIGE" width="80%" border="0" /></div>

4. Modificar los valores de rugosidad mostrados por los valores de diseño y volver a ejecutar _Apply_ y _Compute_.

> Observará que el canal diseñado requiere de una sección mucho más amplia para poder conservar el borde libre de 0.4m. Aproximadamente de 308m en la base de la sección de creciente.

<div align="center"><img src="graph/HECRAS_HDCompositeTractiveForceShieldsUniformFlow3.jpg" alt="R.SIGE" width="80%" border="0" /></div>

5. Debido a que la verificación de la sección por flujo uniforme no tiene en cuenta la amortiguación por el tránsito del hidrograma de entrada, se puede considerar que la altura máxima lámina de agua puede estar mucho más elevada y cercana a 2.8 metros, dejando un borde libre de 0.2 m.

Modificar la altura máxima de la lámina de agua a 2.8 m y volver a calcular la sección. Observará que el ancho de la sección estimada para el valle de creciente es de 98.6m x 2 = 197.2 m de ancho con borde libre de 0.2 m.

El ancho estimado de la sección para la verificación por flujo uniforme es menor al ancho estimado de 200.24 m calculado por el método de la fuerza tractiva.

> Posteriormente, cuando se realice la modelación por flujo no uniforme, observará que el borde libre podrá estar cercano a 0.4 m debido al tránsito y amortiguación de la creciente de diseño (dependiendo del tipo de condición de frontera empleado aguas abajo).

<div align="center"><img src="graph/HECRAS_HDCompositeTractiveForceShieldsUniformFlow4.jpg" alt="R.SIGE" width="80%" border="0" /></div>


## 6. Diseño cauce lateral por Método de la Fuerza Tractiva (Shields) en HEC-RAS

Para el diseño del cauce lateral utilizar los parámetros estimados y registrados para la cuenca W19610:

* Periodo de retorno: Tr 25 años para factor de atenuación 1.00 (o el periodo definido para su proyecto).
* Diseño de sección: trapezoidal simple.
* Caudal de diseño Tr 25yr (m³/s) = 93.3
* Temperatura Agua (ºC) = 15.
* Gradación de los materiales del lecho D50 = 0.146 mm.
* Ángulo de reposo de los materiales (º): 35
* Talud lateral = 10H:1V (estimado a partir de las secciones naturales existentes del cauce lateral).
* n rugosidad de Manning : lecho 0.018, valle 0.035.
* Pendiente de diseño del cauce sinuoso (m/m):  0.00129 (estimado a partir del perfil del cauce lateral).*
* Altura total estimada = 3 m.

1. En el menú _File / New Hydraulic Design Data_, guarde como _LateralRiverTractiveForceShields_ e ingrese los parámetros requeridos.

<div align="center"><img src="graph/HECRAS_HDLateralRiverTractiveForceShields.jpg" alt="R.SIGE" width="90%" border="0" /></div>

Resultados:

* Ancho en la base = 7.24 metros.
* Ancho en la corona = 67.24 metros.
* Tamaño de partículas requeridas para lecho estable = 19.1 mm.


## 7. Diseño cauce lateral por Método de la Fuerza Tractiva (Shields) en R.HydroTools

Utilizando el libro de diseño y análisis [R.HydroTools.DisenoGeometricoHidraulicoVertical.xlsm](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoGeometricoHidraulicoVertical), realice el diseño de la sección estable por el Método de Shields, considerando la curvatura del valle suavizado.

> Previamente, realizamos en la actividad [M01A10](../M01A10), el análisis de la sinuosidad, obteniendo como referencia un factor de 1.29686 para el nuevo cauce sinuoso.
> 
> Considerando que el [eje del valle recto](../../file/table/R.HCMC.NodoValle.xlsx) (entre el nodo inicial y final) tiene una longitud de 4866.87 metros y que el valle suavizado es de 5158.536 metros, el factor de sinuosidad aplicable solo al valle es de 1.0599.


### 7.1. Sección dominante (river)

1. En el libro de Excel, ingrese los parámetros de diseño.

> Para establecer el tipo de sinuosidad y el porcentaje de reducción aplicable a la fuerza tractiva permisible, utilizaremos el factor de sinuosidad 1.29686, con lo que podemos definir 25% de reducción para el cauce dominante, correspondiente a un canal moderadamente sinuoso.

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.FuerzaTractivaRio.jpg" alt="R.SIGE" width="70%" border="0" /></div>

2. Para los parámetros establecidos, encuentre el ancho en la base del canal usando la ecuación de Manning.

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.FuerzaTractivaRio1.jpg" alt="R.SIGE" width="70%" border="0" /></div>

3. Estime el factor de reducción del esfuerzo cortante crítico.

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.FuerzaTractivaRio2.jpg" alt="R.SIGE" width="70%" border="0" /></div>

4. Estime la fuerza tractiva por unidad de área mojada, τo, el tamaño mínimo de partículas requeridas en el lecho para conformar sección estable. Ingrese valores d50 hasta encontrar porcentajes positivos de estabilidad.

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.FuerzaTractivaRio3.jpg" alt="R.SIGE" width="70%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.FuerzaTractivaRio4.jpg" alt="R.SIGE" width="70%" border="0" /></div>

Para la sección del cauce dominante, el tamaño de partículas de recubrimiento a utilizar es de 12 mm en los costados o bancas y 15.5 mm en el fondo, la sección hidráulica tiene un ancho de 71.23 metros con profundidad de 1.5 metros.

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.FuerzaTractivaRio5.jpg" alt="R.SIGE" width="70%" border="0" /></div>

> Con respecto a los valores obtenidos en el módulo de diseño de HEC-RAS cuyo tamaño de partículas de recubrimiento del lecho fue de 13.8 mm, el tamaño considerando la sinuosidad del cauce es mayor y corresponde a 15.5 mm.


### 7.2. Sección creciente (valley)

1. En el libro de Excel, ingrese los parámetros de diseño.

> Para establecer el tipo de sinuosidad y el porcentaje de reducción aplicable a la fuerza tractiva permisible, utilizaremos el factor de sinuosidad 1.0500, con lo que podemos definir 10% de reducción para el cauce dominante, correspondiente a un canal ligeramente sinuoso.
> 
> Con respecto a la [pendiente del valle](../M01A07), utilizaremos como referencia el valor obtenido en actividades anteriores, correspondiente a 0.0011631 m/m. Para su proyecto, evalúe utilizando además la pendiente del cauce principal.
> 
> Con respecto al borde libre, utilizaremos como referencia un valor de 0.2 metros, siguiendo las mismas directrices de la verificación realizada por flujo uniforme, por lo que la altura de diseño del valle será de 1.3 metros.

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.FuerzaTractivaValle.jpg" alt="R.SIGE" width="70%" border="0" /></div>

2. Para los parámetros establecidos, encuentre el ancho en la base del canal usando la ecuación de Manning.

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.FuerzaTractivaValle1.jpg" alt="R.SIGE" width="70%" border="0" /></div>

3. Estime el factor de reducción del esfuerzo cortante crítico.

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.FuerzaTractivaValle2.jpg" alt="R.SIGE" width="70%" border="0" /></div>

4. Estime la fuerza tractiva por unidad de área mojada, τo, el tamaño mínimo de partículas requeridas en el lecho para conformar sección estable. Ingrese valores d50 hasta encontrar porcentajes positivos de estabilidad.

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.FuerzaTractivaValle3.jpg" alt="R.SIGE" width="70%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.FuerzaTractivaValle4.jpg" alt="R.SIGE" width="70%" border="0" /></div>

Para la sección del cauce dominante, el tamaño de partículas de recubrimiento a utilizar es de 14 mm en los costados o bancas y 18.2 mm en el fondo, la sección hidráulica tiene un ancho de 162.85 metros con profundidad de 1.3 metros.

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.FuerzaTractivaValle5.jpg" alt="R.SIGE" width="70%" border="0" /></div>

> Con respecto a los valores obtenidos en el módulo de diseño de HEC-RAS cuyo tamaño de partículas de recubrimiento del lecho fue de 10.8 mm, el tamaño considerando la sinuosidad del cauce y la pendiente del valle suavizado es mayor y corresponde a 18.2 mm.


## 8. Memoria de diseño, geometría de secciones, Yn, Yc

En el libro de diseño y análisis [R.HydroTools.DisenoGeometricoHidraulicoVertical.xlsm](https://github.com/rcfdtools/R.HydroTools/tree/main/tool/DisenoGeometricoHidraulicoVertical), registre los valores de las geometrías de diseño a aplicar en el cauce principal (sección compuesta) y en cauces laterales, verifique la secuencia de comandos CAD y calcule la profundidad normal - Yn y la profundidad crítica del flujo Yc.

> La hoja de memoria de diseño hoja no realiza ningún cálculo de diseño, solo es utilizada para registrar los parámetros de entrada y geometría obtenida de diseño en HEC-RAS. A través de los datos geométricos de entrada se ensambla la tabla de valores de estación y elevación requeridos para modelación hidráulica de canales prototipo en HEC-RAS.


### 8.1 Cauce principal

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.MainChannel.jpg" alt="R.SIGE" width="85%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.MainChannel1.jpg" alt="R.SIGE" width="85%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.MainChannel2.jpg" alt="R.SIGE" width="70%" border="0" /></div>

Para el cálculo de la profundidad hidráulica normal y crítica del cauce sinuoso, utilizaremos los mismos parámetros de entrada utilizados en el módulo HD de HEC-RAS, obtendremos que Yn = 1.328 metros y Yc = 0.916 metros, cuyos valores indican que el perfil del flujo en el canal es M2. 

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.MainChannelRiverYnYc.jpg" alt="R.SIGE" width="85%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.MainChannelRiverYnYc1.jpg" alt="R.SIGE" width="85%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.MainChannelRiverYnYc2.jpg" alt="R.SIGE" width="85%" border="0" /></div>

Con respecto al valle suavizado, utilizaremos como entrada la pendiente del valle correspondiente a 0.0011631 m/m y con función objetivo, buscaremos el valor de la rugosidad equivalente que permite obtener una profundidad normal de 1.3 metros (considerando solo un borde libre de 0.2 metros). La rugosidad obtenida es dee 0.029 con profundidad crítica en 0.699 metros para un perfil tipo M2.

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.MainChannelValleyYnYc.jpg" alt="R.SIGE" width="85%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.MainChannelValleyYnYc1.jpg" alt="R.SIGE" width="85%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.MainChannelValleyYnYc2.jpg" alt="R.SIGE" width="85%" border="0" /></div>

Para futuros análisis, es conveniente estudiar el comportamiento del factor de corrección de la energía cinética o alpha - α, en función de las propiedades geométricas de la sección y las profundidades críticas obtenidas. Para obtener la gráfica de análisis, realice calculos de Yc para factores entre 0.5 y 1.5, podrá observar que su comportamiento no es lineal. Por ejemplo, para la sección correspondiente al cauce dominante, obtendremos:

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.MainChannelRiverAlpha.jpg" alt="R.SIGE" width="60%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.MainChannelRiverAlpha1.jpg" alt="R.SIGE" width="40%" border="0" /></div>


### 8.2 Cauce lateral

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.LateralChannel.jpg" alt="R.SIGE" width="85%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.LateralChannel1.jpg" alt="R.SIGE" width="85%" border="0" /></div>
<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.LateralChannel2.jpg" alt="R.SIGE" width="70%" border="0" /></div>


### 8.3 Geometría CAD

Instrucciones:

* Para crear en CAD la región correspondiente a la sección, seleccione las celdas en cursiva, copie y pegue en el _Command_ de Autocad o Civil3D. 
* Para crear solo la poli-línea de la base, excluir la letra "C" correspondiente al cierre de la poli-línea.

> Notación numérica requerida: separador decimal usando punto (.), separador de miles usando coma (,) y separador de listas usando coma (,).

<div align="center"><img src="graph/R.HydroTools.DisenoGeometricoHidraulicoVertical.CAD.jpg" alt="R.SIGE" width="100%" border="0" /></div>

Sección inicio cauce principal

```
PLine
0,103
21,101.5
84.6,101.5
105.6,100
145.6,100
166.6,101.5
230.2,101.5
251.2,103
C
```

Sección entrega cauce principal

```
PLine
0,102.103
21,100.603
84.6,100.603
105.6,99.103
145.6,99.103
166.6,100.603
230.2,100.603
251.2,102.103
C
```

Sección inicio cauce lateral

```
PLine
0,103
0,103
-33.62,103
-3.62,100
3.62,100
33.62,103
0,103
0,103
C
```

Sección entrega cauce lateral

```
PLine
0,101.71
0,101.71
-33.62,101.71
-3.62,98.71
3.62,98.71
33.62,101.71
0,101.71
0,101.71
C
```



## Actividades de proyecto :triangular_ruler:

Utilizando la [plantilla suministrada](../../file/report/R.HCMC.PlantillaSoporteDesarrollo.docx), cree un documento soporte mostrando las actividades desarrolladas en el orden presentado en esta actividad, junto con los análisis y recomendaciones realizadas, convierta a Adobe Acrobat (.pdf) y guarde en la carpeta _/activity_ del repositorio de datos del proyecto; nombre el archivo con el código de la actividad agregando al final la fecha de control documental en formato aaaammdd (p. ej. M01A13_20250531.pdf).

En la siguiente tabla se listan las actividades que deben ser desarrolladas y documentadas por cada estudiante o grupo de proyecto.

| Actividad | Alcance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| M01A13    | Crear un nuevo proyecto HEC-RAS y utilizando el módulo de diseño, diseñar por los 3 métodos (incluído fuerza tractiva utilizando Shields o Lane), la sección compuesta del cauce principal y las secciones únicas de los cauces laterales. En el libro diseño y anális de Excel, registrar los valores obtenidos e incluir captura de pantalla HEC-RAS HD de la sección dominante y captura de pantalla de la sección de creciente del cauce principal y captura de pantalla de cada cauce lateral diseñado.                                         | 
| M01A13    | En HEC-RAS, verificar por flujo uniforme la sección compuesta. En el libro de Excel, incluir captura de pantalla HEC-RAS HD de la verificación por flujo uniforme para la sección compuesta.                                                                                                                                                                                                                                                                                                                                                         | 
| M01A13    | Registrar la geometría obtenida en el libro de diseño. Crear 3 hojas dentro del libro de Excel y nombrar como CaucePrincipal, CauceLateral1 (próximo a nodo J4585), CauceLateral2 (próximo a nodo J4660).                                                                                                                                                                                                                                                                                                                                            | 
| M01A13    | En el libro de Excel, verificar por flujo uniforme la geometría de las secciones dominante y valle diseñadas en HEC-RAS para el canal principal. Crear copias de la hoja YnYcPrismatic y nombrar como YnYcPrismaticRiver, YnYcPrismaticValley.                                                                                                                                                                                                                                                                                                       | 
| M01A13    | En el libro de Excel y utilizando la hoja de diseño de Fuerza Tractiva, diseñar el canal dominante y el canal del valle del cauce principal, eligiendo el tipo de sinuosidad para cada sección y encontrar el tamaño de material requerido para estabilizar el lecho y los taludes. Comparar los valores con los tamaños de partículas de protección de fondo para lecho estable obtenidas con HEC-RAS (aplicable a canales rectos) y registrar la comparación en las notas generales de la FCD.                                                     | 
| M01A13    | Opcional: verificar la formulación correcta de los libros de cálculo suministrados. En las notas de la ficha de control documental indicar el método de verificación y si se requieren o no ajustes.                                                                                                                                                                                                                                                                                                                                                 |
| M01A13    | En una tabla y al final del informe de avance de esta entrega, indique el detalle de las actividades realizadas por cada integrante de su grupo; utilice las siguientes columnas: `Nombre del integrante`, `Actividades realizadas`, `Tiempo dedicado en horas` (si presenta la entrega individualmente, no es necesaria la presentación de esta tabla).<br><br>Para actividades que no requieren del desarrollo de elementos de avance, indicar si realizo la lectura de la guía de clase y las lecturas indicadas al inicio en los requerimientos. | 

> Nota 1: para la revisión del proyecto final, guarde los libros cálculo de Microsoft Excel y los archivos generados en esta actividad, en las localizaciones indicadas en cada numeral.
>
> Nota 2: una vez el instructor realice la revisión y el estudiante presente las correcciones o ajustes solicitados, será necesario cargar una nueva versión de los archivos en el repositorio del proyecto, incluyendo o actualizando al final del nombre del archivo, la fecha de presentación en formato aaaammdd y manteniendo las versiones anteriores presentadas.
> 
> Nota 3: en el método en el método de Copeland, las gráficas pueden ser mostradas sin seguir una tendencia específica cuando la granulometría tiene materiales muy finos y muy gruesos al mismo tiempo. Cuando los materiales son predominantemente finos o tienen una distribución similar, la curva de estabilidad se dibuja continua como la utilizada en el caso de estudio. Algunas de las gradaciones asignadas a los proyectos de clase han incluido materiales gruesos, en algunos casos de 1 1/2" y 2 1/2".
>
> Nota 4: para el dimensionamiento del ancho de corona en valle correspondiente a la huella de mecanización, considerar el paso de vehículos de carga para explotaciones mineras en dos sentidos y sus dimensiones.

Como referencia para las coronas del canal, utilizar las siguientes especificaciones:

* Largo: 42-4 ft, 12.8-14.94 m (mas largo: 67.59 feet, 20.6 m).
* Alto: 18-24 ft, 5.5-7.31 (vacío).
* Ancho: 27-32 ft, 8,2-9.8 m.
* Capacidad de carga: 100 tons.
* Radio de giro: 65 ft, 19.8 m.
* Referencias: Caterpillar 797 / 797F / 793D, BelAZ 75710, XCMG Xda40.

<div align="center"><img src="graph/MinningTruckCat785.jpg" alt="R.SIGE" width="60%" border="0" /><sub><br>Tomado de: <a href="https://www.cat.com/en_US/products/new/equipment/off-highway-trucks/mining-trucks.html">www.cat.com</a></sub><br><br></div>


## Referencias

* Book: Julian Aguirre
* Ven Te Chow. Hidráulica de canales (Ejemplo 7.4 Ven Te Chow)
* US Army Corps of Engineers. HEC-RAS River Analysis System, Hydraulic Reference Manual, Versión 5.0. CPD-69. 2016.2
* http://fluidos.eia.edu.co/hidraulica/libre/yn.html
* https://www.cat.com/en_US/products/new/equipment/off-highway-trucks/mining-trucks.html



## Control de versiones

| Versión    | Descripción        | Autor                                      | Horas |
|------------|:-------------------|--------------------------------------------|:-----:|
| 2025.06.10 | Migración a GitHub | [rcfdtools](https://github.com/rcfdtools)  |  12   |



##

_R.HCMC es de uso libre para fines académicos, conoce nuestra licencia, cláusulas, condiciones de uso y como referenciar los contenidos publicados en este repositorio, dando [clic aquí](../../LICENSE.md)._

_¡Encontraste útil este repositorio!, apoya su difusión marcando este repositorio con una ⭐ o síguenos dando clic en el botón Follow de [rcfdtools](https://github.com/rcfdtools) en GitHub._


| [:arrow_backward: Anterior](../M01A12/Readme.md) | [:house: Inicio](../../README.md) | [:beginner: Ayuda / Colabora](https://github.com/rcfdtools/R.SIGE/discussions/99999) | [Siguiente :arrow_forward:](../M01A0214/Readme.md) |
|--------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------|----------------------------------------------------|

[^1]: 