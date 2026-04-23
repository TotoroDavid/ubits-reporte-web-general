---
type: strategy
area: conversion
tags: ['ux', 'conversion', 'v2', '2026-abril']
related:
  - 2026-04-15-INDEX-relanzamiento.md
captured_date: 2026-04-15
---

# Estrategia Maestra UX/UI y Conversión para el Relanzamiento Web 

Este documento sintetiza la estrategia de diseño, arquitectura y conversión para el **Web Relaunch** de UBITS bajo el framework LUMOS, basándonos rigurosamente en la auditoría de datos, el comportamiento real de los usuarios, y el ecosistema B2B de 6 módulos.

---

## 1. El Sesgo del "Efecto Login" 
*(Identificaste el mayor distorsionador de la data)*

Has tocado el punto más crítico del comportamiento SaaS: **la mayoría del tráfico en el Home son usuarios actuales buscando dónde hacer Login**.
*   **El Problema:** Entran a `ubits.com`, hacen clic en "Ingresar", y eso cuenta como un "Bounce" (rebote) e infla las visitas, ocultando cómo se comportan los verdaderos prospectos de RR.HH. (María).
*   **Solución Arquitectónica (Webflow):** El botón de "Ingresar a la plataforma" debe estar aislado visualmente en el top-right corner o en un "Nav bar utility". Debe cumplir su función, pero no debe ser visualmente competitivo con el CTA principal.
*   **Solución de Tracking:** Debemos crear un segmento en GA4 que filtre a todo el que hace clic en "Login" en sus primeros 10 segundos para ver cómo navegan *los verdaderos clientes potenciales*.

---

## 2. Abordar el Problema del Drop-Off ("¿Hasta dónde están llegando?")

La auditoría demostró un tiempo de engagement de tan solo **14 segundos en promedio** anual. No estamos logrando que hagan scroll.

### 2.1. El Above The Fold (Lo primero que se ve)
*   **Hero Section:** No podemos seguir vendiendo capacitaciones genéricas. Según el análisis *Long Tail*, el mercado quiere un "LMS" y "Evaluación de Desempeño".
*   **Copy H1:** "El LMS Corporativo todo-en-uno que desarrolla y retiene tu talento." (O similar, mencionando LMS explícitamente).
*   **El CTA Principal:** En lugar de "Hablar con ventas" (alto nivel de compromiso), deberíamos probar **Micro-interacciones** ("Ver el producto en acción", o un Demo Interactivo como SerenaAI). 

### 2.2. Product-Led UI (Mostrar el Software)
*   Las grandes fallas de los SaaS es usar fotos de stock de "empleados sonriendo". Los compradores técnicos de Recursos Humanos quieren **ver cómo luce** la plataforma.
*   **Animación Estratégica:** En lugar de animaciones decorativas, usar componentes interactivos (scroll-jacking o tabs de LUMOS) que muestren *Intranalytics*, *Planes de Desarrollo Individual (PDI)*, y el *Skill Gap Dashboard*. Esto aumenta el _Time on Page_.

---

## 3. Embudos (Funnels) Separados por Intención

Al tener tráfico tan variado (empleados buscando leyes, estudiantes buscando Excel, y HR buscando software), debemos estructurar los caminos desde arriba:

| Tipo de Tráfico | Punto de Entrada | Estrategia de Conversión (CTA) | Ubicación ideal |
| :--- | :--- | :--- | :--- |
| **Directivo RR.HH** | Home, /modulos, Paid Ads | Demo Request / Agenda con Ventas / Hubspot | Nav bar, Sticky Footer, Mitad de Modal. |
| **Investigador B2B** | Alternativas, Casos de Estudio | Descarga de recursos pesados (Reportes de Industria de Talentos) | Botones secundarios. |
| **Lector Casual (Blog)** | Blogpost (vacaciones, excel) | **Suscripción al Newsletter!** (Recordemos que el Email es tu mejor canal: 8.8% Conv. Rate). | Slide-ins laterales discretos. |

> **Regla de ORO:** No interrumpas un artículo de "Trucos de Excel" con un pop-up que dice "Compra un LMS". Córtalo con "Suscríbete al top semanal de Productividad", y luego nútrelos por correo.

---

## 4. Diseño del Botón y el Punto de Conversión (Formulario)

*   **Estado de Falla Actual:** Sabemos que el *trigger* "Abrir form demo" GTM y GA4 está roto desde abril y las `demo_request` están en 1 (vs un promedio de 10-20 semanales). 
*   **La Solución en el Relanzamiento:** 
    1.  **Reducción de Campos:** El buyer B2B de LatAm abandona rápido formularios de 6 campos. Pedir únicamente: *Email corporativo* y *Tamaño de la Empresa*. 
    2.  **UI/UX:** El formulario no debe sacar al usuario de la página (no enviar a `/contacto`). Debe ser un modal pop-up nativo de Webflow o embeberse usando iframes de HubSpot pero con styling in-house (Lumos Utility Classes) para mantener la velocidad de carga.

## 5. Próximos pasos Tácticos

Para trasladar esto a la cancha de Webflow + LUMOS, sugiero estructurar los sprints así:
1.  **Levantamiento Visual:** Maquetar la navegación (Nav) con los 6 módulos separados (Aislamiento B2B).
2.  **Implementación LUMOS:** Instanciar la página `Home` y `Modules Template` usando las clases nativas y aplicar los copies optimizados del SEO Report.
3.  **Data Layer Integrado:** Desde el primer día que se arme Webflow, a los botones (Login, Demo, Descargable) se les inyecta un `data-tracking="login"` para que Tag Manager no se vuelva a romper.
