---
type: report
area: website
tags: ['relanzamiento', 'decision', 'v2']
related:
  - 2026-04-15-INDEX-relanzamiento.md
captured_date: 2026-04-15
---

# Reporte de Decision: Relanzamiento Website UBITS
## Proyecto Existente vs Proyecto Nuevo en Webflow

> **Para:** Juan · **De:** David (Growth Marketing) · **Fecha:** 2026-04-14
> **Deadline:** Fin de abril 2026
> **Fuentes:** Audit interno del sitio actual, 15+ articulos especializados en migracion Webflow/SEO (2025-2026), documentacion oficial Webflow, Reddit r/webflow, mejores practicas B2B SaaS redesign

---

## Resumen Ejecutivo

Hay dos caminos para el relanzamiento. Despues de investigar a fondo, **la recomendacion es Opcion A (reconstruir sobre el proyecto existente)** por una razon dominante: **cero riesgo SEO y cero downtime**. La Opcion B (proyecto nuevo + migracion de dominio) introduce riesgos reales de perdida de trafico que no se justifican dado que ya estamos en Webflow.

---

## El Estado Actual del Sitio

Antes de decidir, es importante que Juan tenga la radiografia real:

| Metrica | Valor |
|---------|-------|
| URLs en sitemap | 340 (327 blogs + 13 core pages) |
| Blog posts indexados | 243 URLs mapeadas |
| Modulos con pagina activa | 5 de 6 (Encuestas devuelve 404) |
| Ultimo `lastmod` del sitemap | **2025-07-02** (9 meses sin actualizar) |
| FAQs | Copy-paste identico en 3 modulos (Aprendizaje, Desempeno, Diagnostico) |
| Metricas en paginas de modulo | Las mismas 3 metricas (93%/71%/82%) repetidas en todos los modulos |
| Homepage | Dice "4 modulos" pero muestra 6 tabs |
| Testimonios | Solo 2 (Sodimac + Alsea) repetidos en todos los modulos; Mercado Libre solo en homepage |
| Reclutamiento | Recientemente rediseñado (ya no dice "Proximamente") |
| Schema/datos estructurados | No implementados |

**Conclusion:** El sitio necesita un relanzamiento, pero los problemas son de **contenido y estructura**, no de plataforma. Webflow funciona bien tecnicamente.

---

## Opcion A: Reconstruir sobre el Proyecto Webflow Existente

### Como funciona
Se trabaja directamente en el proyecto actual de Webflow. Se rediseñan las paginas, se corrige el contenido, se agregan las que faltan (Encuestas, /ia), y se publica. El dominio ubits.com no se toca.

### Pros

| Pro | Detalle |
|-----|---------|
| **Cero riesgo SEO** | Las URLs existentes no cambian. Google no necesita re-indexar nada. No hay periodo de "sandbox" ni caida de rankings. |
| **Sin migracion de dominio** | No hay 48h de propagacion DNS, no hay riesgo de downtime, no hay certificado SSL que re-configurar. |
| **Historial CMS intacto** | Los 327 blog posts en CMS se mantienen con sus URLs, sus fechas de publicacion y cualquier backlink existente. |
| **Staging en Webflow** | Webflow permite trabajar en staging (webflow.io) y publicar cuando este listo. El sitio actual sigue vivo sin interrupcion. |
| **Velocidad de ejecucion** | No hay que migrar nada. Se empieza a rediseñar hoy y se publica cuando este listo. |
| **Integraciones intactas** | GTM, HubSpot, analytics, formularios — todo sigue conectado. No hay que re-configurar nada. |
| **Backlinks preservados** | Cualquier enlace externo a ubits.com/blog/... sigue funcionando. |

### Contras

| Contra | Detalle | Mitigacion |
|--------|---------|------------|
| **Deuda tecnica heredada** | El proyecto puede tener clases CSS desordenadas, componentes viejos, estilos no usados | Se puede limpiar progresivamente. Webflow tiene "Style Manager" para identificar estilos huerfanos |
| **Limitaciones de estructura** | Si el CMS actual tiene campos limitados o colecciones mal diseñadas, hay que ajustarlos | Se pueden agregar campos al CMS existente sin perder data |
| **Clonflictos de diseño** | Cambiar componentes globales (nav, footer) afecta todas las paginas a la vez | Usar Webflow Components (2024+) para aislar cambios |
| **"Peso" del proyecto** | Proyectos viejos pueden ser lentos en el Designer de Webflow | Limpiar paginas/estilos no usados antes de empezar |

---

## Opcion B: Crear Proyecto Nuevo + Migrar Dominio

### Como funciona
Se crea un proyecto Webflow desde cero. Se diseña todo el sitio nuevo en ese proyecto. Cuando esta listo, se re-apunta el DNS de ubits.com al nuevo proyecto y se configuran redirects 301 de todas las URLs viejas a las nuevas.

### Pros

| Pro | Detalle |
|-----|---------|
| **Lienzo limpio** | Sin deuda tecnica. Clases CSS limpias, componentes nuevos, estructura desde cero. |
| **Arquitectura de CMS optimizada** | Se diseñan las colecciones CMS desde cero con los campos exactos que se necesitan. |
| **Posibilidad de renombrar URLs** | Si se quiere cambiar la estructura de URLs (ej: /modulos/aprendizaje → /plataforma/aprendizaje), es mas facil. |
| **Trabajo paralelo** | El equipo puede trabajar en el nuevo proyecto mientras el sitio actual sigue vivo. |

### Contras

| Contra | Detalle | Severidad |
|--------|---------|-----------|
| **Riesgo SEO real** | Toda migracion de dominio/proyecto causa una caida temporal de rankings. Segun multiples fuentes (Broworks, Rapid301, PrettyNiceWebsites, DigiHotshot 2025-2026): "Expect a 10-30% traffic dip for 2-8 weeks, even with perfect 301 redirects." | **ALTA** |
| **327 redirects 301** | Cada URL vieja necesita un redirect a la nueva. Si falta UNA, Google indexa un 404 y pierde esa pagina. Webflow tiene limite de 300 redirects en plan basico. | **ALTA** |
| **Propagacion DNS** | El cambio de DNS tarda 24-48 horas. Durante ese tiempo, algunos usuarios ven el sitio viejo y otros el nuevo. | **MEDIA** |
| **Backlinks rotos** | Si algun redirect falla o si la URL nueva es distinta, los backlinks externos pierden su valor SEO. | **ALTA** |
| **Re-configurar todo** | GTM, HubSpot forms, analytics, custom code, integraciones — hay que instalar todo desde cero en el nuevo proyecto. | **MEDIA** |
| **Contenido CMS manual** | Los 327 blog posts NO se migran automaticamente entre proyectos Webflow. Hay que exportar CSV + re-importar, con riesgo de perder formato, imagenes, relaciones de coleccion. | **ALTA** |
| **Doble costo de hosting** | Dos proyectos Webflow = dos planes de hosting hasta que se complete la migracion. | **BAJA** |
| **Timeline mas largo** | Migrar + QA + redirects + DNS + verificar indexacion = 2-4 semanas extras sobre el diseño puro. | **MEDIA** |

---

## Comparativa Directa

| Criterio | Opcion A (Rebuild) | Opcion B (Nuevo + Migrar) |
|----------|-------------------|--------------------------|
| Riesgo SEO | **Ninguno** | 10-30% caida 2-8 semanas |
| Tiempo de ejecucion | **Mas rapido** (solo diseño) | Mas lento (+2-4 sem QA/migration) |
| Downtime | **Cero** | 24-48h DNS propagation |
| Complejidad | **Baja** | Alta (redirects, CMS, DNS, integraciones) |
| Limpieza tecnica | Parcial (se puede limpiar) | **Total** (lienzo limpio) |
| Costo | **1 plan Webflow** | 2 planes durante transicion |
| Backlinks | **100% preservados** | Depende de calidad de redirects |
| CMS blog (327 posts) | **Intacto** | Export/import manual con riesgo |
| Integraciones (GTM, HS) | **Intactas** | Re-configurar desde cero |
| Timeline para fin de abril | **Factible** | **Muy ajustado / riesgoso** |

---

## La Investigacion: Que Dicen los Expertos (2025-2026)

### Sobre migracion de dominio y SEO

> "Migrating or redesigning your website in Webflow without a solid SEO plan can lead to severe ranking drops, broken links, and traffic loss."
> — Broworks.net (Oct 2025)

> "Expect a temporary traffic dip of 10-30% for 2-8 weeks, even with perfect redirects."
> — Consenso de multiples fuentes especializadas

> "Migrating to Webflow does NOT hurt your SEO authority if done correctly. In fact, most sites experience improved rankings after migration."
> — BrixTemplates (Dec 2025) — Nota: esto se refiere a migrar DESDE otra plataforma A Webflow. UBITS ya esta en Webflow.

### Sobre rebuild vs nuevo proyecto

> "Based on my experience with similar projects, I'd recommend a structured hybrid approach: use the existing project, redesign page by page, and clean up as you go."
> — Reddit r/webflow (2025)

> "The biggest mistake is changing URLs during a redesign. If you keep the same URL structure, you eliminate 80% of SEO migration risk."
> — Rapid301 SEO Migration Checklist (2025)

### Sobre B2B SaaS redesigns

> "A SaaS website redesign should prioritize conversion rate and messaging clarity over visual novelty. The #1 mistake is redesigning without preserving what already converts."
> — Ideapeel B2B SaaS Redesign Guide (Dec 2025)

---

## Recomendacion Final

### Opcion A: Reconstruir sobre el proyecto existente

**Razones:**

1. **UBITS ya esta en Webflow** — la unica razon valida para migrar a un proyecto nuevo seria si estuvieran en WordPress, Wix, o Squarespace. Migrar de Webflow a Webflow no tiene sentido tecnico.

2. **El timeline es fin de abril** — eso es ~2 semanas. Alcanza para rediseñar paginas clave y publicar contenido nuevo. NO alcanza para un proyecto nuevo + 327 redirects + QA + DNS + verificacion de indexacion.

3. **El riesgo no se justifica** — los problemas del sitio (FAQs repetidas, metricas identicas, modulo sin pagina, contenido desactualizado) son problemas de **contenido**, no de plataforma. Se resuelven editando, no migrando.

4. **Los blogs son el activo mas valioso** — 327 posts indexados con URLs estables son equity SEO. Migrarlos manualmente a un proyecto nuevo es el mayor riesgo de la Opcion B.

### Plan de Accion Sugerido (Opcion A)

| Semana | Accion |
|--------|--------|
| **W1 (Abr 14-18)** | Limpiar estilos huerfanos, actualizar nav para incluir los 6 modulos, crear pagina /modulos/encuestas |
| **W1-2** | Reescribir FAQs unicas por modulo, actualizar metricas por modulo, agregar testimonio Mercado Libre a paginas relevantes |
| **W2 (Abr 21-25)** | Implementar Schema JSON-LD (Organization, SoftwareApplication, FAQPage) en cada pagina de modulo |
| **W2** | Corregir homepage ("4 modulos" → "6 modulos"), agregar pagina /ia o /inteligencia-artificial |
| **W3 (Abr 28-30)** | Actualizar sitemap, publicar, verificar indexacion en Google Search Console |

### Si Juan insiste en proyecto nuevo

Si hay razones internas que no conozco (ej: el equipo de desarrollo no tiene acceso al proyecto actual, el proyecto esta en una cuenta de un proveedor externo, hay un redesign de marca completo con nuevos assets), entonces Opcion B es viable PERO:

1. **NO cambiar la estructura de URLs** — /modulos/aprendizaje debe seguir siendo /modulos/aprendizaje
2. **Configurar TODOS los 301 redirects antes del switch DNS** — usar herramienta como Rapid301 para mapear
3. **Exportar CMS completo a CSV y validar import** — antes del switch, no despues
4. **Planear el switch para un viernes por la noche** — minimo trafico
5. **Agregar 2-3 semanas al timeline** — la migracion NO cabe en 2 semanas

---

## Apendice: Problemas Actuales del Sitio (para contexto)

| Pagina | Problema | Impacto |
|--------|----------|---------|
| /modulos/encuestas | 404 — no existe | Modulo activo sin landing page. Pierde todo trafico organico de "encuestas clima laboral" |
| /modulos/desempeno | FAQs son de Aprendizaje (copy-paste) | Confunde LLMs y usuarios. Viola principio GEO #8 |
| /modulos/diagnostico | FAQs son de Aprendizaje (copy-paste) | Mismo problema |
| Todos los modulos | Metricas identicas (93%/71%/82%) | Son metricas de Aprendizaje repetidas. Sin credibilidad por modulo |
| Homepage | "4 modulos" pero muestra 6 | Contradiccion visible |
| Sitemap | lastmod 2025-07-02 en todas las URLs | Google piensa que el sitio no se actualiza hace 9 meses |
| Reclutamiento | Sin FAQs, sin testimonios, sin metricas | Pagina mas debil vs los otros modulos |
| Schema/JSON-LD | No implementado en ninguna pagina | Oportunidad GEO perdida (principio #4 de los 10 principios) |

---

*Reporte generado el 2026-04-14 con data de audit interno + 15 fuentes externas especializadas en Webflow SEO migration.*
