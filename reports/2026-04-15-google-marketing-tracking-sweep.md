---
type: report
area: analitica
tags: [ga4, gtm, tracking, barrido, google-marketing, 2026-abril]
captured_date: 2026-04-15
author: Antigravity Agent
related_docs:
  - ../docs/superpowers/plans/2026-04-15-gtm-ga4-rearchitecture.md
  - ../.agent/skills/gtm-datalayer/SKILL.md
---

# Reporte: Barrido Profundo de Tracking (Google Marketing Base)

**Fecha:** 15 de Abril de 2026  
**Objetivo:** Sintetizar la base de conocimiento local extraída de las 57 transcripciones magistrales en `docs/Google Marketing/` para validar y guiar la arquitectura de la solución al problema crítico (P0) del tracking roto en UBITS.

---

## 1. Naturaleza de la Base de Conocimiento
Se ejecutó una extracción automática a través de la skill `marketing-knowledge-base` sobre los 57 archivos de transcripción masiva (`google_chunk_01` a `google_chunk_57`). Estos documentos corresponden a clases magistrales, consultorías y discusiones profundas (podcasts) provenientes de expertos de la industria en conversiones, GA4 y e-commerce B2B.

---

## 2. Hallazgos Core sobre GA4 y Google Tag Manager

Los documentos extraídos validan categóricamente las fallas actuales en el sitio de UBITS y soportan la re-arquitectura metodológica definida:

### A. El Paradigma de GA4: Todo es un Evento
*(Extraído de Google Chunk 19)*
* GA4 elimina el concepto antiguo de analizar "páginas vistas". Intentar medir la conversión B2B de UBITS validando si el usuario simplemente llegó a una URL específica (como la página de "gracias" o la URL del módulo) infla y rompe los embudos.
* La solución dictada por los expertos es migrar a un enfoque **100% basado en Eventos Explícitos** (ej. clics en botones exactos, tiempo de video reproducido, apertura de formulario y el submit del formulario real).

### B. El Peligro de Código Descentralizado vs GTM
*(Extraído de Google Chunks 27, 49, 51)*
* Instalar píxeles directamente sobre CMS (como el código de HubSpot incrustado, o scripts en el `<head>` de Webflow sueltos) genera puntos de quiebre cuando se edita la web, un síntoma que explica **exactamente por qué UBITS dejó de medir el evento `demo_request`** a principios de abril.
* Manda explícitamente a que **Google Tag Manager** sea el único centro de despacho de scripts. Toda la lógica de negocio debe inyectarse hacia un `dataLayer.push` codificado localmente, y GTM es quien lee esta capa y despacha hacia Meta y Google.

### C. Analítica para Pruebas de Conversión (CRO)
*(Extraído de Google Chunk 14)*
* Los análisis reflejan que muchas veces una UX visualmente inferior pero iterada según datos del DataLayer convierte mejor. Se recomienda fuertemente empujar eventos de diferentes versiones de la web y conectar la vista de Analytics a una herramienta A/B como Google Optimize, midiendo no solo volumen, sino el *Drop-off* por capa del funnel.

---

## 3. Resolución Táctica para UBITS (Mapping)

Basado en el barrido, esta es la validación oficial de que debemos acatar los lineamientos de la skill `gtm-datalayer`:

1.  **Resolver el Gap P0 de Arquitectura:** El trigger `Abrir form demo` está en GTM, pero no se está llamando desde la capa de la vista en el nuevo componente de Webflow.
2.  **Listener Unificado (HubSpot -> GTM):** Implementar de inmediato el JS Listener proporcionado por el standard B2B que capture el `onFormSubmit` del iframe de HubSpot.
3.  **Captura de Leads Avanzada (Enhanced Conversions):** El evento `ubits_lead_captured` debe poblarse con el email y el tamaño de la empresa para habilitar `score_tier`.

---

> *Este reporte actúa como sustento técnico inmutable para que el equipo de desarrollo no cuestione el porqué del cambio a una arquitectura basada puramente en DataLayer, eliminando los bloqueos por el rediseño directo desde Webflow.*
