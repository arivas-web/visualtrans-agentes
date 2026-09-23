# Log de decisiones — Octubre 2026

Generado automáticamente por el pipeline `/pipeline-mensual`. Documenta las
decisiones que en el flujo anterior requerían input humano directo (respuestas de
briefing, OK al calendario) y que ahora el sistema toma de forma autónoma. No
bloquea la ejecución: es un registro para auditoría posterior.

## Entradas de INBOX procesadas

3 entradas procesadas (2026-09-22), todas volcadas a `Eventos_Campañas.txt`:

- Feria Conxemar 2026 (06-08/10/2026) — Visual Trans en stand 2A01 junto al Clúster
  da Función Loxística.
- XIV Congreso FETEIA-OLTRA 2026 en Tenerife (01-04/10/2026) — retos del comercio
  internacional/logística/aduanas (novedades aduaneras, Ley de Movilidad Sostenible,
  relevo generacional).
- DeCA obligatorio a partir del 05/10/2026 (cambio normativo).

No se tocó `Contexto_Visual_Trans.txt`, `Pains_Unificados.txt` ni `Voz_*.txt`: ninguna
entrada de este lote encajaba en esas categorías. `INBOX.md` ha quedado limpio; las 3
entradas se movieron a `INBOX_procesado.md`.

**Nota del archivista:** las 3 entradas no traían fecha propia delante de la línea
(formato recomendado `- YYYY-MM-DD: texto`); estaban agrupadas bajo un encabezado
suelto "Octubre:". No bloquea nada, pero conviene recordarlo para el futuro.

**Nota para agente-calendario:** en las 3 entradas, el campo "Relevancia" (qué
perfil(es) debe tocar el evento) se ha dejado marcado como "perfil(es) a determinar
por agente-calendario" — el archivista no asigna perfiles, esa decisión corresponde
a esta fase.

## Requiere revisión (INBOX ambiguo o contradictorio)

Ninguna. Las 3 entradas eran eventos/normativa con fecha concreta, sin ambigüedad ni
contradicción con reglas existentes.

## Investigación del mes

**Tendencias elegidas y por qué:**
- DeCA digital obligatorio (05/10/2026) — noticia principal del mes: fecha exacta,
  cobertura mediática amplia (transportes.gob.es, Camión Actualidad, Guitrans, GA&P),
  y coincide casi al día con Conxemar y FETEIA. Confianza alta.
- eCMR / digitalización de la carta de porte — complementaria al DeCA pero distinta
  (transporte internacional vs. nacional). Confianza alta.
- IA aplicada a automatización documental/aduanera — tendencia transversal 2026, sin
  hito de fecha concreto. Confianza media (fuentes mayoritariamente blogs de
  proveedores).
- ICS2 en plena implantación (obligatorio desde 1/1/2026, ampliado desde 1/6/2026) —
  telón de fondo normativo, sin hito propio en octubre. Confianza media-alta.

**Ferias/eventos y asignación de perfiles** (resolviendo la pendiente que dejó el
archivista):
- Conxemar 2026 (06-08/10, Vigo, stand 2A01) → **Visual Trans (empresa) y Enrique**
  — ambos tienen en su voz el patrón consolidado de "presencia física en feria".
- XIV Congreso FETEIA-OLTRA (01-04/10, Tenerife, sin participación confirmada de VT)
  → **Emma y Cecilio** — patrón de análisis sectorial/autoridad técnica, más adecuado
  que un post de asistencia no confirmada.

**Pain prioritario del mes y criterio usado:**
- Pain #7 — "Miedo a no estar adaptado a los cambios legales a tiempo".
- Criterio (b) de la cascada: sin campaña comercial activa con urgencia explícita
  (descartada la opción a), pero con noticia normativa del mes (DeCA, fecha exacta
  5/10/2026) que conecta textualmente con el pain. ICS2 refuerza como apoyo
  secundario.
- Opción (c) no aplicable: `output/` no tenía ningún mes anterior (primera ejecución
  del sistema), sin histórico de pains recientes.

**Temas descartados por falta de información:**
- Sistema H1 (CAU) — ya vigente desde 14/10/2025, no es novedad de este mes.
- Actualización TARIC/Nomenclatura Combinada 2027 — fecha de publicación no
  verificada, no se inventó fecha.
- Casos de éxito de clientes — ninguno registrado; se reserva igualmente el 10% del
  calendario con la etiqueta "CASO DE ÉXITO — pendiente Adrián".
- Lanzamientos de producto (Visual Trans / Tariff Code / vForwarding) — sin registro
  este mes en fuentes internas; no se buscó en la web por ser información interna.

## Construcción del calendario

**Resumen de distribución (verificado):** 70 posts totales — Visual Trans 18 (25,7%),
Emma González 13 (18,6%), Cecilio Labrada 13 (18,6%), Enrique Saa 13 (18,6%), Laura
Díaz 13 (18,6%). Pilares exactos: Noticias 42/70 (60,0%), Pains 21/70 (30,0%), Casos
de éxito 7/70 (10,0%). Pain #7 aparece 2 veces (máximo permitido), en Enrique Saa
(08/10 y 29/10), sin coincidir el mismo día en dos perfiles ni en días consecutivos
del mismo perfil. Cero publicaciones en fin de semana.

**Decisiones de relleno y asignación (trasladadas de `calendario.md`):**
- Octubre empieza en jueves → Semana 1 parcial (01-02/10) con carga reducida (6
  posts) en vez de omitirla, coincidiendo con el arranque real de FETEIA (01-04/10).
- Se respetó la asignación explícita del briefing (Conxemar → Visual Trans + Enrique;
  FETEIA → Emma + Cecilio), como excepción justificada a la heurística general de
  "la empresa abre el tema".
- El DeCA (05/10, lunes) se fijó en su fecha exacta de entrada en vigor pese a que
  lunes no es el día de mejor rendimiento histórico, por prioridad de fechas
  normativas fijas.
- Para cubrir el 60% de Noticias con solo 4 hitos sólidos del briefing, se generaron
  ángulos secundarios por perfil/día: balances ("dos semanas de DeCA"), precedente
  del sistema H1/CAU (21/10, como contexto, no como novedad), relevo generacional de
  FETEIA (20/10 y 29/10), y cierres de mes (27-30/10).
- Los 7 slots de Casos de éxito se reservaron como "CASO DE ÉXITO — pendiente
  Adrián" (ningún caso confirmado este mes); 4 de 7 situados cerca de Conxemar por
  ser el contexto más natural.
- No hubo pains nuevos (>20) este mes.
- No existía histórico de meses anteriores en `output/` (mes inaugural del sistema);
  queda documentado para que noviembre 2026 sí pueda aplicar el criterio (c) de la
  cascada de pains.

## Validación del calendario (Fase 2)

- **Google Sheets generado:** "Calendario LinkedIn — Octubre 2026" —
  https://docs.google.com/spreadsheets/d/1BsrQJ68cGyV5SwRmtxsQm_YoUHdB0QtE3ImiDC61JeQ/edit
  (compartido con arivas@visualtrans.com como writer).
- **Correo enviado** a arivas@visualtrans.com, asunto "Calendario LinkedIn Octubre
  2026 — pendiente de validación" (id de mensaje `1a0c9d09191f4792`), con el enlace,
  el resumen de distribución y la petición explícita de validación.
- **Resultado de la validación del usuario (v1):** el usuario pidió 5 correcciones
  antes de aprobar (ver ronda de corrección 1 abajo). No se aprobó la v1.

### Ronda de corrección 1

El usuario solicitó, sobre el Google Sheets v1:
1. Visual Trans debe publicar algo del primer día de FETEIA (01/10).
2. No se van a hacer vídeos — eliminar todos los formatos de vídeo.
3. Regla nueva y permanente: en cualquier evento cubierto por varios perfiles,
   Visual Trans publica siempre antes que el resto.
4. El post "Gracias a quienes pasasteis por el stand en Conxemar" (12/10) pasa de
   Enrique Saa a Emma González.
5. Los perfiles personales (Emma, Cecilio, Enrique, Laura) tienen experiencia y
   autoridad, pero no son operativos — revisar y reformular cualquier enfoque
   planteado en primera persona operativa.

**Correcciones aplicadas (v2):**
1. El post de VT del 01/10 pasa de "DeCA: en 4 días..." a cubrir el arranque de
   FETEIA ese mismo día, antes que Emma y Cecilio. La cuenta atrás del DeCA queda
   absorbida por su cobertura ya sólida en otras fechas (05/10 ×3, 06/10, 19/10 ×2).
2. Se sustituyeron las 14 apariciones de formatos de vídeo ("vídeo corto", "vídeo
   evento", "vídeo/testimonio") por formatos ya usados en el calendario (imagen +
   texto corto, texto largo, etc.). Verificado que no queda ningún formato de vídeo.
3. Revisado evento por evento (FETEIA, Conxemar, DeCA, eCMR, ICS2) y reordenado para
   que Visual Trans publique siempre primero: ajustes en Conxemar (Enrique 02/10 y
   05/10 pasaron a otros temas), eCMR (Emma se movió del 08/10 al 20/10) e ICS2
   (intercambio de temas de VT entre 13/10 y 15/10). La regla se interpretó como
   aplicable a hitos con nombre propio y cobertura cruzada explícita, no a
   tendencias genéricas sin fecha fija (IA, relevo generacional).
4. El post de Conxemar del 12/10 pasa a Emma González (mismo pilar, mismo formato,
   tono suavizado a su voz). Su pain #5 de ese día se trasladó al 15/10 (sin
   solapamiento ni adyacencia con sus otros días de pain: 06/10 y 22/10). Enrique
   recuperó su cadencia con un post nuevo el 12/10, publicado después de VT.
5. Reformuladas 4 entradas de Emma con lenguaje operativo en primera persona
   (01/10, 05/10, 19/10, 26/10) hacia un ángulo de análisis/autoridad sectorial. El
   post de Emma del 15/10 se sustituyó de raíz por el pain trasladado en el punto 4.
   No se encontraron entradas equivalentes en Cecilio, Enrique o Laura.

**Verificación tras los cambios:** 70 posts sin cambio; pilares 60,0% / 30,0% /
10,0% exactos; perfiles sin cambio (VT 18, resto 13 c/u); ningún pain supera 2
apariciones; sin publicaciones en fin de semana.

- **Google Sheets v2 generado:** "Calendario LinkedIn — Octubre 2026 (v2)" —
  https://docs.google.com/spreadsheets/d/1vKsff9V6dDoCYUIEgkYed76DDUX2OShEt8OX8Cx8AfE/edit
  (compartido con arivas@visualtrans.com como writer).
- **Correo de reenvío enviado** a arivas@visualtrans.com, asunto "Calendario
  LinkedIn octubre 2026 (v2, corregido) — pendiente de validación" (id de mensaje
  `1a0c9fbacafcc62e`).
- **Resultado de la validación del usuario (v2):** **APROBADO.** El usuario confirmó
  en la conversación ("Ok, redacta") tras revisar el Google Sheets v2. El pipeline
  continúa con la Fase 3 (redacción por perfil).

## Redacción por perfil

**Visual Trans (empresa)** (18 posts):
- No había nombres reales de clientes ni citas textuales disponibles para los posts
  de evento (FETEIA 01/10 y 29/10, Conxemar 06/10 y 08/10); para no fabricar
  testimonios, se usó el patrón de apertura situacional en primera persona del
  plural y un cierre de invitación al stand, en vez del cierre de agradecimiento con
  nombre propio.
- En el post del 13/10 (ICS2) se evitó afirmar una fecha exacta de la próxima fase
  por no estar verificada; se usó el patrón de pregunta directa respondida en el
  cuerpo.
- Ajuste de cierre del 21/10 y recorte de un conector "Y" en el 27/10 para no
  repetir plantilla ni superar el máximo de usos por post que marca su voz.

**Emma González** (13 posts):
- Sin cifras exactas de adopción de eCMR/DeCA en las fuentes (08/10, 19/10, 20/10,
  27/10); se usaron descripciones cualitativas en vez de inventar cifras.
- En el post del 12/10 (Conxemar) no se inventaron nombres de visitantes; se usaron
  datos reales disponibles (Clúster da Función Loxística, stand 2A01).
- **Nota de nomenclatura de archivo:** el agente guardó el archivo como
  `Emma González.md` (con espacio y tilde), literal a la ruta indicada en el
  prompt, en vez de una convención normalizada tipo `emma-gonzalez.md`. Se ha
  mantenido así consistentemente para los 5 perfiles (mismo criterio en Visual
  Trans, Cecilio, Enrique y Laura), por lo que no hay inconsistencia entre
  archivos.

**Cecilio Labrada** (13 posts):
- Varios posts de Noticias etiquetados como "carrusel de datos"/"en cifras" (FETEIA,
  DeCA, Conxemar, IA, eCMR, resúmenes de mes) no tenían cifras concretas
  verificables en las fuentes internas; se optó por la estructura de "resumen
  ejecutivo por categorías" en vez de inventar números. En el post de IA (20/10) se
  hizo explícito que "todavía no existe una cifra fiable de adopción". El único
  número duro usado es "5 países más" de ICS2 (13/10), literal del calendario.
- El post del 09/10 (Conxemar en cifras) no aplicó el límite de palabras del "post
  de agradecimiento puro" porque el calendario lo asigna explícitamente como
  análisis en cifras, no como post relacional puro.

**Enrique Saa** (13 posts):
- El post del 12/10 es contenido nuevo por la reasignación del post de
  agradecimiento de Conxemar a Emma (corrección 4 del calendario v2); se mantuvo
  pilar Noticias, sin pain, publicado después de Visual Trans ese día.
- Ajuste del borrador del 02/10 para no superar el máximo de 3 emojis por post.
- No se inventaron cifras exactas de adopción/sanciones no respaldadas; se remitió
  esos datos al "primer comentario" en vez de afirmarlos en el cuerpo.

**Laura Díaz** (13 posts):
- Los temas del 20/10 y 22/10 pedían "la cifra que debería preocupar"/"la cifra de
  adopción que pocos comparten" sin que existiera una cifra verificada en las
  fuentes; se reformuló el ángulo hacia la idea de que esa cifra "no se publica",
  sin afirmar un dato falso.
- El post del 29/10 se resolvió con tres hechos verificables del briefing (1 mes, 3
  cambios normativos, 0 prórrogas) en vez de estadísticas externas.
- No se incluyeron hashtags en ningún post: no hay evidencia en Voz_Laura.txt de que
  los use habitualmente.

**Verificación transversal:** los 5 agentes confirmaron explícitamente que no se
usó ningún formato de vídeo, que los slots de Casos de éxito se dejaron sin
redactar ("CASO DE ÉXITO — pendiente Adrián") y que no se mezcló voz entre
perfiles.

## Validación final

**Resultado global definitivo: APTO CON CORRECCIONES MENORES.**

**Ronda 1** (`validacion.md`):
- Correcciones mecánicas aplicadas directamente por el validador: 13 campos
  `FORMATO` de cabecera de `Cecilio Labrada.md` no coincidían literalmente con
  `calendario.md` (corregidos); etiqueta del caso de éxito de Emma (13/10) no era
  la fija del sistema (corregida a "CASO DE ÉXITO — pendiente Adrián").
- **Incidencia crítica detectada** (no mecánica, requería reescritura): los posts
  de Visual Trans del 01/10 y 29/10 (FETEIA) mencionaban Madrid en vez de Tenerife
  e insinuaban presencia física no confirmada de Visual Trans en el congreso; el
  post del 29/10 tenía además una incoherencia temporal ("esta semana" para un
  congreso ya terminado el 04/10).
- Incidencias menores no bloqueantes (documentadas, no corregidas): varios posts
  de Visual Trans sin componente de evento por debajo del rango de 200-350
  palabras de su voz; el post de Cecilio del 09/10 supera el límite de 120 palabras
  para posts de agradecimiento/post-evento (con criterio de excepción documentado
  por el propio redactor); el post de Enrique del 02/10 ligeramente por debajo de
  su rango.

**Ronda de regeneración (única, dentro del límite de una ronda):** se invocó de
nuevo al `agente-redactor` de Visual Trans, exclusivamente para los 2 posts
afectados (01/10 y 29/10), corrigiendo la ciudad, eliminando la insinuación de
presencia física no confirmada y reformulando el del 29/10 como balance
retrospectivo. Ningún otro post del archivo se modificó.

**Ronda 2** (verificación): confirmado que ambos posts quedan corregidos, que
ningún otro post/fila de `Visual Trans.md` se alteró sin querer, y que el resto de
restricciones absolutas se mantiene (casos de éxito sin redactar 7/7, sin venta
directa, sin solapamiento de pains, sin formatos de vídeo, solo días laborables).

**Incidencias sin resolver:** ninguna crítica. Quedan documentadas, sin bloquear la
entrega, las incidencias menores de longitud ya citadas (Visual Trans en posts sin
evento, Cecilio 09/10, Enrique 02/10) — no requieren regeneración según el criterio
del validador.
