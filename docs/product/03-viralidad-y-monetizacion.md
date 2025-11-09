# LoL Roast Wrapped – Viralidad y Monetización

Este documento define **cómo crece el producto (viralidad)** y **cómo genera ingresos (monetización)**, respetando siempre:

- La experiencia de usuario (diversión primero).
- Las políticas de Riot.
- El compromiso de mantener un **free tier completo**.

---

## 1. Objetivo del documento

- Alinear el diseño de producto con:
  - Crecimiento orgánico (qué hace que la gente lo use y lo comparta).
  - Generación de ingresos sin cargarse la experiencia.
- Servir como referencia para:
  - Decidir qué features de viralidad construir primero.
  - Implementar la monetización sin “parches” improvisados.

---

## 2. Estrategia de viralidad

### 2.1. Principios de viralidad

1. **Contenido primero, no “invita a tus amigos” vacío**  
   La viralidad debe venir de que el resultado (Wrapped/Battle/leaderboard) es tan gracioso o humillante que el usuario **quiere** enseñarlo, no porque le fuerces con pop-ups.

2. **Compartir siempre es ganar**  
   Cada vez que alguien comparte:
   - enseña el producto a otros jugadores,
   - alimenta el FOMO (“yo también quiero ver mi roast / mi Battle”).

3. **El flujo de compartir tiene que ser trivial**  
   - Botones claros y accesibles.
   - Links cortos.
   - Imágenes listas para historias/posts.

4. **Viralidad sana (no dark patterns)**  
   - No condicionar features básicas a “invita a X amigos”.
   - No usar spam ni automatizar publicaciones sin consentimiento.

---

### 2.2. Vectores principales de viralidad

#### 2.2.1. Wrapped individual compartible

Cada Wrapped debe ser, por diseño, algo que apetezca compartir:

- **Visual**:
  - Diseño tipo “card”/“poster” con:
    - nickname,
    - timeframe,
    - stats más locas,
    - campeón principal,
    - badge llamativa.
- **Texto**:
  - Extracto corto del roast:
    - 1–2 frases especialmente afiladas.
- **Branding**:
  - Logo/URL de LoL Roast Wrapped.
  - QR o enlace sencillo.

Objetivo: que un simple pantallazo / card sirva para:

- Memear en Discord.
- Subir a historias de Instagram.
- Compartir en X/Twitter.

#### 2.2.2. Battle 1v1 como “reto” social

Battle está diseñado como **mecánica de invitación**:

- Un usuario genera una Battle contra un amigo:
  - Se crea una URL única: `/b/{id}`.
  - Se genera una card 1v1 con ambos nicks y un “ganador moral”.
- El amigo entra a ver el resultado:
  - Ve su propio rendimiento comparado.
  - Tiene CTA directa para generar su propio Wrapped.

Esto crea un bucle:

1. A reta a B (Battle).
2. B entra a ver el Battle.
3. B genera su propio Wrapped.
4. B reta a C, etc.

Requisitos UX:

- Botón “Battle contra un amigo” muy visible en la página de Wrapped.
- Frase clara en la card:
  - “Escanea y genera tu propio roast” / “Haz tu versión”.

#### 2.2.3. Leaderboards como “wall of shame”

Los leaderboards no son un ranking serio; son un **muro de memes**:

- Categorías pensadas para reírse:
  - OTP degenerates,
  - Tilt legends,
  - Vision is optional,
  - ARAM enjoyers, etc.
- Cada vez que un jugador genera un Wrapped:
  - se evalúa si entra en algún leaderboard.
- Cada leaderboard:
  - permite compartir:
    - la tabla,
    - la posición individual del jugador.

Efecto viral:

- La gente quiere “ver dónde está” o “meter a un amigo en el muro de la vergüenza”.
- Los admins de comunidades pueden montar minieventos:
  - “Objetivo del mes: entrar en el top de OTP degenerates”.

#### 2.2.4. Creadores de contenido y streamers

El producto encaja muy bien con streamers:

- Pueden pedir a sus viewers que:
  - generen su Wrapped y se lo pasen,
  - generen Battles entre subs.
- Contenido para directo:
  - reaccionar a roasts,
  - comentar leaderboards del chat/Discord.

Para ellos, la viralidad se refuerza con:

- Una UX muy rápida:
  - no requiere login,
  - con 3 clicks tienen un roast de un viewer.
- Un mensaje claro:
  - “Enseña tu Riot ID en directo y mira cómo te humilla LoL Roast Wrapped.”

En fases posteriores se puede contemplar:

- Página “para creadores” explicando cómo usar la herramienta en stream.
- Parámetros UTM específicos para trackear qué tráfico viene de qué streamer.

#### 2.2.5. Temporadas y eventos

Momentos clave para empujar el uso:

- Fin de Season.
- Fin de split.
- Eventos especiales de Riot (Worlds, etc.)
- Fiestas / vacaciones (verano, Navidad).

Acciones de producto:

- Landing con countdown (“Fin de Season en X días, genera tu Roast de este año”).
- Variantes de cards con temas especiales (Worlds, navidad, etc.).

---

### 2.3. Palancas in–product para la viralidad

#### 2.3.1. CTAs de compartir siempre visibles

En la página de Wrapped:

- Botones:
  - “Compartir card”
  - “Compartir enlace”
  - “Battle contra un amigo”
- No esconderlos:
  - uno en mitad de la página (tras el roast),
  - uno al final del scroll.

En la página de Battle:

- Botones:
  - “Compartir esta Battle”
  - “Generar mi propio Wrapped”
  - “Volver a la landing”

#### 2.3.2. Links cortos y etiquetados

- URLs cortas y limpias:
  - `/w/{id}`,
  - `/b/{id}`,
  - `/lb/{categoria}`.
- Parametrización con UTMs:
  - `?utm_source=discord&utm_medium=share&utm_campaign=wrapped`
  - `?utm_source=streamerX&utm_medium=stream&utm_campaign=battle`

Esto permite medir qué canales funcionan mejor.

#### 2.3.3. Cards listas para redes

- Formatos mínimos:
  - 1080x1920 (story vertical).
  - 1080x1080 (post cuadrado).
- Estilos:
  - Texto grande,
  - poco texto,
  - stats clave,
  - fondo llamativo.

El objetivo es que el usuario no tenga que editar nada: solo descargar/subir.

---

## 3. Estrategia de monetización

### 3.1. Restricciones y principios

#### 3.1.1. Restricciones de Riot

- Debe existir siempre un **free tier completo**:
  - El usuario puede usar el producto sin pagar.
  - No se puede poner paywall sobre:
    - el acceso a sus propias stats,
    - el core del producto en sí (Wrapped + roast básico).
- Está prohibido:
  - vender datos de jugadores,
  - crear productos de apuestas/gambling basados en datos de Riot,
  - ofrecer ventaja competitiva in–game.

#### 3.1.2. Principios propios

1. **No paywall sobre el roast base**  
   El usuario siempre puede obtener un Wrapped con roast sin pagar dinero real.

2. **Monetización opcional y discreta**  
   - Ads y afiliación en posiciones que no bloqueen:
     - la generación del Wrapped,
     - la lectura del roast.

3. **Nada que se sienta “pay to win” ni “pay to humiliate”**  
   No se venderán:
   - roasts “más agresivos” de pago,
   - accesos a datos de otros jugadores restringidos.

4. **Respeto al tono del producto**  
   - Mensajes sobre ads, límites, etc. también con humor,
   - pero claros y transparentes (qué se consigue viendo un anuncio, etc.).

---

### 3.2. Modelo principal: publicidad y afiliación

#### 3.2.1. Display ads (banners, bloques)

Uso de anuncios gráficos/textuales en:

- Landing:
  - se puede incluir algún banner en el cuerpo (no encima del hero principal).
- Página de Wrapped:
  - entre secciones (ej. entre stats y roast),
  - al final de la página.
- Leaderboards:
  - bloque en lateral (desktop) o entre posiciones (mobile con cuidado).

Reglas UX:

- Nunca:
  - antes de mostrar el roast,
  - en un popup intrusivo que bloquee el contenido.
- Siempre:
  - etiquetados como “Publicidad”,
  - integrados visualmente.

#### 3.2.2. Afiliación (hardware, periféricos, etc.)

Tiene mucho sentido ofrecer **recomendaciones patrocinadas**:

- Sillas gaming, ratones, teclados, monitores.
- Packs de skins de LoL o tarjetas regalo (vía tiendas oficiales o generalistas).
- Productos “de meme” relacionados con la cultura gamer.

Integración:

- Bloques del tipo:
  - “Si vas a seguir int-eando, al menos hazlo con buena silla.”
  - Tarjetas con afiliados (Amazon, tiendas gaming).

Condiciones:

- No crear sensación de “pay to improve stats”.
- Presentarlo siempre como recomendaciones de consumo, no como “features de juego”.

---

### 3.3. Modelo secundario: roasts extra a cambio de ver anuncios

Este modelo se encarga de unir **control de coste de IA** con monetización.

Concepto:

- Cada usuario tiene un **límite diario de roasts IA** (p.ej. 5).
- Si llega al límite:
  - puede seguir generando Wrappeds “solo stats” gratis,
  - o ver anuncios para obtener **roasts extra**.

Flujo:

1. El usuario intenta generar un nuevo Wrapped/Battle y ha llegado al límite de IA.
2. Pantalla/modal:
   - “Has llegado al límite de roasts de hoy.”
   - Opciones:
     - “Generar solo stats (sin roast)”
     - “Ver un anuncio para +2 roasts extra”
3. Si el usuario ve el anuncio completo:
   - se le recargan 2 roasts IA.
4. Vuelve al flujo normal de generación.

Claves:

- Nunca se bloquea el acceso a las stats.
- El “pago” se hace viendo anuncios, no con dinero.
- Los roasts extra son un **beneficio opcional**, no una obligación.

---

### 3.4. Líneas futuras de monetización (no MVP)

Estas ideas **no entran en el MVP**, pero se documentan como posibles extensiones:

1. **Cosméticos de presentación**
   - Temas visuales alternativos para el Wrapped:
     - skins visuales,
     - estilos especiales de cards.
   - De pago único o desbloqueables.

2. **Formatos especiales de roast**
   - Roasts “narrativos” (tipo historia, carta, etc.).
   - Ediciones temáticas (ej. Worlds, abril, Halloween).
   - Siempre manteniendo un roast básico gratuito.

3. **Herramientas para creadores de contenido**
   - Paneles especiales para streamers:
     - modo “queue” de roasts de viewers.
   - Branding personalizado (logo del streamer), de pago.

Todas estas propuestas tendrían que revisarse cuidadosamente para cumplir con las políticas de Riot y mantener la filosofía de free tier completo.

---

## 4. Alineación entre viralidad y monetización

Puntos clave donde ambas se tocan:

1. **Más uso = más viralidad = más coste IA**  
   - Por eso:
     - caching,
     - límites diarios,
     - roasts de plantilla como fallback.

2. **Ads como “puente” entre coste y experiencia**  
   - En vez de cortar la IA cuando se supera el presupuesto:
     - se reduce la disponibilidad de roasts IA,
     - se ofrece ver anuncios para ampliarla.

3. **Nada de chantaje tipo “comparte para usar la IA”**  
   - Compartir debe ser una acción deseable por el contenido,
   - no un requisito para usar el producto.

---

## 5. Métricas de crecimiento y monetización

### 5.1. Métricas de viralidad

- **K–factor aproximado**:
  - nº de nuevos usuarios generados por cada usuario actual.
- % de Wrappeds con al menos un intento de compartir.
- Nº de Battles creadas por día.
- Tráfico de entrada por:
  - enlaces compartidos (Discord, X, etc.),
  - tráfico desde canales de streamers concretos (UTMs).

### 5.2. Métricas de monetización

- Ingresos por:
  - 1000 sesiones (RPM),
  - 1000 Wrappeds generados.
- Ratio de:
  - usuarios que llegan a límite IA,
  - usuarios que aceptan ver anuncios para +2 roasts.
- Coste medio de IA por:
  - Wrapped,
  - Battle.

### 5.3. Métricas de equilibrio coste/ingresos

- Coste IA mensual vs ingresos publicitarios/afiliados.
- % de roasts servidos desde cache vs nuevos.
- Evolución del coste IA / usuario activo mensual.

Estas métricas se utilizarán para ajustar:

- Límites diarios,
- recompensas por anuncios,
- agresividad en caching y plantillas.

---

## 6. Roadmap de viralidad y monetización

### 6.1. MVP

Incluye:

- Wrapped compartible:
  - buttons de compartir,
  - link corto.
- Battle 1v1:
  - generación y link compartible.
- Leaderboards básicos:
  - 1–2 categorías.
- Bloques de anuncios discretos (display/afiliados).
- Límite diario de roasts IA (hard limit) con:
  - opción de seguir generando solo stats.

### 6.2. Post–MVP

- Rewarded ads para +2 roasts IA/día.
- Share cards en formato story/cuadrado, generadas desde el backend.
- Leaderboards más completos y visuales.
- Página específica para creadores de contenido.

### 6.3. Fase 2

- Cosméticos visuales (temas, estilos de cards).
- Ediciones especiales de roasts por eventos.
- Herramientas avanzadas para streamers (modo “reaccionando a roasts de chat”).

---

Este documento debe guiar cualquier decisión relacionada con:

- dónde colocar botones de compartir,
- qué tipos de anuncios integrar,
- cuándo y cómo mostrar límites de IA,
- qué features de viralidad y monetización priorizar en el roadmap.
