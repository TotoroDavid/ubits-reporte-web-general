---
type: moc
area: estrategia
tags: [indice, moc, relanzamiento, mapa-conocimiento]
related_areas: [analitica, website, organico, identidad-ubits, laboratorio-growth]
captured_date: 2026-04-15
author: David Toro
---

# 🗺️ INDICE MAESTRO — Relanzamiento Web UBITS

> **Este es TU punto de entrada.** Cuando Juan (o cualquiera) te pida algo sobre el relanzamiento, empieza aqui.  
> **Fecha baseline:** 2026-04-15 | **Deadline relanzamiento:** fin abril 2026

---

## CORRECCION CRITICA (2026-04-16): "Falso Colapso" — 7 meses ciegos, no muertos

> **El "colapso del 99.9%" en GSC era un artefacto de medicion.** Cuando migraron de www a sin-www (~sep 2025), nadie agrego la propiedad correcta en Search Console. El equipo ha estado 7 meses mirando una propiedad vacia. El trafico real probablemente sigue vivo pero SIN MEDIR.
>
> Ademas: Universal Analytics (`UA-233753207-1`) esta hardcodeado y muerto desde 2023. El boton de demo envia eventos al vacio.
>
> → [Super Informe (corregido)](2026-04-16-seo-technical-audit-consolidated.md)
> → [GSC raw data](../data/raw/gsc/2026-04-16/gsc-performance-analysis.md)
>
> **P0 inmediato (5 min):** Agregar propiedad `ubits.com` sin-www en GSC + borrar UA zombie del Custom Code.

---

## ⚡ Acceso rapido por pregunta

### "¿Por que recomiendas rebuild y no proyecto nuevo?"
→ [Brief ejecutivo § Recomendacion](2026-04-15-brief-ejecutivo-juan.md#-la-recomendacion-opcion-a-rebuild-sobre-webflow-existente)  
→ [Decision report completo 2026-04-14](2026-04-14-website-relaunch-decision-report.md)

### "¿Cuanto trafico tenemos?"
→ [Brief § Baseline](2026-04-15-brief-ejecutivo-juan.md#-baseline-anual-real-lo-que-tenemos-hoy) — **519K usuarios/año, 310 demos, 4.87M impresiones**  
→ Raw: [01-resumen-panoramico-anual.md](../data/raw/ga4/2026-04-15/01-resumen-panoramico-anual.md)

### "¿Cuantos demos generamos?"
→ **310 demos exitosos/año** (~26/mes, ~6/semana)  
→ 21,000 form opens/año pero solo 1.48% completa  
→ Raw: [12-resumen-anual.md](../data/raw/ga4/2026-04-15/12-resumen-anual.md)

### "¿Que canal convierte mejor?"
→ **Email 8.86%** > Organic Social 6.51% > Direct 1.14% > Organic Search 0.57%  
→ Raw: [17-canales-anuales-keyevents.md](../data/raw/ga4/2026-04-15/17-canales-anuales-keyevents.md)

### "¿Paid esta corriendo?"
→ **NO.** 93 usuarios de paid en 12 meses. Credito $350 Google Ads sin usar.  
→ Raw: [16-canales-comparacion-anual.md](../data/raw/ga4/2026-04-15/16-canales-comparacion-anual.md)

### "¿Cual es la pagina que mejor convierte?"
→ **`/becas-ia-para-recursos-humanos-google` = 50.84% conversion**  
→ Seguida de `/skilled` con 12.55%  
→ Raw: [21-landing-pages-anuales.md](../data/raw/ga4/2026-04-15/21-landing-pages-anuales.md)

### "¿El SEO funciona?"
→ **Si pero mal convertido.** 4.87M impresiones anuales (P14.96 promedio). 100% de clicks son brand.  
→ **NUEVO (2026-04-16):** Solo 42 de 177 URLs son indexables (24%). Blog entero (37 posts) non-indexable.  
→ Oportunidad: +140K clicks/año optimizando solo 4 paginas  
→ **Audit tecnico completo:** [SEO Technical Audit Consolidated](2026-04-16-seo-technical-audit-consolidated.md)  
→ Raw: [22-search-console-queries-anual.md](../data/raw/ga4/2026-04-15/22-search-console-queries-anual.md) + [25-seo-paginas-destino-anual.md](../data/raw/ga4/2026-04-15/25-seo-paginas-destino-anual.md)

### "¿Cuantas paginas tenemos indexadas?"
→ **SOLO 4 de 756 que Google conoce** (0.5%). Screaming Frog decia 42 "indexables" pero GSC confirma que Google solo indexa 4.  
→ 94% del trafico es brand ("ubits"). 6% generico. Cero product-fit.  
→ [Audit SEO § Correccion critica GSC](2026-04-16-seo-technical-audit-consolidated.md)

### "¿Que problemas tecnicos tiene el sitio?"
→ 44 issues detectados. Top: canonicals rotos (49%), H1 missing (4 paginas), 178 imgs sin alt, 203 imgs sin size  
→ [Audit SEO § Issues criticos](2026-04-16-seo-technical-audit-consolidated.md#2-issues-criticos-del-crawl)

### "¿Que keywords B2B debemos atacar?"
→ "LMS" 18,940 impresiones, "competencias laborales" 10,868, "enps" 4,342, "capacitacion" 8,212+  
→ [Audit SEO § Keywords B2B prioritarias](2026-04-16-seo-technical-audit-consolidated.md#5-google-search-console--long-tail-9896-queries)

### "¿Quien es nuestro usuario?"
→ **70% mujeres, 25-34 años, Spanish, mobile, Chrome+Edge, Colombia+Mexico**  
→ Raw: [26-demografia-completa-anual.md](../data/raw/ga4/2026-04-15/26-demografia-completa-anual.md)

### "¿Que paises convierten mejor?"
→ **El Salvador 4.56%** > Rep. Dominicana 2.87% > Colombia 1.93% > Mexico 1.73%  
→ USA NO es mercado real (0.57% conversion, 13s engagement)  
→ Raw: [26-demografia-completa-anual.md § Conversion por pais](../data/raw/ga4/2026-04-15/26-demografia-completa-anual.md)

### "¿Por que abril 2026 se ve tan mal?"
→ **TRACKING ROTO.** Los demos llegan, pero GA4 no los mide.  
→ Causa probable: publish Webflow elimino GTM snippet o trigger  
→ Accion: revisar GTM container `GTM-5C9SS9Q`  
→ Raw: [auditoria v3.0 § Hallazgo #1](../ops/10_laboratorio-growth/10_auditoria_ga4_abril2026.md)

### "¿Como puedo replicar el exito de /becas-ia?"
→ Template: landing de valor gratuito a cambio de lead  
→ Convierte 50.84% en form completion  
→ Replicar para 2-3 verticales: Harvard Executive, Bancos, Educacion Superior  
→ [Plan tactico § Post-relanzamiento](2026-04-15-plan-tactico-relanzamiento.md#10-plan-post-relanzamiento)

### "¿Como escribo el copy de los modulos?"
→ [Plan tactico § Copy por modulo](2026-04-15-plan-tactico-relanzamiento.md#2-copy-por-modulo) — copy listo para pegar  
→ Fuente: [Argumentario Maria RRHH](../ops/09_sales-enablement/argumentario-modulos-rrhh.md) + [Contexto 6 modulos](../ops/01_identidad-ubits/modulos-contexto-completo.md)

### "¿Que schema JSON-LD pongo?"
→ [Plan tactico § Schema](2026-04-15-plan-tactico-relanzamiento.md#4-schema-json-ld) — codigo listo para copy-paste

### "¿Que redirects 301 necesito?"
→ [Plan tactico § Redirects](2026-04-15-plan-tactico-relanzamiento.md#1-matriz-de-redirects-301) — matriz completa

### "¿Que eventos clave configuro en GA4?"
→ [Plan tactico § GTM y eventos](2026-04-15-plan-tactico-relanzamiento.md#3-configuracion-gtm--eventos-clave)  
→ Lista de 32 eventos actuales: [23-eventos-32-completos.md](../data/raw/ga4/2026-04-15/23-eventos-32-completos.md)

### "¿Que FAQs uso para cada modulo?"
→ [Plan tactico § FAQs unicas](2026-04-15-plan-tactico-relanzamiento.md#8-faq-unicas-por-modulo) — 36 FAQs (6 por modulo)

### "¿Como cambio los title tags y metas?"
→ [Plan tactico § SEO on-page](2026-04-15-plan-tactico-relanzamiento.md#6-optimizacion-seo-on-page) — las 4 paginas con mayor oportunidad

### "¿Que tiene que decir la pagina /modulos/encuestas?"
→ Hoy es 404. [Copy completo en Plan tactico § 7](2026-04-15-plan-tactico-relanzamiento.md#7-pagina-modulos-encuestas-nueva)

### "¿Como construyo la nueva home en Webflow?"

→ [MOC Webflow Build](../docs/v2/MOC-webflow-build.md) — hub operativo con mirror, Lumos KB, progreso por seccion  
→ [Lumos Framework Reference](../docs/v2/lumos-framework-reference.md) — guia consolidada

### "¿Que es Lumos y donde esta la documentacion?"

→ [Lumos Knowledge Base](../docs/v2/lumos/README.md) — 23 docs oficiales scrapeadas (4,796 lineas)  
→ [Databases completas](../docs/v2/lumos/) — all utilities + all variables

### "¿Donde esta el codigo clonado del v2?"

→ [Plan mirror + relanzamiento](2026-04-15-v2-mirror-and-relaunch-plan.md) — metodo wget, approach switch-final  
→ Local: `mirror/v2.ubits.com/` (gitignored, regenerable)

### "¿Que piensas del diseno del v2?"

→ [Design critique](2026-04-15-v2-design-critique.md) — scorecard 6.3/10, 3 intervenciones propuestas

### "¿Que eventos trackea el DataLayer?"

→ [DataLayer spec v1.0](../docs/v2/datalayer-spec.json) — 12 eventos, Consent Mode V2, HubSpot integration

### "¿Cual es el ROI del relanzamiento?"
→ Baseline: 310 demos/año  
→ Si arreglamos form → 2,600 demos/año (**8.4x**)  
→ Si ademas activamos email + paid → 12,000 demos/año (**39x**)  
→ [Brief § ROI](2026-04-15-brief-ejecutivo-juan.md#-roi-estimado-del-relanzamiento)

---

## 📋 Documentos del relanzamiento (ordenados por audiencia)

### 🎯 Para Juan Felipe / Stakeholders
| Documento | Tamaño | Uso |
|-----------|-------:|-----|
| **[Super Informe Consolidado](2026-04-16-seo-technical-audit-consolidated.md)** | **~8 paginas** | **El "circuito roto" completo: SEO + GA4 + GTM + GSC + plan 22 acciones (2026-04-16)** |
| [Brief ejecutivo (actualizado 2026-04-16)](2026-04-15-brief-ejecutivo-juan.md) | ~8 paginas | Decision de negocio + 8 problemas criticos + ROI actualizado |
| [Decision report rebuild vs nuevo](2026-04-14-website-relaunch-decision-report.md) | ~6 paginas | Justificacion tecnica de la opcion A |

### 🔧 Para ti (ejecucion)

| Documento | Tamaño | Uso |
|-----------|-------:|-----|
| [Plan tactico](2026-04-15-plan-tactico-relanzamiento.md) | ~15 paginas | Tu companion durante la ejecucion del relanzamiento |
| [Plan mirror + relanzamiento](2026-04-15-v2-mirror-and-relaunch-plan.md) | ~10 paginas | Mirror wget, approach switch-final, timeline 15 dias, decisiones pendientes |
| [Design critique v2](2026-04-15-v2-design-critique.md) | ~8 paginas | Scorecard 6.3/10 + 3 intervenciones propuestas antes del switch |
| [MOC Webflow Build](../docs/v2/MOC-webflow-build.md) | Hub | Punto de entrada del build operativo en Webflow (progreso por seccion) |
| [Lumos KB](../docs/v2/lumos/README.md) | 23 docs · 4,796 lineas | Framework oficial scrapeado del Notion de Timothy Ricks |
| [Lumos reference consolidada](../docs/v2/lumos-framework-reference.md) | ~15 paginas | Guia rapida en un solo archivo |
| [Client-First + Lumos hybrid](../docs/v2/lumos/21-hero-refactor-example.md) | — | Decision del framework + DOM tree del Hero UBITS |
| [DataLayer spec v1.0](../docs/v2/datalayer-spec.json) | JSON | 32 eventos, Consent Mode V2, HubSpot integration |
| [Plan accion SEO + Analytics](../docs/v2/21_master_seo_analytics_action_plan.md) | ~4 paginas | Hoja de ruta 3 fases: limpieza CMS, SEO on-page, tracking (2026-04-16) |
| Este INDEX | — | Punto de entrada rapido |

### 📊 Para defender la data (evidencia)

| Documento | Contenido |
|-----------|-----------|
| [Auditoria GA4 v3.0](../ops/10_laboratorio-growth/10_auditoria_ga4_abril2026.md) | Analisis consolidado completo |
| [Snapshot metadata](../data/raw/ga4/2026-04-15/snapshot-metadata.md) | Indice de 26 archivos raw |
| [Baseline analysis](2026-04-15-ga4-baseline-analysis.md) | Primer analisis del baseline |
| **[SEO Audit Consolidated](2026-04-16-seo-technical-audit-consolidated.md)** | **Crawl data cruzado con GA4 + GSC. Raw: `docs/seo_auditoria/` (7 CSVs)** |
| [Long-tail SEO Analysis](2026-04-15-long-tail-seo-analysis.md) | Forense 9,896 queries GSC posiciones 251+ |

### 🔍 Para hallazgos especificos

| Hallazgo | Documento |
|----------|-----------|
| /skilled sin documentar | [03_pagina-skilled-hallazgo.md](../ops/11_website/03_pagina-skilled-hallazgo.md) |
| Observaciones criticas | [Log de experimentos](../ops/08_experimentos/log.md) |

---

## 📊 Snapshot GA4 completo (26 archivos raw)

**Ubicacion:** [data/raw/ga4/2026-04-15/](../data/raw/ga4/2026-04-15/)  
**Indice:** [snapshot-metadata.md](../data/raw/ga4/2026-04-15/snapshot-metadata.md)

### Por tipo de data

**📅 Resumenes temporales:**
- [01 — Panoramico anual](../data/raw/ga4/2026-04-15/01-resumen-panoramico-anual.md)
- [02 — 7 dias](../data/raw/ga4/2026-04-15/02-resumen-7-dias.md)
- [03 — 30 dias](../data/raw/ga4/2026-04-15/03-resumen-30-dias.md)
- [12 — Anual con eventos clave](../data/raw/ga4/2026-04-15/12-resumen-anual.md)
- [24 — Panoramico corregido](../data/raw/ga4/2026-04-15/24-panoramico-anual-corregido.md)

**🚪 Adquisicion:**
- [04 — Usuarios por canal 14d](../data/raw/ga4/2026-04-15/04-adquisicion-usuarios-14d.md)
- [05 — Sesiones por canal 14d](../data/raw/ga4/2026-04-15/05-adquisicion-trafico-14d.md)
- [16 — Canales con segmentos anual](../data/raw/ga4/2026-04-15/16-canales-comparacion-anual.md)
- [17 — Canales con key events](../data/raw/ga4/2026-04-15/17-canales-anuales-keyevents.md)
- [18 — Campañas UTM anuales](../data/raw/ga4/2026-04-15/18-campañas-utm-anuales.md)

**🔍 SEO / Search Console:**
- [08 — 7 dias](../data/raw/ga4/2026-04-15/08-search-console-7d.md)
- [15 — Anual impresiones](../data/raw/ga4/2026-04-15/15-search-console-anual.md)
- [22 — Queries anuales (80K)](../data/raw/ga4/2026-04-15/22-search-console-queries-anual.md)
- [25 — SEO por pagina destino](../data/raw/ga4/2026-04-15/25-seo-paginas-destino-anual.md)

**📄 Paginas:**
- [07 — Top 100 paginas](../data/raw/ga4/2026-04-15/07-paginas-top-100.md)
- [11 — Landing pages 14d](../data/raw/ga4/2026-04-15/11-paginas-destino-14d.md)
- [20 — Top 250 paginas anual](../data/raw/ga4/2026-04-15/20-paginas-anuales-top250.md)
- [21 — Landing pages anual](../data/raw/ga4/2026-04-15/21-landing-pages-anuales.md)

**💯 Engagement y conversion:**
- [06 — Engagement 14d](../data/raw/ga4/2026-04-15/06-engagement-14d.md)
- [09 — Audiencias 7d](../data/raw/ga4/2026-04-15/09-audiencias-7d.md)
- [13 — Retencion por cohortes](../data/raw/ga4/2026-04-15/13-retencion-cohortes.md)
- [19 — Eventos detalle anual](../data/raw/ga4/2026-04-15/19-eventos-anuales-detalle.md)
- [23 — 32 eventos completos](../data/raw/ga4/2026-04-15/23-eventos-32-completos.md)

**🌎 Geografia y demografia:**
- [10 — Geografia basica](../data/raw/ga4/2026-04-15/10-geografia.md)
- [14 — Dispositivos 7d](../data/raw/ga4/2026-04-15/14-dispositivos-7d.md)
- [26 — Demografia completa 140 paises](../data/raw/ga4/2026-04-15/26-demografia-completa-anual.md)

---

## 🏢 Contexto UBITS (producto y estrategia)

### Producto (los 6 modulos + Intranalytics)
- [Contexto completo modulos](../ops/01_identidad-ubits/modulos-contexto-completo.md) — 450 lineas cruzando sitio + Zendesk + LinkedIn + keywords
- [Argumentario Maria](../ops/09_sales-enablement/argumentario-modulos-rrhh.md) — traduccion tecnica a lenguaje de HR Director
- [Matriz taxonomia](../ops/01_identidad-ubits/matriz-taxonomia-modulos.md)
- [Mensaje y posicionamiento](../ops/01_identidad-ubits/mensaje-y-posicionamiento.md)
- [ICP y buyer persona](../ops/01_identidad-ubits/icp-y-buyer.md)

### Estrategia SEO de Juan Felipe (docs/SEO/ — 2026-04-16)
- **[Spider Analysis: Estrategia JF vs Realidad Tecnica](2026-04-16-seo-strategy-spider-analysis.md)** — cruce de 21 blogs + keywords + calendarios con GSC/GA4
- [Blogs master catalogo](../data/nueva_data/estrategia-adquisicion-organica-2026/Blogs_master_catalogo.csv) — 60 blogs planificados
- [Calendarios blogs Q1/Q2 2026](../data/nueva_data/estrategia-adquisicion-organica-2026/)
- [Descargables contenido completo](../ops/07_organico/descargables-contenido-completo.md) — 16 lead magnets
- docs/SEO/ (local, no en git) — 21 blogs completos con imagenes, golden keywords, calendarios LLM/descargables, cronograma 2025

### Estrategia SEO / GEO / LLM
- [Estrategia GEO](../ops/07_organico/geo-estrategia.md) — 10 principios GEO aplicados
- [Implementacion GEO](../ops/07_organico/geo-implementacion.md)
- [10 principios originales](../data/nueva_data/geo-llm-optimization/10-principios-optimizacion-llms.md)
- [Long-tail SEO forense](2026-04-15-long-tail-seo-analysis.md) — 9,896 queries GSC

### Tracking y medicion
- [GTM Triggers/Variables/Tags Config](../docs/v2/22_gtm_triggers_variables_config.md) — guia completa para GTM-5M96L5KF
- [DataLayer spec v1.1](../docs/v2/datalayer-spec.json) — 32 eventos, GTM-5M96L5KF
- [Plan accion SEO + Analytics](../docs/v2/21_master_seo_analytics_action_plan.md) — 3 fases operativas
- [Webflow cleanup verification](../src/audit/verify_webflow_cleanup.py) — script test automatizado

### Arquitectura tecnica
- [Arquitectura Webflow](../ops/11_website/01_arquitectura-webflow.md)
- [Analisis integrado SEO](../ops/11_website/02_analisis-integrado-seo.md)
- [Pagina /skilled hallazgo](../ops/11_website/03_pagina-skilled-hallazgo.md)

### Data raw (GSC + GA4)
- [GSC Performance 12 meses](../data/raw/gsc/2026-04-16/gsc-performance-analysis.md)
- [GSC Indexation report](../data/raw/gsc/2026-04-16/gsc-indexation-report.md)
- [Sitemap envenenado analisis](../data/raw/gsc/2026-04-16/sitemap-envenenado-2025-07-02.md)
- [Screaming Frog CSVs](../docs/seo_auditoria/) — 7 CSVs + 7 GSC export dirs
- [GA4 snapshot metadata](../data/raw/ga4/2026-04-15/snapshot-metadata.md) — 26 archivos raw

### Web scraped (producto en vivo, abril 2026)
- [Aprendizaje](../.firecrawl/ubits-modulos-aprendizaje.md)
- [Desempeno](../.firecrawl/ubits-modulos-desempeno.md)
- [Diagnostico](../.firecrawl/ubits-modulos-diagnostico.md)
- [Reclutamiento](../.firecrawl/ubits-modulos-reclutamiento.md)
- [Tareas y Planes](../.firecrawl/ubits-modulos-tareas-y-planes.md)
- [Encuestas](../.firecrawl/ubits-modulos-encuestas.md) — 404
- [Homepage](../.firecrawl/ubits-homepage.md)
- [/skilled](../.firecrawl/ubits-skilled.md)

---

## 🎯 Los 21 hallazgos criticos consolidados

Para que los tengas a la mano cuando te pregunten cualquier cosa (actualizados 2026-04-16 con GSC Performance 12 meses + audit tecnico):

| # | Hallazgo | Dato | Documento |
|---|----------|------|-----------|
| 0 | **GSC CIEGO 7 MESES + UA ZOMBIE** | "Falso colapso": migracion www→sin-www sin actualizar GSC. UA-233753207-1 muerto desde 2023. Demo button no trackea | [Super Informe](2026-04-16-seo-technical-audit-consolidated.md) |
| 1 | **Tracking GA4 roto** | 0 eventos abril 2026 vs 310/año | [Audit v3.0](../ops/10_laboratorio-growth/10_auditoria_ga4_abril2026.md) |
| 2 | **Form abandonment 98.5%** | 21K abren, 310 completan | [23-eventos](../data/raw/ga4/2026-04-15/23-eventos-32-completos.md) |
| 3 | **URLs duplicadas todos modulos** | `/modulos/X` + `/modulo-X` + `/modulo-de-X` | [20-paginas-anuales](../data/raw/ga4/2026-04-15/20-paginas-anuales-top250.md) |
| 4 | **`/becas-ia-google` convierte 50.84%** | 2,500 sesiones → 1,922 key events | [21-landing-pages](../data/raw/ga4/2026-04-15/21-landing-pages-anuales.md) |
| 5 | **`/skilled` convierte 12.55%** | 21K vistas, contenido feb 2024 desactualizado | [03_pagina-skilled](../ops/11_website/03_pagina-skilled-hallazgo.md) |
| 6 | **`/ubits-para-tu-empresa` 9% bounce** | 567K impresiones, solo 0.23% CTR | [25-seo-paginas](../data/raw/ga4/2026-04-15/25-seo-paginas-destino-anual.md) |
| 7 | **Email convierte 16x organic search** | 8.86% vs 0.57% | [17-canales-keyevents](../data/raw/ga4/2026-04-15/17-canales-anuales-keyevents.md) |
| 8 | **SEO real: 4.87M impresiones/año** | Posicion promedio 14.96 | [22-search-queries](../data/raw/ga4/2026-04-15/22-search-console-queries-anual.md) |
| 9 | **Paid completamente apagado** | 93 users/año, credito $350 sin usar | [16-canales-comparacion](../data/raw/ga4/2026-04-15/16-canales-comparacion-anual.md) |
| 10 | **Videos Vimeo muertos** | 206 users/año interactuan con video | [19-eventos-detalle](../data/raw/ga4/2026-04-15/19-eventos-anuales-detalle.md) |
| 11 | **QR codes trackeados (uqr.to)** | 3,800 users/año desde eventos offline | [24-panoramico-corregido](../data/raw/ga4/2026-04-15/24-panoramico-anual-corregido.md) |
| 12 | **Skilled tracking roto mid-2025** | 1ra temp: 1,953 events; 2da: 0 | [18-campañas-utm](../data/raw/ga4/2026-04-15/18-campañas-utm-anuales.md) |
| 13 | **70% usuarios son mujeres** | ICP corregido | [26-demografia](../data/raw/ga4/2026-04-15/26-demografia-completa-anual.md) |
| 14 | **URLs viejas convierten mejor** | `/modulo-aprendizaje` 5.22% vs `/modulos/aprendizaje` 0.69% | [21-landing-pages](../data/raw/ga4/2026-04-15/21-landing-pages-anuales.md) |
| 15 | **"Habilidades blandas" es el Everest** | 185K impresiones/año, P10 | [22-search-queries](../data/raw/ga4/2026-04-15/22-search-console-queries-anual.md) |
| 16 | **Blog 100% non-indexable** | 37 posts canonicalizados, 0 en indice de Google | [SEO Audit](2026-04-16-seo-technical-audit-consolidated.md) |
| 17 | **SOLO 4 PAGINAS INDEXADAS (GSC live)** | Google conoce 756 URLs, indexa 4. 99.5% invisible | [SEO Audit § Correccion critica](2026-04-16-seo-technical-audit-consolidated.md) |
| 18 | **94% trafico es brand, 6% generico** | Cero presencia en busquedas de producto B2B | [SEO Audit § GSC live](2026-04-16-seo-technical-audit-consolidated.md) |
| 19 | **/modulos/reclutamiento sin H1** | Pagina de producto clave sin heading principal | [SEO Audit](2026-04-16-seo-technical-audit-consolidated.md) |
| 20 | **"ubits learning" -76% impresiones** | Google pierde confianza en el sitio como resultado brand | [GSC alerta 2026-04-16](2026-04-16-seo-technical-audit-consolidated.md) |

---

## 📞 Sistemas externos (credenciales y accesos)

| Sistema | ID | Ubicacion | Responsable |
|---------|-----|-----------|-------------|
| GTM Produccion | `GTM-5C9SS9Q` | tagmanager.google.com | [pendiente acceso] |
| GTM MVPs | `GTM-W5QD6DLS` | tagmanager.google.com | [pendiente acceso] |
| Webflow | ubits-com.design.webflow.com | webflow.com | David Toro (Web Admin) |
| GA4 | UBITS Marketing Site | analytics.google.com | [pendiente] |
| HubSpot | Cuenta UBITS | app.hubspot.com | [pendiente] |
| Search Console | ubits.com | search.google.com/search-console | [pendiente] |
| Google Ads | Sin campañas activas | ads.google.com | $350 credito disponible |

---

## 🎪 Wiki interno UBITS (Google Drive — no local)

Links a activos vivos del equipo:

- Deck Macroprocesos: https://docs.google.com/presentation/d/15FEbZmfbgBwg8VsCzKM7T4OH9xGdyvwWW4AlDqWTLJU
- Gantt Q1 2026: https://docs.google.com/spreadsheets/d/16YdZeM1iITsEOsxwkWoyseFByRvHkomJws7jZ22fTZo
- Sales Enablement Bootcamp: https://docs.google.com/spreadsheets/d/1x9F0jt_27IhwtoZHayXCzshoR7PDljlhgEqP84vtzww
- Demos: https://docs.google.com/presentation/d/1BBaF8Lt9SchuxPwxB7_R8VlZopb9IQQy
- Agente Reportador Tests: https://chatgpt.com/g/g-693ab9b7efdc81918f41abc8e1885535

---

## 🗓️ Timeline del relanzamiento

```
Hoy (2026-04-15) ────┬──── Semana 1 (Abr 15-18): Tracking + Contenido
                     │
                     ├──── Semana 2 (Abr 21-25): Copy + SEO + Schema
                     │
                     ├──── Semana 3 (Abr 28-30): QA + Publicacion
                     │
Fin de abril ────────┤ 🚀 RELANZAMIENTO
                     │
                     ├──── Mayo: Monitoreo + A/B test form
                     │
                     ├──── Junio: Optimizacion + campañas nuevos paises
                     │
Jul 2026 ────────────┤ 🎯 Target: 60 demos/mes (2.3x baseline)
                     │
Oct 2026 ────────────┤ 🎯 Stretch: 150 demos/mes (5.8x baseline)
```

---

## 🧭 Como usar este INDEX

### Si Juan te pregunta sobre DECISION
→ Enviale el **Brief ejecutivo** completo.

### Si te pregunta sobre un NUMERO especifico
→ Busca en "Acceso rapido por pregunta" (seccion 1) y manda el link directo al raw.

### Si te pide un COPY o configuracion
→ Ve directo al **Plan tactico** y copia lo que necesite.

### Si alguien del equipo entra nuevo
→ Mandales este INDEX. Desde aqui pueden navegar todo.

### Si no encuentras algo
→ Busca en el **Snapshot metadata** — 26 archivos raw cubren todo lo de GA4.

### Si algo cambia post-relanzamiento
→ Genera nuevo snapshot GA4 en `data/raw/ga4/YYYY-MM-DD/` y crea un nuevo `INDEX-relanzamiento.md` que referencie al actual como baseline.

---

*INDEX generado 2026-04-15. Esta es la fuente de verdad para el relanzamiento. Actualizar si se agregan documentos nuevos.*
