# Plan por fases para desarrollar la memoria con NotebookLM

Este plan organiza la ampliación de `main.tex` a partir de tres notebooks especializados de NotebookLM, sin establecer todavía conexión con el MCP. El objetivo es desarrollar una memoria técnica de instalación receptora de gas natural redactada principalmente en prosa, preservando todas las tablas, figuras, anexos y planos ya presentes en el documento LaTeX.

## Fase 0. Preparación del proyecto y restricciones de edición

Antes de consultar NotebookLM se debe fijar el estado base de la memoria. El archivo principal es `main.tex`, que ya contiene portada, índices, una tabla de datos de partida, figuras de definición de plantas, esquema de instalación, puntos desfavorables, anexo de planos y anexo de cálculos. Todo ese contenido debe conservarse, incluyendo captions, labels, rutas de figuras y PDFs incluidos mediante `\includepdf`.

La estructura de referencia está definida en `..\Planificacion\propuesta_estructura.md`. Esa propuesta plantea una memoria tipo paper con introducción, metodología, resultados, conclusiones, referencias y anexos, apoyada en UNE 60670, RD 919/2006 y el flujo de cálculo con DMElect/GASCOMB. Al desarrollar `main.tex`, se debe adaptar esa estructura al documento existente sin sustituir el material gráfico ni las tablas ya insertadas.

La redacción deberá evitar listas extensas, tablas nuevas innecesarias y enumeraciones mecánicas. Las tablas solo se añadirán si aportan trazabilidad técnica clara; en caso contrario, la información se integrará en párrafos. Las imágenes existentes se mantendrán como hitos narrativos dentro del texto, introduciéndolas y comentándolas antes o después de cada entorno `figure`.

## Fase 1. División funcional de los tres notebooks

Se utilizarán tres notebooks con responsabilidades separadas para evitar mezclar fuentes metodológicas, normativas y teóricas.

`DMElect_Guide` se usará para reconstruir con precisión el flujo de trabajo seguido en DMElect/GASCOMB. Este notebook debe responder sobre la carga del edificio, definición de plantas, trazado de red, selección de accesorios, asignación de aparatos, configuración de potencias, ejecución del cálculo, lectura del mapa de estados y exportación en PDF de la documentación generada. Su contenido alimentará principalmente la sección de metodología y la descripción del anejo de cálculos.

`Normativa_Gas_Natural` se usará para validar técnicamente los resultados. Debe concentrar referencias a UNE 60670, RD 919/2006, condiciones de presión, caudal, ventilación, llaves, acometidas, instalaciones comunes, instalaciones individuales, MOP, velocidades admisibles, materiales y criterios de aceptación. Su contenido alimentará la introducción normativa, la discusión de resultados, las conclusiones y las citas bibliográficas.

`Teoría Gas Natural` se usará para explicar conceptos y componentes. Debe cubrir la función de acometida, llave de acometida, instalación común, montantes, instalación individual, llaves de paso, reguladores si procede, contadores, aparatos de utilización, tuberías, accesorios, materiales y fundamentos de pérdida de carga. Su contenido servirá para redactar la introducción técnica y la subsección de accesorios y materiales.

## Fase 2. Bloque de conexión previsto, sin ejecución todavía

Cuando se decida activar NotebookLM, primero se comprobará si están disponibles herramientas MCP específicas de NotebookLM. Si existen herramientas `mcp__notebooklm-mcp__*`, se dará prioridad al MCP. Si no estuvieran disponibles, se podrá usar el CLI `nlm` como alternativa, pero esa decisión debe quedar explícita antes de trabajar.

El bloque siguiente describe la conexión prevista. Está escrito como guía comentada y no debe ejecutarse en esta fase.

```text
# 1. Comprobar disponibilidad de MCP NotebookLM:
#    - Buscar herramientas mcp__notebooklm-mcp__notebook_list,
#      mcp__notebooklm-mcp__notebook_get, mcp__notebooklm-mcp__notebook_query,
#      mcp__notebooklm-mcp__source_add, mcp__notebooklm-mcp__source_list.
#
# 2. Si el MCP pide autenticación:
#    - Ejecutar autenticación con nlm login fuera del flujo de redacción.
#    - Refrescar credenciales del MCP con refresh_auth si la herramienta existe.
#
# 3. Localizar o crear los notebooks:
#    - DMElect_Guide
#    - Normativa_Gas_Natural
#    - Teoría Gas Natural
#
# 4. Guardar los IDs reales de cada notebook:
#    DMELECT_GUIDE_ID=<id_real>
#    NORMATIVA_GAS_ID=<id_real>
#    TEORIA_GAS_ID=<id_real>
#
# 5. Confirmar fuentes cargadas en cada notebook antes de preguntar:
#    - Manuales, capturas o PDFs de DMElect en DMElect_Guide.
#    - Normas, reglamentos y apuntes normativos en Normativa_Gas_Natural.
#    - Material docente o técnico de teoría y accesorios en Teoría Gas Natural.
```

Si se usa el CLI como respaldo, el patrón equivalente sería:

```text
# nlm login --check
# nlm notebook list
# nlm source list DMELECT_GUIDE_ID
# nlm source list NORMATIVA_GAS_ID
# nlm source list TEORIA_GAS_ID
```

No deben usarse comandos interactivos como `nlm chat start`; para consultas puntuales se empleará `notebook_query` por MCP o `nlm notebook query` por CLI.

## Fase 3. Inventario documental y matriz de fuentes

Antes de redactar, se debe construir una matriz interna de evidencias. Para cada notebook se listarán las fuentes disponibles y se asignará cada una a las secciones de `main.tex` que puede alimentar. En esta fase solo se debe extraer contexto, no modificar aún el LaTeX.

Para `DMElect_Guide`, las consultas deben identificar el procedimiento real seguido en el software y diferenciar lo que fue una decisión de usuario de lo que fue un cálculo automático del programa. Se pedirá una explicación paso a paso en lenguaje de memoria técnica, no una guía de usuario.

Para `Normativa_Gas_Natural`, las consultas deben extraer criterios verificables: límites de presión, condiciones de diseño, exigencias de seguridad y referencias citables. La respuesta debe pedir siempre la norma o documento de origen para poder trasladarlo después a `refs.bib` y citarlo en IEEE.

Para `Teoría Gas Natural`, las consultas deben obtener explicaciones breves pero técnicas de cada elemento de la instalación. La finalidad no es hacer un glosario, sino disponer de material para redactar párrafos fluidos en la introducción y metodología.

## Fase 4. Desarrollo de la introducción

La introducción debe presentar el problema de diseño de una instalación receptora de gas natural en un edificio de viviendas, explicar por qué el dimensionamiento afecta a seguridad, continuidad de suministro y funcionamiento correcto de los aparatos, e introducir DMElect como herramienta de modelado y comprobación.

Se conservará la tabla de datos de partida ya incluida en `main.tex`. El texto deberá conducir hacia esa tabla, explicando que las potencias nominales de caldera, cocina, horno y secadora, junto con el PCS del gas natural, constituyen la base de cálculo de caudales.

Las consultas principales serán al notebook `Teoría Gas Natural` para la explicación general y al notebook `Normativa_Gas_Natural` para justificar el marco reglamentario. La redacción deberá incorporar citas a normativa cuando se añadan las entradas bibliográficas correspondientes.

## Fase 5. Desarrollo de la metodología

La metodología debe explicar primero la topología del edificio y la selección del esquema de instalación. Las figuras `Figuras/definicion_plantas.png` y `Figuras/esquema_instalacion.png` se mantendrán en su posición lógica, acompañadas de texto que describa cómo se interpretaron las plantas, cómo se organizó la instalación común y cómo se conectaron las instalaciones individuales.

La subsección de accesorios y materiales debe redactarse con apoyo del notebook `Teoría Gas Natural`. Se explicará la función de cada componente relevante dentro de la instalación real, evitando listados aislados. Cuando se mencionen materiales, se relacionarán con su uso en tramos concretos, facilidad de montaje, seguridad, compatibilidad normativa y comportamiento frente a pérdidas de carga.

La subsección de optimización del dimensionamiento se redactará con apoyo conjunto de `DMElect_Guide` y `Normativa_Gas_Natural`. Debe explicar cómo DMElect dimensiona o verifica diámetros, cómo se revisan presiones, velocidades y pérdidas de carga, y cómo se decide si el trazado resultante es aceptable. Se debe describir el flujo desde el modelo hasta la generación del anejo de cálculos en PDF.

## Fase 6. Desarrollo de resultados y discusión

La sección de resultados debe apoyarse en las salidas existentes del proyecto: mapa de estados, puntos desfavorables, planos y anejo de cálculo. La figura de puntos desfavorables ya presente debe conservarse y comentarse con texto técnico que explique por qué la acometida y el aparato de utilización más desfavorable son puntos críticos para validar el conjunto.

Las consultas a `DMElect_Guide` deberán pedir cómo interpretar el código de colores o mapa de estados del software, qué variables se deben revisar y cómo se conecta esa lectura con el anejo de cálculos. Las consultas a `Normativa_Gas_Natural` deberán validar si los resultados son aceptables según presiones mínimas, caudales, velocidades y criterios reglamentarios aplicables.

La discusión debe evitar limitarse a afirmar que el software no muestra errores. Debe explicar qué significa que el punto más desfavorable cumpla, cómo se distribuyen las pérdidas desde la acometida hasta los receptores y por qué el dimensionamiento final se considera coherente con la demanda instalada.

## Fase 7. Conclusiones

Las conclusiones deben sintetizar el cumplimiento del objetivo de diseño, la utilidad de DMElect para modelar y documentar la instalación, y la validación normativa del resultado. También pueden mencionar como mejora futura la comparación entre materiales o trazados alternativos, siempre que se mantenga como reflexión técnica y no como una nueva línea de cálculo no realizada.

No se introducirán datos nuevos en conclusiones. Toda afirmación debe proceder de la metodología, los resultados o la normativa ya citada.

## Fase 8. Bibliografía y trazabilidad normativa

Antes de cerrar la memoria se actualizará `refs.bib` con fuentes realmente usadas. Deben sustituirse o complementarse las referencias ajenas al tema que existan actualmente si no se citan en el texto. Las entradas prioritarias serán UNE 60670, RD 919/2006, documentación de DMElect/GASCOMB y material técnico empleado para teoría de instalaciones receptoras de gas.

Las citas se incorporarán en `main.tex` con `\cite{...}` usando el estilo IEEE ya configurado en `preamble.sty`. La bibliografía está actualmente comentada, por lo que deberá reactivarse si se introducen citas formales.

## Fase 9. Integración LaTeX preservando tablas, figuras y anexos

La edición de `main.tex` debe realizarse de forma incremental. Primero se ampliarán los párrafos de secciones y subsecciones existentes. Solo si la estructura queda insuficiente se añadirán subsecciones nuevas, respetando la propuesta de `propuesta_estructura.md`.

No deben eliminarse los entornos `table`, `figure`, `subfigure`, `\myappendix` ni las llamadas `\includepdf`. Deben corregirse únicamente problemas evidentes de coherencia, como títulos o labels duplicados, si se decide hacerlo durante la revisión final.

Los anexos de planos y cálculos permanecerán al final. En el cuerpo de la memoria se hará referencia a ellos mediante `\cref{anex:planos}` y `\cref{anex:calculos}` cuando proceda, explicando que los planos recogen el trazado de la instalación y que el anejo de cálculos contiene la documentación exportada desde DMElect.

## Fase 10. Revisión técnica y compilación

Tras integrar el contenido, se compilará el documento y se revisarán errores de LaTeX, referencias cruzadas, numeración de figuras y tablas, bibliografía y ajuste visual. La revisión final debe comprobar que la memoria mantiene una lectura continua, que los apartados no quedan como notas sueltas y que las figuras y tablas siguen apareciendo correctamente.

La validación mínima consistirá en compilar `main.tex`, revisar `main.log` y abrir `main.pdf`. Si se activa bibliografía, se ejecutará también el flujo con Biber. Cualquier advertencia relevante, como referencias indefinidas o citas sin resolver, debe corregirse antes de dar la memoria por cerrada.

## Consultas modelo para usar más adelante

Estas consultas son plantillas para cuando se active la conexión. Deben adaptarse a las fuentes reales de cada notebook.

```text
# DMElect_Guide:
# "Redacta en prosa técnica el flujo seguido en DMElect/GASCOMB para una instalación receptora de gas natural en edificio de viviendas: carga de plantas, definición de niveles, trazado de instalación común e individual, asignación de aparatos, cálculo, revisión del mapa de estados y exportación del anejo de cálculos. Evita formato de tutorial y enfócalo como metodología de memoria."
#
# Normativa_Gas_Natural:
# "Identifica los criterios normativos aplicables para validar una instalación receptora de gas natural en edificio de viviendas: presiones, caudales, velocidades, llaves, ventilación, materiales y documentación. Devuelve referencias concretas y explica cómo citar cada criterio en una memoria técnica."
#
# Teoría Gas Natural:
# "Explica en prosa la función de los elementos de una instalación receptora de gas natural: acometida, llave de acometida, instalación común, montantes, instalación individual, llaves de paso, contadores, tuberías, accesorios y aparatos de utilización. Relaciona cada elemento con su papel en seguridad, regulación, mantenimiento y pérdida de carga."
```

