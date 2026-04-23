# Plantilla Reporte GA4 y GTM

Esta es la estructura oficial y mejores prácticas para presentar reportes claros, visuales y ejecutivos sobre el estado de la web de UBITS. 

El foco principal debe dividirse siempre en dos pilares:
1. **Rendimiento del sitio (GA4)**
2. **Estado del seguimiento y configuración (GTM y GTA)**

---

## 1. Estructura general del reporte

Todo reporte web debe mantener este formato de 3 secciones (ya sea en documento o presentación):

* **Resumen ejecutivo** (1 página / slide)
* **Rendimiento del sitio en GA4** (4–6 páginas / slides)
* **Estado del tracking en GTM y GTA** (2–3 páginas / slides)

---

## 2. Cómo presentar el estado de GA4 (Rendimiento)

*Nota: Aquí se habla de **resultados**, no de configuración técnica.*

### Elementos clave a incluir:

* **Tráfico general**
    * Visitas, usuarios únicos, sesiones y duración media.
    * Gráfico de tráfico vs. el mes anterior.
* **Canal de adquisición**
    * Orgánico, directo, social, referido, pago.
    * Explicación rápida de qué canal está creciendo o cayendo.
* **Páginas principales**
    * Top 5–10 páginas (vistas de página, porcentaje de rebote, tiempo en página).
* **Conversiones / metas**
    * Eventos principales (leads, contactos, descargas, clics a CTA, etc.).
    * Tasa de conversión o número de conversiones por canal.

**🗣️ Ejemplo de redacción ejecutiva:**
> *"Durante el mes, el sitio recibió 10.500 sesiones, con un incremento del 18% frente al mes anterior. El 35% proviene de tráfico orgánico de Google y el 22% de social. El formulario principal generó 132 leads, lo que representa una tasa de conversión del 12,5%."*

---

## 3. Cómo presentar el estado de GTM y GTA (Tracking)

*Nota: Aquí **no se explica todo el flujo técnico**, sino **si el seguimiento está bien o si hay riesgos**.*

### Sugerencia de subtítulos:

* **Estado general del tracking**
    * GTM funcionando correctamente en el sitio (todas las páginas, sin errores 404).
    * Todas las etiquetas principales (GA4, Facebook Pixel, etc.) activas y publicadas.
* **Estatus de eventos seguidos**
    * Qué eventos están bien configurados (ej.: clics en CTA, envíos de formularios, scroll, clics en botones).
    * Qué eventos están pendientes o rotos (con enlaces o capturas donde se vea el error).
* **Hallazgos de Google Tag Assistant (GTA)**
    * GTA no muestra errores en el tag principal de GA4.
    * Si hay errores (tags duplicados, triggers mal configurados), explicarlo como *"requiere revisión técnica"*.

**🗣️ Ejemplo de redacción ejecutiva:**
> *"El tracking está completamente implementado en GTM y el tag de Google Analytics 4 funciona sin errores visibles según Google Tag Assistant. Hemos validado que los eventos clave (formularios, clics en CTA y videos) se registran correctamente. Queremos proponer ajustar tres eventos adicionales la próxima semana para mejorar la medición de conversiones."*
