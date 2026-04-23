# 📊 Informes del Equipo (Shared Reports)

Bienvenido a la carpeta de **Informes de Crecimiento para el Equipo**. 

Esta carpeta contiene **exclusivamente informes limpios y procesados**, listos para ser consumidos y compartidos con stakeholders, equipo de marketing, producto y ventas.

> **Importante:** Aquí **NUNCA** se almacenarán datos sensibles, contraseñas, listados con PII (Personal Identifiable Information), IPs, correos de clientes no procesados, o información cruda de los scrapers/GA4. Toda la data cruda y confidencial se mantiene aislada en `../data/raw/` o bajo el sistema de secretos.

## 📂 Estructura

- **/analytics/**: Resúmenes ejecutivos de tráfico, conversión, embudos (funnels) y rendimiento de campañas.
- **/seo/**: Reportes de salud del sitio, progreso de indexación, y oportunidades de palabras clave (long-tail, B2B).

## 🔄 Flujo de Trabajo

1. La IA y los motores extraen datos crudos y los guardan en la carpeta maestra protegida (`data/`).
2. Analizamos esos datos y generamos insights estratégicos.
3. Se redactan versiones ejecutivas y limpias (sin ruido técnico) y se guardan aquí para el equipo.

## 🖼️ Cómo añadir pantallazos (Imágenes)
Para hacer los informes mucho más visuales y respaldados con datos reales, hemos creado la carpeta `/assets/`.

1. **Guarda tu pantallazo** (ej. de Google Analytics o HubSpot) en la carpeta `informes_equipo/assets/analytics/` con un nombre claro, como `ga4-trafico-abril.png`.
2. **Inserta la imagen** en tu reporte `.md` usando este código estándar de Markdown:
   ```markdown
   ![Gráfica de tráfico en GA4](../assets/analytics/ga4-trafico-abril.png)
   ```
3. *(Opcional)* Si quieres **controlar el tamaño** de la imagen en GitHub para que no sea inmensa, usa HTML en su lugar:
   ```html
   <img src="../assets/analytics/ga4-trafico-abril.png" width="600" alt="Gráfica de tráfico en GA4">
   ```
