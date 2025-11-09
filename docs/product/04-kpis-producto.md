# LoL Roast Wrapped – KPIs de Producto

Este documento define las **métricas clave (KPIs)** que se usarán para evaluar si el producto está cumpliendo sus objetivos de:

- uso,
- engagement,
- viralidad,
- monetización,
- sostenibilidad de costes (especialmente IA).

No entra en detalles técnicos de implementación (trackers, herramientas), solo en **qué medir, cómo se calcula y para qué sirve**.

---

## 1. Objetivos generales de producto

Antes de hablar de números, recordemos qué queremos conseguir:

1. **Uso recurrente**  
   Que los jugadores vuelvan periódicamente a ver su roast (al menos una vez por mes/split/season).

2. **Engagement social**  
   Que los usuarios no solo consuman su Wrapped, sino que:
   - lo compartan,
   - creen Battles,
   - aparezcan en leaderboards.

3. **Crecimiento orgánico (viralidad)**  
   Que una parte significativa de nuevos usuarios llegue por:
   - enlaces compartidos,
   - Battles recibidas de amigos,
   - contenido de creadores.

4. **Monetización sostenible**  
   Cubrir (y ojalá superar) el coste de IA e infraestructura con:
   - publicidad,
   - afiliación,
   - modelos ligeros de “roasts extra” vía anuncios.

5. **Control de coste de IA**  
   Mantener un coste por usuario razonable sin sacrificar experiencia.

---

## 2. Métricas de uso básico

### 2.1. Usuarios activos

- **DAU (Daily Active Users)**  
  Número de usuarios únicos que generan o consultan al menos un Wrapped/Battle en un día.

- **WAU / MAU**  
  - WAU: usuarios activos únicos en la última semana.
  - MAU: usuarios activos únicos en el último mes.

> **Objetivo inicial:**  
> - Llegar a un MAU “sano” que justifique el proyecto: p.ej. 1.000–5.000 usuarios activos mensuales en la primera etapa.  
> - Ratio DAU/MAU razonable (≥ 15–20 %) indica cierta recurrencia.

### 2.2. Wrappeds y Battles generados

- **Wrapped Generated / día (WG)**  
  Número total de Wrappeds generados (incluyendo repeticiones del mismo usuario).

- **Battles Generated / día (BG)**  
  Número total de Battles 1v1 creadas.

- **Wrapped per User (WPU)**  
  \[
  \text{WPU} = \frac{\text{Wrappeds generados en un periodo}}{\text{Usuarios activos en ese periodo}}
  \]

> **Objetivo inicial:**  
> - WPU ≥ 1,2–1,5 en un mes sugiere que la gente repite el uso más de una vez.

---

## 3. Métricas de engagement

### 3.1. Profundidad de uso

- **Scroll completion rate (SCR)**  
  % de sessions de Wrapped en las que el usuario llega hasta la parte del roast principal.

- **Tiempo medio en página de Wrapped**  
  - Tiempo desde que cargan la página hasta que se van o cambian a otra sección interna.

> **Interpretación:**  
> - SCR bajo ⇒ probablemente el usuario no está leyendo el roast ni viendo los bloques clave.  
> - Tiempo muy corto ⇒ no encuentra valor; muy largo ⇒ puede haber fricción / carga lenta.

### 3.2. Interacción con features sociales

- **Battle Usage Rate (BUR)**  
  % de usuarios que, tras generar un Wrapped, inician al menos una Battle.

  \[
  \text{BUR} = \frac{\text{Usuarios que crean ≥1 Battle}}{\text{Usuarios que generan ≥1 Wrapped}}
  \]

- **Leaderboard View Rate (LVR)**  
  % de usuarios que visitan la sección de Leaderboards.

> **Objetivo inicial:**  
> - BUR ≥ 10–20 % (que una parte significativa quiera compararse).  
> - LVR ≥ 20–30 % (que la gente tenga curiosidad por los rankings).

---

## 4. Métricas de viralidad

### 4.1. Compartición

- **Share Rate (SR)**  
  % de Wrappeds/Battles en los que el usuario realiza al menos una acción de compartir (click en botón de compartir, descarga de card, copiar enlace).

  \[
  \text{SR} = \frac{\text{Wrappeds/Battles con algún evento share}}{\text{Wrappeds/Battles generados}}
  \]

- **Cards Generated per Wrapped (CGW)**  
  Promedio de cards generadas por Wrapped.

> **Objetivo inicial:**  
> - SR ≥ 15–25 % sobre Wrappeds.  
> - Si SR es muy bajo, hay que revisar: valor del roast, visibilidad de los botones, atractivo visual.

### 4.2. Adquisición orgánica

- **Virality / K-factor aproximado (K)**  
  Es una versión simple:

  \[
  K \approx \frac{\text{Usuarios nuevos procedentes de enlaces compartidos}}{\text{Usuarios totales}} 
  \]

- **Referer Breakdown**  
  - % de sesiones que vienen de:
    - `discord`,
    - `twitter`,
    - `instagram`,
    - `twitch`,
    - etc. (usando UTMs).

> **Señal positiva:**  
> - Aumento progresivo del % de tráfico de enlaces compartidos.  
> - Identificación de canales fuertes (ej. Discord y Twitch suelen ser clave).

---

## 5. Métricas de monetización

### 5.1. Ingresos básicos

- **Ingresos totales por periodo (IT)**  
  Suma de:
  - ingresos publicidad display,
  - afiliaciones confirmadas.

- **Ingresos por 1.000 sesiones (RPM)**  

  \[
  \text{RPM} = \frac{\text{Ingresos en un periodo}}{\text{Sesiones en ese periodo}} \times 1000
  \]

- **Ingresos por 1.000 Wrappeds (RPW)**  

  \[
  \text{RPW} = \frac{\text{Ingresos en un periodo}}{\text{Wrappeds generados}} \times 1000
  \]

> **Uso:**  
> - RPM sirve para comparar con benchmarks de publicidad.  
> - RPW es útil para entender “cuánto genera cada Wrapped”, de cara a costes de IA.

### 5.2. Uso de modelos “roasts extra por anuncios”

(para cuando lo implementes, post–MVP)

- **Users Hit IA Limit (UHIL)**  
  Nº de usuarios que llegan al límite diario de roasts IA.

- **Ad Unlock Rate (AUR)**  
  % de usuarios que, al llegar al límite, eligen ver un anuncio para desbloquear roasts extra.

  \[
  \text{AUR} = \frac{\text{Usuarios que completan al menos 1 ad unlock}}{\text{Usuarios que alcanzan el límite IA}}
  \]

> **Interpretación:**  
> - UHIL alto + AUR alto ⇒ la gente quiere más roasts y acepta el intercambio.  
> - UHIL alto + AUR bajo ⇒ probablemente límite demasiado agresivo o UX de anuncios mala.

---

## 6. Métricas de coste y eficiencia (IA + infra)

### 6.1. Coste de IA

- **Tokens IA consumidos por día**  
  Dividido en:
  - prompts,
  - completions.

- **Coste IA total por periodo (C_IA)**

- **Coste IA por Wrapped (C_IA_W)**  

  \[
  \text{C\_IA\_W} = \frac{\text{Coste IA en un periodo}}{\text{Wrappeds generados con IA en ese periodo}}
  \]

- **Coste IA por usuario activo (C_IA_U)**  

  \[
  \text{C\_IA\_U} = \frac{\text{Coste IA en un periodo}}{\text{Usuarios activos en ese periodo}}
  \]

> **Objetivo inicial:**  
> - Mantener C_IA_W en un rango pequeño (céntimos) para que escale bien.  
> - Minimizarlo con:
>   - cache de roasts,
>   - plantillas para perfiles repetidos,
>   - límites diarios.

### 6.2. Eficiencia de cache y plantillas

- **Roast Cache Hit Rate (RCHR)**  

  \[
  \text{RCHR} = \frac{\text{Roasts servidos desde cache}}{\text{Total de roasts servidos}} \times 100
  \]

- **Template Fallback Rate (TFR)**  

  \[
  \text{TFR} = \frac{\text{Roasts servidos usando plantilla}}{\text{Total de roasts servidos}} \times 100
  \]

> **Equilibrio:**  
> - RCHR alto ⇒ bueno para costes y velocidad.  
> - TFR alto ⇒ señal de problemas con la IA (coste, disponibilidad) o límites excesivos.

### 6.3. Coste infra vs ingresos

- **Coste infra mensual (C_INFRA)**  
  Incluye:
  - hosting backend,
  - BD,
  - cache/colas,
  - almacenamiento, etc.

- **Margen bruto aproximado (MB)**  

  \[
  \text{MB} \approx \text{Ingresos} - (\text{C\_IA} + \text{C\_INFRA})
  \]

> **Objetivo mínimo:**  
> - MB ≥ 0 a medio plazo (el proyecto se paga solo).  
> - Idealmente, margen positivo para reinvertir en features o marketing.

---

## 7. Métricas de calidad de experiencia

### 7.1. Rendimiento percibido

(Estos KPIs se conectan con los NFR de rendimiento.)

- **Tiempo de generación del Wrapped (TGW)**  
  p95 desde click en “Generar” hasta mostrar datos + roast.

- **Tiempo de primera respuesta Riot (TTFR)**  
  p95 desde petición al backend hasta recibir datos de Riot (match history, etc.).

- **Tiempo de generación del roast IA (TGR)**  
  p95 desde que se lanza la llamada al proveedor hasta que llega la respuesta.

> Valores aspiracionales:
> - TGW p95 ≤ 3–5 s.
> - TGR p95 ≤ 3 s.

### 7.2. Errores percibidos por usuario

- **Error Rate (ER)**  
  % de intentos de generación de Wrapped/Battle que terminan en error visible (no cuenta fallback a plantillas como error si el usuario recibe un roast cualquiera).

- **Riot Failure Rate (RFR)**  
  % de llamadas a Riot que resultan en error no recuperable.

- **IA Failure Rate (IFR)**  
  % de intentos de generación IA que fallan incluso tras reintentos y acaban en plantilla.

> **Objetivo:**  
> - ER bajo (p.ej. < 2–3 %) para que el usuario no perciba el sistema como frágil.

---

## 8. Métricas cualitativas / percepción

Estas no se pueden medir solo con logs, pero es bueno contemplarlas:

- **NPS / eNPS muy simple**  
  Pregunta tipo:
  > “¿Recomendarías LoL Roast Wrapped a tus amigos?” (0–10)

- **Feedback libre en formularios o Discord**  
  - Comentarios sobre:
    - calidad del roast,
    - tono (demasiado suave / demasiado duro),
    - claridad de la UX,
    - molestias con anuncios o límites.

Estas métricas ayudan a entender **el por qué** detrás de los números.

---

## 9. Cómo usar estas métricas en la toma de decisiones

1. **Producto / UX**
   - SR, BUR, LVR → ¿la gente realmente usa las partes sociales?  
   - SCR, tiempo de página → ¿leen el roast o solo miran arriba?

2. **Crecimiento**
   - K, % tráfico de enlaces compartidos → ¿la viralidad está funcionando?  
   - Canales fuertes (Discord, Twitch, etc.) → ¿dónde reforzar esfuerzos?

3. **Costes**
   - C_IA_W, RCHR, TFR → ¿tenemos que ajustar:
     - prompts,
     - modelos de IA,
     - caching,
     - límites de uso?

4. **Monetización**
   - RPM, RPW, AUR →  
     - ¿los ads son suficientes?,
     - ¿los roasts extra via anuncios interesan?,
     - ¿hay que cambiar el límite diario?

5. **Roadmap**
   - Si viralidad alta pero monetización baja:
     - priorizar mejora de ads / afiliación.
   - Si monetización bien pero uso bajo:
     - priorizar mejoras de producto / UX.

---

Este documento sirve como referencia para:

- definir los eventos de analytics que se implementarán,
- priorizar qué métricas mirar en cada fase,
- tener una base sólida para ajustar el producto sin “disparar a ciegas”.
