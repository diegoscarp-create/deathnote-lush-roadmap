# DEATHNOTE LUSH ROADMAP

Skill para organizar y controlar proyectos con Claude: un roadmap único por proyecto, un equipo fijo de tres roles, un handoff y una bitácora que guardan la continuidad entre sesiones, y un versionamiento acordado desde el inicio.

**Versión:** 0.3.2

**Autor:** www.soportevirtualai.com - Diego Scarpetta, Consultor de Proyectos IA

## Qué hace

- **Roadmap único por proyecto.** Un documento con cuatro secciones fijas: ADR (decisiones tomadas), SPEC (resumen de qué hace el sistema), OPEN DECISIONS (lo que falta decidir) y TAREAS (qué se hizo y qué sigue, con su evidencia).
- **Equipo de tres roles.** Una sesión principal que piensa, define, revisa y aprueba; un agente de pruebas (por defecto Sonnet) y un agente de código (por defecto Haiku). Nadie aprueba su propio trabajo.
- **Handoff y bitácora.** El handoff dice dónde quedó el trabajo y cuál es el siguiente paso; la bitácora registra el proceso (qué se intentó, qué falló y por qué se cambió de rumbo). Se generan juntos, con una palabra clave del usuario y como respaldo al terminar cada lote de tareas.
- **Versionamiento.** Tipo (Alpha, Beta, Release Candidate o ninguno) y numeración (1.0, 0.1, 0.0.1, 1 o personalizada), con reglas para pasar de un tipo a otro.
- **Configuración inicial por usuario.** Idioma, equipo, palabras clave, carpeta del proyecto y versionamiento se eligen al iniciar y se registran como decisión del proyecto. La skill trabaja en el idioma del usuario.

## Cómo usarla

1. Importa el archivo `SKILL.md` como skill en tu cuenta de Claude.
2. En un proyecto, invoca la skill o menciona "DEATHNOTE LUSH ROADMAP".
3. Responde la configuración inicial. Las palabras y la carpeta que propone son valores por defecto que puedes cambiar.

La skill pide una carpeta de tu equipo para guardar el handoff y la bitácora; no guarda datos personales en ellos.

## Licencia

Esta obra se publica bajo la licencia [Creative Commons Atribución-NoComercial 4.0 Internacional (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/). Puedes copiarla, redistribuirla y adaptarla citando al autor y sin fines comerciales. Consulta el archivo `LICENSE`.

Atribución sugerida:

> DEATHNOTE LUSH ROADMAP, de Diego Scarpetta (www.soportevirtualai.com), licenciada bajo CC BY-NC 4.0.

## Contribuciones

La rama principal está protegida: cualquier cambio entra por revisión del autor.
