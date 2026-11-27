# DEATHNOTE LUSH ROADMAP

Skill para organizar y controlar proyectos con Claude: un roadmap único por proyecto, un equipo fijo de cuatro roles, un handoff y una bitácora que guardan la continuidad entre sesiones, y un versionamiento acordado desde el inicio.

**Versión:** 1.0.0

**Autor:** www.soportevirtualai.com - Diego Scarpetta, Consultor de Proyectos IA

## Qué hace

- **Roadmap único por proyecto, siempre al día.** Un documento con seis secciones fijas: ADR (decisiones tomadas), SPEC (resumen de qué hace el sistema), REQUERIMIENTOS (lo que el sistema debe cumplir, con su descripción, su definición y sus tareas), OPEN DECISIONS (lo que falta decidir, cada una en su tabla con estado, opciones y campo libre de contexto), TAREAS (qué se hizo y qué sigue, con su evidencia) y ARCHIVADAS (decisiones descartadas que se pueden restaurar).
- **Equipo de cuatro roles.** Una sesión principal (se recomienda en Opus) que piensa, define, verifica y aprueba; un agente de documentación (por defecto Sonnet), un agente de pruebas (por defecto Sonnet) y un agente de código (por defecto Haiku). Los modelos son sugeridos y se pueden cambiar. Nadie aprueba su propio trabajo y solo la sesión principal marca una tarea como Hecha.
- **Handoff y bitácora.** El handoff dice dónde quedó el trabajo y cuál es el siguiente paso; la bitácora registra el proceso (qué se intentó, qué falló y por qué se cambió de rumbo). Se generan juntos, con una palabra clave del usuario y como respaldo al terminar cada lote de tareas.
- **Versionamiento.** Tipo (Alpha, Beta, Release Candidate o ninguno) y numeración (1.0, 0.1, 0.0.1, 1 o personalizada), con reglas para pasar de un tipo a otro.
- **Configuración inicial por usuario.** Idioma, equipo, palabras clave, carpeta del proyecto y versionamiento se eligen al iniciar y se registran como decisión del proyecto. La skill trabaja en el idioma del usuario.

## Cómo usarla

1. Importa el archivo `SKILL.md` como skill en tu cuenta de Claude.
2. En un proyecto, invoca la skill o menciona "DEATHNOTE LUSH ROADMAP".
3. Responde la configuración inicial. Las palabras y la carpeta que propone son valores por defecto que puedes cambiar.

La skill pide una carpeta de tu equipo para guardar el handoff y la bitácora; no guarda datos personales en ellos.

## Licencia

Esta obra se publica bajo la licencia [MIT](https://opensource.org/license/mit). Puedes usarla, copiarla, modificarla y distribuirla, incluso con fines comerciales, conservando el aviso de derechos de autor y la licencia. Consulta el archivo `LICENSE`.

Las versiones publicadas antes de la 1.0.0 (0.3.2 y anteriores) se publicaron bajo CC BY-NC 4.0 y siguen con esa licencia.

## Contribuciones

La rama principal está protegida: cualquier cambio entra por revisión del autor.
