# Plan Ajustado Para Completar La Memoria

## Resumen

La memoria debe reforzar el vínculo con el guion de la práctica: diseño con DMElect/GASCOMB, trazado libre, equipos instalados, cálculo automático de consumos/simultaneidad, resultados y optimización.

No se añadirán pruebas de estanquidad, purgado ni desarrollo normativo extenso, porque no forman parte del objetivo del proyecto realizado.

## Cambios Recomendados

### Ajustar el alcance en la introducción

Indicar que el trabajo consiste en modelar, calcular y optimizar una instalación receptora de gas natural mediante DMElect/GASCOMB, partiendo de una acometida en MPA.

Aclarar que no se han realizado pruebas de estanquidad ni purgado, por lo que no se desarrollan como resultados del proyecto.

### Añadir "Datos introducidos en DMElect/GASCOMB"

Recoger los principales parámetros usados en el programa:

- Presión de acometida.
- PCS usado.
- Potencias de los aparatos.
- Número de viviendas.
- Potencia de diseño por instalación individual.
- Presión mínima admisible.
- Límites de velocidad y pérdida de carga usados por el programa.

### Corregir la explicación de simultaneidad

Sustituir la redacción que pueda parecer cálculo manual por una explicación operativa: DMElect calcula automáticamente la simultaneidad una vez introducida la potencia de diseño de la instalación individual y el número de viviendas servidas.

Indicar que esta configuración se aplicó en:

- Acometida.
- Acometida interior.
- Montantes.

### Incluir la figura `asignacion_potencias-vivienda.png`

Añadir la figura en la metodología, cerca del apartado de datos de partida o topología, con una leyenda similar a:

> Asignación de potencia de diseño y número de viviendas para el cálculo automático de simultaneidad en DMElect.

Usarla como evidencia gráfica de cómo se configuraron la acometida, la acometida interior y los montantes.

### Añadir "Justificación del trazado elegido"

Explicar por qué se eligió el recorrido desde acometida, armario de regulación, centralización de contadores, montantes y derivaciones hasta cocina.

La justificación debe centrarse en criterios prácticos:

- Claridad del esquema.
- Repetición por plantas.
- Reducción de recorridos.
- Alimentación ordenada de las viviendas.
- Coherencia con el trazado libre pedido en el guion.

### Reforzar "Equipos instalados"

Relacionar explícitamente los equipos pedidos en el guion con el modelo:

- Acometida.
- Armario de regulación.
- Contadores.
- Reductores o reguladores.
- Válvulas de corte.
- Llaves de vivienda.
- Llaves de aparato.

Evitar presentar "purgadores" como prueba o procedimiento realizado.

### Añadir "Proceso de optimización en el programa"

Describir que se revisaron:

- Diámetros.
- Velocidades.
- Pérdidas de carga.
- Presión en el receptor más desfavorable.

Mantener los resultados principales ya existentes y apoyarse en el anejo para los datos completos, sin duplicar tablas extensas.

## Test Plan

- Compilar `Practica_Gas_natural_LaTeX/main.tex`.
- Verificar que la nueva figura existe como `Practica_Gas_natural_LaTeX/Figuras/asignacion_potencias-vivienda.png`.
- Revisar que la simultaneidad quede atribuida al cálculo automático de DMElect, no a un cálculo manual propio.
- Comprobar que no se afirme que se hicieron pruebas de estanquidad, purgado o puesta en servicio.
- Confirmar que la memoria sigue centrada en el guion: software, trazado, equipos, resultados y optimización.

## Supuestos

- La figura `asignacion_potencias-vivienda.png` corresponde a la configuración de potencia de diseño y viviendas en DMElect.
- La normativa solo se usará como apoyo puntual, sin convertirla en un capítulo principal.
- El objetivo es mejorar la memoria existente sin reescribirla por completo.
