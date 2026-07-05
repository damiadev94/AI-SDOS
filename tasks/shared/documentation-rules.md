# Documentation Rules

## Propósito

Este documento establece las reglas obligatorias para la producción de documentación dentro de AI-SDOS.

Su objetivo es garantizar que toda la documentación sea consistente, verificable, reproducible y alineada con el conocimiento existente del proyecto.

Todas las Tasks de documentación y diagramación deberán cumplir estas reglas.

---

# Alcance

Estas reglas aplican a:

* documentación técnica;
* documentación arquitectónica;
* diagramas;
* modelos conceptuales;
* glosarios;
* ADRs;
* cualquier artefacto documental generado por personas o agentes de IA.

---

# Principios

Toda documentación deberá seguir los siguientes principios.

## Single Source of Truth

La documentación existente constituye la única fuente válida de conocimiento.

No deberán introducirse conceptos que no hayan sido previamente definidos.

---

## Documentation as Code

La documentación es un artefacto del sistema.

Debe tratarse con el mismo nivel de calidad, trazabilidad y mantenibilidad que el código fuente.

---

## Consistency First

La consistencia tiene prioridad sobre la velocidad de producción.

Si una nueva pieza contradice documentación existente, deberá detenerse la generación hasta resolver la inconsistencia.

---

## Human in the Loop

Las decisiones arquitectónicas pertenecen al responsable del proyecto.

Las Tasks pueden estructurar, representar y validar información, pero nunca tomar decisiones de arquitectura por iniciativa propia.

---

## Explicit Knowledge

Toda afirmación debe estar respaldada por documentación existente.

No deben inferirse decisiones implícitas cuando afecten la arquitectura del sistema.

---

# Jerarquía de fuentes

Cuando varias fuentes describan el mismo concepto, deberá respetarse el siguiente orden de prioridad.

1. Foundation
2. Domain Discovery
3. Ubiquitous Language
4. Domain Model
5. System Architecture
6. Information Flow
7. Conceptual Data Model
8. Governance
9. ADRs
10. Glossary
11. Otras secciones de documentación

Las decisiones registradas en un nivel superior prevalecen sobre las de un nivel inferior.

---

# Reglas de lectura

Antes de producir cualquier artefacto, la Task deberá:

1. identificar los documentos relevantes;
2. comprender el objetivo del artefacto;
3. verificar que la información sea suficiente;
4. detectar contradicciones;
5. identificar términos del lenguaje ubicuo involucrados.

La generación no deberá comenzar antes de completar este análisis.

---

# Manejo de información incompleta

Si falta información necesaria para producir el artefacto:

* detener la ejecución;
* identificar exactamente qué información falta;
* indicar qué documento debería contenerla;
* solicitar aclaración.

Nunca completar los vacíos mediante suposiciones.

---

# Manejo de contradicciones

Cuando dos documentos entren en conflicto:

* detener la generación;
* identificar ambos documentos;
* describir la contradicción;
* solicitar una resolución antes de continuar.

Nunca elegir una versión arbitrariamente.

---

# Uso del Lenguaje Ubicuo

Todos los términos deberán utilizar exactamente la nomenclatura definida en el Ubiquitous Language.

No deberán:

* traducirse términos oficiales;
* utilizar sinónimos innecesarios;
* introducir nombres alternativos;
* modificar conceptos establecidos.

La terminología debe permanecer uniforme en toda la documentación.

---

# Reutilización

Antes de crear un nuevo contenido deberá verificarse si ya existe:

* un documento equivalente;
* un diagrama similar;
* una definición previa;
* un componente reutilizable;
* una explicación existente.

Siempre se priorizará la reutilización sobre la duplicación.

---

# Alcance de las Tasks

Las Tasks pueden:

* organizar información;
* sintetizar contenido existente;
* representar visualmente conceptos;
* generar documentación;
* validar consistencia.

Las Tasks no pueden:

* modificar la arquitectura;
* redefinir conceptos;
* introducir nuevas decisiones;
* alterar el alcance del proyecto;
* modificar el DDS.

---

# Relación con el DDS

Toda documentación visual deberá utilizar exclusivamente:

* Design Tokens;
* Components;
* Patterns;
* Diagram Framework;
* Diagram Library;
* Templates oficiales.

No deberán incorporarse elementos gráficos externos.

---

# Trazabilidad

Todo artefacto generado debe poder responder claramente:

* ¿Qué documentación fue utilizada?
* ¿Qué conceptos representa?
* ¿Qué decisiones arquitectónicas refleja?
* ¿Qué versión de la documentación sirvió como referencia?

La relación entre documentos debe permanecer explícita.

---

# Calidad

Antes de finalizar cualquier Task deberá verificarse que el resultado sea:

* consistente;
* completo respecto al alcance solicitado;
* comprensible;
* técnicamente correcto;
* alineado con la documentación existente;
* reutilizable;
* mantenible.

---

# Restricciones

Nunca:

* inventar información;
* completar vacíos mediante inferencias;
* modificar documentación existente sin autorización;
* cambiar terminología oficial;
* alterar decisiones arquitectónicas;
* incorporar herramientas o convenciones ajenas al DDS.

---

# Criterios de aceptación

Una Task cumple estas reglas cuando:

* utiliza únicamente información documentada;
* respeta la jerarquía de fuentes;
* mantiene consistencia terminológica;
* identifica correctamente las dependencias documentales;
* reutiliza el DDS cuando corresponde;
* detiene la ejecución ante contradicciones o información insuficiente;
* produce un resultado trazable y verificable.

---

# Evolución

Estas reglas constituyen la política oficial de producción documental de AI-SDOS.

Toda nueva Task deberá referenciar este documento y cumplir sus principios sin duplicar sus contenidos.

Las modificaciones a estas reglas deberán realizarse de forma explícita y aplicarse de manera uniforme a todo el sistema de documentación.
