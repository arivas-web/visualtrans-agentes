# Visual Trans / Visual MS — Ejército de agentes

Esta carpeta es la base de operaciones de un conjunto creciente de
agentes especializados (subagentes de Claude Code) para **Visual
Trans / Visual MS**, empresa española de software B2B para
logística/aduanas (eCMR, DUA, Intrastat, ICS2, AEAT, Verifactu).

Es el hogar general donde se van consolidando los sistemas de agentes
de distintas áreas del negocio conforme existen — el primero en
migrarse aquí es el sistema de contenido de LinkedIn (ver más abajo).

## Estructura

- `.claude/agents/` — un archivo `.md` por agente. Cada agente es un
  subagente de Claude Code: se define con su propio rol, alcance y
  herramientas, y se puede invocar de dos formas:
  1. Dejando que la sesión principal decida delegar en él según su
     descripción.
  2. Pidiéndolo explícitamente por su nombre ("usa el agente X para
     ...", "habla directamente con X").
  La invocación es siempre por el campo `name` del agente, sea cual
  sea la carpeta donde viva el archivo — Claude Code descubre
  subagentes de forma recursiva dentro de `.claude/agents/`, así que
  los de un mismo sistema se agrupan en su propia subcarpeta (p. ej.
  `.claude/agents/linkedin/`) sin que eso afecte a cómo se invocan.
- `.claude/commands/` — comandos de barra (`/nombre-comando`) que
  actúan como orquestadores de un flujo concreto, invocando a varios
  subagentes en orden. `/pipeline-mensual` es el primero.
- `orquestador.md` — coordina el trabajo entre el resto de agentes,
  mantiene una vista general de qué hace cada uno, y ayuda a diseñar
  agentes nuevos con un estilo consistente. Es un agente de propósito
  general, distinto de los orquestadores específicos de un flujo (como
  `/pipeline-mensual`).

## Cómo trabajar aquí

- La sesión por defecto (esta misma, la que ves al abrir Claude Code
  en esta carpeta) es de propósito general: puede resolver cosas
  sueltas directamente o delegar.
- Para tareas de coordinación general o para pedir un estado del
  "ejército", invoca al agente **orquestador**.
- Para un flujo de trabajo concreto ya definido (como el mensual de
  LinkedIn), usa su comando dedicado en vez de pedirlo suelto.
- Para tareas puntuales de un dominio muy concreto, puedes hablar
  directamente con el agente especializado, sin pasar por el
  orquestador.
- Los agentes nuevos se añaden como archivos sueltos en
  `.claude/agents/`.

---

## Sistema LinkedIn — pipeline mensual

Migrado el 2026-09-23 desde el repo independiente `arivas-web/linkedin-agent`
(commit `6d617fb`), que queda archivado sin recibir más commits nuevos —
este repo pasa a ser el único sitio donde vive y se ejecuta.

Arquitectura de agente orquestador + subagentes casi 100% autónoma para
generar el calendario editorial mensual de LinkedIn (~65-70 posts/mes en 5
perfiles), con un único punto de fricción humana intencional: la validación
del calendario mensual antes de redactar ningún post. Objetivo de negocio:
100.000 impresiones/mes.

### Cómo lanzar el pipeline completo

```
/pipeline-mensual octubre 2026
```

Una sola invocación ejecuta todo el flujo de principio a fin: procesa
`linkedin/INBOX.md`, investiga tendencias/normativas/eventos del mes, construye el
calendario, redacta los posts de los 5 perfiles, genera una presentación
(.pptx) con un post por diapositiva para revisión visual, y los valida
contra las restricciones absolutas. No pide confirmación en ningún punto
**salvo uno**: en cuanto el calendario está construido, lo envía como
Google Sheets por correo a `arivas@visualtrans.com` y el pipeline se
detiene ahí hasta que se valida la conversación (en el chat, no en el
propio Sheets). Tras esa confirmación, continúa solo hasta el final sin
más pausas. El comando está definido en
`.claude/commands/pipeline-mensual.md`.

Todo el trabajo del pipeline (cada fase, cada ronda de corrección) se
comitea y pushea automáticamente a `main` sin pedir confirmación en cada
paso (ver "Git y entrega continua" más abajo) — esta rama es compartida
con el orquestador y el resto de agentes de este repo.

### Tu único trabajo manual: `linkedin/INBOX.md`

Escribe ahí, en cualquier momento, cualquier cosa suelta: una noticia, un
evento nuevo, un cambio de tono para un perfil, un pain nuevo, una campaña
que se activa, un caso de éxito disponible. Sin formato obligatorio, solo
con fecha delante. La próxima vez que corra `/pipeline-mensual`, el
`agente-archivista` la clasifica, la incorpora al archivo estructurado
correspondiente y la mueve a `linkedin/INBOX_procesado.md` con fecha de proceso
(histórico, nunca se borra). No hace falta tocar ningún otro archivo ni
relanzar nada aparte del comando habitual.

### Dónde viven los datos de este sistema

```
/linkedin/INBOX.md                      ← tú escribes aquí libremente
/linkedin/INBOX_procesado.md            ← histórico de lo ya incorporado (auditable)
/linkedin/Contexto_Visual_Trans.txt     ← productos, propuesta de valor, argumentario
/linkedin/Pains_Unificados.txt          ← los pains numerados con descripción completa
/linkedin/Eventos_Campañas.txt          ← ferias, webinars, lanzamientos, normativas con fecha, campañas
/linkedin/Voz_VT.txt                    ← documento de voz — Visual Trans (empresa)
/linkedin/Voz_Ceci.txt                  ← documento de voz — Cecilio Labrada
/linkedin/Voz_Emma.txt                  ← documento de voz — Emma González
/linkedin/Voz_Enrique.txt               ← documento de voz — Enrique Saa
/linkedin/Voz_Laura.txt                 ← documento de voz — Laura Díaz
/linkedin/output/[mes-año]/briefing.md          ← investigación del mes
/linkedin/output/[mes-año]/calendario.md        ← calendario completo en markdown
/linkedin/output/[mes-año]/posts/[perfil].md    ← posts redactados, uno por perfil
/linkedin/output/[mes-año]/validacion.md        ← informe del agente-validador
/linkedin/output/[mes-año]/log-decisiones.md    ← auditoría de decisiones autónomas
```

Estos archivos de datos (voz, contexto, pains, eventos, inbox, output) se
reorganizaron el 2026-09-23 de la raíz del repo a `linkedin/`, para no
llenar la raíz de ficheros propios de un solo sistema a medida que se
añadan más agentes de otras áreas. Los subagentes los leen con una ruta
relativa desde la raíz del repo (`Read linkedin/Voz_Ceci.txt`) — mover el
archivo de definición de un subagente a una subcarpeta de
`.claude/agents/` no cambia estas rutas, porque se resuelven contra el
directorio de trabajo del proyecto, no contra dónde vive el `.md` del
agente. Si en el futuro se añaden agentes de otras áreas del negocio con
sus propios ficheros de datos, dales su propia carpeta en la raíz (p. ej.
`atencion-cliente/`) siguiendo este mismo patrón.

### Arquitectura de agentes

**Orquestador de este flujo** = el comando `/pipeline-mensual` (no es un
subagente propio; es el hilo principal de Claude Code siguiendo las
instrucciones de `.claude/commands/pipeline-mensual.md`). Coordina la
invocación de los subagentes en orden, decide en los puntos ambiguos, y
mantiene el log de decisiones. Es distinto del agente **orquestador**
general de este repo (ver arriba), que coordina entre sistemas de agentes,
no dentro de uno.

**Subagentes** (`.claude/agents/linkedin/`), cada uno con contexto
aislado y responsabilidad única:

| Agente | Responsabilidad |
|---|---|
| `agente-archivista` | Procesa `linkedin/INBOX.md`, clasifica y vuelca a los archivos estructurados |
| `agente-investigador` | Investiga tendencias, normativas, ferias y decide el pain prioritario del mes |
| `agente-calendario` | Construye el calendario aplicando pilares, no-solapamiento de pains y asignación por perfil; lo envía como Google Sheets por correo a `arivas@visualtrans.com` |
| `agente-redactor` | Redacta los posts de un perfil concreto (se invoca 1 vez por perfil, parametrizado, en paralelo) |
| `agente-presentacion` | Construye un .pptx con un post por diapositiva a partir de lo ya redactado, para revisión visual — entregable auxiliar, no bloquea el pipeline |
| `agente-validador` | Verifica el resultado final contra las restricciones absolutas antes de entregar |

Además de estos 5 (más el parametrizable `agente-redactor`), el propio comando
`/pipeline-mensual` gestiona una **Fase 4.5** de aprobación humana (ver más
abajo) — no es un subagente, es una pausa del orquestador del flujo.

`agente-redactor` es un único agente parametrizable en vez de 5 agentes
separados: el orquestador del pipeline lo invoca cinco veces (una por
perfil, en paralelo) indicándole en el prompt de la tarea qué perfil le
toca y qué documento de voz debe leer.

### Reglas de negocio

- Distribución de pilares: 60% Noticias, 30% Pains, 10% Casos de éxito
  (los casos de éxito **nunca se redactan** — solo se reserva el slot
  `CASO DE ÉXITO — pendiente Adrián`).
- No-solapamiento de pains: nunca el mismo pain el mismo día en dos
  perfiles, nunca en días consecutivos del mismo perfil, máximo 2
  apariciones por pain al mes.
- Asignación de pains por perfil según voz y audiencia (ver
  `agente-calendario.md`).
- Patrones de alto rendimiento específicos por perfil (ver cada
  `linkedin/Voz_[perfil].txt`).
- Restricciones absolutas: nunca lenguaje de venta directa, solo días
  laborables, cierres obligatorios por perfil, voz nunca improvisada ni
  mezclada entre perfiles.

Estas reglas viven repartidas entre los documentos de voz (`linkedin/Voz_*.txt`),
los datos de negocio (`linkedin/Contexto_Visual_Trans.txt`, `linkedin/Pains_Unificados.txt`)
y las reglas de distribución fijas embebidas en `agente-calendario.md` —
no hace falta mantener una copia separada: cada subagente lee lo que
necesita de estos archivos en tiempo de ejecución.

### Git y entrega continua

El pipeline comitea y pushea directamente a `main` después de cada fase
que produzca archivos nuevos o modificados (Fase 0, Fase 1, Fase 2
—incluidas sus rondas de corrección—, Fase 3, Fase 3.5, Fase 4, y la
creación de `APROBADO.md` en la Fase 4.5) sin pedir confirmación al usuario
en cada paso. Esta autorización es permanente y no debe volver a
solicitarse en cada ejecución del pipeline; es independiente de las dos
pausas reales del sistema (validación del calendario en Fase 2, aprobación
de los posts en Fase 4.5), que siguen siendo exclusivamente sobre el
contenido, no sobre git. Las protecciones generales de git siguen
intactas: nunca `--force`, nunca `--no-verify`, nunca reescribir historia
ajena.

### Entrega a gráficas (Magnific) — GitHub Actions

Desde 2026-09-23 hay una segunda pieza del sistema, propiedad de un
compañero del usuario, en **otro repo de Claude Code** distinto de este:
genera las gráficas de cada post con Magnific y publica el resultado
(texto + imagen, en una sola llamada) en Metricool. Ese repo no vive aquí
y este documento no lo gestiona — solo describe el contrato de entrega
entre los dos.

**Disparo:** el pipeline se detiene en la Fase 4.5 hasta que el usuario
aprueba explícitamente los posts ya redactados y validados (ver arriba).
Al aprobar, se crea `linkedin/output/[mes-año]/APROBADO.md` y se pushea a
`main`. Eso es lo único que activa lo que sigue — nunca el resto de
commits automáticos del pipeline.

**`.github/workflows/aviso-graficas.yml`** escucha únicamente cambios en
`linkedin/output/**/APROBADO.md` sobre `main`, detecta el mes-año aprobado,
y manda un `repository_dispatch` (`event_type: posts-aprobados`) al repo
del compañero, con este payload:

```json
{
  "event_type": "posts-aprobados",
  "client_payload": {
    "mes": "2026-10",
    "repo": "arivas-web/visualtrans-agentes",
    "calendario": "linkedin/output/2026-10/calendario.md",
    "posts_dir": "linkedin/output/2026-10/posts",
    "validacion": "linkedin/output/2026-10/validacion.md"
  }
}
```

**Secretos pendientes de configurar** (Settings → Secrets and variables →
Actions de este repo) antes de que el workflow funcione — sin ellos falla
con un mensaje explícito en vez de callar:
- `GRAFICAS_REPO` — `owner/repo` del compañero en GitHub.
- `GRAFICAS_DISPATCH_TOKEN` — token con permiso para disparar
  `repository_dispatch` en ese repo.

**Lo que pasa después ya no es cosa de este repo:** el repo del compañero
necesita su propio workflow escuchando `repository_dispatch` con
`types: [posts-aprobados]`, que lea los ficheros indicados en
`client_payload` (necesita acceso de lectura a este repo — vía token o
haciendo el propio repo público/con colaborador añadido) y lance su
agente de Claude Code en modo sin supervisión para generar las gráficas y
publicar en Metricool.

### Auditoría

Cada ejecución del pipeline genera su propio
`linkedin/output/[mes-año]/log-decisiones.md` con todo lo que antes requería
aprobación manual: qué tendencias se eligieron y por qué, qué pain se
priorizó, qué entradas de INBOX quedaron marcadas como "requiere revisión",
y el resultado de la validación final. El pipeline nunca se detiene a
esperar respuesta a este log — es para auditar el resultado *después*, no
para bloquear la ejecución.
