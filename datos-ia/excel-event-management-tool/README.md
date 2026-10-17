# Excel Event Management Tool

Herramienta de gestión de eventos en Excel con VBA: formulario de registro de asistentes, previsión de asistencia con FORECAST.ETS, Goal Seek sobre precio y asistentes, y un tablero interactivo con botón de actualización.

> Event management tool built in Excel with VBA: attendee registration form, attendance forecast with FORECAST.ETS, Goal Seek on ticket price and attendance, and an interactive dashboard with a refresh button.

## Problema

El planificador de la cumbre Tech Innovators Summit necesita prever cuánta gente va a asistir al próximo evento, ver si el precio de la entrada alcanza para cubrir los costos y llegar al beneficio objetivo, y seguir las inscripciones en un tablero que se actualice sin rehacer nada a mano. Parte de 100 inscripciones registradas entre noviembre de 2022 y noviembre de 2024.

## Qué hice

- **Base de datos:** tabla estructurada (`tblAttendees`) con los 100 asistentes (contacto, tipo de asistencia, sesión, precio de entrada y fecha de registro) y una columna calculada con el mes de registro. El precio depende solo de la sesión (Cybersecurity 300 €, Data Analytics 450 €, Artificial Intelligence 700 €).
- **Formulario de usuario en VBA (`AttendeeForm`):** controles ActiveX (TextBox, ComboBox, OptionButton, ListBox) y botones Submit, Fetch, Update y Cancel para dar de alta asistentes, recuperarlos por ID y modificarlos, con validación de los datos (por ejemplo, la forma del correo). Código comentado, en módulos separados para los datos y para el tablero.
- **Previsión:** resumen mensual de inscripciones y venta de entradas, y previsión de 12 meses con `FORECAST.ETS` (estacionalidad automática, intervalo de confianza del 95 %), entrenada con los 23 meses completos y contrastada con `FORECAST.ETS` de estacionalidad 12 y `FORECAST.LINEAR`. Resultado: 63 asistentes previstos para los próximos 12 meses.
- **Goal Seek:** con los supuestos del dataset (beneficio objetivo 45.000 €, marketing 9.000 €, costos operativos 4.300 €), el precio medio necesario es de 925,40 € o hacen falta 121 asistentes. Con la asistencia prevista y el precio actual (483 €) el beneficio previsto es de 17.129 €, así que la demanda actual sola no alcanza para llegar al objetivo.
- **Tablero interactivo:** indicadores (asistentes, ingresos, precio medio y beneficio de la selección), tres gráficos dinámicos (ingresos por sesión, asistentes por mes, en línea contra presencial), dos segmentaciones (tipo de asistencia y sesión) y una escala de tiempo, todo conectado. El botón `Actualizar Cuadro de Mando` ejecuta una macro que refresca las tablas dinámicas y los gráficos y vuelve a correr Goal Seek.
- **Reto presupuestario:** una hoja aparte del mismo libro (`Cuadro de Mando Actualizado`) con el escenario de marketing 10.000 €, costos operativos 25.000 € y beneficio objetivo 100.000 € (la consigna dice «100.00 euros» y lo leí como 100.000 €, porque con costos de 35.000 € un objetivo de 100 € no tiene sentido; está aclarado en la hoja). El precio medio necesario es de 2.142,86 € o hacen falta 280 asistentes, y la hoja calcula el precio por sesión que corresponde.
- **Decisión de modelado:** los Goal Seek parten de la asistencia prevista (63) y no de las 100 inscripciones históricas, porque la consigna define los ingresos como precio medio por asistencia prevista y las 100 inscripciones cubren dos ciclos anuales, no un evento. Con las 100 como base el precio necesario sería de 583 €. La hoja `Proyecciones` trae una tabla de sensibilidad con las demás bases.

## Herramientas

Excel (tablas estructuradas, tablas y gráficos dinámicos, segmentaciones, escala de tiempo, FORECAST.ETS, Goal Seek, validación de datos) · VBA (UserForm, controles ActiveX, macros) · asistencia de IA para armar el código y los libros, verificados con scripts propios y una prueba manual en Excel de escritorio.

## Contexto

Proyecto acumulativo del curso *Automation & Advanced Techniques with Copilot in Excel* (Coursera / Microsoft), cuarto curso del **Certificado Profesional Microsoft Excel**. El dataset es el provisto por el curso (asistentes de ejemplo del Tech Innovators Summit), no datos reales. La columna `Dietary Preference` no venía en el dataset: es **sintética** (30 Vegetarian, 28 Non-Vegetarian, 21 Gluten-Free y 21 Vegan, asignadas al azar con semilla fija 20241109) y está declarada como tal en el libro.

## Archivos

Es un libro con macros (`.xlsm`): al abrirlo hay que habilitar el contenido (si Windows lo bloquea, en Propiedades tildar Desbloquear). El formulario necesita Excel de escritorio para Windows.

- [`event-dashboard.xlsm`](./event-dashboard.xlsm): libro único con todo el proyecto (Tareas 1 a 7): base de datos, formulario, previsión, Goal Seek, tablero con su macro y, en la hoja `Cuadro de Mando Actualizado`, el reto presupuestario. Corresponde al segundo de los dos archivos de la entrega en Coursera e incluye todo lo del primero.

---

[Volver al portafolio](../../README.md)
