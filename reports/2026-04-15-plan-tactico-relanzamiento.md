---
type: report
area: estrategia
tags: [plan-tactico, relanzamiento, copy, redirects, gtm, schema, 2026-abril]
related_areas: [website, analitica, identidad-ubits, organico]
captured_date: 2026-04-15
author: David Toro
related_docs:
  - 2026-04-15-brief-ejecutivo-juan.md
  - 2026-04-15-INDEX-relanzamiento.md
---

# Plan Tactico de Relanzamiento — Fin Abril 2026

> **Brief ejecutivo:** [2026-04-15-brief-ejecutivo-juan.md](2026-04-15-brief-ejecutivo-juan.md)  
> **Indice maestro:** [2026-04-15-INDEX-relanzamiento.md](2026-04-15-INDEX-relanzamiento.md)  
> **Fecha:** 2026-04-15 · **Autor:** David Toro

Documento tactico con checklists accionables, copy listo para pegar, y configuraciones tecnicas. Es el companion del brief ejecutivo para Juan.

---

## 📑 Tabla de contenido

1. [Matriz de redirects 301 urgentes](#1-matriz-de-redirects-301)
2. [Copy por modulo (Maria + GEO)](#2-copy-por-modulo)
3. [Configuracion GTM + eventos clave GA4](#3-configuracion-gtm--eventos-clave)
4. [Schema JSON-LD por pagina](#4-schema-json-ld)
5. [Rediseño de formulario de demo](#5-rediseño-formulario-demo)
6. [Optimizacion SEO on-page (title + meta)](#6-optimizacion-seo-on-page)
7. [Pagina /modulos/encuestas (nueva)](#7-pagina-modulos-encuestas-nueva)
8. [FAQ unicas por modulo](#8-faq-unicas-por-modulo)
9. [Checklist pre-publicacion (QA)](#9-checklist-pre-publicacion)
10. [Plan post-relanzamiento](#10-plan-post-relanzamiento)

---

## 1. Matriz de redirects 301

Basado en data anual de [20-paginas-anuales-top250.md](../data/raw/ga4/2026-04-15/20-paginas-anuales-top250.md).

### Problema detectado

URLs duplicadas conviven en los modulos. Google las indexa como paginas distintas, dividiendo autoridad SEO.

### Decision canonica recomendada

Usar `/modulos/X` como canonica (URL nueva) porque:
- Es la ruta activa actual
- Esta en el sitemap XML
- Coincide con la navegacion del sitio
- Permite jerarquia limpia `/modulos/aprendizaje/caso-X`

**Excepcion:** Mantener los redirects 301 de URL viejas hacia la canonica para no perder el equity SEO que generan.

### Matriz completa

| URL origen (redirect desde) | URL destino (canonica) | Status | Vistas anuales | Prioridad |
|-----------------------------|------------------------|--------|---------------:|-----------|
| `/modulo-aprendizaje` | `/modulos/aprendizaje` | 301 | 26,225 | P0 |
| `/modulo-de-aprendizaje` | `/modulos/aprendizaje` | 301 | 832 | P0 |
| `/modulo-desempeno` | `/modulos/desempeno` | 301 | 1,587 | P0 |
| `/modulo-diagnostico` | `/modulos/diagnostico` | 301 | 944 | P0 |
| `/inicio` | `/` | 301 | 172 | P1 |
| (404 actual) `/modulos/encuestas` | (nueva pagina a crear) | — | 0 | P0 |

### Implementacion en Webflow

En Webflow Dashboard → Project Settings → Publishing → 301 Redirects:

```
/modulo-aprendizaje       → /modulos/aprendizaje
/modulo-de-aprendizaje    → /modulos/aprendizaje
/modulo-desempeno         → /modulos/desempeno
/modulo-diagnostico       → /modulos/diagnostico
/inicio                   → /
```

### Nota critica

**NO eliminar las paginas viejas antes de hacer el redirect**. Primero implementar 301s, despues despublicar (no eliminar) las paginas originales. Esto preserva el SEO.

### Verificacion

Post-redirect, validar con:
- `curl -I https://ubits.com/modulo-aprendizaje` → debe devolver `301` + header `Location: https://ubits.com/modulos/aprendizaje`
- Google Search Console → "Indexing" → Removal report → verificar que Google actualice el indice (toma 1-4 semanas)

---

## 2. Copy por modulo

**Fuentes:** 
- [Contexto 6 modulos](../ops/01_identidad-ubits/modulos-contexto-completo.md)
- [Argumentario Maria RRHH](../ops/09_sales-enablement/argumentario-modulos-rrhh.md)
- [Los 10 principios GEO](../ops/07_organico/geo-estrategia.md)

### Estructura obligatoria por modulo (principio GEO #3)

Cada pagina de modulo debe seguir este esqueleto:

```
H1: Nombre oficial del modulo (ej: "Modulo de Aprendizaje")
↓
Tagline en 1-2 oraciones (definicion clara)
↓
H2: Por que tu equipo necesita [modulo]
- Explicacion desde la perspectiva de Maria (HR Director, empresa 500 emp)
- Problema real que resuelve (no feature)
↓
H2: Que incluye el modulo
- Lista de funcionalidades concretas (no abstractas)
- Cada una con ejemplo de uso
↓
H2: Para quien es
- Rol, industria, tamaño empresa
- Diferenciacion vs alternativas
↓
H2: Preguntas frecuentes
- 6-8 FAQs UNICAS del modulo (no copy-paste de Aprendizaje)
↓
CTA: Habla con ventas (form optimizado)
```

### Modulo Aprendizaje — Copy optimizado

**H1:** Acelera el desarrollo de tus colaboradores con nuestro LMS corporativo con IA

**Tagline:** UBITS Learning es el modulo LMS todo-en-uno que centraliza la formacion de empresas de 100-10,000 colaboradores en LatAm, con un catalogo de 14,000 contenidos de Harvard, Stanford, WOBI, TED, AWS y Microsoft.

**H2: Por que tu equipo necesita el Modulo de Aprendizaje**

Como Director/a de Recursos Humanos, sabes que el presupuesto de capacitacion se diluye comprando cursos separados en Harvard, Coursera y proveedores locales. El resultado: un caos de contratos, imposibilidad de medir ROI, y equipos que no aprovechan lo que ya compraste.

Con UBITS Learning, consolidas todo en una sola plataforma. Tu equipo accede a 14,000+ contenidos con un solo login. Tu area de RRHH mide exactamente quien estudia, cuantas horas invierte, y que competencias desarrolla. Y tu Director Financiero recibe un reporte de ROI claro.

**H2: Que incluye el modulo LMS**

- **Catalogo Standard y MAX:** 14,000+ contenidos en 30+ competencias y 150+ habilidades, de Harvard Business Impact, Stanford, WOBI, TED, AWS, Microsoft y The Linux Foundation
- **LMS Creator:** Sube tus propios videos, PDFs y presentaciones. Crea tu universidad corporativa en horas, no meses
- **Planes de formacion personalizados (Learning Map):** Asigna rutas completas a personas, equipos o toda la compañia con fechas limite y alertas
- **Reporteria avanzada:** Tableros en tiempo real con tiempo de estudio, completitud y desarrollo de competencias por empleado, equipo, pais y conglomerado
- **Universidad Corporativa personalizada:** Tus logos, colores y certificados. Tus empleados entran a "La Universidad de [Tu Empresa]", no a UBITS
- **Gestion de visibilidad:** Controla que cursos ven los ejecutivos y cuales los colaboradores
- **Rutas de aprendizaje estructuradas:** Rutas oficiales pre-armadas + rutas custom para tu industria
- **App movil iOS y Android:** Aprendizaje en cualquier momento, desde cualquier lugar

**H2: Para quien es el modulo de Aprendizaje**

- **Tamaño de empresa ideal:** 100 a 10,000 colaboradores
- **Roles target:** Director/a de RRHH, Gerente de Formacion, Learning & Development Manager
- **Industrias donde mas ROI genera:** Retail, Finanzas, Tecnologia, Servicios, Industria Manufacturera, Consumo Masivo
- **Geografias:** LatAm (Colombia, Mexico, Ecuador, Chile, Peru, Bolivia, Centroamerica)

**Diferenciacion vs alternativas:**

- **Vs comprar cursos sueltos (Coursera, Udemy, etc.):** Un solo contrato consolida todo. Reduces 80% la carga administrativa.
- **Vs Moodle/otros LMS open-source:** No necesitas equipo tecnico para mantenerlo. Setup en 2 semanas, no 6 meses.
- **Vs LinkedIn Learning:** Contenido en español con calidad Harvard, no solo ingles traducido.

**H2: Preguntas frecuentes del Modulo de Aprendizaje**

*(ver seccion 8 de este documento — FAQs unicas)*

### Modulo Desempeno — Copy optimizado

**H1:** Impulsa el crecimiento de tu equipo con la nueva Matriz de Talento 9-box con IA

**Tagline:** UBITS Desempeño integra evaluaciones 360°, gestion de objetivos y matriz de talento en una sola vista para juntas de talento, planes de sucesion y decisiones estrategicas.

**H2: Por que tu equipo necesita el Modulo de Desempeno**

Hoy, las evaluaciones de desempeno en tu empresa seguramente viven en Excel, Google Forms o Microsoft Teams. El CEO pregunta "quienes son nuestras estrellas?" y no tienes datos consolidados para responder. Los lideres postergan las juntas de talento porque el proceso es tedioso y subjetivo.

Con UBITS Desempeno, diseñas una evaluacion una vez y la asignas masivamente. La IA resume las respuestas abiertas. Visualizas el mapa completo de talento en una Matriz 9-box que puedes escalar hasta 25-box. Juntas de talento ya no son de 4 horas — son de 1 hora con datos reales.

**H2: Que incluye el modulo Desempeno**

3 sub-modulos integrados:

- **Evaluaciones 360°:**
  - Diseño flexible alineado a cultura y competencias
  - Privacidad configurable por pregunta/evaluador
  - **IA que resume respuestas abiertas** automaticamente
  - Asignacion masiva con recordatorios
  - Vista Admin, Lider (comparativa equipo vs area vs empresa) y Colaborador

- **Objetivos y OKRs:**
  - Medidas cuantitativas, cualitativas o por hitos
  - Alineacion a estrategia empresarial
  - Seguimiento en tiempo real con evidencias
  - Retroalimentacion continua documentada
  - Reportes automatizados

- **Matriz de Talento (9-box a 25-box):**
  - Cuadrantes desempeño × potencial
  - Personalizable desde 2×2 hasta 25-box
  - Historicos guardados para analisis longitudinal
  - Exportacion rapida para juntas de talento
  - **Se integra con Tareas y Planes** para ejecutar PDIs automaticamente

**H2: Para quien es el modulo de Desempeno**

- **Tamaño empresa ideal:** 200-10,000 colaboradores (donde tiene sentido hacer 360 formales)
- **Roles target:** Director/a RRHH, Head of People, Talent Manager, Chief People Officer
- **Problema concreto que resuelve:** Eliminar el caos de evaluaciones en Excel y llegar a la junta directiva con datos duros, no opiniones

**Diferenciacion:**

- **Vs Lattice/Culture Amp:** Interfaz en español + integracion nativa con aprendizaje + IA que resume
- **Vs Excel/Forms:** Automatizacion masiva + reporte en tiempo real + matriz de talento visual
- **Vs modulos de SAP SuccessFactors:** Setup en semanas, no 6 meses. Precio accesible para empresas 100-500 empleados

*(FAQs unicas en seccion 8)*

### Modulo Diagnostico — Copy optimizado

**H1:** Descubre el potencial de tu equipo con assessments psicometricos validados

**Tagline:** UBITS Diagnostico evalua competencias criticas con pruebas psicometricas validadas y conecta cada brecha con una solucion de aprendizaje automatica.

**H2: Por que tu equipo necesita el Modulo de Diagnostico**

El CEO pregunta "en que esta fuerte y debil el equipo comercial?". Hoy te basas en la opinion del jefe del area — subjetiva, sesgada, sin metodologia. Cuando propones un plan de formacion, no puedes defender con datos por que elegiste esos cursos.

Con UBITS Diagnostico, aplicas una evaluacion validada psicometricamente al equipo. Obtienes un mapa claro: "operaciones tiene 85% en habilidades tecnicas pero 40% en liderazgo". La plataforma **conecta automaticamente** la brecha con cursos del catalogo. En minutos, tienes un plan de formacion justificado con datos.

**H2: Que incluye el modulo Diagnostico**

- Assessment estrategico de competencias (pre-armadas o custom)
- Pruebas psicometricas **validadas** (no tests de internet)
- Deteccion automatica de brechas por persona, equipo o area
- Informes detallados con recomendaciones accionables
- **Conexion automatica a planes de formacion** del catalogo Aprendizaje
- Tracking por competencia con fechas de expiracion
- Historicos para medir evolucion tras planes de formacion

**H2: Para quien es el modulo de Diagnostico**

- **Tamaño empresa ideal:** 100-5,000 colaboradores
- **Roles target:** Learning & Development Manager, Talent Manager, HR Business Partner
- **Caso de uso tipico:** Planes anuales de formacion basados en datos, no en suposiciones

**Diferenciacion:**

- **Vs consultorias externas:** No pagas $50K-100K USD por un assessment externo. Lo corres cuando quieras con la plataforma.
- **Vs tests online gratuitos:** Pruebas psicometricas reales, validadas, con metodologia publicada

*(FAQs unicas en seccion 8)*

### Modulo Reclutamiento — Copy optimizado

**H1:** Encuentra el match perfecto con SerenaAI: el primer AITS 100% construido con IA

**Tagline:** UBITS Reclutamiento automatiza entrevistas por voz, scoring de CVs y feedback a candidatos con IA — para que tu equipo dedique tiempo a decisiones estrategicas, no a filtros manuales.

**H2: Por que tu equipo necesita el Modulo de Reclutamiento**

Tienes 200 candidatos para 3 vacantes de ventas. Tu equipo de reclutamiento pasa 2 semanas filtrando CVs, haciendo llamadas de 15 minutos, y perdiendo candidatos porque no contestaron a tiempo. La experiencia del candidato es pesima — los que no quedan nunca reciben feedback.

Con UBITS Reclutamiento + SerenaAI, la IA entrevista a los 200 candidatos por voz, analiza habilidades blandas y tecnicas, y entrega una shortlist con puntaje de compatibilidad. WhatsApp envia recordatorios automaticos. A los que no quedan, les llega feedback empatico automatico. En horas, no semanas.

**H2: Que incluye el modulo Reclutamiento**

- **SerenaAI — Entrevistas automatizadas por voz:**
  - Entrevista 200 candidatos simultaneos
  - Transcripcion completa
  - Analisis de habilidades blandas y tecnicas
  - Puntaje de compatibilidad con la vacante
  - Recomendaciones para siguiente paso

- **CV Scoring con IA:**
  - Filtros personalizados por criterio
  - Ranking automatico por compatibilidad
  - Priorizacion por experiencia, educacion, certificaciones

- **Seguimiento automatizado por WhatsApp:**
  - Recordatorios de entrevista
  - Confirmaciones automatizadas
  - Notificaciones de estado del proceso

- **Feedback automatico empatico:**
  - A candidatos no seleccionados
  - Fortalece marca empleadora
  - Deja puerta abierta para futuras vacantes

- **Panel de control en tiempo real:**
  - Embudo completo (CVs recibidos → entrevistas → shortlist → contratados)
  - Tiempos por etapa
  - Metricas de conversion

**H2: Para quien es el modulo de Reclutamiento**

- **Tamaño empresa ideal:** 500-10,000 colaboradores (donde hay volumen de reclutamiento continuo)
- **Roles target:** Head of Talent Acquisition, Recruitment Manager, HR Director
- **Caso de uso tipico:** Reclutamiento masivo (ej: call centers, retail, operaciones) o procesos criticos con muchos candidatos

**Diferenciacion:**

- **Vs ATS tradicionales (Workday, Greenhouse):** La IA entrevista, no solo organiza CVs. 10x mas eficiente.
- **Vs agencias externas:** Scaleable sin aumentar presupuesto
- **Vs LinkedIn Recruiter:** Integrado al ecosistema de desarrollo post-contratacion (aprendizaje, desempeño)

*(FAQs unicas en seccion 8)*

### Modulo Tareas y Planes — Copy optimizado

**H1:** De la estrategia a la accion: organiza, ejecuta y haz seguimiento a las tareas en un solo lugar

**Tagline:** UBITS Tareas y Planes convierte los compromisos de desarrollo del talento en acciones visibles con responsables, fechas y trazabilidad real — impulsado por IA.

**H2: Por que tu equipo necesita el Modulo de Tareas y Planes**

Hiciste la evaluacion 360. Descubriste que el equipo de ventas tiene brechas en negociacion. El resultado se quedo en un PDF de 47 paginas que nadie abrio. 6 meses despues, nada cambio.

Con UBITS Tareas y Planes, la evaluacion se convierte automaticamente en un Plan de Desarrollo Individual (PDI): "Juan — completar curso de negociacion avanzada antes del 30 de junio — responsable: su jefe directo". Con fecha, responsable, evidencias y seguimiento. El PDI es ejecutable, no decorativo.

**H2: Que incluye el modulo Tareas y Planes**

- Crear planes colaborativos o individuales con tareas asignadas, fechas y prioridades
- **Generar PDIs automaticamente desde evaluaciones 360** (integracion con Desempeno)
- Agregar evidencias y comentarios para dar trazabilidad al avance
- Diseñar plantillas personalizadas (PDI, plan de clima, plan de sucesion)
- Carga masiva de planes
- **IA que genera planes flexibles u operativos en segundos**

**H2: Para quien es el modulo de Tareas y Planes**

- **Tamaño empresa ideal:** 100-10,000 colaboradores
- **Roles target:** L&D Manager, Team Leaders, HR Business Partners
- **Caso de uso tipico:** Bajar estrategia de talento a ejecucion concreta post-evaluaciones

**Diferenciacion:**

- **Vs Asana/Monday:** Especializado en desarrollo de talento, no gestion general
- **Vs planillas Excel:** Automatizado, con evidencias, integrado a evaluaciones
- **Vs otros modulos RRHH:** El unico que cierra el loop diagnostico → aprendizaje → desempeño → accion

*(FAQs unicas en seccion 8)*

### Modulo Encuestas / Clima y Cultura — NUEVA pagina

**H1:** Escucha la voz de tu equipo con eNPS, Clima y Cultura

**Tagline:** UBITS Encuestas te permite medir satisfaccion, clima y cultura con confidencialidad garantizada. Toma decisiones con datos reales, no con intuicion.

**H2: Por que tu equipo necesita el Modulo de Encuestas**

El CEO te pregunta "la gente esta contenta aqui?". Hoy dices "creo que si" porque no tienes datos. La rotacion en ventas subio 15% y no sabes por que. Cuando lanzaste el programa de home office hibrido, nadie te dijo si estaba funcionando.

Con UBITS Encuestas, mides eNPS cada trimestre, clima laboral cada año, y encuestas puntuales cuando lanzas iniciativas. Todo con confidencialidad garantizada — los colaboradores responden honestamente. Los resultados llegan en tableros visuales que puedes llevar a la junta directiva.

**H2: Que incluye el modulo Encuestas**

3 sub-soluciones integradas:

- **eNPS (Employee Net Promoter Score):**
  - Encuesta de 1 pregunta: "¿Recomendarias esta empresa para trabajar?"
  - Escala -100 a +100
  - Medicion trimestral para ver tendencias

- **Clima y Cultura:**
  - Encuestas completas de satisfaccion (comunicacion, liderazgo, desarrollo, balance)
  - Confidencialidad total (respuestas no rastreables a persona)
  - Deteccion de factores negativos por area/equipo

- **Encuestas personalizadas:**
  - Bancos de preguntas preestablecidos
  - Encuestas custom para cualquier necesidad
  - Reportes automaticos con insights clave

**H2: Para quien es el modulo de Encuestas**

- **Tamaño empresa ideal:** 50+ colaboradores
- **Roles target:** Chief People Officer, HR Director, Employee Experience Manager
- **Caso de uso tipico:** Medir impacto de iniciativas de cultura, detectar riesgos de rotacion, cumplir normativas (algunos paises exigen medicion de clima)

**Diferenciacion:**

- **Vs Google Forms:** Confidencialidad garantizada tecnologicamente
- **Vs Culture Amp/Peakon:** Integracion nativa con aprendizaje para cerrar brechas
- **Vs consultorias de clima:** Mediciones continuas, no 1 vez al año

*(FAQs unicas en seccion 8)*

---

## 3. Configuracion GTM + Eventos Clave

### GTM Container: `GTM-5C9SS9Q`

Container ID detectado en produccion. Documentado en [docs/v1/01_stack_and_ecosystem_analysis.md:18](../docs/v1/01_stack_and_ecosystem_analysis.md#L18).

### Estado esperado vs real

**Eventos clave anuales (funcionando):**
- Abrir form demo: 21,000
- Registro Newsletter: 703
- Registro Exitoso Form DEMO 30 dias: 310

**Eventos clave abril 2026 (ROTOS):**
- Abrir form demo: 0
- Registro Exitoso Form DEMO: 0

### Diagnostico GTM (requiere tu acceso)

1. **Entrar a tagmanager.google.com → Container `GTM-5C9SS9Q`**
2. **Verificar triggers existentes:**
   - [ ] `Abrir form demo` — Custom Event / Click / Form Submit?
   - [ ] `click_boton_demo` — existe?
   - [ ] `Registro Newsletter` — existe?
   - [ ] `Registro Exitoso Form DEMO 30 dias` — existe?
3. **Verificar tags que envian a GA4:**
   - [ ] Measurement ID correcto (G-XXXXXXXXXX)
   - [ ] Tags no pausados
   - [ ] Firing conditions correctas
4. **Revisar Versions panel:**
   - Fecha de la ultima publicacion (historial de marzo/abril 2026)
   - Numero de versiones nuevas
   - Cambios en los ultimos publishes
5. **Preview mode:**
   - Abrir ubits.com con Tag Assistant
   - Navegar al form demo
   - Ver si el evento dispara en tiempo real

### Eventos clave a configurar POST-relanzamiento

Ver lista completa de 32 eventos en [23-eventos-32-completos.md](../data/raw/ga4/2026-04-15/23-eventos-32-completos.md).

**Key events oficiales (marcar como "Conversion" en GA4):**

| Nombre del evento | Cuando dispara | Criticidad |
|-------------------|----------------|-----------|
| `demo_request` | Form demo submit exitoso | 🔴 P0 |
| `demo_form_open` | Click en boton demo O abrir pagina demo | 🔴 P0 |
| `newsletter_signup` | Form newsletter exitoso | 🟡 P1 |
| `resource_download` | Click en link de descarga (PDF/CSV) | 🟡 P1 |
| `module_page_engagement` | Visita a /modulos/X con engagement >30s | 🟢 P2 |
| `skilled_registration` | Registro exitoso a webinar Skilled | 🟡 P1 |
| `becas_application` | Submit exitoso en /becas-ia-* | 🔴 P0 (convierte 50%) |
| `pricing_view` | Visita a /ubits-para-tu-empresa con scroll >70% | 🟡 P1 |
| `login_attempt` | Click en "Iniciar sesion" (LXP) | 🟢 P2 |
| `video_complete` | Video UBITS completado >80% | 🟢 P2 |

### Configurar audiencias custom

Ver [09-audiencias-7d.md](../data/raw/ga4/2026-04-15/09-audiencias-7d.md) para contexto.

**Audiencias adicionales sugeridas:**

| Audiencia | Criterio | Uso |
|-----------|----------|-----|
| "Lectores Blog" | 1+ vista a /blog/ con engagement >60s | Retargeting a demo |
| "Visitantes Modulos" | 1+ vista a /modulos/* | Retargeting B2B |
| "Prospects Alta Intencion" | Abrio form demo + no completo | Remarketing urgente |
| "Becarios" | Vistas a /becas-ia-* | Nurture especifico |
| "Skilled Attendees" | Registrados via /skilled | Upsell a demo |
| "Colombia Hot" | Colombia + 3+ sesiones + 60s+ engagement | Outreach ventas |

---

## 4. Schema JSON-LD

### Por que (principio GEO #4)

Los LLMs (ChatGPT, Claude, Perplexity, Gemini) priorizan contenido con schema estructurado. Implementar aumenta la probabilidad de que UBITS sea mencionada correctamente cuando alguien pregunta sobre HR software en LatAm.

Ademas, Google Search muestra rich snippets que mejoran CTR.

### Schema Organization (root del sitio)

Pegar en Webflow → Project Settings → Custom Code → Head:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "UBITS",
  "alternateName": ["UBITS Learning Solutions", "UBITS Learning"],
  "url": "https://ubits.com",
  "logo": "https://ubits.com/logo.png",
  "description": "UBITS es el software todo-en-uno de gestión de recursos humanos que integra aprendizaje, desempeño, diagnóstico, reclutamiento con IA, tareas y planes, y encuestas de clima en una plataforma cloud unificada para empresas de 100 a 10,000 colaboradores en América Latina.",
  "foundingDate": "2018",
  "foundingLocation": {
    "@type": "Place",
    "address": {
      "@type": "PostalAddress",
      "addressCountry": "CO"
    }
  },
  "numberOfEmployees": {
    "@type": "QuantitativeValue",
    "value": 239
  },
  "sameAs": [
    "https://www.linkedin.com/company/ubits",
    "https://www.youtube.com/@ubits",
    "https://www.facebook.com/ubitscolombia",
    "https://www.instagram.com/ubits"
  ],
  "contactPoint": {
    "@type": "ContactPoint",
    "contactType": "sales",
    "email": "ventas@ubits.co",
    "availableLanguage": ["es", "en"]
  },
  "address": {
    "@type": "PostalAddress",
    "addressCountry": "CO",
    "addressLocality": "Bogotá"
  }
}
</script>
```

### Schema SoftwareApplication (por modulo)

Template para cada `/modulos/X`:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "SoftwareApplication",
  "name": "UBITS Aprendizaje",
  "applicationCategory": "BusinessApplication",
  "applicationSubCategory": "Human Resources",
  "operatingSystem": "Cloud-based, iOS, Android",
  "description": "Módulo LMS corporativo con IA que centraliza la formación de empresas de 100-10,000 colaboradores en LatAm, con catálogo de 14,000 contenidos de Harvard, Stanford, WOBI, TED, AWS y Microsoft.",
  "featureList": [
    "Catálogo Standard y MAX con 14,000+ contenidos",
    "LMS Creator para contenido propio",
    "Planes de formación (Learning Map)",
    "Reportería avanzada en tiempo real",
    "Universidad Corporativa personalizada",
    "Gestión de visibilidad de contenido",
    "Rutas de aprendizaje estructuradas",
    "App móvil iOS y Android"
  ],
  "offers": {
    "@type": "Offer",
    "priceCurrency": "USD",
    "priceSpecification": {
      "@type": "PriceSpecification",
      "price": "Contactar ventas",
      "priceCurrency": "USD"
    }
  },
  "provider": {
    "@type": "Organization",
    "name": "UBITS",
    "url": "https://ubits.com"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.8",
    "ratingCount": "1000",
    "description": "Basado en 1,000+ empresas en LatAm"
  }
}
</script>
```

**Duplicar y ajustar** para cada modulo (Desempeno, Diagnostico, Reclutamiento, Tareas y Planes, Encuestas).

### Schema FAQPage (por modulo)

Template por modulo:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "¿Qué es el módulo de Aprendizaje de UBITS?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "El Módulo de Aprendizaje de UBITS es el LMS corporativo que permite a empresas de 100-10,000 colaboradores centralizar formación con un catálogo de 14,000 contenidos de Harvard, Stanford, WOBI, TED, AWS y Microsoft."
      }
    }
    // ... 5-8 FAQs por modulo
  ]
}
</script>
```

**Importante:** Las FAQs en el schema deben coincidir EXACTAMENTE con las FAQs visibles en la pagina (seccion 8 de este documento).

### Schema BreadcrumbList (todas las paginas internas)

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Home",
      "item": "https://ubits.com/"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Módulos",
      "item": "https://ubits.com/modulos/"
    },
    {
      "@type": "ListItem",
      "position": 3,
      "name": "Aprendizaje",
      "item": "https://ubits.com/modulos/aprendizaje"
    }
  ]
}
</script>
```

### Schema Article (en blogs)

Template para cada post de blog:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "{{titulo del blog}}",
  "image": "{{url imagen destacada}}",
  "datePublished": "{{YYYY-MM-DD}}",
  "dateModified": "{{YYYY-MM-DD}}",
  "author": {
    "@type": "Person",
    "name": "{{autor}}"
  },
  "publisher": {
    "@type": "Organization",
    "name": "UBITS",
    "logo": {
      "@type": "ImageObject",
      "url": "https://ubits.com/logo.png"
    }
  },
  "about": ["{{tema principal}}", "{{tema secundario}}"]
}
</script>
```

---

## 5. Rediseño formulario demo

### Problema: 98.5% form abandonment

21,000 usuarios abren el form anualmente. Solo 310 lo completan.

### Form actual (detectado en scraping 2026-04-15)

6 campos:
1. Nombre
2. Apellido
3. ¿Actualmente usas UBITS? (Sí/No)
4. Correo corporativo
5. Nombre de tu empresa
6. Número de móvil

\+ Checkbox "Deseas suscribirte al newsletter"  
\+ Checkbox "Acepto política de datos"

**Friction points:**
- Telefono requerido (movil) — puede ser razon de abandonment
- "Usas UBITS ya?" — pregunta redundante para lead qualification
- 2 checkboxes simultaneos con consent language

### Form propuesto (3 campos)

Version A — Minima:

1. Email corporativo
2. Nombre y empresa
3. CTA: "Solicitar demo gratuito"

**Mobile-first design:**
- Un solo step (no wizard)
- Labels grandes
- Auto-focus en primer campo
- Botón full-width
- Mensaje post-submit claro

Version B — Con qualifier suave:

1. Email corporativo  
2. Nombre completo
3. Empresa + tamaño (dropdown: <100, 100-500, 500-5000, 5000+)
4. CTA: "Solicitar demo gratuito"

### A/B test post-relanzamiento

Correr A/B test:
- **Control:** Form actual (6 campos)
- **Variante A:** Form minima (3 campos)
- **Variante B:** Form con qualifier (4 campos)

**Metrica de exito:** Form completion rate (demos exitosos / form opens)

**Duracion minima:** 2 semanas o 500 submits por variante

**Hipotesis:** Variante A incrementa completion rate 3x minimo (de 1.48% a 4.5%).

---

## 6. Optimizacion SEO on-page

### Las 4 paginas con mayor oportunidad (data de [25-seo-paginas-destino-anual.md](../data/raw/ga4/2026-04-15/25-seo-paginas-destino-anual.md))

Paginas bien posicionadas (P1-P2) pero con CTR bajo. Reescribir title + meta description puede multiplicar trafico sin crear contenido nuevo.

#### 1. `/ubits-para-tu-empresa` — DIAMANTE

- Impresiones: 567,393/año
- Posicion: 1.83 (top 2 de Google)
- CTR actual: **0.23%**
- Clicks: 1,322/año
- **Bounce rate: 9%** (el mejor del sitio)

**Title actual (estimado):** `UBITS para tu empresa`

**Title propuesto:**

```
UBITS para tu empresa | Software todo-en-uno RRHH LatAm | 14K cursos
```

**Meta description propuesta:**

```
Gestiona aprendizaje, desempeño, reclutamiento con IA y clima laboral en una sola plataforma. 1,000+ empresas LatAm confían en UBITS. Solicita demo gratis.
```

**Impacto estimado:** CTR 0.23% → 8-12% = **+40,000-60,000 clicks/año**

#### 2. `/comunidad-de-aprendizaje`

- Impresiones: 459,108/año
- Posicion: 1.75
- CTR actual: **0.18%**
- Clicks: 837/año

**Title propuesto:**

```
Comunidad de aprendizaje corporativo | UBITS | Únete gratis
```

**Meta description propuesta:**

```
Recibe recursos exclusivos, invitaciones a eventos y conversaciones con 10,000+ líderes de RRHH en LatAm. Únete gratis a la comunidad UBITS.
```

#### 3. `/recursos-descargables`

- Impresiones: 195,708/año
- Posicion: 1.14 (top 1)
- CTR actual: **1.08%**

**Title propuesto:**

```
Recursos gratis para RRHH | Plantillas, guías y checklists | UBITS
```

**Meta description propuesta:**

```
Descarga plantillas de PDI, matrices 9-box, guías de clima laboral y más. 30+ recursos gratuitos creados para equipos de RRHH en LatAm.
```

#### 4. `/blog/ejemplos-habilidades-tecnicas-y-blandas` (el Everest)

- Impresiones: 865,433/año
- Posicion: 10.32 (pagina 2)
- CTR: 0.98%
- Clicks: 8,441/año

**Keyword target:** "habilidades blandas" (185K impresiones, P10)

**Accion:** No solo optimizar meta — mejorar contenido para subir de P10 a P3-5:
- Agregar schema Article + FAQ
- Aumentar profundidad de contenido (actualmente ~1,500 palabras, ir a 3,000+)
- Agregar tabla comparativa habilidades tecnicas vs blandas
- Incluir ejemplos de empresas reales
- Agregar 10 FAQs estructuradas

**Impacto estimado:** Subir de P10 a P3-5 → CTR 1% → 8-12% = **+60,000-100,000 clicks/año**

### Oportunidad total de estas 4 paginas

**~+140,000 clicks organicos adicionales/año** sin crear contenido nuevo.

---

## 7. Pagina /modulos/encuestas (nueva)

### Estado actual

`https://ubits.com/modulos/encuestas` → **404 confirmado** via Firecrawl scraping (2026-04-15)

### Contenido a crear

Ver seccion 2 de este documento — "Modulo Encuestas / Clima y Cultura — NUEVA pagina".

### Schema a implementar

- SoftwareApplication (UBITS Encuestas)
- FAQPage con 6 FAQs unicas del modulo
- BreadcrumbList

### Keywords target

| Keyword | Volumen mensual | Dificultad |
|---------|----------------:|-----------:|
| encuestas clima laboral | 1,300 | Media |
| eNPS | 260 | Baja |
| medir clima organizacional | 600 | Media |
| encuestas satisfaccion laboral | 880 | Media |
| evaluacion clima empresa | 320 | Baja |

**Total volumen potencial:** ~3,360 impresiones/mes = 40K/año

**Ventaja:** Competidores en LatAm no tienen contenido GEO-optimizado en este cluster.

### Url canonica

`/modulos/encuestas` — alineada con el resto de modulos

### Internal linking

Esta pagina debe linkearse desde:
- Homepage (menu principal de modulos)
- `/modulos/aprendizaje` (seccion de modulos relacionados)
- Blog `/blog/diagnostico-clima-laboral-4-pasos`
- Blog `/blog/interpretar-calcular-enps`
- Blog `/blog/encuestas-clima-laboral-mirada-detallada`

---

## 8. FAQ unicas por modulo

### Problema actual

Desempeno y Diagnostico tienen FAQs COPY-PASTE de Aprendizaje (detectado en scraping 2026-04-15). Viola principio GEO #5 y #8.

### FAQs Modulo Aprendizaje (6)

1. **¿Qué es el módulo de Aprendizaje de UBITS?**  
Es el LMS corporativo que permite a empresas de 100-10,000 colaboradores centralizar formación con un catálogo de 14,000 contenidos de Harvard, Stanford, WOBI, TED, AWS y Microsoft.

2. **¿Cuántos contenidos incluye el catálogo?**  
Más de 14,000 contenidos en 30+ competencias y 150+ habilidades, en formatos de curso, podcast, ideas de libros, charlas y microlearning.

3. **¿Puedo subir mis propios cursos?**  
Sí. Con LMS Creator cargas videos, PDFs, presentaciones y evaluaciones. Personalizas la experiencia con tus colores, logo y certificados propios.

4. **¿Cuánto tiempo toma implementar UBITS Learning?**  
El setup estándar toma 2-3 semanas desde la firma del contrato hasta la activación de los primeros usuarios.

5. **¿En qué países opera UBITS?**  
UBITS opera en Colombia, México, Ecuador, Chile, Perú, Bolivia, Centroamérica y República Dominicana, atendiendo a empresas en 10 países de LatAm.

6. **¿Tienen app móvil?**  
Sí. UBITS Learning tiene app nativa para iOS y Android con búsqueda, zona de estudio y descargas offline.

### FAQs Modulo Desempeno (6)

1. **¿Qué es el módulo de Desempeño de UBITS?**  
Es la solución integrada de evaluaciones 360°, gestión de objetivos y Matriz de Talento (9-box a 25-box) para empresas de 200-10,000 colaboradores.

2. **¿Cómo funciona la IA en las evaluaciones 360?**  
La IA resume automáticamente las respuestas abiertas de los evaluadores, identifica fortalezas y áreas de mejora, y sugiere acciones de desarrollo — eliminando el trabajo manual de consolidar cientos de comentarios.

3. **¿Puedo personalizar la Matriz de Talento?**  
Sí. Desde una matriz simple 2×2 hasta una 25-box. Guarda históricos para análisis longitudinal y exporta reportes para juntas de talento.

4. **¿Se integra con el módulo de Aprendizaje?**  
Sí. Las brechas detectadas en evaluaciones 360 pueden generar automáticamente un Plan de Desarrollo Individual (PDI) en el módulo de Tareas y Planes con cursos sugeridos del catálogo.

5. **¿Cuántas personas pueden evaluar en una 360?**  
Sin límite. Puedes incluir jefes, pares, clientes internos, subordinados y autoevaluación. Configura el peso de cada perspectiva.

6. **¿La información es confidencial?**  
Sí. La privacidad es configurable por pregunta y por evaluador. Los colaboradores ven solo los resultados agregados, no comentarios individuales identificables.

### FAQs Modulo Diagnostico (6)

1. **¿Qué es el módulo de Diagnóstico de UBITS?**  
Es la herramienta de assessments con pruebas psicométricas validadas que detecta brechas de competencias en tu equipo y las conecta automáticamente con planes de formación.

2. **¿Las pruebas psicométricas están validadas?**  
Sí. Todas las pruebas tienen validación psicométrica con metodología publicada, a diferencia de tests gratuitos de internet.

3. **¿Cómo se conecta con el módulo de Aprendizaje?**  
Automáticamente. Cuando se detecta una brecha (ej: "liderazgo 40%"), el sistema sugiere cursos específicos del catálogo para cerrarla.

4. **¿Qué competencias puedo evaluar?**  
Competencias técnicas, blandas, de liderazgo, culturales y operativas. Puedes usar las pre-armadas o crear assessments custom para tu industria.

5. **¿Cuánto tiempo toma completar un assessment?**  
Depende del diseño. Los assessments estándar toman 15-30 minutos por colaborador. Los custom pueden ser más largos o cortos según tus necesidades.

6. **¿Para qué tamaño de empresa funciona?**  
100-5,000 colaboradores. Para empresas más pequeñas, el ROI del assessment psicométrico suele ser menor. Para empresas mayores, funciona por unidad de negocio.

### FAQs Modulo Reclutamiento (6)

1. **¿Qué es el módulo de Reclutamiento de UBITS?**  
Es el primer AITS (Applicant Intelligence Tracking System) 100% construido con IA: entrevistas automatizadas por voz con SerenaAI, scoring de CVs, seguimiento por WhatsApp y feedback automático a candidatos.

2. **¿Cómo funcionan las entrevistas con SerenaAI?**  
SerenaAI llama por voz a los candidatos, les hace preguntas adaptadas al cargo, analiza habilidades blandas y técnicas en tiempo real, y entrega una transcripción + puntaje de compatibilidad.

3. **¿En qué idiomas funciona SerenaAI?**  
Actualmente en español. Estamos validando inglés y portugués para 2026.

4. **¿Cómo se integra con WhatsApp?**  
Via WhatsApp Business API. Enviamos recordatorios de entrevista, confirmaciones, notificaciones de estado y feedback post-entrevista automáticamente.

5. **¿Reemplaza completamente al equipo de reclutamiento?**  
No. Automatiza lo operativo (filtros, entrevistas iniciales, seguimiento) para que tu equipo dedique tiempo a decisiones estratégicas: evaluación final, negociación, cultura fit.

6. **¿Para qué tipo de vacantes funciona mejor?**  
Procesos con alto volumen de candidatos: call centers, retail, operaciones, tecnología. Para cargos ejecutivos muy específicos, complementa al equipo humano sin reemplazarlo.

### FAQs Modulo Tareas y Planes (6)

1. **¿Qué es el módulo de Tareas y Planes de UBITS?**  
Es el gestor de tareas y planes de desarrollo del talento que convierte los compromisos (PDIs, planes de clima, sucesión) en acciones visibles con responsables, fechas y trazabilidad real.

2. **¿Cómo se generan PDIs automáticamente?**  
Cuando completas una evaluación 360 en el módulo Desempeño, el sistema detecta las brechas y genera un PDI borrador con tareas sugeridas, fechas y responsables. Tú lo ajustas y asignas.

3. **¿Funciona sin el módulo de Desempeño?**  
Sí. Puedes crear planes desde cero sin una evaluación previa. Útil para planes de onboarding, sucesión, clima, o cualquier iniciativa de desarrollo.

4. **¿Qué tipo de evidencias puedo cargar?**  
Archivos (PDFs, imágenes, videos), enlaces a cursos completados, comentarios de progreso, y integraciones con LinkedIn Learning o certificados externos.

5. **¿Cómo la IA genera planes?**  
Le describes el objetivo (ej: "plan de liderazgo para nuevos gerentes") y la IA propone tareas, cursos del catálogo, fechas sugeridas y métricas de éxito. Tú lo ajustas.

6. **¿Puedo asignar planes masivamente?**  
Sí. Carga masiva con plantilla Excel o replicación automática desde un template guardado.

### FAQs Modulo Encuestas (6) — NUEVA

1. **¿Qué es el módulo de Encuestas de UBITS?**  
Es la suite de medición de clima organizacional que incluye eNPS, encuestas de clima y cultura, y encuestas personalizadas — todo con confidencialidad garantizada tecnológicamente.

2. **¿Qué es eNPS y cómo se calcula?**  
eNPS (Employee Net Promoter Score) es la pregunta "¿Recomendarías esta empresa para trabajar?" con escala 0-10. Se calcula: % Promotores (9-10) menos % Detractores (0-6). Arriba de +20 es bueno; abajo de 0 indica problemas.

3. **¿La confidencialidad es real?**  
Sí. Técnicamente garantizada. Los administradores ven resultados agregados por área/equipo (mínimo 5 personas por grupo para preservar anonimato), nunca respuestas individuales.

4. **¿Con qué frecuencia debería medir clima?**  
eNPS: trimestral. Clima completo: anual. Encuestas específicas (post-evento, post-iniciativa): cuando sea relevante. La plataforma permite automatizar cualquier cadencia.

5. **¿Puedo comparar resultados entre áreas?**  
Sí. Los reportes permiten filtrar por área, país, nivel de cargo, antigüedad y otros atributos custom. Identificas exactamente dónde está el problema.

6. **¿Cómo convierto resultados en acciones?**  
El módulo se integra con Tareas y Planes para generar planes de acción por área basados en los resultados. Ej: "Ventas tiene eNPS -10, crear plan de comunicación interna con 5 acciones en 90 días."

---

## 9. Checklist pre-publicacion (QA)

### Tecnico

- [ ] GTM snippet presente en `<head>` de todas las paginas (verificar con View Source)
- [ ] GTM container `GTM-5C9SS9Q` funcionando (Preview mode)
- [ ] Eventos clave configurados en GA4 como "Conversions"
- [ ] Google Search Console — property verification activa
- [ ] Sitemap XML actualizado (`/sitemap.xml`) con todas las paginas canonicas
- [ ] Robots.txt permite indexacion (`User-agent: * / Allow: /`)
- [ ] 301 redirects configurados y probados con `curl -I`
- [ ] HTTPS en todas las paginas (no mixed content)
- [ ] Core Web Vitals — LCP <2.5s, CLS <0.1, INP <200ms
- [ ] Mobile responsive en los 6 modulos + homepage
- [ ] Form de demo funcional (submit llega a HubSpot + GA4)
- [ ] Integracion HubSpot — forms conectados a pipeline

### Contenido

- [ ] 6 modulos con paginas activas (incluye `/modulos/encuestas` creada)
- [ ] Copy de cada modulo sigue estructura GEO (H1, tagline, problema, features, para quien, diferenciacion, FAQs)
- [ ] FAQs UNICAS por modulo (no copy-paste)
- [ ] Metricas unicas por modulo (93%/71%/82% solo en Aprendizaje, cada modulo con sus propias stats)
- [ ] Testimonios distribuidos correctamente (no los mismos Sodimac+Alsea en todos lados)
- [ ] Homepage dice "6 modulos" (no "4 modulos")
- [ ] `/skilled` actualizado con temporada 2026 (no feb 2024)

### SEO

- [ ] Schema Organization en root
- [ ] Schema SoftwareApplication por modulo (6 paginas)
- [ ] Schema FAQPage por modulo (coincidiendo con FAQs visibles)
- [ ] Schema BreadcrumbList en todas las paginas internas
- [ ] Schema Article en todos los blogs (327 posts)
- [ ] Title + meta optimizados en las 4 paginas top (ubits-para-tu-empresa, comunidad, recursos, blog habilidades)
- [ ] Alt text en todas las imagenes
- [ ] Internal linking correcto (modulos linkean entre si, blogs linkean a modulos relevantes)
- [ ] Lastmod en sitemap actualizado a 2026-04-30 (relanzamiento date)

### Analytics

- [ ] Key events marcados como "Conversions" en GA4 Admin
- [ ] Audiencias custom creadas (ver seccion 3)
- [ ] Google Ads linked a GA4 (para futuras campañas)
- [ ] HubSpot tracking code instalado
- [ ] UTM parameters definidos para campañas (template en `data/nueva_data/gwt-naming-system/`)

### QA funcional

- [ ] Visita homepage en Chrome, Edge, Safari, Firefox
- [ ] Mobile test en iPhone + Android (al menos 3 dispositivos)
- [ ] Flujo demo completo end-to-end: homepage → modulo → form → submit → thank you
- [ ] Flujo newsletter end-to-end
- [ ] Flujo blog → CTA a modulo → demo
- [ ] Videos cargan (verificar si es Firewall Vimeo — probablemente migrar a YouTube)

---

## 10. Plan post-relanzamiento

### Mayo 2026 — Consolidacion

- [ ] Primera semana: monitorear que tracking funcione (demos medidos correctamente)
- [ ] Snapshot GA4 post-relanzamiento (para medir delta vs baseline 2026-04-15)
- [ ] Activar Google Ads con credito $350 (keywords top 10 actuales)
- [ ] Reactivar email marketing mensual con UTMs correctas
- [ ] A/B test de formulario (3 vs 4 vs 6 campos)

### Junio 2026 — Optimizacion

- [ ] Analizar resultados del A/B test de formulario
- [ ] Implementar ganador del A/B test
- [ ] Lanzar campañas en Dominican Republic + El Salvador (mercados sub-explotados con alta conversion)
- [ ] Revisar Chile (41K users, solo 1.36% conversion — investigar causa)
- [ ] Segundo batch de schema markup (casos de exito, industrias)

### Q3 2026 — Expansion

- [ ] Replicar formato `/becas-ia-*` para 2-3 verticales nuevos
- [ ] Optimizar cluster `/habilidades/*` (contenido pillar page)
- [ ] Lanzar programa de referidos
- [ ] Iniciar content marketing estacional (navidad, amor y amistad, vuelta a clases)

### KPIs de exito del relanzamiento

Medicion a 90 dias post-relanzamiento vs baseline:

| KPI | Baseline (2026-04-15) | Target (Jul 2026) | Stretch (Oct 2026) |
|-----|----------------------:|------------------:|-------------------:|
| Demos/mes | 26 | 60 | 150 |
| Newsletter signups/mes | 59 | 150 | 300 |
| CTR organico | 9.29% | 11% | 13% |
| Tiempo medio/sesion | 16s | 30s | 60s |
| Form completion rate | 1.48% | 15% | 30% |
| Paid traffic/mes | 8 users | 500 users | 2,000 users |
| Paginas modulo tracked | 5 | 6 | 6 |

---

## 📎 Referencias del plan

### Data raw (para defender cada numero)
- [Snapshot metadata](../data/raw/ga4/2026-04-15/snapshot-metadata.md) — 26 archivos indexados
- [Landing pages SEO](../data/raw/ga4/2026-04-15/21-landing-pages-anuales.md)
- [Canales con conversion](../data/raw/ga4/2026-04-15/17-canales-anuales-keyevents.md)
- [Queries SEO](../data/raw/ga4/2026-04-15/22-search-console-queries-anual.md)
- [Demografia](../data/raw/ga4/2026-04-15/26-demografia-completa-anual.md)

### Documentos relacionados
- [Brief ejecutivo para Juan](2026-04-15-brief-ejecutivo-juan.md)
- [Indice maestro](2026-04-15-INDEX-relanzamiento.md)
- [Contexto producto UBITS](../ops/01_identidad-ubits/modulos-contexto-completo.md)
- [Argumentario Maria](../ops/09_sales-enablement/argumentario-modulos-rrhh.md)
- [Estrategia GEO](../ops/07_organico/geo-estrategia.md)
- [Arquitectura Webflow](../ops/11_website/01_arquitectura-webflow.md)

### Configuraciones externas
- GTM Container: `GTM-5C9SS9Q` (production)
- GTM Container MVPs: `GTM-W5QD6DLS`
- Webflow: ubits-com.design.webflow.com
- HubSpot: cuenta UBITS
- GA4: property UBITS Marketing Site

---

*Plan tactico generado 2026-04-15. Se actualiza con cada iteracion post-relanzamiento.*
