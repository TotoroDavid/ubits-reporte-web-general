---
type: audit
area: organico
tags: [seo, auditoria-tecnica, ga4, gsc, relanzamiento, master, juan-felipe]
captured_date: 2026-04-16
author: David Toro
---

# 🚀 Auditoría Técnica SEO & Analítica: Reporte Consolidado de Crecimiento (Super Informe)

> **Resumen Ejecutivo:** Este reporte consolida la evidencia de 7 archivos CSV (Screaming Frog), 26 exportaciones de GA4, 9,896 consultas de Google Search Console, y las inspecciones de GTM. El objetivo es proporcionar a VPs y stakeholders (Juan Felipe) la fotografía completa del "circuito roto" que frena nuestro crecimiento y el plan exacto para llevar la plataforma comercial de 310 demos/año a niveles óptimos de captación B2B.

---

## CORRECCION CRITICA: "Falso Colapso" — Ceguera de medicion, no caida real de trafico

> **CORRECCION (2026-04-16, analisis de codigo fuente + Antigravity):** El "colapso del 99.9%" que veiamos en GSC era un **artefacto de medicion**, no una caida real de trafico. Alrededor del 20 de septiembre de 2025, el sitio migro de `www.ubits.com` a `ubits.com` (sin www). **Nadie agrego la nueva propiedad sin-www en Google Search Console.** El equipo ha estado mirando una propiedad vacia (`https://www.ubits.com/`) durante 7 meses — que solo muestra 301 redirects porque todo se va al dominio sin www.

### Que paso realmente

1. **~Sep 20, 2025:** El sitio migro de `www.ubits.com` a `ubits.com` (sin www)
2. **Nadie agrego la nueva propiedad** sin-www en Google Search Console
3. **7 meses mirando la propiedad vacia:** El equipo (herramientasmarketing@ubits.co) ha estado viendo data de `www.ubits.com` — que solo devuelve 301 redirects (100% confirmado en crawl stats)
4. **El trafico probablemente SIGUE VIVO** en `ubits.com` — pero GSC no lo mide porque la propiedad no esta configurada

### Evidencia

| Dato | Fuente | Que demuestra |
|------|--------|---------------|
| 100% de crawls a www devuelven 301 | GSC Crawl Stats (2026-04-14) | www es cascaron vacio |
| www: 752 no indexadas, 4 indexadas | GSC Coverage www | Solo redirects |
| sin-www: 243 no indexadas | GSC Coverage ubits.com | Numeros mas realistas |
| GA4: 519K usuarios/año | GA4 anual snapshot | GA4 SI mide el sitio real (sin www) |
| "ubits" 342K clicks pre-sept, 107 post | GSC Performance (dominio) | La propiedad de dominio hereda el problema de medicion |

### El "Sitemap Envenenado" (El 4to Zombie)

Se descubrió que el archivo `sitemap.xml` actualizado el 2025-07-02 **sigue ordenando a Google indexar explícitamente todas las URLs con `www.ubits.com`**. 
Esto ha creado un "Bucle Mortal" para Google desde septiembre:
1. El Sitemap le grita a Google: *"¡Debes indexar `https://www.ubits.com/blog`!"*
2. Googlebot va a esa URL para hacerle caso. 
3. El servidor le responde con un *301 Redirect*: *"Aquí no hay nada, estamos en `ubits.com/blog`"*.
4. Google se confunde totalmente y marca el sitio completo como **"Error: Página con Redirección"**. Por ende no indexa nada. El mismo mapa web activo es el arma que sabotea el rastreo.

### Los 4 "zombies" del sitio (3 en codigo + 1 en sitemap)

Analisis del `<head>` de ubits.com en produccion:

```
ACTIVO:
  GTM-5C9SS9Q                    ← Google Tag Manager (funciona)
  HubSpot 3296735                ← Tracker (vivo, pesado)
  Leadfeeder YEgkB8lx0xy8ep3Z   ← Tracker (vivo, pesado)
  ActiveCampaign 611871346       ← Tracker (vivo, pesado)

ZOMBIE (muerto pero presente):
  UA-233753207-1                 ← Universal Analytics (MUERTO desde julio 2023)
  gtag("click_boton_demo")       ← Envia a UA muerto — NO REGISTRA NADA
```

**Impacto:** 5 scripts cargando en paralelo (GTM + UA zombie + Leadfeeder + HubSpot + ActiveCampaign) destrozan Core Web Vitals. El boton de demo envia eventos a Universal Analytics muerto — los clicks no se registran en ningun sistema.

### Acciones inmediatas

| Accion | Tiempo | Impacto |
|--------|--------|---------|
| **Agregar propiedad `ubits.com` en GSC** | 5 min | Recupera 7 meses de visibilidad perdida |
| **Corregir sitemap.xml** (quitar www de todas las URLs) | 5 min | Elimina las 521 "Paginas con redireccion". Webflow lo regenera al publicar V2 |
| **Borrar `gtag('config', 'UA-233753207-1')`** del Custom Code | 5 min | Elimina script zombie |
| **Migrar `click_boton_demo` a DataLayer + GTM** | 30 min | Demo clicks se registran en GA4 |
| **Auditar si Leadfeeder/ActiveCampaign siguen en uso** | 1h | Potencial mejora CWV si se eliminan |

**Acceso GSC:** herramientasmarketing@ubits.co (Propietario), jsanchez@ubits.co (Completo)

**Dato fuente:** [data/raw/gsc/2026-04-16/gsc-performance-analysis.md](../data/raw/gsc/2026-04-16/gsc-performance-analysis.md)

---

## CORRECCION: Indexacion real (GSC en vivo, 2026-04-16)

> Solo **4 paginas indexadas** de 756 que Google conoce. Las 752 restantes no estan en el indice.

| Fuente | Paginas "indexables" | Paginas realmente indexadas |
|--------|--------------------:|----------------------------:|
| Screaming Frog (tecnico) | 42 | — |
| **Google Search Console (real)** | — | **4** |
| Paginas que Google conoce pero NO indexa | — | **752** |

**Lectura:** Screaming Frog mide si hay blockers tecnicos. GSC mide si Google DECIDIO indexar. La diferencia (42 vs 4) significa que Google ve el sitio pero lo considera de baja calidad/relevancia para 38 paginas adicionales. Los canonicals rotos, H1 duplicados, contenido bajo y estructura plana causan que Google descarte paginas que tecnicamente podria indexar.

### Desglose Oficial de GSC: Las 752 páginas rechazadas
Cruzando con la exportación `Problemas críticos.csv` descargada de Google Search Console:

| Motivo de exclusión en Google | Páginas | % (de 752) | Diagnóstico Growth |
|-------------------------------|--------:|----------:|--------------------|
| **Página con redirección** | **521** | 69% | Basura histórica, cadenas de redirects mal hechas al pasar de V1 a V2. |
| **Bloqueada por robots.txt** | **102** | 14% | *¡Alerta grave!* SFrog vió 5, pero Google rebotó en 102. Bloqueo masivo intencional. |
| **Rastreada: sin indexar** | **84** | 11% | Thin content. Google la leyó pero dictaminó que es contenido basura/delgado. |
| **No se ha encontrado (404)** | **14** | 2% | 14 páginas rotas. Google sigue intentando visitarlas por links históricos. |
| **Excluida por noindex** | **13** | 2% | Noindex explicito. Revisar si intencionado (jobs, drafts) o error. |
| **Canonica adecuada (alt.)** | **12** | 2% | OK — correctamente apuntando a versión canonica principal. |
| **Descubierta: sin indexar aún** | **5** | <1% | En cola de rastreo de Google — no urgente. |
| **Duplicada: sin canonical** | **1** | <1% | Resolver: agregar su propio tag canonical. |

**Advertencia adicional:** 1 pagina esta indexada PESE a estar bloqueada por robots.txt. Google la considero importante y la indexo de todas formas.

### Cruce profundo: GSC + Screaming Frog + Indexability

**1. Las 521 redirecciones = migracion V1→V2 + www→non-www**
El drilldown de Coverage muestra que la mayoria son URLs de `/blog/`, `/contenidos/`, `/casos-de-exito/`, `/industrias/` y `/speakers-skilled-*`. El subdominio `www.ubits.com/` aporta 65 URLs non-indexable (100%). La tendencia es positiva: bajo de 706 en enero a 521 en abril (limpieza en progreso). **Accion:** Forzar 301 consolidado www→non-www en Webflow Hosting. Las URLs de `/contenidos/` que redireccionan a `/blog/` son correctas — solo limpiar las cadenas rotas.

**2. Las 102 "bloqueadas por robots.txt" = parametros HubSpot, NO contenido real**
El drilldown revela que las 102 URLs son variantes con parametros `__hstc`, `__hssc`, `__hsfp` de HubSpot y UTMs de campanas. Las URLs base unicas bloqueadas son ~25-30. El robots.txt probablemente tiene una regla que bloquea query parameters. **Accion:** Esto NO es tan critico como pensabamos — no es contenido real bloqueado. Verificar robots.txt pero la prioridad baja de P0 a P2.

**3. Las 84 "rastreadas sin indexar" = problema de calidad confirmado**
Cruzando con `issues_overview_report.csv`: 15 paginas con thin content (<200 palabras), 20 con multiples H1, 16 meta descriptions truncadas, 4 sin H1. Google ve estas senales y decide que la pagina no merece estar en el indice. **Accion:** Mejorar contenido, fijar H1, escribir meta descriptions. Este es el bucket que mas impacta la indexacion real.

### Los 3 buckets accionables (prioridad corregida)

**Bucket 1: Calidad de 84 paginas rechazadas — FIX DE MAYOR IMPACTO**
Son las paginas que Google ya rastrea pero rechaza. Mejorar H1, contenido, metas = conversion directa a paginas indexadas. Impacto: potencialmente +84 paginas indexadas.

**Bucket 2: 521 redirecciones — CONSOLIDAR**
Forzar www→non-www definitivo. Limpiar cadenas de redirect. La tendencia ya es positiva (706→521). Impacto: libera crawl budget.

**Bucket 3: 404s + noindex (27 paginas) — LIMPIEZA**
14 paginas rotas + 13 con noindex. Redirect 301 las 404, verificar si los 13 noindex son intencionales.

---

## El Insight Central: "El Circuito Roto"

Cruzando la visibilidad tecnica en Google con la fuga de usuarios en sitio, hemos mapeado por que los Leads cualificados no estan llegando y por que perdimos capacidad de reaccion:

1. **Top of Funnel (Search):** Generamos **52,200 impresiones recientes** (+14%) — Google nos muestra...
2. **Pero nadie clickea:** Solo **54 clicks** (-17% tendencia). **94% de las queries son brand** ("ubits", "ubit").
3. **El Cuello de Botella Real:** Google conoce 756 URLs pero **solo indexa 4**. El 99.5% del sitio es invisible.
4. **Las 4 paginas indexadas:**
   - `ubits.com/` (homepage) — 28 clicks, +211%
   - `ubits.com/comunidad-de-aprendizaje` — 25 clicks, -51%
   - 1 blog post con 1 click
   - 1 pagina adicional
5. **Friccion de Conversion:** De lo poco que llega, **21,000 abren el formulario** de demo/año...
6. **Abandono Masivo:** ...pero el **98.5% abandona** el formulario.
7. **Bottom of Funnel Real:** Solo **310 demos exitosas/año**.
8. **Ceguera de Datos:** Tracking GA4 roto desde abril → **0 data para optimizar**.

### Datos GSC en vivo (capturados 2026-04-16)

| Metrica | Valor | Tendencia |
|---------|-------|-----------|
| Paginas indexadas | **4** | Estable |
| Paginas NO indexadas | **752** | — |
| Clicks recientes | 54 | -17% |
| Impresiones recientes | 52,200 | +14% |
| Trafico brand | **94%** | — |
| Trafico generico | **6%** | — |
| Core Web Vitals | Sin datos | Google no tiene suficiente muestra |
| HTTPS | 2 paginas OK, 0 no-HTTPS | — |

### Queries (100% brand)

| Query | Clicks | Tendencia |
|-------|-------:|-----------|
| ubits | 29 | +61% |
| ubit / ubits login / ubits ingresar | 11 | -45% |
| ubits cursos | 3 | Nuevo |
| certificado ubits | 1 | Nuevo |
| ubis | 1 | Nuevo |

### Contenido en caida

| Pagina | Clicks | Cambio |
|--------|-------:|--------|
| `/comunidad-de-aprendizaje` | — | **-51% (-26 clicks)** |
| `/blog/integracion-ia-capacitacion-empresarial` | — | **-100% (-3 clicks)** |

### Alerta GSC

> "Recientemente, una consulta ha recibido menos impresiones de lo habitual: **ubits learning** -76%"

Esto puede indicar que Google esta perdiendo confianza en el sitio como resultado autoritativo para la propia marca.

---

## 1. Inventario del Crawl (Screaming Frog 2026-04-15)

Se rasteo la arquitectura tecnica subyacente de la web.

- **Total paginas creadas en Webflow CMS**: 174
- **URLs que Google conoce**: 756 (muchas mas de las que el crawler encontro navegando)
- **URLs HTML descubiertas navegando**: 85 (Cerca de 90 paginas son "Huerfanas").
- **Indexables tecnicamente (sin blockers)**: 42 de 177 variaciones URL (24%)
- **REALMENTE indexadas por Google**: **solo 4** (0.5% del total que Google conoce)
- **Bloqueo Critico:** El **Blog entero (37 articulos estructurados)** tiene directivas No-index (canonicalizados), lo que supone 0 presencia organica de nuestra estrategia de contenido educativo.

## 2. Issues Técnicos por Prioridad (Top 10)
Con base en los reportes exportados:

| N.º | Prioridad | Problema Técnico | Volumen Afectado | Impacto en Growth |
|----|----------|-------------------|-------------------|---------|
| 1 | **ALTA** | URLs sin Canonical o Mal Asignadas | 64 URLs | Divide/destruye nuestra autoridad frente a Google. |
| 2 | **ALTA** | Directiva "Noindex" | 1 URL y Blog entero | Bloqueo absoluto de tráfico orgánico en esas rutas. |
| 3 | **ALTA** | Bloqueo en Robots.txt (Internal) | 5 URLs | Rastreadores rebotan intentando explorar el sitio. |
| 4 | **ALTA** | Sin enlaces de salida interna (Dead end) | 6 URLs | El usuario entra y no tiene cómo seguir navegando (Fuga). |
| 5 | **MEDIA** | H1 Múltiples o Ausentes | 24 URLs | Destroza la optimización para motores de Inteligencia Artificial (GEO/AEO). |
| 6 | **MEDIA** | Imágenes gigantescas (>100kb) | 85 imágenes | Ralentiza la página bajando el Score de Core Web Vitals. |
| 7 | **MEDIA** | Page Titles repetidos / largos | +25 URLs | Baja la tasa de clics (CTR) en las páginas de resultados. |
| 8 | **BAJA** | Falta Alt-text en imágenes | 178 imágenes | Perdida total del tráfico orgánico proveniente de Image Search. |
| 9 | **BAJA** | H2 duplicados / faltantes | 26 URLs | Mala jerarquización visual y semántica. |
| 10 | **BAJA** | Seguridad: Falta Referrer Policy | 85 URLs | Puntos menos en validaciones de seguridad de dominios corporativos B2B. |

## 3. Estado de Jerarquías de Contenido (Headings H1 / H2)
Para responder y posicionar bajo modelos de IA (ChatGPT, Gemini, Perplexity), UBITS requiere arquitecturas estrictas.
- Puntos ciegos: Varias de nuestras "landing page bandera" como `/modulos/reclutamiento` no tienen un atributo `H1` (Heading Master).
- El motor se confunde leyendo 2 y hasta 3 mensajes principales por página en lugar de una promesa de valor jerárquica clara.

## 4. Estado de Meta-Data (Titles & Descriptions)
Encontramos 16 descripciones "kilométricas" (>985 px) que Google está truncando; 6 URLs clave y dinámicas que carecen de metas, lo que causa que Google indexe trozos de código o texto basura del footer en los resultados B2B.

## 5. Google Search Console: Long-Tail y Nubes B2B (9,896 queries)
El cruce GSC vs Tráfico confirma que dominamos marca pura, pero desaprovechamos volumen bruto en la industria B2B de Hispanoamérica.
- **Top Oportunidades Long-Tail:** "LMS" (18,940 impr.), "competencias laborales" (10,868 impr.), "capacitación" (8,212 impr.), "enps" (4,342).
- **El Everest de UBITS:** El término "Habilidades blandas" genera **185K impresiones al año**, pero por falta de indexabilidad técnica, vegetamos en la posición #10.

## 6. Cruce Técnico + Analítico (GA4)
Lo descubierto en GA4 se explica ahora mediante el Screaming Frog Audit:
* La URL `/ubits-para-tu-empresa` tiene un triste **CTR del 0.23%**. ¿La causa? Revisando el CSV de Metadata, tiene el Title equivocado.
* `/becas-ia-google` convierte súper bien **(50.84%)**, pero las URLs convencionales de los módulos como `/modulos/aprendizaje` apenas en **0.69%**. Las caídas responden a UX pobre (imágenes de 100kb) y canibalización (existen `/modulos/X` + `/modulo-X` + `/modulo-de-X`).

## 7. Estado de Tag Management (GTM y Analítica)
* **Status:** ROTO post-abril. Las metas se cumplen localmente pero el puente hacia Google Ads está destrozado o sin configuración V2.
* **Consent Mode V2:** Ausente (riesgo de -30% data publicitaria).
* **Ausencia de Tracking de Micro-conversiones:** Requerimos el Sub-sistema A de Webflow Data Layer. Universal Analytics (Tag descontinuado) sigue ensombreciendo el DOM.

---

## 8. 📅 Plan de Acción Priorizado (22 Acciones por Semana)

### Prioridad Cero (P0): Regla de Negocio
> **🚨 La campaña "Clima y Cultura" y todo esfuerzo PAGO queda BLOCKED hasta que el Blog sea indexable.** Enviar prospectos sin base orgánica es quemar presupuesto.

| Semana | Acción | Área | Responsable |
|--------|---------|------|-------------|
| **S1** | Quitar el tag Noindex de la base del Blog | SEO Técnico | Growth Web Admin |
| **S1** | Archivar o Eliminar las 90 páginas huérfanas en CMS | Arquitectura | Growth Web Admin |
| **S1** | Reestructurar Canonicals de las 64 páginas top | SEO Técnico | Growth Web Admin |
| **S1** | Habilitar Consent Mode V2 en contenedor GTM-5C9SS9Q | Analítica | Ops / Tracking |
| **S1** | Eliminar y purgar código hardcodeado UA-233753207-1 | Código | Frontend |
| **S2** | Implementación del Subscript de Listener (GTM Webflow) | Analítica | Ops / Tracking |
| **S2** | Inyección de H1 Core en `/modulos/reclutamiento` y Home | On-Page | Growth Content |
| **S2** | Reparación de los "Múltiples H1" (20 landings clave) | On-Page | Growth Content |
| **S2** | Configuración LinkedIn Insight Tag (Retargeting) | Pauta B2B | Marketing Ops |
| **S2** | Optimizar las 85 imágenes >100kb y forzar formato WebP | Performance | Frontend |
| **S3** | Integración del Passback Offline de Demos desde HubSpot | B2B CRM | Growth / Sales |
| **S3** | Reescritura masiva usando Gemini de los +178 Alt-text | On-Page | Growth Content |
| **S3** | Ajustar extensión de los +25 Title Tags y Meta-Descriptions | On-Page | Growth Content |
| **S3** | Refactorizar Menú/Footer para recuperar páginas valiosas | Arquitectura | Diseño |
| **S3** | Creación y despliegue del Schema B2B JSON-LD Orgánico | SEO Técnico | Especialista SEO |
| **S4** | Testing A/B de Simplificación de Formulario de Agendar Demo | CRO / Website | Ops |
| **S4** | Cargar URLs correctas 301 de la arquitectura de la Web V2 | Arquitectura | Ops |
| **S4** | QA final sobre el registro de Key Events en Google Analytics 4 | Analítica | Especialista Datos |
| **S4** | Deploy total de mejoras - RELANZAMIENTO Webflow Production | Deploy | Lead Web Admin |
| **S5** | Revisar primer reporte de "Micro-interacciones" en Dashboards | Analytics | Equipo Data |
| **S5** | Levantar bloqueo P0: Arrancar campaña "Clima y Cultura" | Paid Media | Demand Gen |
| **S5** | Check reintegro de Demos en Data-Loop publicitario (HubSpot>Ads) | CRM Ops | Ops / Sales | 

---

## 9. 📈 Tabla de KPIs (Baseline vs Target Relaunch)

| Metrica Clave Comercial | BASELINE (Anual Hoy) | Target Q1 Post-Relaunch (Extrapolado Anual) | Growth Factor |
|-------------------------|---------------------|--------------------------------------------|---------------|
| Demos Validados / Año   | **310 demos** | **2,600 demos** *(si mejoramos CTA/UX)* | **8.4x** |
| Impresiones Reales SEO | 4.87M | 8.5M *(Habilitando index del 76% oculto)* | + 74% |
| Tasa Indexabilidad | 24% | 98% (Clean architecture) | + 300% |
| Conversión Form Demo | 1.48% (21k intentan) | 6.5% B2B Standard | + 4.3x |
| Eventos Trackeados/Día | 0 (Roto Abril) | ~2,500 interacciones trazables DataLayer | Vuelve la Luz |

---

## 10. 🔗 Mapas de Archivos y Tareas Pendientes
- **Crawl Audit:** `docs/seo_auditoria/` (7 CSVs)
- **GA4 Raw 26 files:** `data/raw/ga4/2026-04-15/`
- **Índice Maestro de Tareas:** `reports/2026-04-15-INDEX-relanzamiento.md`
- **Track GTM Implementation:** `docs/v2/20_webflow_tracking_implementation.md`

> *La clave del relanzamiento no es un diseño vistoso, es reconectar los cables del motor de adquisición que hoy corta el 98.5% del potencial comercial de UBITS. — Growth Team, 16 de Abril 2026.*
