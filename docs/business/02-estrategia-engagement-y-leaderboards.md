# LoL Roast Wrapped – Estrategia de Engagement y Leaderboards

Este documento profundiza en:

- Cómo se busca **engagement recurrente** (que la gente vuelva y juegue con la herramienta).
- Cómo se diseñan los **leaderboards** y su relación con:
  - la experiencia,
  - los límites diarios,
  - la ubicación de anuncios.

---

## 1. Objetivos de engagement

1. **Repetición de uso**  
   Que los jugadores no usen LoL Roast Wrapped solo una vez, sino:
   - al finalizar semanas/meses,
   - al cerrar un split/season,
   - cuando quieren trolear a amigos.

2. **Uso social**  
   Que la experiencia no se limite al jugador consigo mismo:
   - Battles 1v1,
   - compartir cards,
   - aparecer en leaderboards.

3. **Engagement “ligero” pero frecuente**  
   No se pretende que el usuario pase horas dentro de la web; se busca:
   - visitas cortas pero frecuentes,
   - generación de contenido que después vive en otras plataformas.

---

## 2. Bucles de engagement (engagement loops)

### 2.1. Loop 1 – “Me roasteo a mí mismo”

1. El usuario genera su Wrapped.
2. Ve stats + roast → se ríe / se reconoce.
3. Comparte el resultado (card / enlace).
4. Recibe comentarios de amigos (“wtf, qué malo eres”, “pásame el link”).
5. Vuelve en:
   - unas semanas,
   - al final del split/season,
   - o cuando siente que “ha tryhardeado mucho” y quiere ver si cambian los roasts.

**Palancas de diseño:**

- Recordatorios suaves en la landing tipo:
  - “¿Cuánto has troleado este mes? Genera tu Wrapped de las últimas 2 semanas.”
- Timeframes predeterminados que invitan a recaps frecuentes (1–2 semanas, 1 mes).

---

### 2.2. Loop 2 – “Battle con amigos”

1. Usuario A genera un Wrapped.
2. Ve el botón “Battle contra un amigo”.
3. Introduce el Riot ID de B → se genera una Battle 1v1.
4. A comparte el enlace de la Battle con B.
5. B entra:
   - ve el resultado,
   - genera su propio Wrapped.
6. B puede iniciar una nueva Battle contra C.
7. El ciclo continúa dentro de una comunidad (amigos, Discord, stream).

**Palancas de diseño:**

- Battle muy accesible desde el Wrapped (CTA claro).
- En la página de Battle:
  - CTA para que cada jugador genere su propio Wrapped.
  - Botones de compartir.

---

### 2.3. Loop 3 – “Wall of shame” (Leaderboards)

1. Cada vez que un usuario genera un Wrapped:
   - el sistema evalúa sus stats,
   - decide si entra en alguna categoría de leaderboard.
2. El usuario, en algún momento, visita la sección Leaderboards:
   - busca si está,
   - ve qué otras locuras han hecho otros.
3. Si aparece:
   - puede querer “subir” o “bajar” en ciertas categorías (OTP, tilt, etc.),
   - o compartir su posición.
4. La comunidad puede hacer minijuegos:
   - “A ver quién entra primero en top 10 OTP degenerates con X champ.”

**Palancas de diseño:**

- Leaderboards accesibles desde:
  - menú principal,
  - el propio Wrapped (“¿Quieres ver si tu desgracia tiene premio?”).
- Copy orientado a diversión, no a competitividad seria.

---

## 3. Diseño de leaderboards

### 3.1. Filosofía de los leaderboards

- No son un ranking oficial de habilidad.
- Son **rankings de comportamientos “memeables”**.
- No buscan premiar al “mejor jugador”, sino destacar:
  - al más OTP,
  - al más ARAM addict,
  - al más tilteado, etc.

### 3.2. Categorías iniciales (ejemplos)

Algunas categorías que encajan bien:

- **OTP Degenerates**
  - Criterio: % de partidas en el mismo campeón por encima de cierto umbral.
  - Métrica base: porcentaje de partidas con el champ principal.

- **Tilt Legends**
  - Criterio: patrones de rachas largas de derrotas, KDA muy bajo en muchas partidas, etc.
  - Métrica base: una combinación de rachas y stats.

- **Vision is Optional**
  - Criterio: número muy bajo de wards colocados / visión comparada con media estimada (si se puede inferir).
  - Métrica base: wards por minuto o similar.

- **ARAM Enjoyers / Refugees**
  - Criterio: % muy alto de partidas en ARAM vs ranked.
  - Métrica base: % de partidas ARAM.

- **Farm Simulator Enjoyers**
  - Criterio: CS alto pero poca conversión en victorias, etc.
  - Métrica base: CS/min elevado con winrate bajo.

> Importante: los detalles exactos de cada fórmula se pueden ajustar; lo relevante aquí es la **intención** de cada leaderboard.

### 3.3. Estructura de cada leaderboard

Cada leaderboard:

- Se define por:
  - nombre,
  - descripción humorística,
  - métrica de ranking,
  - umbrales mínimos (p.ej. número mínimo de partidas para ser elegible).
- Muestra:
  - posición,
  - alias público,
  - valor de la métrica,
  - algún dato decorativo (champ principal, región, icono).

UX:

- Alias:
  - nunca mostrar el Riot ID completo por defecto.
  - formato “Summoner***1234” o similar.
- Opcionalmente, en futuro con login:
  - el usuario podría ver qué alias le corresponde desde su panel.

---

## 4. Límites diarios y su impacto en el engagement

### 4.1. Rol de los límites

Los límites de roasts IA no solo protegen costes; también:

- introducen una **sensación de recurso valioso** (“mis roasts diarios”),
- fomentan una rutina (“entro cada día a ver qué tal mi desgracia”),
- evitan que unos pocos usuarios abusen del sistema.

### 4.2. Comportamiento esperado del usuario

Con un límite tipo: 5 roasts IA/día:

- Usuarios curiosos:
  - usarán 1–2 roasts para sí mismos,
  - 1–2 para Battle con amigos,
  - quizá alguno para experimentar con periodos distintos.
- Usuarios intensos:
  - llegarán al límite más a menudo,
  - pueden aceptar ver anuncios (cuando se implemente) para conseguir roasts extra.

### 4.3. Mensajería y UX en los límites

- Al acercarse al límite (por ejemplo al 80 %):
  - se puede mostrar un mensaje suave:
    - “Te queda 1 roast IA hoy. Úsalo con sabiduría (o no).”
- Al llegar al límite:
  - no se bloquea el uso por completo:
    - se ofrece seguir generando solo stats,
    - se sugiere volver mañana,
    - y, en futuro, ver anuncios para obtener más roasts.

---

## 5. Ubicación de anuncios y relación con la experiencia

### 5.1. Principios de colocación

1. **Nunca antes de ver el contenido principal**  
   - El usuario debe ver su Wrapped y su roast sin obstáculos.
2. **Anuncios integrados, no popups agresivos**  
   - Preferencia por:
     - bloques dentro de la página,
     - banners ligeros,
     - recomendaciones afiliadas.

3. **Claridad y honestidad**  
   - Siempre etiquetar “Publicidad”, “Sponsor”, etc.
   - No camuflar anuncios como contenido nativo del producto sin indicarlo.

### 5.2. Posiciones recomendadas

**Landing**

- Bloque de publicidad:
  - por debajo de la sección principal,
  - integrado en el diseño.

**Página de Wrapped**

- Posibles ubicaciones:
  - entre secciones (por ejemplo entre “Campeones y roles” y “Rango y progreso”),
  - al final del scroll, debajo de la zona de compartir.
- Nunca:
  - sobre el hero,
  - entre el usuario y el roast principal (ni como muro de pago ni como interstitial full–screen).

**Leaderboards**

- En desktop:
  - columna lateral para publicidad.
- En mobile:
  - bloque de publicidad después de cierto número de posiciones (p.ej. tras el top 10).

### 5.3. Relación con los roasts extra vía anuncios

Cuando exista el mecanismo de “ver anuncio para +2 roasts IA”:

- Esa UI debe:
  - ser opcional,
  - explicar claramente:
    - qué se consigue,
    - qué se va a mostrar (un vídeo/banner),
    - cómo se protege la privacidad.
- Idealmente:
  - integrar con formatos tipo rewarded ads para tener mejor monetización sin necesidad de muchos banners invasivos.

---

## 6. Cómo encajan leaderboards, límites y anuncios en el largo plazo

### 6.1. Escenario ideal de uso

- Un usuario:
  - entra varias veces al mes para generar Wrappeds,
  - aparece en algún leaderboard (para bien o para mal),
  - comparte Wrappeds/Battles,
  - eventualmente ve algunos anuncios (display o rewarded),
  - sigue usando el producto porque le divierte, no porque “deba”.

### 6.2. Ajustes esperados según métricas

En función de las métricas (ver `docs/product/04-kpis-producto.md`):

- Si:
  - **SR (Share Rate)** es bajo → revisar visibilidad y calidad de cards y CTAs.
- Si:
  - **LVR (visitas a leaderboards)** es bajo → revisar accesos y copy.
- Si:
  - **UHIL (usuarios que llegan al límite IA)** es muy bajo → quizá el límite es demasiado alto, o el uso más bajo de lo esperado.
- Si:
  - **UHIL alto + AUR bajo (poca gente acepta ver ads)** → reconsiderar UX de anuncios, límites o valor percibido de los roasts extra.
- Si:
  - **Leaderboards están vacíos** → ajustar umbrales mínimos para entrar, o reconsiderar algunas categorías.

---

## 7. Resumen operativo

- Los **leaderboards** son una palanca de engagement y humor, no una métrica de habilidad.
- Los **límites diarios** protegen el coste de IA y crean un “ritual” de uso diario sin romper la experiencia.
- La **publicidad** debe estar:
  - presente pero no intrusiva,
  - siempre por detrás de la prioridad principal: ver tu roast y compartirlo.
- Los **creadores de contenido** con sus comunidades son actores clave en la difusión:
  - loops de Battle y leaderboards encajan muy bien con directos y Discord.

Este documento debe consultarse siempre que se plantee:

- añadir una nueva categoría de leaderboard,
- cambiar los límites diarios,
- introducir nuevas posiciones para anuncios,
- rediseñar flujos de Battle o compartir.
