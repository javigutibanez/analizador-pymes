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

## Visualización interactiva — Semana 4
### Novedades respecto a Semana 3
- Descarga de datos fundamentales de empresas cotizadas comparables vía yfinance
- Fusión de PYMEs y cotizadas en un único DataFrame con columna tipo
- Gráfico comparativo interactivo de márgenes PYMEs vs cotizadas por sector
- Valoraciones orientativas por comparables sectoriales con descuento de liquidez del 30%
- Exportación a Excel con 4 hojas: Ranking v0.2, Estadística, Por sector, Valoraciones

### Comparables sectoriales utilizados
| Sector | Cotizada | Ticker |
|---|---|---|
| Hostelería | McDonald's | MCD |
| Moda | Inditex | ITX.MC |
| Salud | Fresenius | FRE.DE |
| Educación | Pearson | PSO |
| Ferretería | Fastenal | FAST |
| Gestoría | H&R Block | HRB |

### Archivos de esta semana
- **analizador_pymes_v02.xlsx** — Excel con 4 hojas listo para entregar a un inversor
- **comparativa_pymes_cotizadas.html** — Gráfico interactivo PYMEs vs cotizadas por sector

## ANALIZADOR DE PYMEs v0.2 - COMPLETADO MES 2

### Qué hace
- Analiza 9 empresas de 7 sectores distintos
- Calcula 5 ratios financieros automáticamente
- Estadística descriptiva completa: media, mediana, desviación, percentiles
- Análisis de correlaciones entre variables financieras
- Scoring estadístico por percentiles (más robusto que umbrales manuales)
- Dashboard visual con 4 gráficos: ranking, scatter, histogramas, sectorial
- Dashboard interactivo en HTML con Plotly
- Comparativas sectoriales: márgenes de PYMEs vs cotizadas del mismo sector
- Valoraciones orientativas usando PER sectorial con descuento de liquidez
- Exporta a Excel con 4 hojas y a HTML interactivo
 
### Próxima versión (Mes 3)
- Series temporales: datos de varios años en lugar de un snapshot
- Proyección de KPIs a 12 meses con Prophet
- Detección de estacionalidad en los ingresos

## Analizador de PYMEs v0.3 — MES 3

SEMANA 1 
### Novedades de esta semana
- Dataset temporal con 3 años de datos históricos por empresa (2022-2024)
- Operaciones con DatetimeIndex: filtrado por fecha, crecimiento interanual y media móvil
- Visualización de la evolución de facturación y márgenes por empresa (2 gráficos)
- Ranking de calidad de crecimiento — CAGR × margen como índice compuesto
- Proyección simple de facturación a 2025 basada en CAGR histórico

### Archivos de esta semana
- **evolucion_facturacion.png** — Panel 3x3 con la evolución de cada empresa
- **evolucion_margenes.png** — Evolución comparada de márgenes de las 9 empresas

SEMANA 2
markdown## Analizador de PYMEs v0.3 — Semana 2 

### Novedades de esta semana
- Instalación de Prophet — librería de series temporales de Meta (Facebook)
- Primera proyección de facturación a 12 meses con intervalos de confianza al 80%
- Proyección automatizada en bucle para las 9 empresas simultáneamente
- Tabla de escenarios — pesimista, central y optimista por empresa
- Corrección de escala: datos anuales convertidos a mensuales para Prophet

### Nota técnica
Los datos históricos son anuales. Prophet trabaja con frecuencia mensual (`freq='MS'`),
por lo que los datos se dividen entre 12 al entrenar y la proyección resultante
es directamente comparable con la facturación anual de 2024.

### Archivos de esta semana
- **proyeccion_prophet.png** — Gráfico automático de Prophet de la empresa con mejor CAGR
- **proyeccion_limpia.png** — Gráfico personalizado con banda de confianza al 80%

### Proyección a 12 meses — escenario central
| Empresa | Fact. 2024 | Central proyectado | Crecimiento |
|---|---|---|---|
| Ferretería García | 320.000€ | 326.504€ | +2.0% |
| Clínica Dental García | 295.000€ | 301.504€ | +2.2% |
| Clínica Dental Martínez | 280.000€ | 286.504€ | +2.3% |
| Tienda Moda Sol | 210.000€ | 214.336€ | +2.1% |
| Bar El Rincón | 180.000€ | 184.336€ | +2.4% |
| Academia Idiomas Sol | 160.000€ | 164.336€ | +2.7% |
| Academia English House | 155.000€ | 159.878€ | +3.1% |
| Gestoría Pérez | 140.000€ | 143.794€ | +2.7% |
| Peluquería Ana | 95.000€ | 97.710€ | +2.9% |

SEMANA 3
## Analizador de PYMEs v0.3 — Semana 3 

### Novedades de esta semana
- Detección de anomalías estáticas con z-score — compara las 9 empresas entre sí en 2024
- Bandas de control temporales — detecta cambios bruscos en el margen histórico de cada empresa
- Sistema de alertas consolidado con nivel de riesgo por empresa (Alto / Medio / Bajo)
- Exportación a Excel con 3 hojas: resumen de alertas, detalle z-score y proyecciones Prophet

### Resultados del sistema de alertas — z-score 2024
| Empresa | Variable | Valor | Z-score | Tipo |
|---|---|---|---|---|
| Academia English House | crecimiento_pct | 6.2% | +1.81 | ALTO |
| Tienda Moda Sol | margen_bruto_pct | 33.3% | -1.61 | BAJO |
| Ferretería García | facturacion | 320.000€ | +1.58 | ALTO |
| Ferretería García | margen_bruto_pct | 34.4% | -1.53 | BAJO |

### Interpretación
- **Academia English House** — crecimiento más alto del portfolio, señal positiva a seguir
- **Tienda Moda Sol** — margen más bajo del conjunto, perfil más débil del portfolio
- **Ferretería García** — empresa más grande pero con margen estructuralmente bajo para su sector

### Archivos de esta semana
- **alertas_pymes_v03.xlsx** — 3 hojas: Resumen alertas, Alertas z-score, Proyecciones
- **analizador_pymes_v03_s3.ipynb** — notebook actualizado con bloques 38-40
