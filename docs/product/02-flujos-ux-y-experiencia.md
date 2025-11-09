# LoL Roast Wrapped – Flujos de UX y Experiencia de Usuario

Este documento describe **cómo usa el producto un jugador real**, qué pantallas ve, qué decisiones toma y qué estados especiales debe manejar la interfaz.

No es un documento técnico (no habla de endpoints ni modelos de datos), sino de **experiencia y recorrido del usuario**.

---

## 1. Mapa general de la experiencia

### 1.1. Páginas / vistas principales

A alto nivel, el producto tiene estas vistas:

1. **Landing principal**
2. **Pantalla de generación de Wrapped**
3. **Página de resultados de Wrapped (detalle)**
4. **Pantalla de Battle 1v1 (formulario)**
5. **Página de resultados de Battle 1v1**
6. **Sección de Leaderboards**
7. **Pantallas de compartir (share cards)**
8. **Estados especiales**:
   - límite de IA alcanzado,
   - pocos datos / jugador inactivo,
   - errores de Riot / IA,
   - mensajes legales y de confianza.

### 1.2. Tipos de entrada al producto

El usuario puede llegar por distintos “puntos de entrada”:

- **Tráfico directo / SEO / enlace compartido**
  - Llega a la **landing principal** `/`.
- **Enlace compartido de un amigo**
  - Llega directamente a:
    - un **Wrapped concreto** `/w/{id}`, o
    - un **Battle concreto** `/b/{id}`.
- **Desde redes / contenido de creadores**
  - Normalmente caerá en la landing, pero puede haber enlaces directos a:
    - página de Battle,
    - página de Leaderboards.

Cada entrada debe permitir que el usuario entienda **rápido**:

- qué hace la web,
- qué tiene que hacer para “sacar su roast”.

---

## 2. Flujo principal: generar un Wrapped personal

Este es el flujo **core** del producto y debe ser el más pulido.

### 2.1. Paso 1 – Landing

**Objetivo:** que el usuario entienda en segundos lo que ofrece la herramienta y quiera probar su primer roast.

Elementos clave de la landing:

- **Hero (zona superior):**
  - Título claro:  
    > “Tu *Spotify Wrapped* del LoL, pero en versión roast.”
  - Subtítulo corto explicando el concepto:
    > “Mete tu Riot ID, elige un periodo y deja que la IA se ría de tu forma de jugar.”
  - Formulario simple:
    - Campo de Riot ID (`gameName#tagline`).
    - Selector de región (ej. EUW, EUNE, NA…).
    - Selector de rango temporal (desplegable):
      - Última semana,
      - Últimas 2 semanas,
      - Último mes,
      - Últimos 2 meses,
      - Split actual,
      - Season actual.
    - Botón principal: **“Generar mi Roast Wrapped”**.

- **Ejemplos visuales (debajo de la hero):**
  - Capturas de un Wrapped ya generado.
  - Extracto de un roast gracioso (censurado si hace falta).
  - Una card de Battle 1v1.

- **Bloque de confianza:**
  - Mensaje tipo:
    - “Usamos las APIs oficiales de Riot, nunca tu contraseña.”
    - “No damos ventaja in–game, solo nos reímos de tus stats.”

- **CTA secundarios:**
  - Botón a **Leaderboards**.
  - Botón a **Battle 1v1**.

Acción esperada:  
el usuario rellena el formulario y hace clic en **“Generar mi Roast Wrapped”**.

---

### 2.2. Paso 2 – Estado de carga (“Generando tu Roast”)

Tras enviar el formulario, el usuario pasa a una vista de **loading con feedback**:

- Mensaje tipo:
  - “Pidiendo tus datos a Riot…”
  - “Contando cuántas horas has tirado en ARAM…”
  - “Preparando un roast a la altura de tus int’s…”

- Elementos de UX:
  - **Skeleton loading** para el layout de la página de Wrapped:
    - bloques borrosos donde aparecerán estadísticas,
    - espacio reservado donde aparecerá el roast.
  - Indicador de progreso *aproximado*:
    - 1/3 – “Obteniendo partidas de Riot”
    - 2/3 – “Calculando tus stats de desgracia”
    - 3/3 – “Generando tu roast con IA”

- Consideraciones:
  - Idealmente, tiempo de carga total (stats + IA) < 3–5 s.
  - Si se alarga, mostrar mensajes tipo “Esto está tardando más de la cuenta, culpa de los servidores…”.

---

### 2.3. Paso 3 – Página de Wrapped (resultado)

Esta es la vista principal de valor. Debe estar pensada para:

- **tener una narrativa clara al hacer scroll**, y  
- **ser capturable y compartible** con facilidad.

#### 2.3.1. Estructura general

Secciones recomendadas (de arriba a abajo):

1. **Hero del Wrapped**
2. **Tu vida en la Grieta en este periodo**
3. **Campeones y roles**
4. **Rango y progreso**
5. **Hábitos tóxicos / tendencias**
6. **Roast principal (texto IA)**
7. **Badges / logros graciosos**
8. **Acciones sociales: compartir y Battle 1v1**
9. **Bloques de anuncios / afiliación (no intrusivos)**

#### 2.3.2. 1. Hero del Wrapped

Elementos:

- Icono / avatar del jugador (dato de Riot).
- Nombre del jugador (gameName#tagline o versión anonimizada).
- Timeframe seleccionado.
- Región.
- Stats “de tarjeta de visita”:
  - nº de partidas en el periodo,
  - winrate global,
  - campeón más jugado,
  - rol más frecuente.

Objetivo: que con **un vistazo** se entienda quién es el jugador y qué se está analizando.

#### 2.3.3. 2. “Tu vida en la Grieta en este periodo”

Bloque con métricas de volumen y ritmo:

- Partidas por día / semana.
- Horas estimadas jugadas.
- Distribución por tipo de cola (ranked, flex, ARAM…).
- Rachas notables:
  - mayor racha de victorias,
  - mayor racha de derrotas (“tilt streak”).

Presentación sugerida:

- Gráficas muy simples (barras/pastel).
- Texto acompañante divertido:
  - “Has jugado como si esto fuera un trabajo a media jornada.”
  - “Ha habido semanas en las que tu vida era literalmente la Grieta.”

#### 2.3.4. 3. Campeones y roles

Aquí se resuelve el “¿qué juegas realmente?”:

- Campeón más jugado (“tu OTP”).
- Top 3 campeones con:
  - partidas,
  - winrate,
  - KDA promedio.
- Roles más frecuentes:
  - top, jungle, mid, ADC, support.

Extras:

- Detectar si el jugador es “OTP degenerado”:
  - >30% de partidas en un solo campeón.
- Detectar si rellena roles sin sentido (ej. muchos champs off–meta).

Presentación:

- Grid con tarjetas de campeón.
- Pequeños comentarios tipo:
  - “Has decidido que cambiar de champ es para cobardes.”
  - “Tu champion pool es un buffet libre, y tú te lo has comido todo.”

#### 2.3.5. 4. Rango y progreso

Sección dedicada a rankeds:

- Rango inicial del periodo.
- Rango máximo alcanzado.
- Rango final.
- Cambio neto de ligas/divisiones (subida, bajada, estancamiento).

Visual:

- Línea o escalera que muestra el progreso (o la caída).
- Etiquetas tipo:
  - “Te has quedado atascado en la misma división.”
  - “Has escalado, pero te has estampado al final.”

#### 2.3.6. 5. Hábitos tóxicos / tendencias

Sección más “memeable”:

- % de partidas con:
  - early surrender,
  - AFK (si se puede inferir por tiempo jugado),
  - mucha diferencia de muertes vs kills,
  - builds raras, etc. (en la medida posible).
- Datos tipo:
  - % de partidas ARAM vs ranked.
  - ¿Juegas más cuando vas en racha o cuando estás tilteado?

Pocas métricas, mucha interpretación en texto:

- “Has buscado refugio en ARAM cuando las rankeds te han partido la cara.”
- “Tus builds dicen ‘soy main YouTube guide, no meta’.”

#### 2.3.7. 6. Roast principal (texto IA)

Bloque central:

- Texto de 180–300 palabras.
- Tono:
  - sarcástico,
  - agresivo pero controlado,
  - con referencias directas a las stats mostradas arriba.
- Maquetación:
  - ancho de lectura cómodo, tamaño de fuente legible,
  - posible fondo sutil para diferenciarlo del resto.

Idealmente, este bloque se siente como la “voz de narrador” de todo el Wrapped.

#### 2.3.8. 7. Badges / logros graciosos

Pequeñas chapas/insignias que el jugador “gana” según sus stats:

- “OTP degenerado”
- “Tilt legend”
- “Vision is optional”
- “ARAM refugee”
- “Farm simulator enjoyer”

Cada badge:

- se activa por una condición simple de stats,
- se muestra con icono + título + frase corta.

Objetivo UX:

- dar pequeños momentos “gif–recortables”,
- motivar al usuario a mejorar su badge (o a empeorarlo, en broma).

#### 2.3.9. 8. Acciones sociales: compartir y Battle 1v1

La parte de **acción al final del scroll**:

- Botón para **generar card** (imagen) con:
  - stats clave,
  - campeón principal,
  - extracto del roast,
  - branding de la web.
- Botones para compartir:
  - “Compartir en Discord”
  - “Compartir en X/Twitter”
  - “Copiar enlace”
- Bloque “Battle contra un amigo”:
  - Campo para introducir Riot ID de tu amigo.
  - Botón “Compararme con este desgraciado” → lleva a flujo de Battle.

#### 2.3.10. 9. Bloques de anuncios / afiliación

Reglas básicas para UX:

- Nunca bloquear el acceso al roast.
- Ubicaciones recomendadas:
  - entre secciones (por ejemplo entre “Campeones y roles” y “Rango y progreso”),
  - al final de la página (debajo de las acciones sociales).
- Estilo:
  - integrados visualmente,
  - etiquetados claramente como “Publicidad” o “Sponsor”.

---

## 3. Flujo Battle 1v1 (comparar dos jugadores)

### 3.1. Paso 1 – Acceso al Battle

El usuario puede llegar:

- Desde la landing (botón “Battle 1v1”).
- Desde un Wrapped (botón “Compararme con un amigo”).

Ambos casos llevan a la misma vista:

- **Pantalla de Battle** con:

  - Campo “Tu Riot ID” (pre-rellenado si vienes de un Wrapped).
  - Campo “Riot ID del oponente”.
  - Selector de región (si no se deduce).
  - Selector de timeframe.
  - Botón “Iniciar Battle”.

### 3.2. Paso 2 – Loading de Battle

Similar a la carga del Wrapped, pero adaptado:

- Mensajes tipo:
  - “Comparando quién int-ea más fuerte…”
  - “Mirando quién se ha casado con un champion y quién con el elo hell…”

Skeleton:

- Dos columnas (Jugador A y Jugador B) vacías,
- espacio reservado para el roast comparativo.

### 3.3. Paso 3 – Página de resultados de Battle

Estructura:

1. **Header comparativo**
   - Avatar + nombre de A y B.
   - Timeframe.
   - Badge de “ganador moral” global (p.ej. quien tenga peor/“más memeable” resultado).

2. **Comparativa de stats clave (tabla o grid)**
   - Partidas jugadas.
   - Winrate.
   - KDA.
   - Campeón más jugado.
   - Horas jugadas.
   - Racha tilt más grande.

3. **Roast comparativo**
   - Texto de 120–220 palabras.
   - Narra la historia de la rivalidad:
     - quién “carrea la desgracia del dúo”,
     - quién no sale del elo hell,
     - quién vive en ARAM.

4. **Badges de Battle**
   - “Carrea la desgracia”
   - “Amigo carried”
   - “Ambos merecen ban de rankeds”

5. **Acciones sociales**
   - Generar card 1v1 para redes.
   - Botones de compartir.
   - CTA para que cada jugador genere su Wrapped individual.

---

## 4. Flujo de Leaderboards

### 4.1. Acceso

Desde:

- menú superior (“Leaderboards”),
- links al final del Wrapped (“Mira en qué ranking entras”).

### 4.2. Estructura de la vista

Elementos:

- Selector de:
  - **Categoría**:
    - OTP degenerates,
    - Tilt legends,
    - Vision is optional,
    - ARAM enjoyers,
    - etc.
  - **Timeframe**:
    - Última semana,
    - Último mes,
    - Split,
    - Season.

- Lista de ranking:
  - Posición (1, 2, 3…).
  - Alias público del jugador (no el Riot ID completo, por privacidad).
  - Métrica que define el ranking (ej. % de partidas con mismo champ).
  - Icono del campeón principal (si aplica).

### 4.3. Comportamiento UX

- En filas del ranking:
  - Opción de **ver el Wrapped** asociado (si el usuario pulsa y es público).
  - Tooltip explicando por qué ese jugador está ahí (“75% de tus partidas con Yasuo en ARAM”).

- Mensajes para listas vacías:
  - “Aún no hay suficiente gente haciendo el ridículo en esta categoría. Sé el primero.”

---

## 5. Flujos de compartir (share cards)

### 5.1. Desde Wrapped

Opciones:

- Botón “Generar card para stories”.
- Botón “Generar card cuadrada”.

Flujo UX:

1. El usuario pulsa un tipo de card.
2. Se muestra estado de “Generando imagen…”.
3. Se presenta una **previsualización** de la card:
   - Opción de descargar.
   - Opción de compartir (si el navegador lo soporta).

Contenido típico de la card:

- Nick + timeframe.
- Stats clave (3–4 máximo).
- Campeón principal o badge llamativo.
- Extracto corto del roast.
- Logo/URL del producto.

### 5.2. Desde Battle

Similar al Wrapped, pero:

- Se muestran ambas columnas con A y B.
- Se destaca el “ganador moral” en la card.
- Extracto de una frase del roast comparativo.

---

## 6. Estados especiales y vacíos

### 6.1. Pocos datos / jugador inactivo

Situación: el jugador ha jugado muy poco en el periodo (ej. 2–3 partidas).

UX esperada:

- Aún se genera un Wrapped, pero:
  - Se muestra un mensaje claro tipo:
    - “No has jugado casi nada en este periodo, así que el roast va a ser más por tu ausencia que por tus plays.”
  - La parte visual se reduce a:
    - nº de partidas,
    - campeones jugados,
    - quizá alguna mini–racha.

- El roast se orienta a “AFK / jugador semi–retirado” en vez de sacar conclusiones profundas.

### 6.2. Error de Riot API / rate limit

Situación: Riot responde con error, timeout, o rate limit.

UX:

- Mensaje de error contextual:
  - “Los servidores de Riot están de resaca, inténtalo de nuevo en unos minutos.”
- Si hay datos cacheados recientes:
  - Ofrecer usarlos:  
    “Podemos generar un roast con datos de hace X días.”

### 6.3. Error de IA

Situación: fallo al generar el roast (timeout, error del proveedor, coste excedido, etc.).

UX:

- El usuario **no se queda sin Wrapped**:
  - Se le muestra su panel de stats.
  - Se genera un roast de plantilla (menos personalizado, pero funcional).
- Mensaje sutil:
  - “La IA se ha quedado pensando demasiado, así que te traemos un roast de la casa.”

### 6.4. Límite diario de IA alcanzado

Situación: el usuario excede el límite de roasts IA gratuitos.

UX:

- Pop-up al intentar generar un nuevo Wrapped/Battle:
  - Indica:
    - cuántos roasts ha usado ya,
    - cuántos le quedan (0),
    - opciones:
      - seguir generando sólo stats,
      - ver anuncios (si está implementado) para conseguir roasts extra.

- Si elige “stats sólo”:
  - Flujo igual que CU-001 pero sin llamar a IA (solo panel visual).
  - La sección de roast puede mostrar:
    - un texto genérico o un mensaje invitando a volver otro día.

---

## 7. Diseño responsive y patrones de interacción

### 7.1. Mobile–first

La mayor parte del tráfico vendrá de móvil (links en redes, Discord, etc.), por lo tanto:

- Layout pensado primero para pantallas ~360–414 px de ancho.
- Scroll vertical claro:
  - hero → resumen → stats → roast → social.
- Botones grandes y bien espaciados.
- Textos cortos al inicio de cada sección para no saturar.

### 7.2. Desktop

En escritorio:

- Aprovechar el ancho para:
  - colocar ciertas secciones en 2 columnas (ej. métricas + descripción),
  - mostrar comparativas en Battle de forma más rica.
- Aun así, la maqueta debe seguir siendo “capturable” en una sola card si el usuario hace screenshot.

### 7.3. Lenguaje y tono de interfaz

- Botones y textos breves, con humor ligero pero claros:
  - “Generar mi Roast Wrapped”
  - “Compararme con un amigo”
  - “Ver mi desgracia”
- Mensajes de error siempre humanizados:
  - Nunca un simple “Error 500”.
  - Siempre algo en tono del producto + explicación útil.

---

## 8. Resumen de principios UX clave

1. **Entrada mínima**: un formulario simple en la landing (Riot ID + región + periodo).
2. **Tiempo hasta ver algo divertido**: objetivo < 1 minuto desde que aterriza en la web.
3. **Narrativa clara al hacer scroll**:
   - quién eres → cuánto juegas → qué juegas → cómo progresas → qué hábitos tienes → roast → compartir.
4. **No romper la experiencia por límites técnicos**:
   - si Riot o la IA fallan, el usuario sigue obteniendo algo.
5. **Todo empuja hacia compartir o hacer Battle**:
   - CTAs visibles al final del Wrapped y en puntos estratégicos.
6. **Respetar siempre las políticas y el espíritu de Riot**:
   - sin paywalls sobre datos,
   - sin ventaja competitiva,
   - sin MMR alternativo,
   - con mensajes claros de no–afiliación.

Este documento debe ser la referencia para cualquier decisión de **diseño de pantallas y flujos de interacción**.  
Los detalles técnicos (endpoints, modelos de datos, etc.) se definen en otros documentos de arquitectura y requisitos.
