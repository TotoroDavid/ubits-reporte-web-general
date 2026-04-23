---
type: report
area: website
tags: [relanzamiento, v2, diseno, ux, conversion, critica, 2026-abril]
captured_date: 2026-04-15
author: David Toro
audience: Juan (stakeholder), equipo diseno/Webflow
status: active
related:
  - 2026-04-15-v2-mirror-and-relaunch-plan.md
  - 2026-04-15-homepage-relaunch-design-evidence.md
  - 2026-04-15-brief-ejecutivo-juan.md
  - 2026-04-15-plan-tactico-relanzamiento.md
---

# Crítica de Diseño — v2.ubits.com Home Relanzamiento

> **Qué es este documento:** Lectura crítica del diseño del v2 (home relanzamiento) combinando las imágenes del [design evidence](2026-04-15-homepage-relaunch-design-evidence.md) + el HTML/CSS del [mirror local](2026-04-15-v2-mirror-and-relaunch-plan.md). Objetivo: identificar qué del diseño entrega conversión enterprise y qué necesita intervención antes del switch final.
>
> **Audiencia:** Juan y quien decida cambios de diseño antes del publish.

---

## TL;DR

- **Como objeto visual: 8/10.** Premium, moderno, diferenciado en EdTech LatAm.
- **Como máquina de conversión B2B enterprise: 6.3/10 promedio ponderado.**
- El footer email-only es la pieza más fuerte (triplicará captura TOFU).
- Faltan 4 secciones estructurales para cerrar deals >$50K ARR (cómo funciona, integraciones, seguridad, case study).
- Los testimoniales, métricas y copy de módulos son **placeholder-level**; si se publican tal cual, bajan credibilidad enterprise.

---

## 1. Fortalezas del diseño (lo que NO hay que tocar)

| # | Fortaleza | Por qué importa |
|---|-----------|-----------------|
| 1 | **Arquitectura de secciones estándar SaaS premium** (Hero → Social proof → Problem → Solution → Testimonials → Metrics → FAQ → CTA) | Es el layout que los buyers B2B ya saben leer. No les pide aprender nada nuevo |
| 2 | **Module selector interactivo** (5 tabs con chat UI embebido) | Convierte cards estáticas en exploración activa → más dwell time y señal de ecosistema vivo |
| 3 | **Video Serena embebido** | Producto se demuestra, no se describe. 10x más persuasivo que "impulsado por IA" escrito |
| 4 | **Colorflow background en CTA final** | Rompe patrón monocromático, visualmente memorable, incrementa tiempo de atención antes del abandono |
| 5 | **Footer con email-only capture (1 campo)** | Psicológicamente brillante. Ataca directo el 98.5% form abandonment del baseline |
| 6 | **Jerarquía tipográfica controlada** (Outfit display + Inter body, palabras clave en cyan) | Premium, diferenciable de competidores |
| 7 | **Paleta teal/cyan sobre blanco** | Se aleja de rojos/amarillos de academia tradicional; posiciona como enterprise SaaS |

**Lineamiento:** todo lo anterior es base del relanzamiento. **No tocar.**

---

## 2. Debilidades críticas (matadores silenciosos de conversión)

### 2.1. Hero con un solo CTA — se pierde el 60% MOFU

El botón `Solicita una demo hoy` asume visitante con decisión tomada. Pero el 70% del tráfico orgánico (4.87M impresiones/año) es **TOFU descubriendo UBITS por primera vez**.

**Falta botón secundario calibrado a intención media:**

| Botón | Intención | Destino |
|---|---|---|
| `Solicita una demo hoy` (primario, azul) | Alta, BOFU | Form corto 3 campos → calendario HubSpot |
| `Ver cuánto puedes ahorrar` (secundario, outline) | Media, MOFU | Calculadora ROI → chat Serena → form |

Sin el segundo CTA, pierdes al ~60% que investiga sin estar listo para hablar con sales.

### 2.2. Testimoniales rotos — y no es solo bug, es falta de carne

Evidencia del [markdown extraído del mirror](../reports/2026-04-15-v2-mirror-and-relaunch-plan.md):

- 3 testimoniales repiten el **mismo texto**: *"Es un gran aliado estratégico para nuestro proceso de reclutamiento y entrenamiento"* (Sebastian Correa, Luisa Vargas, Karla Gómez)
- Avatares duplicados (Karla Gómez usa el mismo `avatar-1.png` que Amanda Sarmiento)
- Sin resultado cuantificado

**Lo que debería ser un testimonial B2B enterprise que cierra ventas:**

> *"Con UBITS, Mercado Libre redujo su time-to-hire de 45 días a 18 días. Serena AI nos ahorra 200 horas/mes de screening manual."*
> **— Sebastian Correa, HR Lead, Mercado Libre** *(foto real, no avatar genérico)*

**Acción:** escribir 3-4 testimoniales reales con nombre + rol + empresa + **número de impacto** antes de publish.

### 2.3. Las 3 métricas son vanity, no impacto

| Métrica actual | Problema |
|---|---|
| `+1000 empresas` | Tamaño del cliente base — no dice qué logran |
| `+5 agentes IA` | Irrelevante para el buyer — un CMO no compra cantidad de agentes |
| `14.000 contenidos` | Posicionamiento **catálogo de cursos** — justo el que están abandonando con la narrativa V2 |

**Métricas que cierran deals enterprise:**

- `15M horas de aprendizaje entregadas en 2025`
- `3M candidatos procesados por Serena AI`
- `92% de clientes recontrata año 2`
- `40% reducción promedio en time-to-hire`
- `Tiempo promedio de implementación: 21 días`

Las actuales le hablan al jefe de producto. Las de impacto le hablan al que firma el cheque.

### 2.4. Los módulos no se diferencian — podrían ser Docebo

Copy actual del módulo Aprendizaje: *"Carga tus cursos o accede a nuestro catálogo global. Nuestro tutor de IA conversacional resuelve dudas al instante."*

Eso mismo lo dicen: **TalentLMS, Docebo, Moodle, Cornerstone, 360Learning**. El buyer que compara 3 proveedores no distingue a UBITS con esa descripción.

**Falta el "only we do this" por módulo.** Ejemplo reescrito:

> **Aprendizaje**
> A diferencia de los LMS tradicionales, UBITS conecta cada curso al mapa de competencias 9-box del módulo Desempeño. Sabes qué aprender es **relevante para la promoción de cada colaborador**, no solo "contenido disponible".

Ese nivel de especificidad es lo que diferencia premium de commodity.

### 2.5. FAQ no resuelve objeciones del buyer enterprise

Las 5 preguntas actuales son objeciones de **decisor intermedio**:

- *¿La licencia solo aplica si compro la suite completa?*
- *¿Es difícil implementar toda una plataforma nueva?*
- *¿UBITS reduce el tiempo operativo de mis colaboradores?*
- *¿Dónde puedo tener más info sobre las soluciones con AI?*
- *¿Reemplazará la IA el toque humano de mi equipo?*

**Las objeciones REALES que bloquean un deal enterprise:**

- ¿Cumplen SOC 2 Type II? ¿ISO 27001?
- ¿Compatibles con SSO (Okta, Azure AD, Google Workspace)?
- ¿Integran con Workday / SAP SuccessFactors / BambooHR?
- ¿Datos hosteados en LatAm o US? ¿Cumplen Habeas Data CO / LFPDPPP MX?
- ¿Pricing por usuario o flat rate? ¿Escala a 5,000 empleados?
- ¿Qué SLA tienen? ¿Downtime histórico?
- ¿Puedo exportar mis datos si decidimos salirnos?

Sin esas respuestas, el buyer enterprise pide RFP largo (3 meses) o se va al competidor.

### 2.6. Bugs de copy que bajan credibilidad

Identificados en el mirror:

- **Palabras pegadas (probable corrupción al exportar desde Figma):**
  - *"Lagestióndeltalentonodeberíasentirsecomoarmarunrompecabezasaciegas"*
  - *"Atraertalentotecuestameses.Capacitassinsabersihayimpactoreal"*
  - *"Evalúaseldesempeñousandohojasdecálculoobsoletas.Tuempresapierdesuventajacompetitiva.Nosotroslocambiamos"*

- **Nav con links `#` huecos:** `Por qué Ubits`, `Ubits AI`, `Iniciar sesión` no resuelven
- **Footer con links `#` huecos:** `Skilled`, `Blog`, `Sala de prensa`, `Contacto`, `Términos`, `Colombia/México/Chile/Perú`

**Riesgo:** si se publican tal cual, comunican "sitio sin QA" — letal para buyer enterprise que asocia calidad de sitio = calidad de producto.

---

## 3. Gaps estructurales (secciones que faltan)

| # | Sección faltante | Por qué importa | Dónde ponerla |
|---|---|---|---|
| 1 | **"Cómo funciona" en 3 pasos** | TOFU necesita entender la mecánica antes de agendar | Entre Problem statement y Module selector |
| 2 | **Logos de integraciones** (Workday, BambooHR, SAP SuccessFactors, Slack, Teams, Google Workspace) | Enterprise no compra sin integraciones claras | Después de "Empresas líderes ya optimizan" |
| 3 | **Badges de seguridad/compliance** (SOC 2, ISO 27001, Habeas Data CO, LFPDPPP MX) | Table stakes para cualquier deal enterprise LatAm | Barra delgada antes del CTA final |
| 4 | **Case study destacado** (video 90s + números reales de 1 cliente marquee) | La prueba social fuerte cierra deals | Después de Module selector |
| 5 | **Pricing indicator** (rango "desde $X/empleado/mes" o calculadora) | 60% del funnel B2B investiga sin hablar con sales | Cerca del hero o sección dedicada |
| 6 | **Segmentación por industria/tamaño** | CHRO retail y CHRO fintech tienen dolores distintos | CTAs secundarios: "UBITS para Retail / Fintech / Telcos" |

---

## 4. Scorecard por dimensión

| Dimensión | Score | Comentario |
|---|---:|---|
| Estética visual | 8/10 | Premium, moderno, diferenciado en EdTech LatAm |
| Jerarquía + UX de navegación | 7/10 | Clara, pero nav con links `#` muertos es amateur |
| Copy (calidad de palabra) | 5/10 | Bugs visibles + testimoniales duplicados + métricas vanity |
| Diferenciación competitiva | 4/10 | Los módulos podrían ser Docebo o Cornerstone |
| Conversión BOFU (deals enterprise) | 5/10 | Falta seguridad, integraciones, case studies, pricing signal |
| Conversión MOFU (research mode) | 3/10 | No hay segundo CTA, no hay calculadora, no hay "cómo funciona" |
| Conversión TOFU (captura pasiva) | 8/10 | Footer input-only es brillante — gran ganador |
| Accesibilidad + Performance | Pendiente | Requiere Lighthouse audit (fuentes externas + videos + colorflow iframe pesan) |

**Score global ponderado: 6.3/10 como sitio de producción enterprise.**

---

## 5. Las 3 intervenciones quirúrgicas antes del switch final

Sin cambiar el look & feel, solo agregando/corrigiendo:

### Intervención 1 — Arreglar lo que YA está (1 día)

- [ ] Fix bugs de copy ("Lagestióndeltalento…" y las otras 2 instancias)
- [ ] Escribir 3 testimoniales reales con foto + rol + empresa + número de impacto
- [ ] Reemplazar las 3 métricas vanity por 3 métricas de impacto
- [ ] Conectar nav `#` a páginas reales (o esconder items si no existen aún)
- [ ] Descargar avatares únicos (no repetir `avatar-1.png`)

### Intervención 2 — Agregar 3 secciones críticas (2-3 días)

- [ ] **"Cómo funciona"** — 3 steps con íconos, entre Problem y Modules
- [ ] **"Integraciones"** — strip de logos bajo Social proof (Workday, BambooHR, SAP, Slack, Teams, Google Workspace, Okta)
- [ ] **"Certificaciones & seguridad"** — barra delgada de badges antes del footer CTA (SOC 2, ISO 27001, Habeas Data, LFPDPPP)

### Intervención 3 — Segundo CTA en hero + Case study (1 día)

- [ ] Agregar botón secundario `Ver ROI para tu equipo` → Calculadora (skill `ubits-funnel`)
- [ ] Case study con video 90s de **1 cliente marquee** (ideal: Mercado Libre o Cencosud con número cuantificado)

**Total: 4-5 días de trabajo de diseño/copy** para pasar de 6.3/10 a 8.5/10 como máquina de conversión real.

---

## 6. Escenarios según autoridad de cambios

| Escenario | Aplicabilidad | Qué se hace | Resultado esperado |
|---|---|---|---|
| **A. Autoridad plena** (David + designer interno con horas) | Ideal | Las 3 intervenciones completas antes del switch | Home 8.5/10 al publicar |
| **B. Autoridad parcial** (hand-off cerrado con agencia, solo custom code Webflow) | Medio | Intervenciones 1 y 3 (copy fixes + segundo CTA vía custom code) | Home 7/10 al publicar |
| **C. "Ship lo que está, itera después"** (Juan presiona deadline) | Realista si el deadline es duro | Solo fix de bugs de copy + nav `#` → páginas reales + footer listener | Home 6.5/10 al publicar, iterar en mayo |

**Mi recomendación:** escenario A si hay designer disponible esta semana. Si no, B. C solo si Juan lo impone explícitamente y entendemos que iteración en mayo es obligatoria.

---

## 7. Qué necesito de ti para avanzar

1. **¿Quién tiene autoridad de modificar el diseño?** (David + designer / agencia externa / solo custom code Webflow)
2. **¿Cuál de los 3 escenarios (A/B/C) aplica?**
3. **¿Tenemos foto + rol + número de impacto de 3-4 clientes para testimoniales reales?** (Mercado Libre, Cencosud, Alsea, Totalplay son los mejores candidatos por tamaño)
4. **¿Hay case study en video ya producido de algún cliente?** (si no, capturar uno rápido vía Loom con HR Lead de Mercado Libre)

Con respuesta a estas 4 preguntas, ejecuto la propuesta de intervenciones en la semana.

---

## 8. Referencias

- **Plan maestro relanzamiento:** [2026-04-15-v2-mirror-and-relaunch-plan.md](2026-04-15-v2-mirror-and-relaunch-plan.md)
- **Design evidence (Antigravity):** [2026-04-15-homepage-relaunch-design-evidence.md](2026-04-15-homepage-relaunch-design-evidence.md)
- **Brief ejecutivo:** [2026-04-15-brief-ejecutivo-juan.md](2026-04-15-brief-ejecutivo-juan.md)
- **Plan táctico:** [2026-04-15-plan-tactico-relanzamiento.md](2026-04-15-plan-tactico-relanzamiento.md)
- **DataLayer spec:** [../docs/v2/datalayer-spec.json](../docs/v2/datalayer-spec.json)

---

*Última actualización: 2026-04-15 — David Toro*
