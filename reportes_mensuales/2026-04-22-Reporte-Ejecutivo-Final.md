# 📊 Reporte de Desempeño Digital — Ubits.com
### Período: 1 marzo – 22 abril 2026 | Fuentes: GA4 + Google Search Console
---
## 🔍 ¿Qué está pasando con el tráfico?
El sitio recibe en promedio **~21,000 sesiones semanales** en semanas laborales normales, con un pico de **24,457 sesiones** en la primera semana de marzo. La semana del 30 de marzo al 5 de abril bajó un 22% vs. el promedio, atribuible a Semana Santa — comportamiento esperado en audiencias B2B.

**Lo más importante a entender:** todo el tráfico que llega al sitio viene de personas que ya conocen Ubits. El sitio aún **no está atrayendo demanda nueva** de forma orgánica.

---
## 📉 El gran problema: el blog rankea, pero nadie hace clic
Las páginas del blog de Ubits aparecen en miles de búsquedas en Google, pero los usuarios no entran. Esta brecha entre impresiones (cuántas veces aparece el sitio) y clics (cuántas veces entran) es la principal oportunidad de mejora.

| Tipo de contenido | Impresiones | Clics | CTR |
|---|---|---|---|
| Marca / Home | 19,172 | 9,062 | **47.3%** ✅ |
| Blog informacional | ~82,358 | ~834 | **~1.0%** 🔴 |
| Módulos / Producto | 12,363 | 361 | **2.9%** 🟡 |
| Industrias / Gobierno | 7,519 | 34 | **0.5%** 🔴 |

El blog acumula más de **82,000 impresiones** en el período — Google está mostrando el contenido de Ubits a decenas de miles de personas — pero el CTR promedio es menor al 1%. Esto se resuelve con una optimización de títulos SEO y meta descriptions, **sin necesidad de crear contenido nuevo**.

---
## 🎯 Las páginas con mayor oportunidad inmediata (Quick Wins)
Estas son las páginas donde el volumen ya existe pero el CTR es bajo — si se mejoran los títulos y descripciones, el tráfico puede crecer de inmediato sin inversión adicional:

| Página | Impresiones | CTR actual | CTR posible | Clics potenciales |
|---|---|---|---|---|
| `/blog/ejemplos-habilidades-tecnicas-y-blandas` | 20,807 | 0.3% 🔴 | 3% | +600 clics/período |
| `/blog/top-10-habilidades-profesionales` | 10,040 | 0.4% 🔴 | 3% | +260 clics/período |
| `/blog/cursos-online-mas-vendidos` | 9,721 | 0.4% 🔴 | 3% | +250 clics/período |
| `/blog/que-es-capacitacion-corporativa` | 5,879 | 1.0% 🟡 | 4% | +175 clics/período |
| `/blog/importancia-pausas-activas` | 5,086 | 1.0% 🟡 | 4% | +150 clics/período |

---
## 🌎 Situación por Mercados LATAM
Colombia y México son los dos mercados con más visibilidad, pero México tiene un problema grave: **44,251 impresiones con solo 5.6% de CTR** vs. Colombia que logra 10.7% con menos impresiones. Perú también aparece con 17,336 impresiones y apenas 2.3% CTR.

| País | Clics | Impresiones | CTR | Estado |
|---|---|---|---|---|
| Colombia | 2,955 | 27,707 | 10.7% | ✅ Bien |
| México | 2,460 | 44,251 | **5.6%** | 🟡 Suboptimal |
| Ecuador | 1,153 | 9,539 | 12.1% | ✅ Bien |
| Chile | 588 | 16,320 | **3.6%** | 🔴 Oportunidad |
| Perú | 407 | 17,336 | **2.3%** | 🔴 Oportunidad |
| Honduras | 566 | 2,297 | 24.6% | ✅ Excelente |

---
## ⚠️ Punto Crítico: Las conversiones están en CERO en GA4
Este es el hallazgo más urgente de todo el reporte. A pesar de que los eventos de formulario (`form_submit_lead`) y los clics en CTAs de demo están correctamente instalados en GTM, **ninguno está declarado como conversión en GA4**. El campo de conversiones devuelve 0 para todos los 53 días del período.

**¿Qué significa esto en la práctica?**
- Google Ads y Meta **no pueden optimizar sus campañas** porque no reciben señal de conversión.
- No hay forma de calcular CPL (Costo por Lead) real en ninguna plataforma.
- El bidding automático de las campañas está "ciego" — gastando presupuesto sin saber qué funciona.
- No es posible medir cuál canal, página o campaña genera más leads.

---
## ✅ Plan de Acción Priorizado

### 🔴 Urgente (esta semana)
1. **Declarar conversiones en GA4**: Marcar `form_submit_lead` y los eventos de clic en demo como Key Events en la interfaz de GA4 → activa optimización de campañas pagadas de inmediato.
2. **Conectar conversiones a Google Ads y Meta**: Una vez declaradas en GA4, importarlas a Google Ads para activar Smart Bidding por CPL.

### 🟡 Corto plazo (próximas 2–3 semanas)
3. **Optimizar títulos SEO y meta descriptions del blog**: Priorizar las 5 páginas con alto volumen de impresiones y CTR bajo — potencial de +1,000 clics orgánicos adicionales por período sin costo.
4. **Completar tracking pendiente**: Formularios emergentes del blog y formularios de descargables secundarios para tener visibilidad completa del funnel de contenidos.
5. **Revisar estrategia para México y Perú**: Son los mercados con mayor volumen de impresiones y CTR más bajo — posible desalineación entre el contenido y la intención de búsqueda local.

### 🟢 Mediano plazo (próximo mes)
6. **Crear contenido orientado a demanda no-brand**: El sitio actualmente no captura búsquedas del tipo "plataforma capacitación empresarial", "LXP para empresas", "software de e-learning corporativo" — keywords transaccionales con intención de compra.
7. **Configurar micro-conversiones adicionales**: Scroll profundo en páginas de producto, interacción con acordeones y tabs, reproducción de videos — para nutrir el modelo de atribución completo.
