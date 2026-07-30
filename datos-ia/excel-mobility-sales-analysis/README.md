# Excel Mobility Sales Analysis

Limpieza, estandarización y análisis de un dataset de ventas global desordenado, llevado a un workbook con dashboard, 6 PivotTables y hallazgos accionables.

> Cleaning, standardization and analysis of a messy global sales dataset, delivered as a polished workbook with a dashboard, 6 PivotTables and actionable findings.

## Problema

Una empresa global de movilidad (monociclos, scooters y skateboards eléctricos) quiere analizar tendencias de venta por producto y región, identificar a sus mejores vendedores y medir el impacto de los descuentos. El dataset crudo lo hace imposible: filas duplicadas, precios en tres monedas con formato inconsistente y guardados como texto, distancias en dos sistemas de unidades y celdas vacías.

## Qué hice

- **Diagnóstico inicial documentado** antes de tocar nada: 17 filas duplicadas (161 → 144 únicas), 12 valores faltantes en Min Speed, precios en ₹/¥/€ como texto, distancias mezcladas en millas y metros.
- **Limpieza:** eliminación de duplicados por identificador único e imputación de los faltantes (Min Speed es determinista por tipo de producto, así que la imputación es exacta, no estimada).
- **Estandarización:** precios convertidos a una sola moneda (EUR, con tipos de cambio de referencia del BCE documentados en una hoja `Lookups`), unidades al sistema métrico (km/h, km) y columna de ventas netas de descuento.
- **Reestructuración:** dirección separada en calle/ciudad/código postal, país y continente vía tablas de lookup, nombre y apellido combinados, rango de velocidad en formato legible. Las columnas originales quedan ocultas, no borradas.
- **Análisis:** 6 PivotTables y 8 gráficos (ventas por región, tendencia mensual con % MoM, performance trimestral, ranking de vendedores, mix de productos) más un dashboard con 6 KPIs.
- **Hallazgo del análisis propio:** el descuento casi no mueve el volumen — con un 15% promedio de descuento, el uplift en unidades por orden es de apenas +0,16%, y en monociclos es negativo. Se resigna margen sin comprar volumen.
- El flujo de limpieza se armó con prompts a un asistente de IA integrado en Excel, en pasos acotados y verificables: detectar los formatos presentes en la columna primero, convertir por grupo después, validar al final.

## Herramientas

Excel (Remove Duplicates, Text to Columns, tablas de lookup, fórmulas de conversión, PivotTables, gráficos, formato condicional, dashboard de KPIs) · prompting de flujos de limpieza de datos con IA en Excel.

## Contexto

Proyecto acumulativo del curso *Data Cleaning and Processing with Copilot in Excel* (Coursera / Microsoft), segundo módulo del **Certificado Profesional de Microsoft Excel**. El dataset es el provisto por el curso (ventas de ejemplo), no datos reales de una empresa.

## Archivos

- [`mobility-sales-analysis.xlsx`](./mobility-sales-analysis.xlsx) — workbook final: datos limpios, lookups documentados, 6 PivotTables y dashboard
- [`mobility-sales-dataset.xlsx`](./mobility-sales-dataset.xlsx) — dataset original, sin modificar

---

[Volver al portafolio](../../README.md)
