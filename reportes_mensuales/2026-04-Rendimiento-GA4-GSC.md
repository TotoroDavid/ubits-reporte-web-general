# Reporte de Rendimiento Web UBITS (GA4 + GSC)
**Período analizado:** 1 de marzo – 22 de abril de 2026

## 1. Resumen Ejecutivo de Tráfico
El sitio Ubits.com registró un total de **164,578 sesiones** con **140,065 usuarios** en el período analizado. La semana de mayor tráfico fue la del 2–8 de marzo con 24,457 sesiones, probablemente asociada a un impulso de campañas de captación.

---

## 2. Métricas Globales GA4

| Métrica | Valor total / promedio |
|---|---|
| **Sesiones totales** | 164,578 |
| **Usuarios totales** | 140,065 |
| **Usuarios nuevos** | 66,809 (48.4% del total) |
| **Páginas vistas** | 202,327 |
| **Eventos totales** | 709,058 |
| **Tasa de engagement** | 34.7% promedio |
| **Tasa de rebote** | 65.3% promedio |

> **Insight:** La tasa de rebote del 65.3% es consistente a lo largo de todo el período, sin grandes variaciones semanales, lo que sugiere un patrón estable de comportamiento de usuarios. Semanas como las de Semana Santa (finales de marzo / inicio de abril) muestran caídas naturales de volumen esperadas en B2B.

---

## 3. Rendimiento por Semana

| Semana | Sesiones | Usuarios | Usuarios Nuevos | Eventos |
|---|---|---|---|---|
| Feb 23 – Mar 1 | 1,182 | 1,035 | 575 | 5,422 |
| Mar 2–8 | 24,457 | 21,287 | 12,086 | 101,645 |
| Mar 9–15 | 21,111 | 17,948 | 8,614 | 93,250 |
| Mar 16–22 | 21,881 | 18,395 | 8,572 | 97,162 |
| Mar 23–29 | 23,589 | 19,880 | 8,917 | 102,721 |
| Mar 30 – Abr 5 | 16,353 | 13,879 | 6,292 | 70,481 |
| Abr 6–12 | 21,642 | 18,417 | 8,287 | 93,399 |
| Abr 13–19 | 23,154 | 19,543 | 9,152 | 98,093 |
| Abr 20–26 (parcial) | 11,209 | 9,681 | 4,314 | 46,885 |

---

## 4. Búsqueda Orgánica (Google Search Console)
Los datos de GSC muestran que el tráfico orgánico está altamente concentrado en **búsquedas de marca**. La query "ubits" genera 30 clics desde la home con 53,723 impresiones (CTR: 0.06%) y posición promedio 9.2 en resultados.

| Query | Clics | Impresiones | CTR | Posición |
|---|---|---|---|---|
| ubits (home) | 30 | 53,723 | 0.06% | 9.2 |
| ubits (comunidad) | 16 | 36,089 | 0.04% | 1.0 |
| ubits login | 14 | 3,133 | 0.45% | 5.8 |
| ubits learning | 4 | 2,316 | 0.17% | 3.2 |
| ubits cursos | 3 | 955 | 0.31% | 1.2 |

> **Insight SEO:** La página `/comunidad-de-aprendizaje` captura la mayoría de clics de intención navegacional (login). Hay una **oportunidad importante**: las queries de marca tienen CTR muy bajos desde la home (0.06%), indicando que los usuarios no están encontrando fácilmente la página principal en resultados de búsqueda.

---

## 5. Estado del Tracking (GTM + GA4)
Conforme a las notas de implementación, el contenedor de GTM está correctamente instalado en todas las páginas clave: home, productos/módulos, landings de demo, pricing y blog. Los eventos activos incluyen `form_submit_lead`, clics en CTAs de demo y engagement profundo en páginas de producto.

> **🚨 Observación Crítica:** El campo `conversions` en GA4 devuelve **0 para todos los días** del período. Los eventos de formulario y CTA se registran correctamente como eventos, pero **aún no están declarados como conversiones en GA4**. 

---

## 6. Acciones Prioritarias Recomendadas
1. **Declarar conversiones en GA4**: Marcar `form_submit_lead` y CTAs de demo como *key events/conversiones* para activar el bidding inteligente en campañas pagadas.
2. **Mejorar CTR orgánico de la home**: Optimizar el title tag y meta description para queries de marca directa (posición 9.2 con 53k impresiones es tráfico potencial perdido).
3. **Completar tracking pendiente**: Formularios emergentes del blog y formularios de descargables secundarios.
4. **Investigar caída Semana Santa**: La semana 30 Mar – 5 Abr registró 30% menos sesiones; validar si hubo pausa de campañas pagadas o es comportamiento estacional normal.
