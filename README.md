# Analizador de PYMEs

Herramienta para analizar la salud financiera de pequeñas y medianas empresas.

## Qué hace
- Calcula margen bruto, ratio de endeudamiento y facturación por empleado
- Asigna un nivel de riesgo financiero (bajo, medio, alto)

## Estado actual Semana 1
Versión 0.0 — análisis de una empresa individual con diccionario Python

## Estado actual — Semana 2
- Analiza 5 empresas simultáneamente con pandas
- Calcula 4 ratios financieros automáticamente
- Filtra y ordena empresas por criterios de inversión
- Comparativa sectorial con groupby
- Exporta resultados a CSV y Excel

## Analizador de PYMEs v0.1 — completado Semana 4
### Qué hace
- Analiza 7 empresas de distintos sectores
- Calcula 5 ratios financieros automáticamente
- Asigna scoring de riesgo con pd.cut()
- Genera ranking de oportunidades con puntuación 1-8
- Exporta a Excel con dos hojas (Ranking y Datos)

----------------------------------------------------------------------

## Analizador de PYMEs v0.2 — en progreso (Mes 2)
### Novedades respecto a v0.1 Semana 1
- Análisis estadístico completo del conjunto (describe, std, percentiles)
- Matriz de correlaciones entre variables financieras
- Análisis estadístico por sector (media, mediana, dispersión)
- Scoring por percentiles — más robusto que el scoring manual
- 9 empresas de 7 sectores distintos
- Dashboard visual con 4 gráficos matplotlib: ranking, scatter, histogramas, comparativa sectorial

## Dashboard visual Semana 2

![Dashboard PYMEs v0.2](dashboard_pymes_v02.png)

El dashboard incluye:
- Ranking de oportunidades coloreado por nivel de riesgo
- Mapa de margen vs deuda (scatter plot)
- Distribución estadística del margen bruto (histograma)
- Score medio por sector (comparativa sectorial)

## Visualización interactiva — Semana 3

4 gráficos interactivos generados con Plotly. Descarga los archivos HTML y ábrelos en el navegador para explorarlos.

- **ranking_interactivo.html** — Ranking de las 9 empresas por score, filtrable por nivel de riesgo
- **scatter_interactivo.html** — Mapa de oportunidades margen vs deuda, coloreado por sector con hover completo
- **radar_empresas.html** — Perfil financiero comparativo de las 2 mejores empresas en 5 dimensiones
- **dashboard_interactivo.html** — Dashboard completo con ranking y scatter en dos paneles

Novedades respecto a Semana 2
- Gráficos HTML interactivos: hover, zoom y filtrado por sector desde la leyenda
- Radar chart con normalización de variables para comparativa multidimensional
- Dashboard interactivo exportable y compartible como archivo HTML
