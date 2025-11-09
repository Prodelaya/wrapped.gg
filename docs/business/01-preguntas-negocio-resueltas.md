# LoL Roast Wrapped – Preguntas de Negocio Resueltas

Este documento recoge las **decisiones clave de negocio** que afectan al diseño del producto y de la arquitectura, en formato de preguntas y respuestas.

La idea es tener un sitio único donde consultar “¿qué decidimos sobre X?” sin tener que rebuscar entre documentos de producto, técnico o brainstorming.

---

## P01 – ¿Habrá historial completo de Wrappeds del usuario?

**Pregunta**  
¿La aplicación mostrará un historial completo de todos los Wrappeds que ha generado un jugador a lo largo del tiempo (seasones, splits, etc.)?

**Decisión**  
- **MVP**:  
  - No habrá un “historial completo” sofisticado tipo “timeline personal”.
  - El sistema **puede** guardar Wrappeds en base de datos (para cache, leaderboards, métricas), pero la interfaz solo mostrará:
    - el Wrapped actual,
    - y, opcionalmente, los últimos X Wrappeds recientes (si se quiere añadir más adelante).
- **Fase futura**:  
  - Si se introduce login (idealmente con Riot RSO), se podrá ofrecer una vista de historial más completa.

**Motivación**  
- UX: evitar sobrecargar al usuario con pantallas extra en el MVP.
- Técnica: simplificar el modelo y la necesidad de filtros/consultas de histórico.
- Negocio: no hay una necesidad clara de que el usuario consulte Wrappeds de hace muchos meses para obtener valor inmediato.

---

## P02 – ¿Habrá cuentas de usuario y login?

**Pregunta**  
¿El usuario necesitará crear una cuenta o iniciar sesión para usar el producto?

**Decisión**  
- **MVP**:
  - No habrá sistema de cuentas propio (email/contraseña).
  - No habrá login obligatorio con Riot RSO.
  - El uso será **anónimo**: basta con introducir Riot ID + región + timeframe.
- **Futuro**:
  - Se deja la puerta abierta a integrar **login con Riot (RSO)** para:
    - reclamación de perfiles,
    - histórico personal,
    - opciones de privacidad más avanzadas.

**Motivación**  
- Reducir fricción: cuanto menos pasos para ver el roast, mejor.
- Reducir responsabilidad legal (gestión de cuentas, contraseñas, RGPD).
- Encaja con el objetivo de ser una herramienta de uso rápido y compartible.

---

## P03 – ¿Cómo se identifica y limita a un usuario si no hay login?

**Pregunta**  
Si no hay login, ¿cómo se aplican límites diarios de IA o se previene el abuso?

**Decisión**  
- Se usará una combinación de:
  - **IP**,
  - **huella de navegador (fingerprint ligero)**,
  - y **cookies/localStorage** para identificar sesiones.
- Se almacenará un registro de **uso diario** por identificador anónimo:
  - nº de roasts IA generados ese día,
  - si ha conseguido roasts extra viendo anuncios (cuando exista esa feature).
- No se asociará esta información a datos personales (PII).

**Motivación**  
- Necesidad de controlar el coste de IA sin obligar al usuario a registrarse.
- Mantener un nivel de privacidad razonable (identificación anónima).

---

## P04 – ¿Cuál es el límite diario de uso de IA por usuario?

**Pregunta**  
¿Cuántos roasts generados por IA puede obtener un usuario al día?

**Decisión (versión inicial)**  
- Límite gratuito orientativo:
  - **5 roasts IA/día** por identificador (IP/fingerprint).
- Por encima de ese límite:
  - El usuario puede seguir generando Wrappeds **solo con stats**, sin roast IA.
  - Opcionalmente, podrá desbloquear roasts extra viendo anuncios (feature post–MVP).

> Nota: las cifras exactas (5, 10, etc.) se podrán ajustar según métricas de uso y costes.

**Motivación**  
- Proteger el presupuesto de IA.
- Incentivar un uso recurrente diario sin permitir abuso masivo.
- Evitar que el servicio se corte por completo cuando se alcance el presupuesto mensual.

---

## P05 – ¿Se guardan todas las partidas del jugador o solo agregados?

**Pregunta**  
¿El sistema almacena cada partida individual del jugador o solo datos agregados (snapshots)?

**Decisión**  
- El sistema:
  - **No almacenará el histórico de todas las partidas individualmente** (no pretende ser un OP.GG 2).
  - Calculará un **StatsSnapshot** por jugador + timeframe:
    - partidas jugadas,
    - métricas agregadas (KDA medio, winrate, roles, champs, etc.),
    - indicadores de comportamiento (OTP, tilt, ARAM enjoyer, etc.).
- Los snapshots servirán para:
  - alimentar el Roast Engine,
  - generar leaderboards,
  - cachear resultados de Wrappeds.

**Motivación**  
- Reducir almacenamiento y complejidad de consultas.
- Mantener el foco en el valor transformativo (roast + wrapped), no en analítica granular.

---

## P06 – ¿Qué ocurre si un jugador tiene muy pocas partidas en el periodo?

**Pregunta**  
¿Cómo tratamos jugadores “inactivos” o con pocas partidas en el periodo seleccionado?

**Decisión**  
- Se definirá un **umbral mínimo de partidas** por timeframe (por ejemplo, 5 partidas para un mes; los valores exactos se ajustarán más adelante).
- Si el jugador no llega al umbral:
  - Se genera un **Wrapped simplificado**:
    - menos secciones,
    - métricas más generales.
  - El roast se orienta hacia:
    - “AFK / jugador casual / semi–retirado”
    - en vez de analizar en profundidad su rendimiento.
- Nunca se devuelve un error “no tienes suficientes datos”; siempre se devuelve **algo**.

**Motivación**  
- Evitar frustrar a jugadores casuales.
- Mantener el tono de humor (“no juegas casi, también podemos roastear eso”).

---

## P07 – ¿Puede el usuario “reclamar” su perfil o pedir que no se le liste?

**Pregunta**  
Si el sistema usa alias anónimos y leaderboards, ¿puede un jugador pedir que no se le muestre o reclamar su perfil?

**Decisión**  
- **MVP**:
  - Los leaderboards muestran alias **anonimizados** (p. ej. “Summoner***4829”).
  - No se expone un perfil público navegable desde la web (solo Wrappeds generados ad–hoc).
  - No se implementa todavía un flujo de “opt–out” fino a nivel de jugador.
- **Futuro con RSO / cuentas**:
  - Se podrá ofrecer un panel de privacidad donde:
    - el jugador elija si aparece o no en leaderboards,
    - pueda solicitar borrado de datos.

**Motivación**  
- MVP simple sin panel de usuario.
- Minimizar superficie de soporte al usuario (peticiones manuales).
- El uso de alias anónimos reduce el riesgo de exposición.

---

## P08 – ¿Qué rangos temporales oficiales soportará el producto?

**Pregunta**  
¿Qué periodos (timeframes) podrá elegir el usuario al generar un Wrapped?

**Decisión (MVP)**  
- Timeframes soportados:
  - Última semana (1W),
  - Últimas 2 semanas (2W),
  - Último mes (1M),
  - Últimos 2 meses (2M),
  - Split actual,
  - Season actual.
- Internamente, si un timeframe largo tiene muy pocas partidas, se aplica la lógica de jugador inactivo (ver P06).

**Motivación**  
- Cubrir:
  - uso frecuente (1–2 semanas),
  - recap mensuales,
  - momentos “grandes” (split/season).
- Evitar combinaciones arbitrarias que compliquen UX y lógica (fechas libres, etc.).

---

## P09 – ¿Cómo encaja el producto con las políticas de Riot?

**Pregunta**  
¿Hay algún conflicto con Riot a nivel de monetización, datos o tipo de producto?

**Decisión**  
- El producto se clasifica claramente en:
  - **Uso permitido** por Riot:
    - usa solo datos post–partida,
    - genera contenido transformativo (roast),
    - no ofrece ventaja competitiva in–game,
    - respeta free tier para todos los jugadores.
- Queda expresamente **prohibido** en el diseño:
  - crear ladder alternativo,
  - mostrar o inferir MMR/Elo alternativo,
  - usar datos para apuestas/gambling,
  - vender datos de jugadores.

**Motivación**  
- Evitar cualquier problema al solicitar clave de producción.
- Proteger el proyecto ante cambios de política de Riot.

---

## P10 – ¿Qué cosas hemos decidido explícitamente NO hacer (al menos en el MVP)?

**Pregunta**  
¿Qué ideas se descartan por ahora para mantener el alcance bajo control?

**Decisión (lista no exhaustiva)**  

1. No habrá:
   - sistema de login propio con email/contraseña,
   - perfil público navegable estilo “OP.GG 2.0”,
   - overlays en partida o herramientas en tiempo real,
   - recomendaciones de builds/estrategias optimizadoras.

2. No se harán:
   - rankings de “mejores jugadores” serios,
   - servicios de pago por mejorar stats,
   - funcionalidades que puedan interpretarse como coaching in–game de pago apoyado en datos de Riot.

3. No se harán (por políticas y ética):
   - apuestas basadas en rendimiento del jugador,
   - venta de datos de jugadores a terceros.

**Motivación**  
- Mantener el foco: humor, wrapped, roasts.
- Respetar los límites legales y de reputación.
- Evitar convertir el proyecto en una mezcla confusa de tracker + herramienta de apuestas + etc.

---

## P11 – ¿Qué papel tienen los creadores de contenido en la estrategia?

**Pregunta**  
¿Se piensa en streamers/creadores como usuarios clave?

**Decisión**  
- Sí, pero **sin features especiales en el MVP**.
- El producto está diseñado para:
  - ser fácil de usar en directo,
  - que los viewers generen su Wrapped y el streamer lo pueda mostrar.
- A nivel de producto:
  - se contemplan UTMs para atribuir tráfico a creadores,
  - se deja espacio futuro para una página “para streamers”.

**Motivación**  
- Aprovechar el potencial de difusión que tienen los creadores.
- No atascar el MVP en funcionalidades avanzadas para streamers.

---

## P12 – ¿Cuál es el objetivo principal: mejorar al jugador o entretenerle?

**Pregunta**  
¿El foco es enseñar al jugador a mejorar o hacerle reír?

**Decisión**  
- Objetivo principal: **entretenimiento + auto–conciencia gamer + contenido compartible**.
- Objetivo secundario:
  - cierta “conciencia” de sus hábitos de juego (OTP, tilt, ARAM), pero sin pretensión de ser coach.
- Todo el diseño (UX, IA, métricas) está alineado con esta prioridad.

**Motivación**  
- Diferenciarse de la mayoría de herramientas existentes.
- Ajustar expectativas: el usuario viene a que le roastéen, no a buscar builds.

---

Este documento se debe mantener actualizado cada vez que se tome una **decisión de negocio importante**.  
Si en otro documento aparece algo que contradice este, lo correcto es actualizar aquí primero.
