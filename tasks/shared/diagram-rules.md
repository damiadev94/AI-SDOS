# Diagram Rules

## Propósito

Este documento establece las reglas oficiales para la producción de diagramas dentro de AI-SDOS.

Su objetivo es garantizar que todos los diagramas sean consistentes, legibles, reutilizables y alineados con el Design Documentation System (DDS).

Todas las Tasks que generen documentación gráfica deberán cumplir estas reglas.

---

# Alcance

Estas reglas aplican a cualquier diagrama generado para AI-SDOS, incluyendo:

* Diagramas de contexto
* Diagramas C4
* Diagramas de componentes
* Diagramas de flujo
* Diagramas de secuencia
* Diagramas de estados
* Diagramas de dependencias
* Diagramas conceptuales
* Roadmaps
* Timelines
* Árboles de decisión
* Mapas mentales
* Cualquier otro tipo soportado por la Diagram Library

---

# Principios

## Clarity First

Todo diagrama debe comunicar una única idea principal.

Si un diagrama intenta explicar demasiados conceptos simultáneamente, deberá dividirse en varios diagramas.

---

## Architecture Before Aesthetics

La precisión arquitectónica tiene prioridad sobre la estética.

El diseño visual debe facilitar la comprensión, nunca modificar el significado.

---

## One Responsibility per Diagram

Cada diagrama debe responder una única pregunta.

Ejemplos:

* ¿Cómo está compuesto el sistema?
* ¿Cómo fluye la información?
* ¿Qué dependencias existen?
* ¿Cómo interactúan los agentes?

Nunca intentar responder varias preguntas independientes en un mismo diagrama.

---

## Reuse Before Creation

Todo diagrama deberá construirse reutilizando exclusivamente los elementos proporcionados por el DDS.

No deberán crearse componentes gráficos nuevos.

---

# Selección del tipo de diagrama

Antes de comenzar, la Task deberá identificar el tipo de diagrama más apropiado.

Como referencia:

| Objetivo                 | Tipo recomendado  |
| ------------------------ | ----------------- |
| Ecosistema del sistema   | Context Diagram   |
| Contenedores principales | Container Diagram |
| Módulos internos         | Component Diagram |
| Flujo de ejecución       | Flow Diagram      |
| Interacciones temporales | Sequence Diagram  |
| Cambios de estado        | State Diagram     |
| Dependencias             | Dependency Graph  |
| Relaciones conceptuales  | Mind Map          |
| Cronología               | Timeline          |
| Planificación            | Roadmap           |
| Decisiones               | Decision Tree     |

No deberá utilizarse un tipo de diagrama para representar información que otro tipo comunica de forma más clara.

---

# Composición

Todo diagrama deberá construirse utilizando únicamente:

* Canvas
* Node
* Connector
* Group
* Boundary
* Swimlane
* Label
* Title
* Legend
* Notes

No deberán incorporarse elementos externos al Diagram Framework.

---

# Organización visual

Siempre que sea posible:

* mantener una lectura de izquierda a derecha o de arriba hacia abajo;
* agrupar elementos relacionados;
* minimizar cruces de conectores;
* mantener alineación consistente;
* utilizar espaciado uniforme;
* evitar superposición de elementos.

La disposición debe facilitar la lectura sin necesidad de explicaciones adicionales.

---

# Jerarquía visual

La importancia de los elementos deberá representarse mediante:

* agrupación;
* posición;
* tamaño relativo;
* espaciado;
* niveles de contención.

Nunca mediante colores arbitrarios o estilos personalizados.

---

# Conectores

Los conectores deberán:

* representar relaciones reales;
* indicar claramente la dirección cuando corresponda;
* evitar cruces innecesarios;
* mantener un recorrido simple;
* finalizar en puntos claramente identificables.

No deberán utilizarse conectores decorativos.

---

# Agrupaciones

Los grupos deberán representar únicamente relaciones lógicas reales.

Ejemplos:

* módulos;
* bounded contexts;
* capas;
* subsistemas;
* dominios;
* actores.

Nunca utilizar agrupaciones únicamente por razones estéticas.

---

# Etiquetas

Las etiquetas deberán:

* ser breves;
* utilizar la terminología oficial;
* evitar abreviaturas no documentadas;
* mantener una nomenclatura consistente.

Cada elemento deberá tener un nombre único dentro del mismo diagrama.

---

# Leyendas

Todo diagrama que utilice símbolos o convenciones deberá incluir una leyenda.

La leyenda deberá explicar únicamente elementos presentes en el diagrama.

---

# Notas

Las notas deberán utilizarse únicamente para:

* aclaraciones importantes;
* restricciones;
* supuestos explícitamente documentados;
* referencias relevantes.

Las notas no deben sustituir información estructural del diagrama.

---

# Consistencia visual

Todos los diagramas deberán:

* reutilizar los mismos Design Tokens;
* mantener tipografía uniforme;
* utilizar el mismo sistema de espaciado;
* reutilizar Components y Patterns;
* respetar los Templates oficiales.

No deberán existir diferencias visuales injustificadas entre diagramas.

---

# Restricciones técnicas

Todos los diagramas deberán:

* utilizar exclusivamente HTML y SVG;
* ser compatibles con impresión en A4;
* ser responsive;
* no utilizar JavaScript;
* no utilizar estilos inline;
* no depender de frameworks externos.

---

# Accesibilidad

Todo diagrama deberá:

* mantener contraste suficiente;
* utilizar estructura HTML semántica cuando corresponda;
* incluir títulos claros;
* evitar depender exclusivamente del color para comunicar información.

---

# Validación

Antes de finalizar, la Task deberá verificar que:

* el tipo de diagrama es el adecuado;
* representa correctamente la documentación existente;
* no introduce información nueva;
* mantiene consistencia visual con el DDS;
* reutiliza exclusivamente componentes oficiales;
* puede comprenderse sin explicaciones adicionales.

---

# Criterios de aceptación

Un diagrama cumple estas reglas cuando:

* responde una única pregunta arquitectónica;
* utiliza el tipo de diagrama adecuado;
* reutiliza exclusivamente el DDS;
* mantiene una organización visual clara;
* utiliza terminología oficial;
* es técnicamente correcto;
* es imprimible;
* es mantenible;
* es consistente con el resto de la documentación.

---

# Evolución

Estas reglas constituyen el estándar gráfico oficial de AI-SDOS.

La incorporación de nuevos tipos de diagramas deberá realizarse ampliando la Diagram Library del DDS, nunca modificando las reglas aquí definidas.

Toda Task de diagramación deberá referenciar este documento como fuente de verdad para la producción gráfica.
