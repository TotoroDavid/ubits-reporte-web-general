## 📊 Reporte de Auditoría de Tracking — Ubits.com
**Fecha de investigación:** 22 de abril de 2026
**Fuentes verificadas:** Inspección directa del sitio ubits.com (home, blog, módulos, páginas de formulario), código fuente embebido en página, Google Search Console (recurso https://www.ubits.com/)

---

### 🔎 Hallazgos verificados en el sitio

#### 1. Contenedor GTM
A partir del código fuente observable en todas las páginas visitadas, **no se detectó un ID de contenedor GTM (GTM-XXXXXX) explícito en el HTML**. Sin embargo, sí se encontró **el método `gtag()` activo**, lo que indica que GA4 podría estar instalado directamente (sin GTM como intermediario) o que GTM lo inyecta pero no es visible en el HTML estático. Esta distinción es relevante: si GA4 se dispara vía `gtag` nativo, el contenedor GTM no es imprescindible, pero sí lo sería para los píxeles de Meta, Google Ads y LinkedIn.

> ⚠️ **Diferencia con el reporte recibido:** Los reportes afirman que GTM está instalado correctamente. No fue posible confirmar visualmente el ID de contenedor `GTM-XXXXXX` en el HTML de ninguna página visitada. Esto puede deberse a limitaciones del entorno de inspección (extensiones de Chrome en conflicto), pero conviene verificarlo directamente en DevTools o con GTM Preview.

---

#### 2. Google Analytics 4 (GA4)
Se confirma la presencia del método `gtag("event", "click_boton_demo", {...})` activo en el código del sitio, en todas las páginas (incluyendo páginas de error 404). Esto **valida la presencia del snippet de GA4 o GTM con configuración de gtag**, aunque el Measurement ID `G-XXXXXXX` no fue recuperable directamente en este contexto.

✅ **Consistente con el reporte recibido** en cuanto a que GA4 está configurado y los eventos de CTA están parcialmente implementados.

---

#### 3. HubSpot Forms (CRM)
Se detectó HubSpot Forms integrado en múltiples páginas con:
- **Portal ID:** `3296735`
- **Form IDs:** `7491ec2e-0ae0-4d49-ad14-a80fbfd3131e` (formulario de demo / contacto comercial) y `891a70de-be06-4385-aefc-b64927c0d560` (boletín de noticias en footer)

Este es el mecanismo principal de captura de leads. Los eventos de `form_submit_lead` mencionados en los reportes deben estar vinculados a estos formularios de HubSpot.

---

#### 4. ActiveCampaign (tracking de visitantes)
Se detectó el script de ActiveCampaign Site Tracking en todas las páginas:
- **Script:** `https://diffuser-cdn.app-us1.com/diffuser/diffuser.js`
- **Account ID:** `611871346`
- Parámetros: `vgo('setTrackByDefault', true)` — tracking activo por defecto

Esto es un hallazgo **no mencionado en los reportes recibidos**. Indica que hay una capa de tracking adicional (ActiveCampaign) que puede estar duplicando o complementando la medición de sesiones y leads.

---

#### 5. Meta Pixel / LinkedIn Insight Tag / Google Ads
**No se pudo confirmar ni descartar** la presencia de estos píxeles en las páginas visitadas, dado que el entorno de inspección JS estaba bloqueado por un conflicto de extensiones de Chrome. Los reportes afirman que están activos en las landings de campañas de captación. Esto requeriría validación directa con GTM Preview o DevTools en un navegador limpio.

---

#### 6. Páginas clave del funnel — Estado crítico encontrado ⚠️

| URL visitada | Estado |
|---|---|
| `/` (Home) | ✅ Activa, tracking presente |
| `/blog` | ✅ Activa, artículos visibles |
| `/modulos/aprendizaje` | ✅ Activa (redirige correctamente) |
| `/solicitar-demo` | ❌ **Página no encontrada (404)** |
| `/pricing` | ❌ **Página no encontrada (404)** |
| `/habla-con-ventas` | ❌ **Página no encontrada (404)** |

> 🚨 **Hallazgo crítico:** Las páginas `/solicitar-demo`, `/pricing` y `/habla-con-ventas` están devolviendo error 404. Estas son páginas clave del funnel mencionadas en los reportes como destinos de conversión. Aunque los CTAs en el sitio pueden apuntar a anchors (`href="#"`) que abren formularios en modal/overlay, estas URLs por sí mismas no tienen contenido. Esto puede significar pérdida de tráfico de pago o campañas que enlacen a estas URLs directamente.

---

#### 7. Google Search Console — Estado de indexación
Desde Search Console se observó:
- **Páginas indexadas: 4** (muy bajo para un sitio de software B2B)
- **Páginas sin indexar: 7.327** con los siguientes motivos principales:
  - Páginas con redirección: 496
  - Bloqueadas por robots.txt: 88
  - No encontradas (404): 14
  - Excluidas con `noindex`: 13
  - Rastreadas pero sin indexar: 105
- **1 URL indexada con advertencia:** "Se ha indexado aunque un archivo robots.txt la tenía bloqueada"

Esto impacta directamente la capacidad de medir tráfico orgánico en GA4, ya que la mayoría del contenido del sitio no está indexado.

---

### ✅ Validación vs. reportes recibidos

| Afirmación del reporte | Estado verificado |
|---|---|
| GTM instalado en páginas clave | ⚠️ No confirmado directamente (posible limitación del entorno) |
| GA4 disparando sin errores | ✅ Parcialmente confirmado (gtag presente) |
| Eventos de CTA de demo configurados | ✅ Confirmado (`click_boton_demo` en código) |
| Píxeles de Meta, Google Ads, LinkedIn activos | ⚠️ No verificable en este entorno |
| Advertencias menores en Tag Assistant | ⚠️ No verificable directamente |
| Landings de "Solicita una demo" y pricing operativas | ❌ **Páginas en 404 — requiere acción urgente** |

---

### 🛠️ Recomendaciones priorizadas

**Inmediato:**
1. **Restaurar o redirigir** las URLs `/solicitar-demo`, `/pricing` y `/habla-con-ventas` — si los CTAs del sitio o campañas de pago apuntan a estas URLs, se está perdiendo tráfico de conversión sin tracking.
2. **Verificar el GTM ID** en un navegador limpio con DevTools (Network tab, buscar `gtm.js?id=GTM-`) para confirmar qué contenedor está activo.

**Corto plazo:**
3. Validar si ActiveCampaign y GA4 están midiendo los mismos eventos sin duplicación.
4. Auditar el estado de indexación en Search Console — con solo 4 páginas indexadas, la visibilidad orgánica es mínima y el tráfico orgánico en GA4 no refleja el potencial real del sitio.
5. Revisar el bloqueo de 88 URLs por `robots.txt` para asegurar que no se estén excluyendo páginas de producto o landings relevantes.
