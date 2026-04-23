---
type: report
area: estrategia
tags: [brief, relanzamiento, juan, decision, baseline, 2026-abril]
related_areas: [analitica, website, organico, laboratorio-growth]
captured_date: 2026-04-15
author: David Toro
audience: Juan (stakeholder relanzamiento)
related_docs:
  - 2026-04-15-plan-tactico-relanzamiento.md
  - 2026-04-15-INDEX-relanzamiento.md
  - 2026-04-14-website-relaunch-decision-report.md
  - ../ops/10_laboratorio-growth/10_auditoria_ga4_abril2026.md
---

# Brief Ejecutivo — Relanzamiento Web UBITS · Fin Abril 2026

> **Para:** Juan · **De:** David (Growth Marketing)  
> **Fecha:** 2026-04-15 · **Deadline relanzamiento:** fin abril 2026  
> **Documento tactico:** [2026-04-15-plan-tactico-relanzamiento.md](2026-04-15-plan-tactico-relanzamiento.md)  
> **Data raw:** [data/raw/ga4/2026-04-15/](../data/raw/ga4/2026-04-15/) (26 archivos)

---

## Resumen ejecutivo (30 segundos)

**UBITS ha estado ciega 7 meses.** Cuando migraron de `www.ubits.com` a `ubits.com` (~septiembre 2025), nadie actualizo Google Search Console. El equipo ha estado mirando una propiedad vacia que solo muestra redirects — el trafico real probablemente sigue vivo pero sin medir. Ademas, el boton de demo envia eventos a Universal Analytics (muerto desde julio 2023) — los clicks no se registran en ningun sistema.

**5 problemas criticos que el relanzamiento debe resolver:**

1. **GSC desconfigurado 7 meses** — la propiedad `ubits.com` sin www nunca se agrego (fix: 5 minutos)
2. **Universal Analytics zombie** — `UA-233753207-1` hardcodeado, muerto desde 2023. El boton de demo no trackea
3. **Solo 4 paginas indexadas** en la propiedad www (la sin-www tiene 243 no indexadas, estado real pendiente)
4. **98.5% de form abandonment** (21K abren form → 310 completan)
5. **5 scripts pesados en el head** destruyen Core Web Vitals

**Recomendacion:** Reconstruir sobre el Webflow existente. Paso 0 urgente: agregar propiedad correcta en GSC + eliminar UA zombie + migrar evento demo a DataLayer.

---

## 📊 Baseline anual real (lo que tenemos hoy)

| Metrica | Valor anual | Benchmark B2B |
|---------|------------:|---------------|
| Usuarios activos | 519,000 | — |
| Usuarios nuevos | 483,000 (93%) | Sano |
| Sesiones | 1,269,980 | — |
| Tiempo medio/usuario | 40s | 60-180s (debajo) |
| Impresiones Google | **4,868,622** | — |
| Clicks Google | **527,441** | — |
| Posicion promedio SEO | 14.96 | P10 ideal |
| **Demos exitosos/año** | **310** (~26/mes) | 0.5-1% target |
| Newsletter signups/año | 703 | 1-3% target |
| Form demo abiertos | 21,000 | — |
| **Form completion rate** | **1.48%** | **30-50%** |

### El ICP corregido (por data real)

- **70% mujeres** (vs 30% hombres)
- **25-34 años** dominante
- **Spanish** 99%+
- **Mobile 90%** identificado
- **Chrome 73% + Edge 13%** (enterprise)
- **Colombia 29% + Mexico 23% + Ecuador 8%** = mercados core

---

## 🚨 Los 3 problemas criticos

### Problema #1: Tracking GA4 roto (P0 urgente)

**Evidencia:**

| Evento clave | Anual 2025-2026 | Abril 1-15 | Diagnostico |
|--------------|----------------:|-----------:|-------------|
| Abrir form demo | 21,000 | **0** | 🔴 Roto |
| Registro Newsletter | 703 | 14 | 🔴 Casi nulo |
| Registro Exitoso Form DEMO | 310 | **0** | 🔴 Roto |

**Hipotesis:** Un publish de Webflow en marzo/abril elimino el custom code del `<head>` o desconecto el trigger de GTM container `GTM-5C9SS9Q`. **Los demos siguen llegando a HubSpot, pero GA4 no los mide.**

**Accion P0:** Verificar GTM container antes del relanzamiento. Si se relanza sin tracking, estaremos ciegos al impacto.

### Problema #2: Form abandonment del 98.5%

**El funnel real:**

```
519,000 usuarios anuales
       ↓ 1.49% click CTA demo
  7,729 click boton demo
       ↓ (otros entran por otras vias)
  8,666 abren form demo (21,000 eventos total)
       ↓ 1.48% completa el form
    310 demos completados
```

**96.94% de la gente que ABRE el form, no lo completa.** Esto es el bottleneck real — no es trafico, es UX del formulario.

**Causas probables:**
- Formulario muy largo (6+ campos)
- Mobile UX pobre (90% es mobile)
- Sin value prop clara de que reciben
- Sin prueba social en el form
- Consent mode bloqueando submission

**Oportunidad:** Si bajamos abandonment del 98.5% al 70% (standard B2B), pasamos de 310 a **~2,600 demos/año** (8.4x).

### Problema #3: URLs duplicadas en TODOS los modulos

**Data anual de vistas:**

| Modulo | URL nueva `/modulos/X` | URL vieja `/modulo-X` | URL viejissima `/modulo-de-X` | Total | Key events |
|--------|-----------------------:|----------------------:|------------------------------:|------:|-----------:|
| Aprendizaje | 51,083 | 26,225 | 832 | 78,140 | 974 |
| Desempeno | 3,266 | 1,587 | — | 4,853 | 79 |
| Diagnostico | 1,682 | 944 | — | 2,626 | 125 |
| Reclutamiento | 1,765 | — | — | 1,765 | 0 |
| Tareas y Planes | 221 | — | — | 221 | 0 |
| Encuestas | **404** | — | — | 0 | 0 |

**Paradoja critica:** Las URLs viejas convierten MEJOR que las nuevas:
- `/modulo-aprendizaje`: 5.22% conversion
- `/modulos/aprendizaje`: 0.69% conversion
- `/modulo-de-aprendizaje`: **21.15% conversion** (viejissima)

**Causa:** Las URLs viejas reciben trafico de emails y campañas historicas con alto intent. Las nuevas reciben trafico organico "curioso".

---

## 🏆 Los 5 hallazgos mas accionables

### Hallazgo #1: `/becas-ia-para-recursos-humanos-google` convierte 50.84%

- 2,500 sesiones → **1,922 key events**
- Es la **pagina #1 de conversion** del sitio entero
- **10.4% de TODA la conversion anual** viene de esta pagina
- Formato: landing de beca/valor gratuito a cambio de lead

**Accion:** Replicar este formato para **2-3 verticales mas** (Harvard executive, Bancos, Educacion superior).

### Hallazgo #2: `/ubits-para-tu-empresa` es el diamante subutilizado

- **567,393 impresiones/año** (posicion 1.83 en Google — casi siempre TOP 1)
- Solo **1,322 clicks** (0.23% CTR)
- **9% bounce rate** = la MEJOR pagina de retencion del sitio
- Los que llegan, se quedan

**Accion:** Reescribir title tag + meta description. Si CTR sube a 10%, **+55,000 clicks/año**.

### Hallazgo #3: `/skilled` es un motor de conversion secundario

- 21,000 vistas anuales (#5 del sitio)
- **12.55% conversion rate** como landing
- **Contenido de febrero 2024** (2 años desactualizado)
- 2,325 key events/año (segunda fuente de conversion)

**Accion:** Actualizar contenido a temporada actual 2026 + conectar al funnel de demo.

### Hallazgo #4: Email convierte 16x mejor que Organic Search

| Canal | Sesiones | Conversion | Eficiencia |
|-------|---------:|-----------:|-----------|
| Email | 15,878 | **8.86%** | 🔥 |
| Organic Social | 8,766 | 6.51% | 🔥 |
| Direct | 186,056 | 1.14% | OK |
| **Organic Search** | **875,707** | **0.57%** | Bajo |

**Organic Search mueve el volumen pero no convierte.** Email es pequeño pero eficiente. Una campana decente de email es equivalente a 16 campañas de SEO en terminos de demos.

**Accion:** Activar email marketing con UTMs correctas. Infraestructura existe (una sola campaña funciona con UTM: `email / mkt-skilled-2025-segunda-temporada` con 4,900 sesiones).

### Hallazgo #5: Paid esta **completamente apagado**

- **93 usuarios de paid en 12 meses** (Paid Other 78 + Paid Search 9 + Paid Social 4 + Display 2)
- Cero campañas de Google Ads corriendo
- Credito $350 disponible sin usar
- 0 campañas LinkedIn Ads

**Accion:** Activar Google Ads post-relanzamiento con las keywords donde ya aparecemos en top 10 (para subir a top 3).

---

## 💡 La recomendacion: Opcion A (Rebuild sobre Webflow existente)

### Por que NO crear un proyecto nuevo

| Factor | Opcion A (Rebuild) | Opcion B (Nuevo + 301) |
|--------|--------------------|-----------------------|
| Riesgo SEO | **Cero** | 10-30% caida 2-8 semanas |
| Timeline fin de abril | **Factible** | Muy ajustado/riesgoso |
| Blogs preservados (327) | **Intactos** | Export/import manual con riesgo |
| Backlinks externos | **100%** | Depende de 301 perfectos |
| Integraciones (GTM, HubSpot) | **Intactas** | Re-configurar desde cero |
| Costo | 1 plan Webflow | 2 planes (transicion) |

### Por que reconstruir sobre lo existente

1. **UBITS ya esta en Webflow** — migrar de Webflow a Webflow no tiene sentido
2. **327 blogs indexados son equity SEO** — no se pueden mover sin riesgo
3. **4.87M impresiones/año estan atadas a las URLs actuales** — cambiar URLs = reset parcial
4. **Timeline apretado** — 2 semanas alcanza para rediseñar, no para migrar

### Excepcion: Si NO tenemos acceso al proyecto actual

Si el proyecto esta en cuenta de un proveedor externo sin acceso, entonces Opcion B es viable **pero**:
- Agregar 2-3 semanas al timeline
- **NO cambiar estructura de URLs** (`/modulos/X` debe seguir siendo `/modulos/X`)
- Configurar 327 redirects 301 ANTES del switch DNS
- Exportar CMS completo y validar import

---

## 💰 ROI estimado del relanzamiento

### Baseline (hoy): 310 demos/año

### Escenarios post-relanzamiento

| Escenario | Accion | Demos/año | Multiplicador |
|-----------|--------|----------:|--------------:|
| Sin cambios | Solo rediseño visual | 310 | 1x |
| Form abandonment 70% | Acortar formulario + mobile UX | 2,600 | **8.4x** |
| Form abandonment 50% + SEO CTR | + optimizar meta descriptions | 5,200 | **17x** |
| + Email reactivado | Campaña mensual con UTMs | 7,000 | **23x** |
| + Paid activado | Google Ads + LinkedIn | 12,000 | **39x** |

**Si solo arreglamos el form (menos UX de 5 campos a 3), el ROI es 8.4x sin aumentar trafico.**

---

## 🗓️ Plan de accion propuesto

### Semana 1 (Abr 15-18): Diagnostico y fix tracking

- [ ] Revisar GTM container `GTM-5C9SS9Q` — trigger `Abrir form demo`
- [ ] Verificar snippet GTM en `<head>` de Webflow
- [ ] Confirmar demos siguen llegando a HubSpot (aunque no se midan)
- [ ] Configurar key events oficiales en GA4
- [ ] Crear pagina `/modulos/encuestas` (hoy 404)

### Semana 2 (Abr 21-25): Contenido y SEO

- [ ] Rediseñar formulario de demo (reducir campos, mobile-first)
- [ ] Escribir FAQs unicas por cada modulo (hoy copy-paste)
- [ ] Implementar Schema JSON-LD por modulo
- [ ] Reescribir title + meta de `/ubits-para-tu-empresa`
- [ ] Actualizar `/skilled` con temporada 2026
- [ ] Definir URL canonica por modulo (vieja vs nueva)

### Semana 3 (Abr 28-30): QA y publicacion

- [ ] Configurar 301 redirects de URLs duplicadas
- [ ] QA en staging (6 modulos + homepage + paginas conversion)
- [ ] Publicar y verificar tracking en produccion
- [ ] Submit sitemap actualizado en Google Search Console

### Post-relanzamiento (mayo)

- [ ] Activar Google Ads con credito $350
- [ ] Reactivar email marketing con UTMs
- [ ] Snapshot GA4 post-relanzamiento (medir delta)
- [ ] Iterar sobre top 10 hallazgos

---

## 🔬 ADDENDUM 2026-04-16: Auditoria Tecnica SEO (Screaming Frog + GSC)

> Datos incorporados el 16 de abril tras completar crawl tecnico del sitio.

### Problema #4: El sitio es 99.5% invisible para Google

Google Search Console (verificado 2026-04-16) muestra que solo **4 paginas estan indexadas de 756 que Google conoce**. El desglose de las 752 no indexadas:

| Motivo (segun Google) | Paginas | Accion |
|------------------------|--------:|--------|
| **Pagina con redireccion** | **521** | www→non-www + URLs legacy. Limpieza de redirects |
| **Bloqueada por robots.txt** | **102** | CRITICO — robots.txt bloquea 102 paginas. Fix inmediato |
| **Rastreada pero rechazada por Google** | **84** | Google las vio y decidio que no valen. Mejorar calidad |
| **404 (paginas rotas)** | **14** | Redirect 301 a paginas relevantes |
| **Noindex explicito** | **13** | Verificar si intencionado |
| **Canonica adecuada + otros** | **18** | Normal |

**El fix con mayor impacto:** Corregir el robots.txt puede desbloquear 102 paginas de un solo cambio. Las 84 "rastreadas sin indexar" necesitan mejora de contenido individual.

### Problema #5: 90+ paginas huerfanas en Webflow

De las 174 paginas construidas en Webflow, solo 85 son alcanzables navegando el sitio. Las restantes ~90 son:
- Clones abandonados (`new-home`, `new-homee`, `inicioo`)
- Landings de eventos pasados (`summit-2023`, `navidad-descargas`)
- Borradores publicados accidentalmente
- Paginas de valor sin links internos (calculadoras, recursos)

**Accion:** Inventario completo → archivar basura, conectar paginas de valor al menu.

### Problema #6: Estructura de headings destruida

| Pagina | Problema |
|--------|---------|
| `/modulos/reclutamiento` | **Sin H1** — pagina de producto clave |
| Homepage | **6 H1s** — Google no sabe cual es el titulo |
| `/blog` listing | **47 H1s** — cada card es un H1 |
| `/skilled` | H1 de **391 caracteres** — parrafo, no titulo |
| 20 paginas | H1 multiples |
| 11 paginas | Sin H2 (sin estructura de secciones) |

### Problema #7: Performance web degradado

| Issue | Alcance | Impacto |
|-------|--------:|---------|
| Imagenes sin size attributes | 203 (95%) | CLS / Core Web Vitals penalizado |
| Imagenes sin alt text | 178 (83%) | SEO imagenes + accesibilidad |
| Imagenes > 100KB | 85 (40%) | LCP / page speed degradado |
| Links internos sin anchor text | 79 (93%) | Google no entiende interlinking |

### Keywords B2B con oportunidad real

El analisis de 9,896 queries de cola larga revela keywords product-fit que UBITS puede capturar:

| Keyword | Impresiones/año | Posicion | Accion |
|---------|----------------:|---------:|--------|
| `lms` | 18,940 | 14.5 | Incluir "LMS Corporativo" en H1 homepage |
| `competencias laborales` | 10,868 | 22.6 | Blog + link a /diagnostico |
| `capacitacion` | 8,212+ | 22.9 | Core keyword — toda la arquitectura |
| `enps` | 4,342 | 14.3 | Crear /modulos/encuestas (hoy 404) |
| `planes de sucesion` | 1,805 | 6.8 | A punto de pagina 1 |

### Problema #8: Tracking y Tags rotos/obsoletos

| Componente | Estado | Urgencia |
|------------|--------|----------|
| GTM Container `GTM-5C9SS9Q` | Snippet desconectado | P0 — sin medicion |
| Universal Analytics `UA-233753207-1` | Hardcodeado en produccion | Eliminar — obsoleto |
| Consent Mode V2 | No implementado | Riesgo 30% data loss para Ads |
| Micro-conversiones (cta_click, faq) | No existen | Ceguera ToFu/MoFu |
| DataLayer v1.0 spec | Lista, no implementada | Contiene 32 eventos |

---

## 💰 ROI estimado ACTUALIZADO del relanzamiento

### Baseline (hoy): 310 demos/año + 42 paginas indexables

### Escenarios post-relanzamiento (actualizados con audit tecnico)

| Escenario | Accion | Demos/año | Paginas indexables | Multiplicador |
|-----------|--------|----------:|-------------------:|--------------:|
| Sin cambios | Solo rediseño visual | 310 | 42 | 1x |
| **Fix SEO tecnico** | **Blog indexable + canonicals + H1** | **500** | **80+** | **1.6x** |
| + Form abandonment 70% | Acortar formulario + mobile UX | 2,600 | 80+ | **8.4x** |
| + SEO CTR optimizado | Meta descriptions + keywords B2B | 5,200 | 80+ | **17x** |
| + Email reactivado | Campaña mensual con UTMs | 7,000 | 80+ | **23x** |
| + Paid activado | Google Ads + LinkedIn | 12,000 | 80+ | **39x** |

**Nuevo insight:** Solo arreglar los problemas tecnicos de SEO (sin tocar el form) ya duplica las paginas indexables y deberia mover la aguja ~60% en demos organicos.

---

## 🔍 Preguntas para Juan (decisiones pendientes)

1. **Tenemos acceso directo al Webflow project?** — si no, cambia la recomendacion
2. **Quien tiene acceso a GTM `GTM-5C9SS9Q`?** — necesito diagnostico de trigger roto
3. **Hay backlog de cambios de marca/visual ya decidido?** — o el relanzamiento es solo tecnico?
4. **Hay presupuesto adicional para Google Ads/LinkedIn Ads?** — el $350 es credito inicial
5. **Quien decide URLs canonicas?** — tiene que alinearse con SEO team (si existe)
6. **NEW: Quien publico en Webflow en marzo/abril?** — necesitamos saber que publish elimino el GTM snippet
7. **NEW: Existe script de Universal Analytics `UA-233753207-1` que debamos preservar por algun dashboard viejo?** — o lo eliminamos

---

## 📎 Documentos de referencia (consolidado 2026-04-16)

### Para Juan (Decision)
- [Este brief (actualizado 2026-04-16)](2026-04-15-brief-ejecutivo-juan.md) — resumen ejecutivo + ROI
- [Decision rebuild vs nuevo (2026-04-14)](2026-04-14-website-relaunch-decision-report.md) — justificacion Webflow

### Para ejecucion
- [Plan tactico del relanzamiento](2026-04-15-plan-tactico-relanzamiento.md) — copy, redirects, configs
- [Indice maestro del relanzamiento](2026-04-15-INDEX-relanzamiento.md) — navegacion rapida (18 hallazgos)
- [Plan accion maestro SEO + Analytics](../docs/v2/21_master_seo_analytics_action_plan.md) — hoja de ruta 3 fases
- **[Audit SEO tecnico consolidado](2026-04-16-seo-technical-audit-consolidated.md)** — crawl cruzado con GA4 + GSC (22 acciones)

### Analisis
- [Auditoria GA4 v3.0](../ops/10_laboratorio-growth/10_auditoria_ga4_abril2026.md) — tracking, canales, conversion
- [Long-tail SEO forense](2026-04-15-long-tail-seo-analysis.md) — 9,896 queries, trafico B2C contaminado
- [Analisis integrado SEO + arquitectura](../ops/11_website/02_analisis-integrado-seo.md) — hallazgos 2026-04-13
- [Hallazgo /skilled](../ops/11_website/03_pagina-skilled-hallazgo.md)

### Data raw
- [Snapshot metadata GA4](../data/raw/ga4/2026-04-15/snapshot-metadata.md) — 26 archivos raw
- [Crawl data Screaming Frog](../docs/seo_auditoria/) — 7 CSVs (indexability, issues, H1, H2, titles, metas, GSC)
- [DataLayer spec v1.0](../docs/v2/datalayer-spec.json) — 32 eventos definidos
- [GTM tracking plan](../docs/v2/16_gtm_analytics_tracking_plan.md) — arquitectura de medicion
- [Webflow tracking implementation](../docs/v2/20_webflow_tracking_implementation.md) — scripts de implementacion

### Producto y estrategia
- [Contexto completo 6 modulos + Intranalytics](../ops/01_identidad-ubits/modulos-contexto-completo.md)
- [Argumentario "Maria" HR](../ops/09_sales-enablement/argumentario-modulos-rrhh.md)
- [10 principios GEO](../ops/07_organico/geo-estrategia.md)

---

*Brief generado 2026-04-15, actualizado 2026-04-16 con audit tecnico SEO (Screaming Frog + GSC long-tail). Toda la data es verificable con fuentes raw.*
