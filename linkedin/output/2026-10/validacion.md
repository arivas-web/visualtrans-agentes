# Validación — Octubre 2026

## Resultado global: APTO CON CORRECCIONES MENORES (ver actualización en "Ronda 2" al final del documento — incidencia crítica ya resuelta)

Ninguna de las cuatro restricciones que bloquean automáticamente el "APTO" (casos de
éxito redactados, lenguaje de venta directa, solapamiento de pains, publicación en
fin de semana) se ha incumplido. Se han aplicado varias correcciones mecánicas y se
reporta una incidencia de contenido (factual, sobre Visual Trans y FETEIA) que por su
gravedad se marca como CRÍTICA y que el orquestador debería resolver — idealmente con
una regeneración puntual de 2 posts de Visual Trans — antes de la publicación, aunque
no invalida el resto del calendario ni de los 68 posts restantes.

## Correcciones aplicadas automáticamente

- `output/2026-10/posts/Cecilio Labrada.md` — el campo `FORMATO` de las 13 entradas
  no coincidía literalmente con `calendario.md` (el redactor había normalizado
  "carrusel de datos" → "multiimagen" e "infografía"/"imagen + texto corto" →
  "imagen"). Se ha corregido el campo `FORMATO` de las 13 entradas para que cite
  exactamente el texto de `calendario.md` (01/10, 06/10, 07/10, 09/10, 13/10, 14/10,
  16/10, 20/10, 21/10, 23/10, 27/10, 28/10, 30/10). No se ha tocado el cuerpo de
  ningún post, solo la cabecera de entrega.
- `output/2026-10/posts/Emma González.md` — el campo `TEMA` del post del 13/10
  (Casos de éxito) decía "Caso de éxito pendiente (contexto Conxemar)" en vez de
  citar literalmente la etiqueta fija del sistema. Se ha corregido a "CASO DE ÉXITO
  — pendiente Adrián", igual que en `calendario.md` y en el resto de perfiles. El
  cuerpo del post ya era correcto (solo contenía la etiqueta pendiente).

## Incidencias que requieren decisión del orquestador

- **[CRÍTICA]** `posts/Visual Trans.md`, perfil Visual Trans, fechas 01/10 y 29/10 —
  contenido factualmente incorrecto y contradictorio con las propias fuentes del
  pipeline sobre FETEIA. `briefing.md` y `log-decisiones.md` dejan explícito que (a)
  el XIV Congreso FETEIA-OLTRA se celebra en **Tenerife**, del 01 al 04/10, y (b) que
  "la entrada de origen no confirma participación directa de Visual Trans en el
  congreso... se sugiere tratarlo como ángulo de autoridad/opinión sectorial más que
  como 'os esperamos en nuestro stand'" (briefing.md, sección Ferias y eventos) — por
  eso FETEIA se asignó a Emma y Cecilio, no a Visual Trans, y la incorporación de VT a
  esa cobertura en la ronda 2 del calendario debía limitarse a "seguir" el evento, no
  a anunciar presencia física. Pese a ello:
  - El post del 01/10 dice "Si estáis por **Madrid** estas jornadas, nos encontraréis
    por allí. Nos vemos por los pasillos." — ciudad incorrecta (es Tenerife, no
    Madrid; los posts de Emma y Cecilio del mismo día sí dicen correctamente
    "Tenerife") y, además, da a entender presencia física de Visual Trans en el
    evento pese a que esa participación no está confirmada en ninguna fuente del
    pipeline.
  - El post del 29/10 dice "Esta semana, en los pasillos de FETEIA, una palabra se
    repitió más que ninguna: relevo generacional." — el congreso terminó el 04/10;
    tres semanas y media después no puede estar ocurriendo "esta semana" ni Visual
    Trans puede estar "en los pasillos" de un evento ya cerrado. Es una
    incoherencia temporal objetiva, no una cuestión de estilo.
  - Recomendación: regenerar el cuerpo de estos 2 posts (no el resto del calendario)
    corrigiendo la ciudad y eliminando cualquier lenguaje que implique presencia
    física en directo; el 29/10 debería formularse como balance retrospectivo ("hace
    unas semanas, en FETEIA...") y no como crónica en tiempo real. No se ha corregido
    aquí porque implica reescribir contenido creativo, fuera del mandato de
    corrección mecánica del validador.

- **[MENOR]** `posts/Visual Trans.md`, varios posts de pilar Noticias/Pains sin
  componente de evento (p. ej. 02/10 Pain #16 ≈95 palabras, 08/10 Pain #9 ≈106
  palabras, 12/10 Noticias/infografía comparativa ≈93 palabras, 05/10 Noticias/DeCA
  ≈98 palabras, 27/10 y 29/10 "texto largo/opinión" ≈135-165 palabras) — quedan
  sistemáticamente por debajo del rango de 200-350 palabras que `Voz_VT.txt`
  documenta para "posts de producto o normativa" (sección 1, "Longitud"), acercándose
  más al rango de 60-120 palabras reservado a posts de evento/congreso. No es un
  patrón puntual sino repetido en buena parte de los posts no-evento del perfil.
  Recomendación: revisar con `agente-redactor` si se amplía el desarrollo de estos
  posts al rango documentado, o si se documenta formalmente una nueva franja de
  longitud más corta para pains/noticias breves de VT (para no dejar la regla de
  longitud desactualizada respecto al uso real).

- **[MENOR]** `posts/Cecilio Labrada.md`, fecha 09/10 ("Conxemar en cifras") —
  ~152 palabras y cierra con "Gracias a todos los que os acercasteis al stand estos
  días", un cierre de agradecimiento post-evento. `Voz_Ceci.txt` (regla 12) fija un
  máximo de 120 palabras para "el post de agradecimiento o post-evento". El propio
  redactor documentó en su nota de log que decidió no aplicar ese límite por
  considerar el post "de análisis en cifras" y no un agradecimiento puro; dado que sí
  incluye un cierre de agradecimiento explícito, se traslada la decisión al
  orquestador para confirmar si el criterio de excepción es aceptable o si conviene
  recortarlo.

- **[MENOR]** `posts/Enrique Saa.md`, fecha 02/10 — ≈135 palabras, ligeramente por
  debajo del rango de 150-350 palabras que documenta `Voz_Enrique.txt` para sus
  posts propios recientes. Diferencia pequeña (15 palabras), no se considera
  bloqueante pero se deja anotada para el cómputo agregado de longitud.

## Checklist de restricciones absolutas

- [x] Casos de éxito nunca redactados — verificado en los 7 slots (VT 07/10 y
  22/10; Emma 13/10; Cecilio 14/10; Laura 15/10; Enrique 21/10 y 28/10): todos
  contienen únicamente "CASO DE ÉXITO — pendiente Adrián", sin cuerpo de post.
- [~] Voz respetada en los 5 perfiles — cumplida en general (aperturas, cierres,
  formato visual, léxico y "lo que nunca haría" de cada `Voz_*.txt` se respetan en
  63 de 63 posts con contenido), con la salvedad de la incidencia crítica de
  contenido factual/tono en Visual Trans (FETEIA, 01/10 y 29/10) descrita arriba.
- [x] Solo días laborables — las 70 filas de `calendario.md` caen entre lunes y
  viernes; los fines de semana de octubre 2026 (03-04, 10-11, 17-18, 24-25, 31) no
  tienen ninguna entrada, verificado por cálculo independiente del día de la semana.
- [x] No-solapamiento de pains — verificado pain por pain (recuento de
  `calendario.md` recalculado de forma independiente y contrastado contra el campo
  `PAIN #` de los 5 archivos de posts): ningún pain se repite el mismo día en dos
  perfiles distintos, ninguno se repite en días consecutivos del mismo perfil, y
  ninguno supera 2 apariciones en el mes.
- [x] Sin lenguaje de venta directa — búsqueda de "contrata", "descuento", "compra
  ahora" y variantes en los 5 archivos de posts: sin resultados.
- [~] Longitud dentro de rango por perfil — cumplida en Emma, Cecilio (salvo la nota
  del 09/10) y Laura; casi cumplida en Enrique (una entrada 15 palabras por debajo
  de rango); sistemáticamente por debajo de rango en varios posts de Visual Trans
  (ver incidencias MENORES arriba).
- [x] Cierres obligatorios respetados — Enrique cierra los 11 posts con contenido
  siempre con CTA al primer comentario y el emoji 👇, nunca con pregunta abierta;
  Visual Trans no tiene posts de cliente este mes (sin caso de éxito confirmado), por
  lo que la fórmula fija de agradecimiento con nombre propio no aplica; el resto de
  perfiles cierra según los patrones de pregunta/remate documentados en su voz.
- [x] Hashtags correctos — no aparece ningún hashtag en el cuerpo de ningún post de
  los 5 perfiles (verificado por búsqueda). Laura, la única con hashtag ocasional
  documentado en su voz, optó por omitirlos este mes por falta de un tag verificado
  como habitual; es una decisión razonable, no una infracción.
- [x] Formato de entrega correcto en todos los posts — los 5 archivos usan la
  estructura `PERFIL / FECHA / PILAR / PAIN # / TEMA / FORMATO` de forma uniforme.
  Se corrigieron 13 campos `FORMATO` de Cecilio Labrada y 1 campo `TEMA` de Emma
  González (ver "Correcciones aplicadas automáticamente") para que coincidan
  literalmente con `calendario.md`.
- [x] Ningún formato de vídeo — confirmado por búsqueda de "vídeo"/"video" en los 5
  archivos de posts y en `calendario.md`: no aparece ningún formato de vídeo en
  ninguna cabecera ni en el cuerpo de ningún post; los únicos resultados son las
  notas de log de los propios agentes confirmando la eliminación.

---

## Ronda 2 — Verificación de la regeneración de Visual Trans (01/10 y 29/10)

Se ha revisado `posts/Visual Trans.md` completo tras la regeneración de los 2 posts
señalados como incidencia CRÍTICA en la Ronda 1, y se ha repetido una comprobación
rápida de conjunto sobre el resto de restricciones absolutas.

**1. Post del 01/10 — ciudad y presencia física.** Reescrito. El nuevo texto ("Hoy
arranca el XIV Congreso FETEIA-OLTRA 2026... Seguiremos de cerca lo que se hable
estos días") no menciona Madrid, Tenerife ni ninguna otra ciudad, y no contiene
ninguna fórmula que insinúe presencia física de Visual Trans en el evento (se ha
eliminado "si estáis por Madrid... nos encontraréis por allí"). El post queda
planteado como seguimiento editorial a distancia, en línea con lo que `briefing.md`
recomienda para este perfil ("tratarlo como ángulo de autoridad/opinión sectorial,
no como asistencia física no confirmada"). **Confirmado, incidencia resuelta.**

**2. Post del 29/10 — incoherencia temporal.** Reescrito. El nuevo texto abre con "A
principios de mes, en el Congreso FETEIA-OLTRA 2026..." y continúa "varias semanas
después la conversación sigue tan vigente como entonces", formulado explícitamente
como balance retrospectivo. No queda ninguna referencia en presente/directo ("esta
semana", "en los pasillos ahora") que sugiera crónica en vivo de un evento cerrado el
04/10. **Confirmado, incidencia resuelta.**

**3. Resto del archivo sin alteraciones no deseadas.** Se ha releído `posts/Visual
Trans.md` completo (18 entradas: 01, 02, 05, 06, 07, 08, 12, 13, 14, 15, 19, 20, 21,
22, 26, 27, 28, 29 de octubre) y se ha contrastado cabecera por cabecera contra las
18 filas de Visual Trans en `calendario.md`: mismas fechas, mismos pilares, mismos
pain#, mismos formatos (incluido el cambio de FORMATO del 29/10 a "texto largo",
que ahora sí coincide literalmente con `calendario.md`, corrigiendo de paso una
discrepancia menor que en la Ronda 1 no se había señalado por no ser entonces el
foco). Los dos slots de "Casos de éxito" (07/10 y 22/10) siguen conteniendo
únicamente la etiqueta "CASO DE ÉXITO — pendiente Adrián". El resto de los 16 posts
con contenido conserva el texto ya validado en la Ronda 1, sin cambios de fondo.
**Confirmado: no se ha alterado ningún otro post ni fila del archivo.**

**4. Comprobación rápida de conjunto sobre las restricciones absolutas (5 perfiles):**
- Casos de éxito sin redactar: los 7 slots del mes (VT 07/10 y 22/10; Emma 13/10;
  Cecilio 14/10; Laura 15/10; Enrique 21/10 y 28/10) contienen únicamente la etiqueta
  "CASO DE ÉXITO — pendiente Adrián", sin cuerpo de post. Sin cambios respecto a la
  Ronda 1.
- Lenguaje de venta directa: búsqueda de "contrata", "descuento", "compra ahora" (y
  variantes) en los 5 archivos de posts — sin resultados.
- Solapamiento de pains: los posts del 01/10 y 29/10 regenerados son de Pilar
  Noticias, sin `PAIN #` asignado (—), por lo que la regeneración no introduce ningún
  riesgo nuevo de solapamiento; el resto del cómputo de pains no se ha visto alterado
  al no haberse tocado ningún otro post.
- Sin formato de vídeo: búsqueda de "vídeo"/"video" en los 5 archivos de posts — solo
  aparecen en notas de log (confirmando la ausencia de vídeo) y en la palabra
  "videollamada" del post de Laura (concepto distinto a un formato de entrega en
  vídeo); ningún post usa formato de vídeo.
- Solo días laborables: 01/10 es jueves y 29/10 es jueves, ambos confirmados como
  laborables en `calendario.md`; no cambia el resultado ya verificado en la Ronda 1
  de que las 70 filas del mes caen entre lunes y viernes.

### Resultado global final: APTO CON CORRECCIONES MENORES

La incidencia CRÍTICA de la Ronda 1 (contenido factualmente incorrecto y
contradictorio sobre FETEIA en `posts/Visual Trans.md`, 01/10 y 29/10) queda
**resuelta** tras la regeneración: no quedan incidencias críticas ni bloqueantes
abiertas. Se mantienen documentadas, sin bloquear el resultado, las incidencias
MENORES ya trasladadas al log de decisiones en la Ronda 1 (longitud por debajo de
rango en varios posts de Visual Trans, en el post del 09/10 de Cecilio Labrada y en
el post del 02/10 de Enrique Saa). El calendario y los posts del mes quedan listos
para publicación.
