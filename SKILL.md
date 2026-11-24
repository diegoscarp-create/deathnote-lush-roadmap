---
name: deathnote-lush-roadmap
description: Organiza cualquier proyecto con el DEATHNOTE LUSH ROADMAP y un equipo fijo de tres roles (sesión principal y dos agentes; por defecto Sonnet prueba y Haiku programa) que la sesión principal dirige, revisa y aprueba. Usar al iniciar o retomar un proyecto.
---

# DEATHNOTE LUSH ROADMAP

Versión 0.3.2

Autor: www.soportevirtualai.com - Diego Scarpetta, Consultor de Proyectos IA. Repositorio oficial: https://github.com/diegoscarp-create/deathnote-lush-roadmap. Licencia: CC BY-NC 4.0.

Esta skill define cómo se organiza y se controla un proyecto: un roadmap único por proyecto, un equipo fijo de tres roles, un handoff y una bitácora que guardan la continuidad, y un versionamiento acordado. Aplica a cualquier proyecto en el que el usuario la invoque o mencione "DEATHNOTE LUSH ROADMAP".

La skill sirve a cualquier usuario: no tiene datos de una persona en particular. Las palabras y la carpeta que trae son propuestas por defecto que el usuario puede cambiar al iniciar; lo elegido se registra como ADR del proyecto.

**Nombre y siglas.** "DEATHNOTE LUSH ROADMAP" es solo el nombre de esta skill: el roadmap es el cuaderno único donde queda escrito lo decidido, lo hecho y lo pendiente de un proyecto. ADR = Architecture Decision Record (registro de decisión). SPEC = especificación (resumen de qué hace el sistema). OD = decisión abierta (open decision). T = tarea.

## 0. Idioma

Trabaja en el idioma del usuario, cualquiera que sea. Detéctalo en su primer mensaje y confírmalo en la configuración inicial. Desde ahí van en ese idioma la conversación, el contenido del roadmap, las fichas de encargo, el handoff, la bitácora y las palabras por defecto.

Quedan fijos en cualquier idioma: el título `DEATHNOTE LUSH ROADMAP — <Proyecto>` y las siglas ADR y SPEC. OPEN DECISIONS y TAREAS se traducen al idioma del usuario. No cambies el idioma de un roadmap que ya existe. Cuando esta skill nombra una sección (ADR, SPEC, OPEN DECISIONS, TAREAS), se refiere a ella en cualquier idioma, con el encabezado que le toque en el idioma del roadmap; por ejemplo, TAREAS es TASKS en inglés.

## 1. Configuración inicial

Se hace una sola vez por proyecto, cuando la skill se lanza en un proyecto que aún no tiene su configuración registrada como ADR. Si ya está registrada, úsala y no vuelvas a preguntar.

### 1.1 Tabla de definiciones (solo lectura)

Antes de preguntar nada, muestra en el chat una tabla de solo lectura con:

- **Roles del equipo.**
  - Sesión principal: piensa, organiza, define seguridad, UX y diseño, escribe los encargos, revisa y aprueba.
  - Agente de pruebas: prueba función, UX y seguridad, y reporta con evidencia. No corrige código.
  - Agente de código: programa, prueba su código y corrige lo que se le indique.
- **Archivos del proyecto.**
  - Roadmap: documento editable con decisiones (ADR), resumen del sistema (SPEC), decisiones abiertas y tareas. Es la fuente de verdad del proyecto.
  - Handoff: dónde quedó el trabajo, qué quedó a medias, el siguiente paso, la versión vigente y el enlace al roadmap. Sirve para retomar. Se guarda en la carpeta del proyecto en el PC y el último también en la memoria de Claude, si está disponible.
  - Bitácora: registro del proceso, con fecha: qué se intentó, qué falló y por qué se cambió de rumbo. No copia el roadmap. Se guarda solo en la carpeta del proyecto en el PC.
- **Numeración de versiones.**
  - 0.0.1 (mayor.menor.parche). Es la más clara para desarrollos: parche (0.3.1) para correcciones; menor (0.4.0) para funciones nuevas que no rompen lo anterior; mayor (1.0.0) para cambios que rompen compatibilidad, o la primera versión estable.
  - 0.1 / 1.0. Dos niveles. Basta para documentos o proyectos pequeños.
  - 1. Solo conteo de entregas.
  - Personalizada. El usuario escribe su propio formato.
- **Tipos de versión.** Alpha (en construcción), Beta (completa, en prueba con usuarios reales), Release Candidate o RC (candidata, solo correcciones), Ninguna.

Avisa en la misma tabla que la skill usará una carpeta del PC del usuario (o la ubicación que él elija, si la sesión no tiene acceso a su PC) para guardar el handoff y la bitácora.

### 1.2 Preguntas

Haz las preguntas con la herramienta de preguntas de Claude, en dos pantallas (una tercera, solo si el usuario quiere cambiar el modelo de algún agente). El usuario solo elige una opción o escribe la suya; los textos de las preguntas no se editan. Marca la opción recomendada en cada pregunta escribiendo "(Recomendada)" al final de su etiqueta.

**Pantalla 1**
1. **Idioma de trabajo.** El detectado (recomendado) u otro.
2. **Equipo.** Por defecto (recomendado): agente de pruebas en Sonnet y agente de código en Haiku. O cambiar el modelo de cada agente: si elige cambiar, haz después una pantalla adicional con una pregunta de seguimiento por cada agente que quiera cambiar. Explica en una línea por qué se recomienda el equipo por defecto: la sesión principal razona y aprueba, Sonnet verifica y Haiku programa barato y rápido.
3. **Palabras clave.** Dejar las de por defecto (recomendado) o cambiar alguna. Por defecto, en el idioma del usuario:
   - Ejecutar un lote de tareas: "dale" o "ejecuta" (cualquiera de las dos sirve).
   - Releer el roadmap y procesar respuestas: "lee el death note".
   - Generar handoff y bitácora: "cierre".
   - Saltar las objeciones y opciones en una tarea: "directo".
   Avisa al usuario que son palabras comunes y que pueden dispararse sin querer en una conversación normal; sugiérele elegir frases menos comunes si le preocupa autorizar sin intención. Si quiere cambiar alguna, pídele en texto libre cuál y la palabra nueva.
4. **Carpeta del proyecto en el PC.** Una carpeta con el nombre del proyecto, dentro de la carpeta de documentos del usuario (recomendada), u otra ruta o ubicación que escriba el usuario (por ejemplo la nube o un repositorio, si la sesión no tiene acceso a su PC, como en móvil o web).

**Pantalla 2**
1. **Tipo de versión.** Alpha, Beta, RC o Ninguna. Recomendado: usar tipos (empezar en Alpha) para desarrollos, y Ninguna para documentos.
2. **Numeración.** 1.0, 0.1, 0.0.1 o 1; la opción de escribir sirve para la personalizada. Recomendado para desarrollos: 0.0.1, con la primera versión en 0.1.0. Recomendado para documentos: formato 0.1, con la primera versión en 0.1.

Si la sesión no tiene la herramienta de preguntas, muestra la tabla con las preguntas, sus opciones y la recomendada, y el usuario responde por escrito.

Registra todo lo elegido como un ADR del proyecto: idioma, modelos del equipo, palabras clave, carpeta, tipo de versión y numeración. Usa esas palabras y modelos en adelante. En el resto de esta skill, las palabras de ejecutar, de releer, de cierre y de saltar objeciones son las que eligió el usuario.

Si la carpeta del PC no está disponible, díselo al usuario y aplica lo que dice la sección 7 para ese caso.

## 2. El roadmap

El roadmap es la única fuente de verdad del proyecto: qué se decidió, qué se hizo, qué está pendiente, qué no se ha definido y qué hace cada agente.

- Es un documento editable por proyecto, titulado `DEATHNOTE LUSH ROADMAP — <Proyecto>`.
- Para encontrarlo, abre el enlace que trae el último handoff. Si no hay handoff o el enlace falla, búscalo por nombre entre los documentos o artefactos del usuario. Si el entorno no tiene ni artefactos ni documentos editables, crea el roadmap como un único archivo de texto en la carpeta del proyecto, con las mismas cuatro secciones y reglas. Créalo solo si no existe. Nunca crees un segundo roadmap para el mismo proyecto.
- Tiene cuatro secciones fijas, en este orden, y arriba enlaces para saltar a cada una. Debe leerse bien en un panel angosto: listas y bloques cortos, sin tablas anchas.

### ADR
Decisiones tomadas. Cada una: `ADR-NNN · fecha`, la decisión en una o dos frases y su motivo. Un ADR no se edita: si la decisión cambia, se agrega uno nuevo que reemplaza al anterior. Si la decisión va contra la recomendación dada, se anota.

### SPEC
Resumen de qué hace el sistema, un renglón por módulo con los ADR que lo sustentan, la versión vigente con su tipo, y enlace al documento de diseño completo si existe.

### OPEN DECISIONS
Lo que falta decidir. Cada decisión es un bloque `OD-NNN · pregunta` con:
- Opciones. Siempre incluyen "Dejar para después".
- Objeción principal.
- Recomendación.
- Respuesta: línea en blanco que solo llena el usuario.
- Lectura: cómo interpretas su respuesta, con fecha.

Una respuesta clara pasa a ADR con ID nuevo y fecha, y el bloque sale de esta sección. No cierres una decisión si la respuesta solo repite la objeción, no elige nada o contradice un ADR: pide que la aclare. "Dejar para después" la mantiene abierta y marca como bloqueadas las tareas que dependen de ella.

### TAREAS
Una fila por tarea: `T-NNN`, la tarea con su origen entre paréntesis (ADR u OD), el responsable (Principal, agente de pruebas, agente de código o Usuario) y el estado. Debajo del texto de la tarea va una línea de evidencia: qué se probó, resultado y fecha.

Estados: Pendiente, En curso, En pruebas, En revisión, Devuelta, Hecha, Bloqueada. Solo la sesión principal pasa una tarea a Hecha.

## 3. El equipo

Siempre hay tres roles. Los modelos de los agentes son los que eligió el usuario en la configuración inicial (por defecto Sonnet para pruebas y Haiku para código).

- **Sesión principal.** Piensa, organiza, define y controla. Define seguridad, UX y diseño. Escribe las fichas de encargo, revisa lo que entregan los agentes y aprueba o devuelve. Debe correr en el modelo más capaz que el usuario tenga; la skill no puede cambiar ese modelo, así que al iniciar recuérdaselo en una línea si hace falta.
- **Agente de pruebas.** Prueba función, UX y seguridad de lo que se construye, y reporta hallazgos con evidencia. No corrige código.
- **Agente de código.** Programa, prueba su propio código y corrige lo que la sesión principal indique.

Lanza cada agente con la herramienta de agentes indicando su modelo de forma explícita; no dependas del modelo por defecto. Si el entorno no permite elegir el modelo de un agente, díselo al usuario, usa el que haya y regístralo en un ADR nuevo que reemplace al de configuración. Si la sesión no tiene forma de lanzar agentes, dilo al usuario antes de empezar y no simules que existen.

Las tareas sin código (documentos, decisiones, diseño) las hace la sesión principal y las revisa el agente de pruebas.

## 4. Flujo de cada tarea

1. La sesión principal escribe la ficha de encargo y pone la tarea En curso.
2. El agente de código programa, ejecuta sus pruebas y entrega su informe.
3. La tarea pasa a En pruebas: el agente de pruebas prueba función, UX y seguridad contra los criterios de la ficha, sin tomar el informe del agente de código como verdad.
4. La tarea pasa a En revisión: la sesión principal lee el cambio y los dos informes, y aprueba (Hecha) o devuelve (Devuelta) con indicaciones concretas.
5. La evidencia y el estado se escriben en el roadmap.

Nadie aprueba su propio trabajo. Si una tarea se devuelve dos veces, la sesión principal deja de reenviarla: la resuelve ella misma o se la plantea al usuario. Lo que resuelva ella misma lo prueba el agente de pruebas antes de marcarlo Hecha.

Código sensible (acceso y permisos, separación de datos entre clientes, credenciales, dinero, datos personales): la prueba de seguridad del agente de pruebas es obligatoria y la sesión principal lee el cambio completo, línea por línea, antes de aprobar.

## 5. Ficha de encargo

Cada agente empieza sin memoria de la conversación. Toda delegación lleva una ficha autónoma con:

- Tarea y su ID en el roadmap.
- Objetivo: qué debe quedar funcionando y para qué.
- Contexto mínimo: las decisiones (ADR) y la parte del diseño que aplican, copiadas, no referidas.
- Idioma de trabajo del proyecto.
- Archivos que puede tocar y los que no.
- Criterios de aceptación comprobables.
- Qué debe devolver: qué hizo, qué probó y con qué resultado, qué no pudo hacer y qué dudas quedan.

Un solo agente escribe en cada archivo a la vez. Dos tareas que tocan los mismos archivos van una después de la otra.

## 6. Versionamiento

Usa el tipo y la numeración que eligió el usuario. El tipo se combina con el número: 0.3.0-alpha, 0.3.0-beta, 0.3.0-rc.1, 0.3.0 (estable). Con otras numeraciones se combina igual: 1.0-beta, 2-rc.1.

Si se usan tipos, estas son las reglas de paso recomendadas:

- **Alpha → Beta.** Existen todas las funciones planeadas para esa versión, pasan las pruebas de los dos agentes sin fallas que bloqueen y el código sensible tiene su prueba de seguridad aprobada.
- **Beta → RC.** Usuarios reales lo usaron durante el periodo de prueba que se acuerda al proponer el paso a Beta, no hay fallas críticas ni altas abiertas y el usuario lo aprueba. Desde aquí no entran funciones nuevas.
- **RC → Estable.** Una ronda completa de pruebas no encuentra fallas nuevas y el usuario da el visto bueno. Si aparece una falla seria, se corrige y sale rc.2, sin volver a Beta.
- Solo se vuelve a Alpha, con número nuevo, si hay que agregar funciones o cambia el diseño.

La sesión principal propone cada cambio de versión o de tipo, con el motivo, y el usuario lo aprueba. Los agentes no cambian la versión. La versión vigente se anota en la SPEC del roadmap, en el handoff y en la release del repositorio cuando lo haya.

## 7. Handoff y bitácora

Se generan juntos y de la misma forma, en modo mixto:

- Cuando el usuario dice la palabra de cierre.
- Como respaldo automático, al terminar cada lote de tareas autorizado con la palabra de ejecutar.

Ninguno de los dos casos necesita otra autorización.

- **Handoff.** Dónde quedó el trabajo, qué quedó a mitad de camino, el siguiente paso, la versión vigente, las referencias a los ADR del lote y el enlace directo al roadmap (o su ruta, si el roadmap es un archivo). No repite el roadmap. Se guarda en la carpeta del proyecto en el PC (el historial completo) y el último también en la memoria de Claude, si está disponible, reemplazando al anterior.
- **Bitácora.** Una entrada con fecha por cada generación: qué se intentó, qué falló, por qué se cambió de rumbo y qué se aprendió. No copia el roadmap. Se agrega al archivo de bitácora en la carpeta del proyecto en el PC; no va a memoria.

Si el PC no está disponible, guarda el handoff en memoria (si la hay), entrega la bitácora pendiente al usuario como archivo o como texto en el chat para que no se pierda, avísale, y copia los dos archivos al PC apenas esté disponible. Si tampoco hay memoria, entrega los dos al usuario en el chat para que los guarde él, y repite el aviso al terminar el siguiente lote hasta que queden guardados.

## 8. Reglas

- Nada se ejecuta sin la palabra de ejecutar del usuario. Su señal autoriza un lote de tareas definido, no el proyecto entero. Actualizar el roadmap con contenido ya definido no espera señal.
- Ante cada indicación del usuario, da sus mejores objeciones y opciones antes de ejecutar, salvo en tareas triviales o cuando use la palabra de saltar objeciones.
- Los agentes no borran, publican, suben ni despliegan nada. Esas acciones las hace la sesión principal, con autorización del usuario.
- Lo que dice un agente es evidencia por verificar, no un hecho. No reportes al usuario como comprobado algo que solo afirmó un agente.
- No se guardan datos personales en el roadmap, en las fichas, en los informes, en el handoff ni en la bitácora.
- Informa al usuario con resultados, no con el detalle de cada paso: qué quedó hecho, qué se devolvió y por qué, y qué necesita de él.

## 9. Al iniciar y al cerrar

- **Al lanzar la skill en un proyecto nuevo:** haz la configuración inicial (sección 1) antes de cualquier otra cosa.
- **Al iniciar o retomar:** lee el último handoff del proyecto, abre el roadmap con su enlace (o búscalo por nombre si falla) y léelo completo antes de proponer nada. Di en pocas líneas qué está hecho, qué está pendiente, la versión vigente y qué espera respuesta del usuario.
- **Cuando el usuario diga la palabra de releer:** relee el roadmap, procesa las respuestas nuevas de OPEN DECISIONS y dile cómo interpretas cada una antes de cambiar nada.
- **Cuando el usuario diga la palabra de cierre:** deja el roadmap al día (estados, evidencias, decisiones, versión) y genera el handoff y la bitácora (sección 7).
