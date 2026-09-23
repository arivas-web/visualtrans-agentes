# Visual Trans / Visual MS — Ejército de agentes

Esta carpeta es la base de operaciones de un conjunto creciente de
agentes especializados (subagentes de Claude Code) para **Visual
Trans / Visual MS**, empresa española de software B2B para
logística/aduanas (eCMR, DUA, Intrastat, ICS2, AEAT, Verifactu).

No sustituye a otros montajes puntuales que ya existan para temas
concretos (p. ej. el coordinador de contenidos de LinkedIn en
`agente-linkedin-coordinador/`). Esta carpeta es el hogar general
donde se irán añadiendo agentes especializados de distintas áreas del
negocio conforme se necesiten.

## Estructura

- `.claude/agents/` — un archivo `.md` por agente. Cada agente es un
  subagente de Claude Code: se define con su propio rol, alcance y
  herramientas, y se puede invocar de dos formas:
  1. Dejando que la sesión principal decida delegar en él según su
     descripción.
  2. Pidiéndolo explícitamente por su nombre ("usa el agente X para
     ...", "habla directamente con X").
- `orquestador.md` — coordina el trabajo entre el resto de agentes,
  mantiene una vista general de qué hace cada uno, y ayuda a diseñar
  agentes nuevos con un estilo consistente.
- `linkedin.md` — gestiona el calendario y la redacción de LinkedIn
  para el perfil de empresa y los perfiles personales (Emma, Cecilio,
  Enrique, Laura). Su contexto y voces de cada perfil viven en
  `linkedin/` al lado de este archivo.

## Cómo trabajar aquí

- La sesión por defecto (esta misma, la que ves al abrir Claude Code
  en esta carpeta) es de propósito general: puede resolver cosas
  sueltas directamente o delegar.
- Para tareas de coordinación, planificación entre varios agentes, o
  para pedir un estado general del "ejército", invoca al agente
  **orquestador**.
- Para tareas de un dominio muy concreto, una vez existan agentes
  especializados, se les puede hablar directamente sin pasar por el
  orquestador.
- Los agentes nuevos se añaden como archivos sueltos en
  `.claude/agents/`, siguiendo el mismo formato que `orquestador.md`.
