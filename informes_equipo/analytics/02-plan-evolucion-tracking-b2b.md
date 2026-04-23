# 🎯 Plan de Acción: Evolución del Tracking GA4 para B2B

**Objetivo:** Transicionar de medir métricas de vanidad (tráfico) a medir **Pipeline Real**.
**Contexto:** Actualmente, UBITS cuenta con un alto volumen de tráfico de Awareness, pero perdemos la trazabilidad en el embudo. Esta implementación está diseñada para mapear las 4 etapas del embudo B2B en LatAm (Awareness → Consideración → Intención → Acción/Expansión).

---

## 🛠️ 1. Eventos Críticos a Implementar (GTM + GA4)

Estos 10 eventos transformarán nuestro Google Analytics en un panel de pipeline de marketing-a-ventas.

### Etapa 1: Awareness (El usuario nos descubre)
*   **`blog_article_read`**: Disparado cuando el usuario hace scroll al 75% en `/blog/` o `/recursos/`. Nos dirá quién realmente lee nuestro contenido, no solo quién abre la URL.
*   **`video_play`**: Reproducción de videos embed (Casos de éxito, demos de producto). Es una señal fuerte de intención que hoy es invisible.

### Etapa 2: Consideración (El usuario nos evalúa)
*   **`product_page_engaged`**: Timer de 30 segundos activo solo en URLs de producto (`/modulos/`). Separa a los curiosos de los evaluadores activos.
*   **`pricing_page_view`**: Visitas a `/precios/` o `/planes/`. La señal de intención comercial más directa del sitio.
*   **`case_study_or_estudio_view`**: Visitas a la sección `/estudios/`. Un usuario que valida socialmente es de alto valor.

### Etapa 3: Intención (El usuario muestra señales de compra)
*   **`demo_form_start`**: Foco en el primer campo del formulario de demo. Necesario para diagnosticar por qué se nos cae la gente al momento de pedir demo.
*   **`demo_form_submit` (🏆 KEY EVENT)**: Envío exitoso de la solicitud. Este es el corazón de nuestra conversión y debe ser exportado a Google Ads.
*   **`newsletter_signup`**: Suscripción al newsletter. Necesario para evaluar la salud de nuestra base de leads top-of-funnel (TOFU).

### Etapa 4: Acción y Expansión (Usuarios activos desde LXP)
*   **`lxp_referral_engaged`**: Sesiones que vienen de `lxp.ubitslearning.com` a páginas de producto. Clave para diseñar flujos de upsell y cross-sell con clientes actuales.
*   **`whatsapp_or_chat_click`**: Clics en los botones de "Hablar con un experto". Vital para LatAm donde muchos leads directos entran por WhatsApp.

---

## 👥 2. Audiencias GA4 para Segmentación y Google Ads

Una vez implementados los eventos, crearemos estas 5 audiencias en GA4 para inyectarlas directamente en Google Ads y LinkedIn Ads:

1.  **Alta intención (Visitó demo pero no envió):** Remarketing ("¿Te quedaste con preguntas?").
2.  **Consideración activa (Vio 2+ páginas de producto):** Nutrición con ads de casos de éxito.
3.  **Blog readers listos para nutrir:** Remarketing con descargables/guías para capturar sus correos.
4.  **Usuarios LXP con interés de expansión:** Coordinación con CRM (Account Management) para upsells.
5.  **Leads activos (Demo solicitada):** Exclusión de campañas de adquisición (ahorro de presupuesto) y creación de "Audiencias Similares" (Lookalikes).

---

## 🚀 3. Prioridad y Cronograma de Ejecución

Esta tabla de prioridades nos asegura tener el sistema funcionando en 1 día de trabajo técnico, para tener data procesable en menos de 30 días.

| Prioridad | Implementación | Herramienta | Tiempo Est. |
|-----------|----------------|-------------|-------------|
| 🔴 **Inmediata** | `demo_form_submit` (Key Event) + Audiencia "Demo solicitada" | GTM + GA4 | 1-2h |
| 🔴 **Inmediata** | `newsletter_signup` (Diagnóstico de tracking) | GTM + GA4 | 1h |
| 🟠 **Alta** | `pricing_page_view` + Audiencia "Alta intención sin envío" | GTM + GA4 | 30m |
| 🟠 **Alta** | `whatsapp_or_chat_click` | GTM | 30m |
| 🟡 **Media** | `blog_article_read` + Audiencia "Blog readers" | GTM + GA4 | 1h |
| 🟡 **Media** | `product_page_engaged` + Audiencia "Consideración activa" | GTM + GA4 | 1h |
| 🟢 **Importante** | `lxp_referral_engaged` + Audiencia "LXP expansión" | GTM + GA4 | 1-2h |
| 🟢 **Importante** | `demo_form_start` (Diagnóstico de abandono) | GTM | 45m |
| ⚪ **Complementario**| `video_play` y `case_study_or_estudio_view` | GTM | 50m |

> *Con estas mejoras instaladas, nuestras reuniones de marketing ya no serán sobre "cuántas visitas tuvimos", sino sobre "cuántos de esos visitantes se movieron al siguiente paso del embudo".*
