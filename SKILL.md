---
name: deathnote-lush-roadmap
description: Organiza cualquier proyecto con el DEATHNOTE LUSH ROADMAP y un equipo fijo de cuatro roles (sesión principal que dirige y aprueba, y agentes de documentación, pruebas y código) con estados, controles y verificación independiente. Usar al iniciar o retomar un proyecto.
---

# DEATHNOTE LUSH ROADMAP

Versión 1.0.0

Autor: www.soportevirtualai.com - Diego Scarpetta, Consultor de Proyectos IA. Repositorio oficial: https://github.com/diegoscarp-create/deathnote-lush-roadmap. Licencia: MIT.

Esta skill define cómo se organiza y se controla un proyecto: un roadmap único por proyecto, un equipo fijo de cuatro roles, un handoff y una bitácora que guardan la continuidad, y un versionamiento acordado. Aplica a cualquier proyecto en el que el usuario la invoque o mencione "DEATHNOTE LUSH ROADMAP".

La skill sirve a cualquier usuario: no tiene datos de una persona en particular. Las palabras y la carpeta que trae son propuestas por defecto que el usuario puede cambiar al iniciar; lo elegido se registra como ADR del proyecto.

**Nombre y siglas.** "DEATHNOTE LUSH ROADMAP" es solo el nombre de esta skill: el roadmap es el cuaderno único donde queda escrito lo decidido, lo hecho y lo pendiente de un proyecto. ADR = Architecture Decision Record (registro de decisión). SPEC = especificación (resumen de qué hace el sistema). OD = decisión abierta (open decision). T = tarea.

## 0. Idioma

Trabaja en el idioma del usuario, cualquiera que sea. Detéctalo en su primer mensaje y confírmalo en la configuración inicial. Desde ahí van en ese idioma la conversación, el contenido del roadmap, las fichas de encargo, el handoff, la bitácora y las palabras por defecto.

Quedan fijos en cualquier idioma: el título `DEATHNOTE LUSH ROADMAP — <Proyecto>` y las siglas ADR y SPEC. REQUERIMIENTOS, OPEN DECISIONS, TAREAS y ARCHIVADAS se traducen al idioma del usuario, igual que todos los rótulos, nombres de roles, estados y marcas nuevos (estados de decisiones y de tareas, nombres de las filas de las tablas, "Archivada el", "(archivada)", "Restaurar" y las tres opciones fijas). No cambies el idioma de un roadmap que ya existe. Cuando esta skill nombra una sección (ADR, SPEC, REQUERIMIENTOS, OPEN DECISIONS, TAREAS, ARCHIVADAS), se refiere a ella en cualquier idioma, con el encabezado que le toque en el idioma del roadmap; por ejemplo, TAREAS es TASKS en inglés.

## 1. Configuración inicial

Se hace una sola vez por proyecto, cuando la skill se lanza en un proyecto que aún no tiene su configuración registrada como ADR. Si ya está registrada, úsala y no vuelvas a preguntar.

### 1.1 Tabla de definiciones (solo lectura)

Antes de preguntar nada, muestra en el chat una tabla de solo lectura con:

- **Roles del equipo.**
  - Sesión principal (se recomienda que corra en Opus): piensa, define, organiza el trabajo, propone UX y diseño para que el usuario los apruebe, verifica a los agentes y aprueba. No escribe código ni documentos.
  - Agente de documentación: escribe el roadmap, las fichas de encargo, el handoff, la bitácora y los manuales, y consolida los informes de los demás agentes.
  - Agente de pruebas: es el QA; prueba función, UX y seguridad, y reporta con evidencia. No corrige código.
  - Agente de código: programa, corrige, prueba su propio código y actualiza la documentación técnica.
  - Los modelos de los agentes son sugeridos y el usuario puede cambiarlos. Nadie aprueba su propio trabajo y solo la sesión principal marca una tarea como Hecha.
- **Archivos del proyecto.**
  - Roadmap: documento editable con decisiones (ADR), resumen del sistema (SPEC), requerimientos (lo que el sistema debe cumplir), decisiones abiertas (cada una en una tabla con sus opciones), tareas y decisiones archivadas. Es la fuente de verdad del proyecto y se mantiene al día durante todo el trabajo.
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
2. **Equipo.** Por defecto (recomendado): agente de documentación en Sonnet, agente de pruebas en Sonnet y agente de código en Haiku. O cambiar el modelo de cada agente: si elige cambiar, haz después una pantalla adicional con una pregunta de seguimiento por cada agente que quiera cambiar. Explica en una línea por qué se recomienda el equipo por defecto: la sesión principal razona y aprueba, Sonnet documenta y verifica, y Haiku programa barato y rápido. Recomienda también, antes de las preguntas, que la sesión principal corra en Opus: la skill no puede cambiar ese modelo, así que dile que lo elija en el selector de modelo de Claude.
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

Registra todo lo elegido como un ADR del proyecto: idioma, roles y modelos del equipo con su justificación (y si el usuario aceptó el equipo recomendado o lo cambió), palabras clave, carpeta, tipo de versión y numeración. Usa esas palabras y modelos en adelante. En el resto de esta skill, las palabras de ejecutar, de releer, de cierre y de saltar objeciones son las que eligió el usuario.

Si la carpeta del PC no está disponible, díselo al usuario y aplica lo que dice la sección 9 para ese caso.

## 2. El roadmap

El roadmap es la única fuente de verdad del proyecto: qué se decidió, qué se hizo, qué está pendiente, qué no se ha definido y qué hace cada agente.

- Es un documento editable por proyecto, titulado `DEATHNOTE LUSH ROADMAP — <Proyecto>`.
- Para encontrarlo, abre el enlace que trae el último handoff. Si no hay handoff o el enlace falla, búscalo por nombre entre los documentos o artefactos del usuario. Si el entorno no tiene ni artefactos ni documentos editables, crea el roadmap como un único archivo de texto en la carpeta del proyecto, con las mismas seis secciones y reglas. Créalo solo si no existe. Nunca crees un segundo roadmap para el mismo proyecto.
- Tiene seis secciones fijas, en este orden: ADR, SPEC, REQUERIMIENTOS, OPEN DECISIONS, TAREAS y ARCHIVADAS. Arriba lleva la fecha de la última actualización y, debajo, una barra de navegación: una tabla de una fila con una celda por sección (fondo azul claro, el nombre de la sección como enlace a su encabezado), que hace de botones. Si el documento no permite fondos de celda o enlaces internos, usa enlaces entre corchetes en negrita. Todo se presenta en tablas, para que se lea limpio y claro: cada sección usa la tabla que se indica abajo y los textos largos van dentro de la celda, sin listas sueltas. Debe leerse bien en un panel angosto: tablas de hasta tres columnas y bloques cortos.

### ADR
Decisiones tomadas, en una tabla de dos columnas (ADR, Decisión) con dos filas por decisión: la primera lleva `ADR-NNN · fecha` (y "antes OD-NNN" si vino de una decisión abierta) y la decisión en una o dos frases; la segunda, debajo, lleva en la primera celda "Motivo y origen" y en la segunda el motivo con su origen (por ejemplo, "Decisión del usuario; sigue la recomendación"). Un ADR no se edita: si la decisión cambia, se agrega uno nuevo que reemplaza al anterior. Si la decisión va contra la recomendación dada, se anota.

### SPEC
Resumen de qué hace el sistema, en una tabla de tres columnas (Módulo, Qué hace, ADR) con una fila por módulo y los ADR que lo sustentan ("—" si ninguno aplica). Debajo, la versión vigente con su tipo y el enlace al documento de diseño completo si existe.

### REQUERIMIENTOS
Lo que el sistema debe cumplir. Se muestra en una tabla de dos columnas, con una fila por requerimiento. A la izquierda va `REQ-NNN` y su estado en una lista desplegable: Nuevo, Definido (el usuario confirmó la definición), En desarrollo, Cumplido o Cancelado. A la derecha, en un solo bloque: la **Descripción** (lo que pidió el usuario, en sus palabras), la **Definición** (cómo lo entiende la sesión principal, con criterios comprobables para darlo por cumplido), el **Origen** (ADR, OD o petición del usuario con su fecha) y las **Tareas** vinculadas. La definición la propone la sesión principal y solo el usuario la confirma; el estado lo cambia la sesión principal.

Un requerimiento es lo que se necesita; una tarea es el trabajo que lo cumple. Un requerimiento puede tener varias tareas, y las tareas que son solo acciones (preguntar, averiguar, editar un documento) no son requerimientos. El texto de cada tarea indica al final a qué requerimiento sirve ("Requerimiento: REQ-NNN") o que no tiene ninguno. Si el usuario pide convertir una tarea en requerimiento, la tarea no desaparece: queda vinculada como la que lo implementa. Solo la sesión principal marca un requerimiento como Cumplido, cuando sus tareas están Hechas y se cumplen sus criterios. Cada alta, cambio de definición, cumplimiento o cancelación se anota en la bitácora como una línea con fecha, con el código y la descripción; la lista completa no se copia.

### OPEN DECISIONS
Lo que falta decidir. Cada decisión es una tabla de dos columnas (campo y contenido), una tabla por decisión, con estas filas en este orden:

1. **`OD-NNN` y Estado.** La fila de encabezado: a la izquierda el código `OD-NNN` y a la derecha el estado en una lista desplegable. Pendiente (sin respuesta), Respondida (hay una respuesta que aún no se puede cerrar: solo llenó el campo libre, o la respuesta es ambigua o contradice su propio contexto) o Aplazada (eligió "Dejar para después"). Cambia el estado la sesión principal.
2. **Pregunta.**
3. **Opciones.** Una fila por opción, con su letra (a, b, c…) y su consecuencia en una frase. Primero las opciones propias de la decisión: tantas como salgan de tu análisis (mínimo dos), incluidas las que no propuso el usuario si son válidas. Al final, siempre estas tres fijas, con las letras que sigan (el total no es un número fijo). Si después se agrega una opción propia, toma la letra siguiente a las propias, las tres fijas se corren una letra, y le pides al usuario que vuelva a elegir su Respuesta si ya había escrito una:
   - *Dejar para después.* La decisión sigue abierta, con estado Aplazada, y las tareas que dependen de ella quedan Bloqueadas.
   - *No tener en cuenta y archivar.* La quita de las abiertas, no genera ADR y queda anotada en la bitácora y en ARCHIVADAS, con opción de restaurarla.
   - *No tener en cuenta y eliminar.* La quita de las abiertas, no genera ADR y no se guarda en ninguna parte.
4. **Objeción principal.**
5. **Recomendación.**
6. **Respuesta (del usuario).** Una lista desplegable con las letras de las opciones; solo admite una.
7. **Otra opción o contexto (del usuario).** Texto libre para proponer otra opción o explicar su elección.
8. **Lectura (de la sesión principal).** Cómo interpretas su respuesta, con fecha.

El usuario llena solo la Respuesta y el campo de otra opción o contexto. La sesión principal define el Estado, la Lectura y todo lo demás (los escribe el agente de documentación), y ninguno de los dos modifica ni borra las dos celdas del usuario, salvo para limpiarlas al restaurar una decisión. Un documento no permite bloquear celdas, así que esta separación es una regla de trabajo.

Cómo se procesa una respuesta:
- **Opción propia de la decisión.** Pasa a ADR con ID nuevo y fecha, y la tabla sale de esta sección. Si el usuario agregó contexto, se anota en el ADR.
- **Dejar para después.** Estado Aplazada. Una decisión Aplazada se vuelve a leer en cada relectura; si el usuario cambia su Respuesta, procésala como una respuesta nueva y quita el estado Aplazada. Cuando la decisión se cierre, las tareas Bloqueadas por ella vuelven al estado que tenían antes de bloquearse (o a Pendiente si no hay ficha vigente); la sesión principal confirma el desbloqueo.
- **No tener en cuenta y archivar.** La tabla sale de OPEN DECISIONS y se agrega a ARCHIVADAS. Anota el archivo en la bitácora.
- **No tener en cuenta y eliminar.** Quita la tabla sin dejar rastro: ni ADR, ni ARCHIVADAS, ni bitácora. No pidas otra confirmación: elegirla ya es la orden, salvo que el campo de otra opción o contexto la contradiga (entonces pregunta antes). No la menciones después en el handoff, la bitácora, la memoria ni otros bloques del roadmap, y limpia las menciones que ya existan de su código (SPEC, tareas, otras tablas). Haz que el agente de documentación reescriba sin la mención el último handoff guardado en memoria (si no tiene esa herramienta, la sesión principal lo dicta y el usuario lo aplica); lo ya guardado en el PC (handoffs y bitácora anteriores) y cualquier ADR que cite el código no se editan: dile al usuario dónde están para que decida qué hacer. Avisa también que el historial de versiones del documento puede conservar el texto anterior, si el sistema lo guarda.
- **Tareas que dependían de una decisión archivada o eliminada.** Solo las que no estén Hechas ni Canceladas. Quedan Bloqueadas hasta que el usuario elija para cada una: mantenerla (pasa a Pendiente), cancelarla (estado Cancelada) o reasignarla a otra decisión. Si se mantiene una tarea de una decisión archivada, su origen conserva el código con la marca "(archivada)"; si la decisión era eliminada, reescribe el origen como "(petición del usuario, fecha)" sin nombrar el código. Si luego se restaura la decisión, quita la marca "(archivada)" y deja las tareas como estén.
- **Solo llenó "otra opción o contexto".** No cierres la decisión: pon el estado en Respondida, dile cómo lo interpretas y espera su confirmación. Si propone una opción nueva, agrégala como opción y pídele que la elija.
- **Respuesta ambigua, con contexto que la contradice, que repite la objeción, no elige nada o contradice un ADR.** No cierres la decisión: pon el estado en Respondida, pregúntale qué quiso decir y espera.
- **Cuándo se procesa.** En el mismo turno en que veas la respuesta, y siempre al iniciar o retomar y al releer el roadmap.
- **Decisión cerrada: no se modifica.** Una decisión contestada, sin nada pendiente ni por validar, queda cerrada: pasa a ADR (que no lleva controles) o, si se archivó, a ARCHIVADAS. Desde ahí ni su texto ni la opción elegida se modifican; el ADR lleva en su fila de motivo la marca "Cerrada: no se modifica". Un cambio se hace solo con un ADR nuevo que reemplace al anterior. Un documento no permite bloquear celdas, así que el bloqueo es una regla de detección: al iniciar, retomar y releer, compara cada ADR con la versión que registraste (el historial del documento) y, si alguien lo cambió, restaura el texto registrado, avisa al usuario qué cambió y le propone el ADR nuevo si quería cambiar la decisión. Nunca edites tú un ADR ni una decisión cerrada. Un bloqueo real solo es posible compartiendo el documento solo para comentar o con un formulario aparte para las respuestas.

Si el roadmap es un archivo de texto (sin listas desplegables), cada tabla se escribe como lista de líneas con los mismos campos, y el usuario escribe después de `Respuesta:` la letra elegida y después de `Otra opción o contexto:` su texto; el estado se escribe como palabra.

### TAREAS
Una fila por tarea: `T-NNN`, la tarea con su origen entre paréntesis (ADR, OD o petición del usuario con su fecha), el responsable (Principal, Documentación, Pruebas, Código o Usuario) y el estado. Debajo del texto de la tarea va una línea de evidencia: qué se probó, resultado y fecha, marcada como "reportada por agente" hasta que la sesión principal la verifique y entonces "verificada". El texto de la tarea termina con "Requerimiento: REQ-NNN" cuando aplica.

Estados: Pendiente, En definición, Lista para ejecutar, En ejecución, Pendiente de pruebas, En pruebas, Requiere corrección, Pendiente de aprobación, Bloqueada, Cancelada y Hecha. Solo la sesión principal autoriza los estados oficiales, y solo ella pasa una tarea a Hecha. Funciona por puertas: la sesión principal confirma Lista para ejecutar (ficha verificada), Requiere corrección, Pendiente de aprobación, Hecha y el desbloqueo de una Bloqueada; fija ella misma Pendiente, En definición y Cancelada. Los pasos operativos (En ejecución, Pendiente de pruebas, En pruebas, Bloqueada) los declara el agente en su informe y el agente de documentación los registra marcados "reportado por agente"; valen salvo que la sesión principal los objete.

Migración desde versiones anteriores: Pendiente → Pendiente, En definición o Lista para ejecutar; En curso → En ejecución o Pendiente de pruebas; En pruebas → En pruebas; En revisión → Pendiente de aprobación; Devuelta → Requiere corrección; Hecha, Bloqueada y Cancelada conservan su nombre. La sesión principal propone la equivalencia de cada caso ambiguo y el usuario la confirma; se preserva el historial.

### ARCHIVADAS
Las decisiones abiertas que el usuario eligió "No tener en cuenta y archivar". Cada una es una tabla de dos columnas con estas filas:

1. `OD-NNN · Archivada el <fecha>`.
2. Pregunta.
3. Opciones propias, con sus letras y su consecuencia en una frase.
4. Objeción principal.
5. Recomendación.
6. Respuesta, contexto del usuario y Lectura al archivar, resumidos.
7. Restaurar (del usuario): lista desplegable con "—" o "Restaurar".

Se conserva todo lo necesario para reponerla; las tres opciones fijas no se guardan porque siempre se reponen. Si la sección está vacía, deja su encabezado con la línea "Sin decisiones archivadas", en el idioma del roadmap. En un archivo de texto, el usuario escribe en cada archivada la línea `Restaurar: —` o `Restaurar: sí`.

Restaurar: cuando el usuario elija Restaurar (se procesa en el mismo turno en que lo veas, y siempre al iniciar, retomar o releer), devuelve la decisión a OPEN DECISIONS conservando su código, con estado Pendiente, sus opciones propias con las mismas letras, las tres fijas, y la Respuesta, el campo libre y la Lectura vacíos. Quita su tabla de ARCHIVADAS y anota la restauración en la bitácora, con la respuesta y la lectura que tenía. Las decisiones eliminadas no están aquí y no se pueden restaurar.

Las anotaciones de archivar y de restaurar se escriben de inmediato en el archivo de bitácora del PC si está disponible; si no, se acumulan para la siguiente entrada de la bitácora (sección 9) y, como ARCHIVADAS lleva la fecha de cada archivo, se reconstruyen al releer.

## 3. El equipo

Siempre hay cuatro roles. Los modelos de los agentes son los que eligió el usuario en la configuración inicial; los de la tabla de abajo son solo los sugeridos y el usuario puede cambiarlos.

- **Sesión principal.** Piensa, organiza, define y controla. Analiza lo que pide el usuario y define la estrategia; maneja las colas de trabajo, las dependencias y la secuencia; define los objetivos, los criterios de aceptación, las restricciones y los límites de cada encargo; propone la UX y el diseño para que el usuario los apruebe; decide lo técnico dentro del alcance y del diseño ya aprobados; crea agentes, resuelve bloqueos y orienta su trabajo; verifica informes y evidencias, lee línea por línea el código sensible, y aprueba o devuelve. Eleva al usuario todo lo de producto, alcance, diseño y prioridad. No escribe código ni documentos ni modifica el producto. Lee solo lo necesario para decidir, verificar la calidad y aprobar: el roadmap, los informes, la arquitectura, la UX, la seguridad y las evidencias; cualquier cambio si la evidencia no basta. Se recomienda que corra en Opus (o en el modelo más capaz que el usuario tenga). La skill no puede cambiar ese modelo: al iniciar, dile en una línea que se recomienda Opus para la sesión principal y que lo elija en el selector de modelo; si ya corre en uno equivalente, no lo repitas.
- **Agente de documentación.** Escribe el roadmap, las fichas de encargo, el handoff, la bitácora y los manuales de usuario y de operación, y solo documentos del proyecto. Redacta lo que la sesión principal le dicta (objetivos, criterios, límites, estados, decisiones, lecturas): no decide nada técnico ni funcional, no aprueba tareas, no altera objetivos ni criterios y no toca las celdas del usuario. Lee los informes de los demás agentes y se los consolida a la sesión principal, adjuntando siempre los originales completos, sin ocultar fallos ni discrepancias.
- **Agente de pruebas.** Es el QA del equipo. Diseña y ejecuta pruebas unitarias, funcionales, de integración y de regresión, y escribe solo código de prueba, en la carpeta de pruebas que autoriza la ficha; verifica UX, seguridad, los criterios de aceptación y la documentación técnica, a partir de los requisitos originales y sin depender de las pruebas del agente de código; reporta defectos con evidencia reproducible y verifica las correcciones. No modifica código de producto, no corrige defectos, no cambia requisitos, no aprueba ni declara nada Hecho. Tampoco modifica el producto para hacer pasar una prueba.
- **Agente de código.** Programa, corrige, lee el código y lee y actualiza la documentación técnica (README, comentarios, documentación de la API). Ejecuta pruebas unitarias y las verificaciones propias del desarrollo, que valen como evidencia y no como aprobación. Reporta cambios, archivos afectados, resultados, bloqueos, riesgos y dependencias, con contexto suficiente para que otro agente continúe. No cambia el alcance ni los criterios, no decide sobre el producto y solo toca los archivos que se le autorizan.

Cada agente hace solo su rol. Todo lo que esta skill dice que la sesión principal "escribe", "anota" o "actualiza" en el roadmap, la ficha, el handoff o la bitácora lo define ella y lo escribe el agente de documentación.

| Actividad | Principal | Documentación | Pruebas | Código |
| --- | --- | --- | --- | --- |
| Definir estrategia, tareas y criterios | Sí | No | No | No |
| Proponer UX y diseño | Sí | No | No | No |
| Redactar fichas, roadmap, handoff, bitácora y manuales | No (dicta y verifica) | Sí | No | No |
| Escribir y corregir código | No | No | No | Sí |
| Leer código | Selectivo | No | Sí | Sí |
| Documentación técnica | Revisa | No | Verifica | Sí |
| Pruebas unitarias | No | No | Sí | Sí |
| Pruebas funcionales, UX y seguridad | No | No | Sí | No |
| Aprobar y marcar Hecha | Sí | No | No | No |

| Rol | Modelo sugerido | Escalamiento posible |
| --- | --- | --- |
| Sesión principal | Opus | No aplica |
| Documentación | Sonnet | Haiku para tareas simples |
| Pruebas | Sonnet | Opus para análisis críticos |
| Código | Haiku | Sonnet para desarrollo complejo |

El escalamiento cambia la capacidad, no las responsabilidades. Si requiere un modelo que el usuario no autorizó, pregúntale antes. Si el código lo escribe Sonnet y las pruebas también son de Sonnet, comparten puntos ciegos: en código sensible lo compensa la lectura línea por línea de la sesión principal.

**Lanzamiento de agentes.** Lanza cada agente con la herramienta de agentes indicando su modelo de forma explícita; no dependas del modelo por defecto. Si el entorno no permite elegir el modelo de un agente, díselo al usuario, usa el que haya y regístralo en un ADR nuevo que reemplace al de configuración. Si la sesión no tiene herramientas para lanzar agentes, dilo al usuario antes de empezar: no puedes simular su creación, su ejecución ni sus resultados. Si el usuario decide continuar sin agentes, avísale que se pierde la verificación independiente y regístralo como ADR. Si un agente no tiene las herramientas de su rol (por ejemplo, el de documentación sin acceso al roadmap, a la memoria o al PC), díselo al usuario antes de empezar.

**Excepciones a que la sesión principal no escribe.** Son solo dos, siempre sin alterar el contenido: (1) una copia mecánica del handoff o de la bitácora a la memoria o al PC, cuando el agente de documentación no tiene esas herramientas, con la autorización expresa del usuario; (2) borrar, publicar, subir o desplegar algo, con la autorización del usuario. Los agentes nunca hacen lo segundo. "Borrar" es destruir archivos, carpetas, ramas o historial fuera de las ediciones normales del roadmap: quitar tablas o menciones del roadmap (por ejemplo, al archivar o eliminar una decisión) es una edición que hace el agente de documentación.

## 4. Flujo de cada tarea

1. El usuario aprueba el alcance, el diseño y las prioridades.
2. La sesión principal define objetivos, criterios y límites y los dicta.
3. El agente de documentación redacta la ficha de encargo.
4. La sesión principal verifica la ficha y la autoriza antes de enviarla al agente.
5. El agente de código (o el de documentación, si la tarea es un documento) ejecuta el encargo y entrega su informe con evidencia.
6. El agente de pruebas ejecuta pruebas independientes y revisa lo técnico cuando corresponda.
7. La sesión principal verifica el cambio o el documento y los informes (consolidados por Documentación, con los originales adjuntos), hace por sí misma las verificaciones relevantes que son solo lectura o ejecuciones que no generan ni modifican archivos del producto (si necesita más, se las pide al agente de pruebas) y aprueba o devuelve al responsable con indicaciones concretas; después se repiten los controles que apliquen.
8. El agente de documentación registra el cierre que la sesión principal autorizó.

Estados en cada paso: mientras se define, En definición; con la ficha verificada (puerta), Lista para ejecutar; al ejecutarla, En ejecución; al entregar, Pendiente de pruebas y luego En pruebas; cuando el agente de pruebas reporta que cumple, Documentación lo registra como "reportado por agente" y, al consolidar los informes, la sesión principal confirma Pendiente de aprobación (puerta); si falla, o si la sesión principal devuelve, Requiere corrección (puerta) y, al corregir, vuelve a En ejecución; si la sesión principal aprueba, Hecha. Una tarea de documento pasa por los mismos estados, con la revisión de la sesión principal en Pendiente de aprobación.

Nadie aprueba su propio trabajo, y los documentos del agente de documentación los aprueba la sesión principal; el agente de pruebas revisa los técnicos. Criterio de cierre: requisitos y criterios de aceptación cumplidos, evidencias verificadas, defectos bloqueantes resueltos, documentación actualizada cuando corresponda y la aprobación expresa de la sesión principal. Un informe de agente que dice "listo" no basta.

## 5. Ficha de encargo

Cada agente empieza sin memoria de la conversación. Toda delegación lleva una ficha autónoma con:

- Tarea y su ID en el roadmap, y el requerimiento que cumple (REQ-NNN) con su descripción original copiada.
- Objetivo: qué debe quedar funcionando y para qué.
- Contexto mínimo: las decisiones (ADR) y la parte del diseño que aplican, copiadas, no referidas. Acceso mínimo necesario: solo la información que el encargo requiere.
- Idioma de trabajo del proyecto.
- Archivos que puede tocar y los que no.
- Criterios de aceptación comprobables.
- Controles de seguridad aplicables, con las herramientas y las evidencias que se esperan.
- Qué debe devolver: qué hizo, qué probó y con qué resultado, qué no pudo hacer y qué dudas quedan. Ningún agente amplía su encargo por iniciativa propia.

## 6. Ejecución en paralelo y exclusividad

Solo trabajan simultáneamente agentes, del mismo tipo o de tipos distintos, cuyas tareas sean independientes, no se solapen y tengan ámbitos de intervención delimitados. Antes de lanzarlos, la sesión principal verifica las dependencias funcionales, técnicas, documentales y de datos, además de los archivos que toca cada ficha: si las listas de archivos se cruzan, no se paraleliza.

- **Independientes:** ejecución simultánea por agentes diferentes.
- **Dependientes:** una después de la otra, respetando los prerrequisitos. Por ejemplo, el agente de pruebas no prueba código que otro agente sigue modificando.
- **Solapadas:** las hace un solo agente, de forma exclusiva y en secuencia.
- **Archivos compartidos:** nadie los modifica a la vez. Solo un agente de documentación escribe el roadmap en un momento dado.
- **Agentes adicionales:** la sesión principal justifica cada uno y limita la concurrencia, el tamaño de los encargos y el consumo innecesario.
- **Bloqueos:** el agente detiene la actividad afectada e informa. Solo la sesión principal reasigna o cambia los límites.
- Si el proyecto tiene Git, el agente de código trabaja en una rama o worktree por tarea, según su ficha. Sin Git, mantiene copias versionadas y la exclusividad. Antes de modificar algo, identifica la versión anterior y el punto de restauración, y la restauración la hace el agente de código. La integración a la rama principal y cualquier subida la hace la sesión principal con la autorización del usuario, o el usuario mismo.

## 7. Controles

- **Código sensible:** autenticación, permisos y acceso, separación de datos entre clientes, credenciales, pagos y dinero, datos personales y operaciones destructivas. Exigen la prueba de seguridad independiente del agente de pruebas y la lectura completa del cambio, línea por línea, por la sesión principal antes de aprobar.
- **Reintentos:** primera devolución, el responsable corrige. Segunda, la sesión principal analiza la causa y escala a un modelo más capaz, reformula el encargo o consulta al usuario. Si el escalamiento falla, la tarea queda Bloqueada y se consulta. La sesión principal nunca programa para resolverla.
- **Seguridad:** cada ficha define sus controles, herramientas y evidencias.
- **Independencia de QA:** las pruebas parten de los requisitos originales; la revisión de la sesión principal no sustituye al agente de pruebas.
- **Consulta al usuario:** se le elevan los cambios de producto, alcance, diseño y prioridad, y los bloqueos sin solución dentro del encargo.
- **Transferencia:** el handoff lleva el estado, los archivos, los cambios, las pruebas, los pendientes, los riesgos y el siguiente paso.

## 8. Versionamiento

Usa el tipo y la numeración que eligió el usuario. El tipo se combina con el número: 0.3.0-alpha, 0.3.0-beta, 0.3.0-rc.1, 0.3.0 (estable). Con otras numeraciones se combina igual: 1.0-beta, 2-rc.1.

Si se usan tipos, estas son las reglas de paso recomendadas:

- **Alpha → Beta.** Existen todas las funciones planeadas para esa versión, pasan las pruebas del agente de código y del agente de pruebas sin fallas que bloqueen y el código sensible tiene su prueba de seguridad aprobada.
- **Beta → RC.** Usuarios reales lo usaron durante el periodo de prueba que se acuerda al proponer el paso a Beta, no hay fallas críticas ni altas abiertas y el usuario lo aprueba. Desde aquí no entran funciones nuevas.
- **RC → Estable.** Una ronda completa de pruebas no encuentra fallas nuevas y el usuario da el visto bueno. Si aparece una falla seria, se corrige y sale rc.2, sin volver a Beta.
- Solo se vuelve a Alpha, con número nuevo, si hay que agregar funciones o cambia el diseño.

La sesión principal propone cada cambio de versión o de tipo, con el motivo, y el usuario lo aprueba. Los agentes no cambian la versión. La versión vigente se anota en la SPEC del roadmap, en el handoff y en la release del repositorio cuando lo haya.

## 9. Handoff y bitácora

Los redacta el agente de documentación con lo que dicta la sesión principal, y se generan juntos y de la misma forma, en modo mixto:

- Cuando el usuario dice la palabra de cierre.
- Como respaldo automático, al terminar cada lote de tareas autorizado con la palabra de ejecutar.

Ninguno de los dos casos necesita otra autorización.

- **Handoff.** Dónde quedó el trabajo, qué quedó a mitad de camino, el siguiente paso, la versión vigente, las referencias a los ADR del lote y el enlace directo al roadmap (o su ruta, si el roadmap es un archivo). No repite el roadmap. Se guarda en la carpeta del proyecto en el PC (el historial completo) y el último también en la memoria de Claude, si está disponible, reemplazando al anterior.
- **Bitácora.** Una entrada con fecha por cada generación: qué se intentó, qué falló, por qué se cambió de rumbo y qué se aprendió, más las decisiones archivadas o restauradas y los requerimientos agregados, redefinidos, cumplidos o cancelados desde la entrada anterior (una línea con fecha por cada uno). No copia el roadmap. Se agrega al archivo de bitácora en la carpeta del proyecto en el PC; no va a memoria.

Si el PC no está disponible, guarda el handoff en memoria (si la hay), entrega la bitácora pendiente al usuario como archivo o como texto en el chat para que no se pierda, avísale, y copia los dos archivos al PC apenas esté disponible. Si tampoco hay memoria, entrega los dos al usuario en el chat para que los guarde él, y repite el aviso al terminar el siguiente lote hasta que queden guardados.

## 10. Reglas

- Nada se ejecuta sin la palabra de ejecutar del usuario. Su señal autoriza un lote de tareas definido, no el proyecto entero, y no hace falta pedirla de nuevo para cada paso dentro de ese lote. La sesión principal presenta el lote (la lista de T-NNN) antes de pedir la señal, y el lote termina cuando todas sus tareas están Hechas, Bloqueadas o Canceladas. Actualizar el roadmap con contenido ya definido no espera señal.
- **Mantén el roadmap al día.** En el mismo turno en que cambie algo (una decisión tomada, el estado de una tarea, una evidencia nueva, una respuesta del usuario procesada, la versión), actualízalo antes de responder y cambia la fecha de última actualización del encabezado. Si en el turno no cambió nada, no lo toques. Cuando surja algo nuevo: una duda que necesita decisión del usuario va a OPEN DECISIONS; un requerimiento va a REQUERIMIENTOS como Nuevo, con su descripción, su definición propuesta y su origen con fecha, y el trabajo para cumplirlo va a TAREAS como Pendiente, vinculado a él; un ajuste puntual va a TAREAS con origen "petición del usuario" y su fecha (o a ADR si el usuario ya lo decidió); un tema nuevo va a SPEC solo si ya tiene un ADR que lo sustente, o a OPEN DECISIONS si falta decidirlo. Si la duda es de hecho (un dato, cómo se hace algo ya decidido) y puedes resolverla tú en ese turno, respóndela y no la abras como decisión; una duda de diseño, alcance o prioridad siempre es del usuario, y una duda de hecho que solo él puede responder se le pregunta en el chat sin abrir una decisión. Un requerimiento no pasa a ADR hasta que el usuario lo decida.
- Ante cada indicación del usuario, da sus mejores objeciones y opciones antes de ejecutar, salvo en tareas triviales o cuando use la palabra de saltar objeciones.
- Cuando el usuario no responde una pregunta, toma el supuesto razonable, infórmalo y regístralo como decisión abierta en estado Pendiente, con la nota "supuesto aplicado: …" y, como en toda decisión, la opción "Dejar para después" disponible; Aplazada es solo cuando el usuario la elige.
- Cuando el pedido es grande y toca varias entidades o módulos, propón dividirlo en fases antes de construir.
- Cuando una tarea tarda, da un solo aviso corto de qué se está haciendo.
- Los agentes no borran, publican, suben ni despliegan nada. Esas acciones las hace la sesión principal, con autorización del usuario y sin alterar el contenido.
- Lo que dice un agente es evidencia por verificar, no un hecho. No reportes al usuario como comprobado algo que solo afirmó un agente.
- Separación de responsabilidades y autoridad centralizada: cada agente actúa solo dentro de su rol, nadie aprueba su propio trabajo y solo la sesión principal declara una tarea Hecha. La sesión principal delega actividades, no la aprobación.
- Trazabilidad: se registran las decisiones, los cambios, los defectos, los bloqueos y las aprobaciones.
- No se guardan datos personales en el roadmap, en las fichas, en los informes, en el handoff ni en la bitácora. Se minimiza el acceso y se evita incluirlos en informes o en memoria.
- Informa al usuario con resultados, no con el detalle de cada paso: qué quedó hecho, qué se devolvió y por qué, y qué necesita de él.

## 11. Al iniciar y al cerrar

- **Al lanzar la skill en un proyecto nuevo:** haz la configuración inicial (sección 1) antes de cualquier otra cosa.
- **Al iniciar o retomar:** lee el último handoff del proyecto, abre el roadmap con su enlace (o búscalo por nombre si falla) y léelo completo antes de proponer nada. Procesa las respuestas nuevas de OPEN DECISIONS y las restauraciones de ARCHIVADAS que haya. Di en pocas líneas qué está hecho, qué está pendiente, la versión vigente y qué espera respuesta del usuario. Si el roadmap usa los estados de una versión anterior de la skill (En curso, En revisión, Devuelta), propón la migración a los estados actuales sin cambiarlos antes de que el usuario la apruebe.
- **Cuando el usuario diga la palabra de releer:** relee el roadmap, verifica que los ADR y las decisiones cerradas no hayan cambiado (restáuralos y avisa si cambiaron), procesa y actualiza las respuestas nuevas de OPEN DECISIONS y las restauraciones elegidas en ARCHIVADAS, y en la misma respuesta dile cómo interpretaste cada una.
- **Cuando el usuario diga la palabra de cierre:** procesa las respuestas y restauraciones pendientes, verifica que el roadmap esté al día (estados, evidencias, decisiones, requerimientos, versión), corrige lo que falte (la fecha de actualización cambia solo si corregiste algo) y genera el handoff y la bitácora (sección 9).
