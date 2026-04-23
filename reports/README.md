---
type: MOC
area: analitica
tags: [moc, reference]
related_areas: [ingenieria, operacion-growth]
---
# 📈 Central de Reportes (Reports Repository)

Esta carpeta funge como el visualizador oficial de resultados mecánicos. Aquí caen procesados todos los entregables, auditorías automatizadas y listados exportados.

## 🕸️ La Red del Proyecto (¿Cómo nos conectamos?)
- **➡ Generados por:** `../src/` (Los motores como `lead_scorer.py` o `ubits_seo_auditor.py` escupen los resultados directamente aquí).
- **➡ Son interpretados en:** `../ops/` (El equipo lee estos reportes para iterar Sprints de planificación o A/B tests en operaciones).
- **⬅ Diferencia con Data Lake:** Estos reportes son un output final (una radiografía), mientras que `../data/` contiene los insumos crudos que formaron este reporte.

## 📂 Tipos de Archivos

- **Reportes SEO (`.csv`, `.md`)**: Salidas de salud de dominios, listado de enlaces rotos o checks de Core Web Vitals.
- **Scoring de Leads (`lead_scoring_report.csv`)**: Data enriquecida sobre prospectos calificados en Tiers (Gold, Silver) detectados por IA.
- **Auditoría Ejecutiva (`.md`)**: Evaluaciones cualitativas estructurales a presentar a junta directiva.
