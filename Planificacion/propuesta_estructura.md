# Estructura de Paper - Instalación de Gas Natural (UNE 60670)

Esta estructura cumple con las **Reglas Generales para el Trabajo y Prácticas** (formato de máximo 5 páginas) y las directrices de diseño profesional.


## 1. Resumen (Abstract)
*   Máximo 250 palabras.
*   Resumen del diseño de la instalación común e individual.
*   Conclusión principal: Validación de presiones en los aparatos de utilización más desfavorables según MOP.

## 2. Introducción
*   **Definición del problema:** Diseño de la infraestructura necesaria para el suministro de gas natural en un bloque de viviendas.
*   **Datos de partida:** Potencias nominales de aparatos (Caldera 22kW, Cocina 5kW, Horno 12kW, Secadora 11.3kW) y características del combustible (PCS = 40.68 $MJ/m^3$).
*   **Objetivos:** Garantizar el suministro bajo condiciones de seguridad (estanqueidad y ventilación) y optimizar los diámetros de la red.

## 3. Metodología
Este apartado describe el proceso técnico y las bases de cálculo aplicadas.

### 3.1. Modelo Matemático y Asunciones
*   **Cálculo de Caudales:** Determinación del caudal de diseño ($Q_d$) basado en la potencia instalada ($P_i$) y el Poder Calorífico Superior ($PCS$).
    $$Q_s = \frac{\sum P_i}{PCS}$$
*   **Coeficientes de Simultaneidad:** Aplicación de la norma UNE 60670-4 para la reducción de caudales en instalaciones comunes y montantes.
*   **Hipótesis de Diseño:** 
    *   Velocidad del gas $\le 20$ m/s para evitar ruidos y erosión.
    *   Presión de suministro (MOP) asignada en la acometida.
    *   Pérdida de carga máxima admisible según el tramo (Acometida vs. Red Interior).

### 3.2. Flujo de Trabajo en DMELECT (GASCOMB)
1.  **Definición Arquitectónica:** Carga de planos de planta y definición de la jerarquía de niveles del edificio.
2.  **Modelado de la Red:**
    *   Inserción de la **Llave de Acometida** y configuración de la presión de red.
    *   Trazado de la **Instalación Común** y montantes verticales.
    *   Diseño de la **Instalación Individual** por vivienda, situando accesorios (llaves de paso, codos) y aparatos de utilización.
3.  **Configuración de Aparatos:** Asignación de potencias y tipos de consumo para cada receptor.
4.  **Ejecución del Cálculo:** Procesado del algoritmo de dimensionado automático de diámetros comerciales y obtención del **Anejo de Cálculo**.

### 3.3. Experimentos y Resultados Esperados
*   Se busca verificar que la presión en la conexión de entrada de cada aparato sea superior a la mínima establecida por el fabricante y la norma.
*   Se espera una distribución de diámetros decreciente desde la acometida hasta los puntos de consumo, manteniendo las velocidades dentro del rango normativo.

## 5. Resultados y Discusión
*   Presentación del **Mapa de Estados** generado por el software.
*   Análisis del **Punto más Desfavorable**: Comparativa entre la presión disponible y la mínima requerida en el aparato con mayor pérdida de carga (típicamente el horno en la última planta).
*   Justificación de las velocidades obtenidas en los montantes principales.

## 7. Conclusión y Siguientes Pasos
*   Confirmación de que el diseño cumple con los requisitos de la UNE 60670.
*   Posibles mejoras: Uso de materiales alternativos (ej. multicapa vs cobre) para optimizar costes o trazados.

## 7. Referencias
*   Citas en formato IEEE (Norma UNE 60670, RD 919/2006, Manual DMELECT).
