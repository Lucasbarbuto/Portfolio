# Excel Attendance Tracker

Tracker de asistencia para una serie de workshops, construido en Excel combinando fórmulas de búsqueda/condicionales con Copilot para automatizar la carga y el formato de datos.

> Attendance tracker for a workshop series, built in Excel combining lookup/conditional formulas with Copilot to automate data entry and formatting.

## Problema

Organizás una serie de workshops para una ONG de desarrollo comunitario. Necesitás un sistema que cruce asistentes, contacto y departamento con el registro de presencia por evento, calcule el % de asistencia de cada persona y muestre si cumple el requisito mínimo de su grupo — sin cargar todo a mano por cada evento.

## Qué hice

- Armé una tabla estructurada (Insert > Table) que cruza tres fuentes con **VLOOKUP/XLOOKUP** (contacto y departamento) y **SUMIF** (días de presencia real por persona).
- Calculé el % de asistencia y si cada persona cumple el mínimo requerido por su grupo (varía según departamento).
- Formato condicional en tres capas: semáforo por estado de asistencia (presente/ausente), un color por grupo/departamento, y escala de color sobre los días presentes.
- Dos **PivotTables** con gráficos: tendencia de asistencia por día de la semana, y ranking de grupos/individuos por asistencia promedio.
- Usé **Copilot en Excel** para generar y afinar los prompts que resolvieron buena parte de la carga de datos, el resaltado de duplicados y el formato — no como reemplazo de las fórmulas, sino para acelerar el armado.
- Entregué el tracker completo y su versión como **template reutilizable** (`.xltx`), con los datos de ejemplo cargados.

## Herramientas

Excel (tablas, VLOOKUP/XLOOKUP, SUMIF, formato condicional, PivotTables, gráficos) · Copilot en Excel (prompt engineering para tareas de datos).

## Contexto

Proyecto acumulativo del curso *Excel and Copilot Fundamentals* (Coursera / Microsoft), primer módulo del **Certificado Profesional de Microsoft Excel**. El dataset es el provisto por el curso (asistentes de ejemplo), no datos reales de una ONG.

## Archivos

- [`attendance-tracker.xlsx`](./attendance-tracker.xlsx) — workbook completo
- [`attendance-tracker-template.xltx`](./attendance-tracker-template.xltx) — mismo tracker como template

---

[Volver al portafolio](../../README.md)
