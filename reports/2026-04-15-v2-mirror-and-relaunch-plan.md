---
type: report
area: website
tags: [relanzamiento, v2, mirror, webflow, datalayer, gtm, 2026-abril]
captured_date: 2026-04-15
author: David Toro
audience: Juan (stakeholder), equipo Webflow/HubSpot
status: active
related:
  - 2026-04-15-brief-ejecutivo-juan.md
  - 2026-04-15-plan-tactico-relanzamiento.md
  - 2026-04-15-INDEX-relanzamiento.md
  - 2026-04-15-homepage-relaunch-design-evidence.md
  - 2026-04-15-v2-design-critique.md
  - ../docs/v2/datalayer-spec.json
---

# v2.ubits.com — Mirror Local + Plan de Relanzamiento

> **Qué es este documento:** Spec operativo para convertir el código de `v2.ubits.com` (Netlify preview) en el nuevo sitio en Webflow, con tracking GA4/GTM funcional desde día uno. Incluye: método de mirror, análisis crítico del v2, tensiones con el plan táctico previo, plan de ataque de 15 días, y decisiones pendientes.
>
> **Deadline:** Fin de abril 2026.

---

## 1. Qué es el v2 y qué NO es

**v2.ubits.com** es un **spec ejecutable offline** — no el sitio a publicar tal cual. Fue construido como referencia visual y de código para reconstruir la nueva home en Webflow. Hosted en Netlify como preview.

**Cambio de premisa respecto al [plan táctico original](2026-04-15-plan-tactico-relanzamiento.md):** el relanzamiento deja de ser un "restyling" de la home actual y pasa a ser la instalación del **Growth Engine oficial** (motor de captura + tracking + narrativa Talent Architecture).

---

## 2. Mirror local con `wget --mirror`

### 2.1. Método

Se intentó primero con `firecrawl scrape` (HTML limpio/procesado) pero no servía: descarga el HTML post-rendering sin CSS externos ni rutas relativas, y los ES modules del iframe de colorflow se bloquean por CORS en `file://`.

**Solución:** `wget --mirror` con `--convert-links` para reescribir URLs absolutas → rutas relativas, incluyendo asset dependencies de CDNs externos (fonts, JS libs, colorflow embed).

```bash
mkdir -p mirror && cd mirror && wget \
  --mirror \
  --convert-links \
  --adjust-extension \
  --page-requisites \
  --no-parent \
  --span-hosts \
  --domains v2.ubits.com,cdn.jsdelivr.net,cdnjs.cloudflare.com,fonts.googleapis.com,fonts.gstatic.com,colorflow.ls.graphics \
  -e robots=off \
  -U "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0 Safari/537.36" \
  --no-check-certificate \
  --restrict-file-names=windows \
  https://v2.ubits.com/
```

Resultado: **49 MB · 148 archivos · 12 segundos**.

### 2.2. Ubicación (gitignored)

El directorio `mirror/` está en `.gitignore` (tamaño). Para regenerarlo, correr el comando de arriba. Estructura:

```
mirror/
├── v2.ubits.com/
│   ├── index.html              (home — HTML original)
│   ├── form-register-client.html
│   ├── styles.css              (estilos custom completos)
│   ├── script.js               (interacciones custom)
│   ├── images/                 (logo UBITS, hero, 8 logos de clientes)
│   ├── img/                    (avatares)
│   └── video/                  (video-bubble.mp4, video-serena.mp4)
├── cdn.jsdelivr.net/           (intl-tel-input lib)
├── cdnjs.cloudflare.com/       (Font Awesome + webfonts)
├── colorflow.ls.graphics/      (embed.html + assets del fondo animado)
├── fonts.googleapis.com/       (CSS de Google Fonts: Inter, Outfit)
├── fonts.gstatic.com/          (.woff2 de las fuentes)
└── cdn.prod.website-files.com/ (favicon UBITS)
```

### 2.3. Cómo servirlo localmente

**Importante:** no abrir con `file://` doble-click. El iframe de colorflow (fondo animado del CTA final) usa `<script type="module">` y los navegadores bloquean ES modules desde `file://` por seguridad.

```bash
cd mirror && python3 -m http.server 8765
```

Luego abrir:
- Home: http://localhost:8765/v2.ubits.com/index.html
- Form: http://localhost:8765/v2.ubits.com/form-register-client.html

---

## 3. Análisis crítico del v2

### 3.1. Lo que el v2 resuelve respecto al sitio actual

| Problema actual | Cómo lo resuelve v2 |
|---|---|
| Encuestas retorna 404 | Encuestas está visible como módulo 04 |
| Homepage dice "4 módulos" pero hay 6 | v2 muestra 5 módulos coherentemente |
| Form con 10+ campos (98.5% abandon) | Form segmentado por 3 secciones + captura email 1 campo en footer |
| Narrativa "catálogo de cursos" | Narrativa "Talent Architecture" unificada |
| Look & feel dated | Diseño premium B2B SaaS (glassmorphism, gradientes, video Serena) |

### 3.2. Lo que NO está listo en el v2 (hallazgos del mirror)

**Bloqueantes (antes de Webflow):**

- Nav: `Por qué Ubits`, `Ubits AI`, `Iniciar sesión` → todos apuntan a `#` (no implementados)
- Footer: `Skilled`, `Blog`, `Sala de prensa`, `Contacto`, `Términos`, `Colombia/México/Chile/Perú` → todos `#` muertos
- **No tiene tracking GTM** (sin container `GTM-5C9SS9Q`)
- **No tiene schema JSON-LD** (pierde rich snippets)
- **No tiene Consent Mode V2** (riesgo GDPR Colombia)

**Bugs de contenido (antes de copy freeze):**

- Bug de render: `"Lagestióndeltalentonodeberíasentirsecomoarmarunrompecabezasaciegas"` (palabras pegadas)
- 3 testimoniales con texto duplicado (Sebastian, Luisa, Karla dicen: *"Es un gran aliado estratégico para nuestro proceso de reclutamiento y entrenamiento"*)
- Avatares repetidos (Karla Gómez usa el mismo `avatar-1.png` que Amanda)

**Cobertura (vs. SEO actual):**

- Es **one-pager** — no contempla las internas que convierten:
  - `/becas-ia` — 50.84% conversión
  - `/skilled` — 21K vistas/año
  - `/ubits-para-tu-empresa` — 9% bounce
  - `/modulos/*` (6 páginas) — 77K+ vistas/año combinadas

---

## 4. Tensión resuelta: v2 como home, plan táctico para el resto

Lo que veníamos planeando en el [brief ejecutivo](2026-04-15-brief-ejecutivo-juan.md) (rebuild Webflow + 6 módulos + FAQs únicas + redirects 301) **no contradice** al v2 — lo complementa. El v2 reemplaza el `/` (home), el plan táctico aplica a todo lo demás.

### Mapa de decisión consolidado

| Área del sitio | Qué pasa | Fuente de verdad |
|---|---|---|
| `/` (home) | Reconstruir en Webflow a partir del código del mirror v2 | `mirror/v2.ubits.com/index.html` |
| `/modulos/*` | Aplicar copy nuevo + FAQs únicas del plan táctico | [plan táctico §2 y §8](2026-04-15-plan-tactico-relanzamiento.md) |
| `/modulos/encuestas` | Crear de cero (resolver 404) | [plan táctico §7](2026-04-15-plan-tactico-relanzamiento.md) |
| `/becas-ia`, `/skilled`, `/ubits-para-tu-empresa` | **Conservar**, optimizar on-page | [plan táctico §6](2026-04-15-plan-tactico-relanzamiento.md) |
| `/form-register-client` | **Matar** la versión larga, A/B con 3 campos | [plan táctico §5](2026-04-15-plan-tactico-relanzamiento.md) |
| URLs duplicadas módulos | 301 redirects a la versión canónica | [plan táctico §1](2026-04-15-plan-tactico-relanzamiento.md) |

---

## 4.5. Estrategia de publicación: "Switch Final" sin downtime

**Cómo NO romper el SEO ni el tracking durante el relanzamiento:**

En vez de sobrescribir el `/` actual, construir la nueva home como **página secreta dentro del Webflow existente** (ej. `ubits.com/new-home-draft`), auditar a fondo, y solo cuando esté irrompible, hacer el "switch" en la configuración de Webflow para que esa página pase a ser el `/`.

| Beneficio | Por qué importa |
|---|---|
| **Protección absoluta de URLs** | El 100% del SEO existente sigue intacto. Las 4.87M impresiones/año no se tocan. Solo agregamos un "lienzo nuevo" al proyecto |
| **Herencia del tracking global** | La nueva página hereda automáticamente el container `GTM-5C9SS9Q` configurado a nivel de proyecto Webflow |
| **Control para el switch final** | Diseñas, testeas, auditas en URL secreta; cuando esté perfecta, switch en Webflow → es el nuevo `/` sin apagar servidores |
| **Rollback inmediato si algo falla** | Si en post-launch hay regresión de KPIs, el switch reverso es 1 click |

**Implicación operativa:** todo el trabajo de Fase 1 (DataLayer, GTM, Consent Mode) se valida primero en `localhost:8765` con el mirror, luego se pega en `ubits.com/new-home-draft` (sin tráfico), y solo cuando GTM Preview confirma que dispara correctamente, se hace el switch.

---

## 5. Plan de ataque (3 fases)

### Fase 1 — Tracking defensivo + hack del footer

**Objetivo:** dejar de estar ciegos (tracking roto desde marzo) y capturar leads con fricción mínima.

- Inyectar **GTM `GTM-5C9SS9Q`** + **Consent Mode V2** en el `<head>` del v2 local y probar en localhost:8765
- Cablear el **footer input-only** (1 campo email) con listener JS que dispare `ubits_lead_captured` al dataLayer
- Probar end-to-end con GTM Preview Mode **antes** de tocar Webflow
- Definir destino del lead: HubSpot Forms API → contact con `lifecycle_stage: subscriber` + `source: homepage_footer`
- Schema completo del dataLayer en [docs/v2/datalayer-spec.json](../docs/v2/datalayer-spec.json)

**Por qué primero:** si el relanzamiento se publica sin tracking, repetimos el error de marzo/abril. Y el footer de 1 campo es la mayor palanca de conversion (objetivamente triplica captura TOFU vs. form largo).

### Fase 2 — Rutear intención con el funnel Serena AI

**Objetivo:** segmentar CTA por intención del usuario para no sacrificar leads BOFU.

| Botón | Intención | Destino propuesto |
|---|---|---|
| `Agendar demo` (hero + nav, azul primario) | Alta, BOFU | Form corto 3 campos (nombre + email + empresa) → calendario HubSpot |
| `Ver ROI de tu equipo` (secundario) | Media, MOFU | Funnel Serena AI (calculadora ROI + chat) — skill `ubits-funnel` |
| Footer email capture | Baja, TOFU | Nurturing HubSpot secuencia 5 emails |

**Por qué NO mandar todos los CTAs al funnel Serena:** un usuario que ya clickeó "Agendar demo" quiere agendar, no calcular. Meter otra capa de convencimiento cae la conversión BOFU. El funnel Serena es arma MOFU, no universal.

### Fase 3 — Protección SEO + keyword layering

**Objetivo:** no perder las 4.87M impresiones/año + capturar volumen nuevo.

- Tabla de **redirects 301** publicada en Webflow antes del relanzamiento (5 URLs P0 del plan táctico)
- **Keyword "LMS"** NO en H1 (compromete reposicionamiento Talent Architecture) pero sí en:
  - H2/H3 táctico: *"Más que un LMS: plataforma unificada de reclutamiento, aprendizaje, desempeño y encuestas"*
  - Schema `SoftwareApplication.applicationCategory: "LMS, HRIS, Performance Management"`
  - Páginas pSEO long-tail vía skill `pseo-engine` (*LMS para retail*, *LMS con IA en español*, etc.)
- **Canonical tags** para resolver las URLs duplicadas de `/modulos/aprendizaje`

---

## 6. Timeline de 15 días (hoy → 30 abril)

```
HOY (15 abril)
├── Congelar schema DataLayer (docs/v2/datalayer-spec.json)
├── Decisión: destino lead footer (HubSpot Forms API vs. Mailchimp vs. otro)
└── Ratificar Webflow como target de publish

DÍAS 1-3 (16-18 abril)
├── Restaurar GTM-5C9SS9Q en producción actual (P0 urgente)
├── Escribir DataLayer completo en el v2 local
├── Probar con GTM Preview Mode contra localhost:8765
└── Fix bugs de copy del v2 (palabras pegadas, testimoniales duplicados, avatares)

DÍAS 4-8 (19-23 abril)
├── Migrar v2 → Webflow (Symbols + Classes con skill lumos-skill)
├── Pegar GTM + DataLayer al <head> de Webflow
├── Crear /modulos/encuestas (resolver 404)
├── Aplicar plan táctico a páginas internas (FAQs únicas, copy María)
└── Rediseñar /form-register-client → variante 3 campos

DÍAS 9-12 (24-27 abril)
├── Schema JSON-LD por página
├── Tabla 301 publicada
├── A/B test footer vs. hero CTA
└── QA completo pre-publish (Lighthouse, Chrome DevTools, GTM debug)

DÍAS 13-15 (28-30 abril)
├── Soft launch (50% traffic con feature flag si Webflow lo permite)
├── Monitorear demos/conversion 48h
└── Full launch si KPIs holden vs baseline
```

---

## 7. Decisiones pendientes (bloquean ejecución)

| # | Decisión | Dueño | Bloquea |
|---|---|---|---|
| 1 | Schema completo del DataLayer aprobado | David + Juan | Toda Fase 1 |
| 2 | Destino del lead del footer (HubSpot Forms API? Mailchimp? Otro?) | Juan + equipo HubSpot | Footer listener, lead nurturing |
| 3 | Confirmación Webflow como target (no Netlify) | Juan | Fases 2 y 3 completas |
| 4 | Quién ejecuta la migración Webflow (tú, dev interno, agencia) | Juan | Timeline días 4-8 |
| 5 | ¿Se mata `/form-register-client` largo o se A/B testea? | David + Growth | Fase 2 |

---

## 8. Referencias

- **Brief ejecutivo para Juan:** [2026-04-15-brief-ejecutivo-juan.md](2026-04-15-brief-ejecutivo-juan.md)
- **Plan táctico de relanzamiento:** [2026-04-15-plan-tactico-relanzamiento.md](2026-04-15-plan-tactico-relanzamiento.md)
- **INDEX maestro:** [2026-04-15-INDEX-relanzamiento.md](2026-04-15-INDEX-relanzamiento.md)
- **Design evidence (Antigravity):** [2026-04-15-homepage-relaunch-design-evidence.md](2026-04-15-homepage-relaunch-design-evidence.md)
- **Baseline GA4 anual:** [../ops/10_laboratorio-growth/10_auditoria_ga4_abril2026.md](../ops/10_laboratorio-growth/10_auditoria_ga4_abril2026.md)
- **DataLayer spec:** [../docs/v2/datalayer-spec.json](../docs/v2/datalayer-spec.json)
- **Skills relevantes:** `ubits-funnel` (MVP Serena AI), `lumos-skill` (Webflow framework), `pseo-engine` (long-tail SEO), `gtm-datalayer` (tracking spec)

---

*Última actualización: 2026-04-15 — David Toro*
