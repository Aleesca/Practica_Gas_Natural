# Plan: refinamientos de `main.tex`

## Resumen

Este plan recoge los pasos para refinar `Practica_Gas_natural_LaTeX/main.tex` sin implementar todavía los cambios. El objetivo es limpiar referencias no deseadas, simplificar el tratamiento normativo, reforzar la descripción del edificio y de la presión de acometida, y ajustar la redacción metodológica a una voz más pasiva e impersonal.

## Cambios previstos

- Eliminar toda referencia visible a la Universidad de León:
  - Quitar las citas `\cite{TeoriaGasNatural}` de `main.tex`.
  - Eliminar la entrada `TeoriaGasNatural` de `refs.bib` si queda sin uso.
  - Usar el notebook “Teoría Gas Natural” solo como apoyo interno de redacción, sin citarlo ni mencionarlo en la bibliografía.

- Simplificar la sección “Introducción e objetivos”:
  - Reducir el detalle sobre partes concretas de la UNE 60670.
  - Mantener solo una mención general a la normativa utilizada: serie UNE 60670, Real Decreto 919/2006, DMElect/GASCOMB y anejo de cálculo.
  - Evitar que la introducción actúe como desglose normativo pormenorizado.

- Incorporar la presión de acometida:
  - Indicar que la presión de regulación o suministro de la acometida es `\SI{1500}{mmca}`.
  - Relacionarla con el trabajo en Media Presión A y con los límites aplicables de MPA.
  - Mantener la explicación breve, técnica y coherente con los resultados del cálculo.

- Completar la selección del esquema de instalación:
  - Mencionar que el edificio tiene cinco plantas y dos viviendas por planta.
  - Usar ese dato para justificar la solución con instalación común, montantes e instalaciones individuales.

- Revisar la metodología:
  - Priorizar voz pasiva e impersonal.
  - Sustituir expresiones como “el usuario crea”, “el usuario define” o “el usuario debe interpretar”.
  - Usar formulaciones como “se crean los niveles”, “se definen la topología, los materiales y los aparatos” y “los resultados se interpretan y se contrastan”.

## Accesorios

Reestructurar la subsección de accesorios para presentarlos en bullet points:

- Llave de acometida.
- Regulador de presión.
- Contador.
- Llave de vivienda.
- Llaves de conexión de aparato.

Después de la lista, añadir un párrafo sobre el limitador de caudal:

- Explicar que no se incorpora porque no resulta necesario para el esquema desarrollado.
- Añadir que el módulo de DMElect disponible no incluía dicho accesorio como elemento modelable.
- Evitar presentarlo como una omisión de seguridad; debe quedar justificado como una decisión coherente con el alcance del modelo.

## Verificación posterior

Cuando se implemente este plan, comprobar:

- Que no quedan apariciones de `Universidad de Leon`, `Universidad de León`, `TeoriaGasNatural` ni citas asociadas.
- Que el término “usuario” desaparece o queda solo donde sea técnicamente inevitable.
- Que la introducción menciona la normativa sin detallar en exceso cada parte.
- Que la presión de `\SI{1500}{mmca}` aparece asociada a la acometida y a MPA.
- Que `main.tex` compila sin citas rotas ni errores bibliográficos.
- Que el PDF mantiene figuras, anexos y estructura original.

## Supuestos

- Este archivo solo documenta el plan; no supone implementación.
- No se modifica `main.tex`, `refs.bib` ni ningún archivo LaTeX en esta fase.
- No se sobrescribe `Planificacion/plan_fases_desarrollo_memoria_notebooklm.md`.
- El notebook “Teoría Gas Natural” puede servir como apoyo de redacción, pero no debe aparecer como referencia visible en la memoria final.
