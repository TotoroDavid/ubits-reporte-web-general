---
type: report
area: organico
tags: [seo, strategy, spider-analysis, blogs, keywords, content, cross-reference, juan-felipe]
captured_date: 2026-04-16
data_sources:
  - docs/SEO/ (estrategia JF — 21 blogs, calendarios, golden keywords)
  - docs/seo_auditoria/ (Screaming Frog crawl + GSC exports)
  - data/raw/gsc/2026-04-16/ (GSC Performance + Indexation)
  - data/raw/ga4/2026-04-15/ (GA4 snapshot 26 archivos)
  - reports/2026-04-16-seo-technical-audit-consolidated.md
author: David Toro / Growth Lab
---

# Analisis Spider: Estrategia SEO de Juan Felipe vs Realidad Tecnica

> **Proposito:** Cruzar la estrategia SEO planificada (docs/SEO/) con los hallazgos tecnicos (GSC, Screaming Frog, GA4) para entender que se planeo, que se ejecuto, que funciono, y que esta roto.

---

## 1. Inventario de la estrategia de Juan Felipe

### Lo que existe en docs/SEO/

| Asset | Cantidad | Estado |
|-------|---------|--------|
| Blogs escritos (2026) | 21 completos con imagenes | Listos para publicar o ya publicados |
| Blogs planificados (Q1-Q2 2026) | 60+ en calendario | 3/semana programados |
| Descargables (lead magnets) | 28 planificados, ~50 archivos | 20 con copy completo |
| Golden Keywords | 17 keywords principales | Tracking multi-pais |
| Calendario LLM | 11 acciones semanales Q1 | Schema + FAQs + docs tecnicos |
| Cronograma SEO 2025 | Gantt con 7 personas | Backlinks, blogs, diseno, QA |
| Keyword Research Q2 | Investigacion expandida | Por modulo UBITS |

### Equipo SEO documentado

| Persona | Rol |
|---------|-----|
| Valentina Gomez | Automation DAPTA → Webflow |
| Sebastian Prieto | Backlink building |
| Daniel Aya | Diseno web A/B tests |
| Juan David Jurado | Diseno web A/B tests |
| Nicolas Pena | QA de contenido |
| Alain Nantel | Calendario de eventos |
| Santiago Andrade | Calendario de eventos |

---

## 2. Los 21 blogs: Distribucion por modulo vs demanda real

### Blogs escritos por modulo

| Modulo UBITS | Blogs | % | Keywords B2B en GSC (impresiones) |
|-------------|------:|--:|-----------------------------------|
| Reclutamiento | 5 | 24% | ATS, filtrado CVs, entrevistas IA |
| Tareas y Planes | 4 | 19% | gestion tareas, seguimiento, productividad |
| Desempeno | 4 | 19% | evaluacion 360, feedback, indicadores |
| Aprendizaje/LMS | 4 | 19% | LMS (18,940 imp), capacitacion (8,212 imp) |
| Diagnostico/Assessments | 3 | 14% | assessment center, pruebas psicometricas |
| **Encuestas/Clima** | **0** | **0%** | **enps (4,342 imp), clima laboral, satisfaccion** |

### Cruce con demanda GSC real

| Keyword target (blogs JF) | Impresiones GSC 12 meses | Clicks | Posicion | Blog que lo ataca |
|---------------------------|------------------------:|-------:|---------:|-------------------|
| LMS / lms corporativo | 18,940 | 21 | 14.5 | #3 LMS corporativo con IA |
| competencias laborales | 10,868 | 21 | 22.6 | #10 Evaluacion competencias |
| capacitacion empresarial | 8,212+ | 20 | 22.9 | #13 Capacitacion con IA |
| evaluacion de desempeno | ~5,000 | ~15 | ~20 | #9, #14, #19 (3 blogs!) |
| enps | 4,342 | 25 | 14.3 | **NINGUNO — gap Clima** |
| assessment center | ~2,000 | ~10 | ~15 | #15 Assessment center online |
| pruebas psicometricas | ~1,800 | ~8 | ~18 | #20 Pruebas psicometricas |
| planes de sucesion | 1,805 | 23 | 6.8 | No hay blog dedicado |
| reclutamiento con IA | ~1,500 | ~5 | ~25 | #1 Reclutamiento con IA |
| gestion de tareas | ~1,200 | ~5 | ~20 | #2, #7, #12, #17 (4 blogs!) |

### Gaps criticos detectados

**Gap 1: Encuestas/Clima — 0 blogs, 4,342 impresiones para "enps"**
El modulo de Encuestas tiene 0 contenido en los 21 blogs. La keyword "enps" tiene 4,342 impresiones anuales en GSC con posicion 14.3 — a punto de pagina 1. Las keywords del calendario 2026 ("ambiente laboral", "ADN laboral", "satisfaccion del colaborador") tampoco tienen blogs escritos.

**Gap 2: "planes de sucesion" — posicion 6.8, 0 blogs**
Keyword en posicion 6.8 (casi pagina 1) con 1,805 impresiones. No hay blog dedicado.

**Gap 3: Sobre-saturacion en Tareas y Reclutamiento**
4 blogs para Tareas y 5 para Reclutamiento cuando la demanda GSC para esos terminos es menor que para LMS o capacitacion. El blog "gestion de tareas" tiene ~1,200 impresiones pero hay 4 blogs apuntando al mismo cluster.

---

## 3. Estado de publicacion: Blogs escritos vs visibilidad Google

### Los 21 blogs en el sitio web

| Blog JF | URL en sitio | Estado Screaming Frog | Estado GSC |
|---------|-------------|----------------------|------------|
| #1 Reclutamiento IA | /blog/reclutamiento-ia-transformacion-2026 | Non-indexable (Canonicalised) | No indexado |
| #2 Software tareas IA | /blog/software-tareas-ia-empresas | Non-indexable (Canonicalised) | No indexado |
| #3 LMS corporativo IA | /blog/lms-corporativo-ia-capacitacion | Non-indexable (Canonicalised) | No indexado |
| #4 Software desempeno IA | /blog/software-desempeno-ia-optimiza-rendimiento | Non-indexable (Canonicalised) | No indexado |
| #5 Diagnostico organizacional | /blog/diagnostico-organizacional-medicion-sesgos | Non-indexable (Canonicalised) | No indexado |
| #7 Gestion tareas 2026 | /blog/gestion-tareas-corporativas-2026 | Non-indexable (Canonicalised) | No indexado |
| #8 Plataforma aprendizaje | /blog/plataforma-aprendizaje-corporativo-adopcion-real | Non-indexable (Canonicalised) | No indexado |

**Todos los blogs publicados son invisibles.** Estan canonicalizados en Webflow CMS — Google no los indexa.

### Blocker resuelto vs pendiente

| Fix | Estado | Impacto en blogs |
|-----|--------|-----------------|
| Sitemap www → sin-www | RESUELTO (Webflow regenero 512 URLs correctas) | Google ya no recibe URLs falsas |
| GTM zombie UA eliminado | RESUELTO (Custom Code limpio) | No afecta blogs directamente |
| GSC propiedad sin-www | PENDIENTE (5 min) | Sin esto no podemos medir impacto |
| Blog canonical fix en Webflow CMS | **PENDIENTE** | **SIN ESTO, los 21 blogs siguen invisibles** |
| H1 fix en paginas de producto | PENDIENTE | No afecta blogs |

---

## 4. Calendario LLM — Cruce con estado tecnico

Las 11 acciones semanales del calendario LLM dependen de que el sitio sea indexable:

| Semana | Accion LLM | Prerequisito tecnico | Estado |
|--------|-----------|---------------------|--------|
| Ene 16 | Publicar doc tecnico Aprendizaje | Blog indexable | BLOCKED |
| Ene 23 | Doc tecnico Desempeno | Blog indexable | BLOCKED |
| Ene 30 | Doc tecnico Diagnostico | Blog indexable | BLOCKED |
| Feb 6 | Actualizar About UBITS | Pagina indexable | OK (paginas principales SI indexan) |
| Feb 13 | FAQs generales UBITS | Schema ready | OK |
| Feb 20 | FAQs por modulo con schema | Schema ready | OK |
| Feb 27 | Implementar Organization + BreadcrumbList schema | Acceso Webflow | OK |
| Mar 6 | SoftwareApplication schema Aprendizaje | Acceso Webflow | OK |
| Mar 13 | SoftwareApplication schema Desempeno + Diagnostico | Acceso Webflow | OK |
| Mar 20 | Contenido educativo LMS/comparativas | Blog indexable | BLOCKED |
| Mar 27 | Descargables actualizados + changelog | Paginas indexables | BLOCKED parcial |

**5 de 11 acciones estan BLOCKED** hasta que se resuelva la indexabilidad del blog.

### Schema JSON-LD actual vs planificado

| Schema | Planificado (Calendario LLM) | Estado actual en sitio |
|--------|-------|---------|
| Organization | Feb 27 | YA EXISTE (pero con URL www — necesita fix) |
| BreadcrumbList | Feb 27 | No implementado |
| SoftwareApplication | Mar 6-13 | No implementado |
| FAQPage | Feb 20 | No implementado |
| Article (blogs) | Implicito | No implementado |

---

## 5. Golden Keywords — Progreso historico vs estado actual

### Keywords que MEJORARON (pre-colapso medicion, Q2 2024)

| Keyword | Posicion antes | Posicion despues | Impresiones antes → despues |
|---------|---------------:|------------------:|---------------------------:|
| Cultura de aprendizaje | 5 | **1** | 401 → 1,092 |
| capacitacion virtual | 25 | **7** | 509 → 1,911 |
| Universidad corporativa | 17 | **7** | 5 → 2,469 |
| capacitacion empresarial | 13 | **10** | 404 → 1,361 |
| LMS | 33 | **16** | 284 → 4,433 |
| Desarrollo de competencias | 100+ | **11** | 0 → 627 |

### Keywords que RETROCEDIERON

| Keyword | Posicion antes | Posicion despues |
|---------|---------------:|------------------:|
| Capacitacion laboral | 21 | 66 |
| Capacitacion de empleados | 48 | 44 |

### Estado actual (post-migracion, GSC 12 meses)

Muchas de estas keywords que estaban mejorando probablemente perdieron posiciones despues de la migracion www→sin-www de septiembre 2025. El progreso de Q2 2024 se perdio parcialmente. Con el sitemap corregido y el blog re-indexado, deberian recuperarse.

---

## 6. Descargables — Cruce con funnel de conversion

### 28 descargables planificados vs paginas de captura

| Descargable | Prioridad JF | Pagina de captura existe? | Funnel a demo? |
|-------------|-------------|--------------------------|----------------|
| Plantilla FODA para RRHH | Alta | /descargables/ (generico) | No directo |
| Plan de accion | Alta | /descargables/como-construir-tu-plan-de-accion | Si — captura email |
| DNC (diagnostico necesidades) | Alta | No encontrada | No |
| Guia feedback | Alta | /descargables/como-preparar-un-feedback | Si |
| Plantilla SMART | Alta | No encontrada | No |
| Encuesta satisfaccion laboral | Alta | No encontrada | No — gap Clima |

**Hallazgo:** La pagina `/recursos-descargables-para-rrhh` tiene 0 H2 (confirmado en h2_all.csv) y esta indexada. Es la puerta de entrada a los lead magnets pero sin estructura de contenido.

### Cruce con GA4 conversion data

La pagina `/becas-ia-para-recursos-humanos-google` convierte al 50.84% — es basicamente un "descargable" (beca gratuita a cambio de lead). Los 28 descargables de JF deberian seguir este mismo patron: valor gratuito → captura email → nurture → demo.

---

## 7. Pipeline completo: De keyword a demo

Cruzando todo, el pipeline planificado por JF es:

```
Keyword Research (17 golden + expansion por modulo)
    ↓
Blog Content (60+/semestre, 3/semana)
    ↓
Social Distribution (Instagram + LinkedIn images por blog)
    ↓
Descargables (28 lead magnets con email capture)
    ↓
Lead Scoring Email → Prospect Email → Demo
    ↓
HubSpot CRM
```

### Donde se rompe el pipeline HOY

```
Keyword Research (17 golden + expansion)     ✓ HECHO
    ↓
Blog Content (21 escritos, 60+ planificados) ✓ HECHO
    ↓
Webflow Publication                          ✓ PUBLICADOS
    ↓
Google Indexation                            ✗ ROTO — blogs canonicalizados
    ↓
[Google nunca ve el contenido]
    ↓
0 trafico organico a blogs nuevos
    ↓
0 leads de contenido
    ↓
Solo brand traffic (94%) llega al sitio
    ↓
98.5% abandona el form
    ↓
310 demos/ano (de trafico directo/email, no organico)
```

---

## 8. Recomendaciones basadas en el cruce

### P0 — Desbloquear lo que ya existe (impacto inmediato)

| Accion | Por que | Tiempo |
|--------|---------|--------|
| Fix canonical blog en Webflow CMS | 21 blogs escritos + 37 legacy = 58 posts invisibles | 30 min |
| Agregar propiedad ubits.com en GSC | Sin esto no medimos nada | 5 min |
| Verificar que los 21 blogs de JF estan publicados (no draft) | Puede que algunos esten en draft | 15 min |

### P1 — Llenar gaps de contenido (semana 1-2)

| Accion | Por que | Impacto estimado |
|--------|---------|-----------------|
| Crear 3-5 blogs Clima/Encuestas | 0 contenido para modulo con 4,342 impresiones (enps) | Alto — keyword en posicion 14 |
| Blog dedicado "planes de sucesion" | Posicion 6.8, casi pagina 1 | Medio — quick win |
| Reducir duplicacion Tareas (4 blogs → consolidar) | Canibalizacion interna | Medio |

### P2 — Ejecutar calendario LLM (semana 2-3)

| Accion | Del calendario LLM | Prerequisito |
|--------|--------------------|----|
| Schema Organization (fix URL www→sin-www) | Feb 27 planificado | Acceso Webflow |
| Schema SoftwareApplication por modulo | Mar 6-13 planificado | Acceso Webflow |
| FAQs con schema por modulo | Feb 20 planificado | Copy en plan tactico ya existe |

### P3 — Descargables como conversion engine (post-relaunch)

| Accion | Template | Modelo |
|--------|---------|--------|
| Replicar modelo /becas-ia (50.84% conversion) | Landing dedicada + email capture | Para los 9 descargables "Alta" prioridad |
| Estructurar /recursos-descargables con H2 y categorias | Pagina indexada pero sin estructura | Mejora CTR interno |

---

## 9. Mapa spider: Como se conecta TODO

```
                    ESTRATEGIA JF
                    (docs/SEO/)
                        │
        ┌───────────────┼───────────────┐
        ▼               ▼               ▼
   21 BLOGS         GOLDEN KW       CALENDARIO LLM
   (content)        (targeting)     (AI optimization)
        │               │               │
        ▼               ▼               ▼
   PUBLICADOS      GSC TRACKING    SCHEMA MARKUP
   en Webflow      (pre-collapse    (no implementado)
        │            wins: LMS         │
        ▼            pos 33→16)        │
   CANONICALIZADOS     │               │
   (INVISIBLES)        ▼               │
        │          SITEMAP FIX      ◄──┘
        │          (RESUELTO)
        ▼               │
   FIX CANONICAL ◄──────┘
   (PENDIENTE)
        │
        ▼
   58 BLOGS VISIBLES
   EN GOOGLE
        │
        ▼
   TRAFICO ORGANICO      DESCARGABLES (28)
   (estimado: +5,000          │
    clicks/mes)               ▼
        │              LEAD CAPTURE
        └──────┬───────┘
               ▼
          DEMO FUNNEL
          (hoy: 98.5% abandon)
               │
               ▼
          GA4 TRACKING
          (GTM-5M96L5KF limpio)
               │
               ▼
          HUBSPOT CRM
```

---

## 10. Datos fuente

| Fuente | Ubicacion | Que contiene |
|--------|-----------|-------------|
| Estrategia SEO JF | docs/SEO/ | 21 blogs, calendarios, keywords, descargables |
| Screaming Frog crawl | docs/seo_auditoria/ | 7 CSVs: issues, indexability, H1, H2, titles, metas |
| GSC Performance | data/raw/gsc/2026-04-16/ | 12 meses performance + indexation |
| GSC Coverage | docs/seo_auditoria/https___www.ubits.com_-Coverage-*/ | Desglose 752 no indexadas |
| GA4 Snapshot | data/raw/ga4/2026-04-15/ | 26 archivos raw |
| Super Informe | reports/2026-04-16-seo-technical-audit-consolidated.md | Cruce tecnico completo |
| DataLayer Spec | docs/v2/datalayer-spec.json | 32 eventos, GTM-5M96L5KF |
| GTM Config Guide | docs/v2/22_gtm_triggers_variables_config.md | Triggers, variables, tags |
