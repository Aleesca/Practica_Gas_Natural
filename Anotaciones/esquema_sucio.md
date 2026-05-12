# 2 Metodología
El desarrollo del proyecto se ha estructurado en dos fases diferenciadas: la definición
arquitectónica y topológica de la red, y el posterior cálculo hidráulico mediante el
software de simulación DMELECT GASCOMB.
## 2.1 Topología del edificio y selección del esquema de instalación
Para la parametrización inicial, se ha modelado un edificio plurifamiliar de cinco plantas
útiles destinadas a vivienda, más una planta baja destinada a estacionamiento. Se han
definido las siguientes cotas altimétricas:
Planta baja (origen de la acometida): 2,5 m de altura. Al encontrarse por debajo del
nivel de la calle, la acometida penetra en esta cota.
Plantas de viviendas (1ª a 5ª): 2,6 m de altura por nivel, albergando dos viviendas
por planta.
Dada la morfología del edificio (10 viviendas en total), se ha optado por una Instalación
Tipo 7: contadores ubicados en cada vivienda, conectados a una red de distribución
vertical que opera en Media Presión A (MPA). Este esquema permite que las
conducciones generales discurran por el exterior (fachadas o esquinas de patios),
minimizando la servidumbre de paso en el interior del edificio y facilitando el
mantenimiento.
## 2.2 Criterios de modelado en DMELECT
La transcripción del diseño al entorno de simulación ha requerido la adopción de
diversos criterios técnicos para garantizar la convergencia del cálculo:
Definición de nudos de consumo: Se ha diseñado la red interior hasta la cocina de
cada vivienda, introduciendo los consumos nominales de los equipos: caldera (22
kW), horno (12 kW), cocina (5 kW) y secadora (11,3 kW). Es imperativo modelar
cada aparato en un nudo independiente para que el algoritmo del programa aplique
correctamente la formulación del caudal de simultaneidad (Qs).
Continuidad hidráulica: Para el trazado de los montantes a través de los forjados, se
ha empleado la función de 'enlace ortogonal', asegurando la conectividad mediante
identificadores idénticos a los tramos de interconexión vertical en las distintas
plantas.
Configuración de valvulería y regulación: Se ha prescindido de la instalación de
limitadores de caudal en el modelo computacional, tanto por directrices académicas
como por las restricciones operativas de la versión de software empleada. Para la
calibración de las presiones de entrada, se ha asumido la equivalencia
estandarizada de 1 bar ≈ 1 kg/cm²
.
## 2.3 Optimización del dimensionamiento
El diseño persigue una optimización técnico-económica estricta. Se ha habilitado la
función de cálculo automático de diámetros, parametrizando el software para que ajuste
las secciones comerciales al límite superior de la velocidad reglamentaria (20 m/s). Esto evita el sobredimensionamiento innecesario de las líneas, garantizando al mismo tiempo
que no se generen ruidos, vibraciones o fenómenos erosivos excesivos.
# 3 Resultados y Discusión
Una vez ejecutada la simulación hidráulica integral, se ha evaluado el comportamiento
del fluido desde la acometida en MPA hasta las llaves de aparato en Baja Presión (BP).
## 3.1 Evaluación del mapa de estados (Código de colores)
DMELECT GASCOMB implementa una interfaz gráfica de diagnóstico basada en una
codificación cromática para facilitar la revisión normativa de la red:
Elementos en Naranja (Estado Nominal): Constituyen la mayoría de la instalación,
operando con amplios márgenes de seguridad respecto a los umbrales
reglamentarios.
Elementos en Verde (Camino Crítico): Identifican los puntos límite de la instalación
que cumplen estrictamente con la normativa. Es decir, señala los nudos o tramos más desfavorables que aún cumplen con los límites reglamentarios.
Elementos en Rojo (Fuera del límite): Asigna los nudos o tramos que se encuentran más allá del límite.

## 3.2 Análisis de los puntos singulares más desfavorables
La simulación ha arrojado dos singularidades críticas (marcadas en verde), que validan
el ajuste económico del diseño:
Tramo de acometida (Crítico por velocidad): El tramo que conecta la red urbana con
el edificio se identifica como el más crítico por fricción. Al optimizar su diámetro,
absorbe la mayor velocidad de paso (15,43 m/s), manteniéndose por debajo de la
frontera legal de 20 m/s.
Aparato de utilización (Crítico por presión): El software ha detectado el horno de la
vivienda más alejada como el nudo con la presión mínima más ajustada de toda la
red. Que este nudo aparezca en verde certifica que el gas se entrega con una
presión superior al mínimo exigible para Gas Natural (200 mmca).
# 4 Conclusiones
La presente práctica ha permitido consolidar los principios de la mecánica de fluidos
aplicados al diseño de instalaciones receptoras de Gas Natural. De los resultados
obtenidos, se extraen las siguientes conclusiones fundamentales:

1. Eficiencia del Esquema Tipo 7: La distribución exterior en MPA con regulación en el
interior de la vivienda minimiza el diámetro de las canalizaciones comunes,
optimizando la inversión material inicial.
2. Importancia del cálculo desagregado: La discretización de cada aparato en nudos
individuales es una condición necesaria para que las ecuaciones de simultaneidad
proyecten pérdidas de carga realistas.3. Seguridad por validación de extremos: El correcto funcionamiento de los puntos
señalados en verde demuestra que, al satisfacer la normativa el nudo más crítico,
queda validada la operabilidad del 100% de la red.

