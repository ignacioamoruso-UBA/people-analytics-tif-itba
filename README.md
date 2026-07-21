# Caso ITBA Talent — Análisis de Reclutamiento Q2 2026

Trabajo de Integración Final · Certificación en People Analytics · ITBA Escuela de Innovación

---

## Resumen

Análisis cuantitativo del pipeline de selección de una software factory (990 candidatos, 30 requisiciones, 23 contrataciones en Q2). El hallazgo central es un problema de **validez de constructo**: el KPI que motivaba la alarma del área —88% de rechazo de ofertas— resultó ser un artefacto de medición, no una crisis de atracción.

## Contexto

ITBA Talent es una compañía de desarrollo de software bajo modalidad de staff augmentation y software factory. Durante Q2, la firma de contratos con clientes Fintech generó un pico de demanda de talento técnico que el área de Talent Acquisition —con capacidad instalada de 2 recruiters semi-senior— debió absorber.

| Métrica | Valor |
|---|---|
| Candidatos procesados | 990 |
| Posiciones abiertas | 30 |
| Contrataciones | 23 |
| Time to fill promedio | 56 días |
| SLA objetivo | 30 días (estándar) / 45 días (senior) |

## Hallazgos

### 1. El 88% de rechazo no mide lo que dice medir

Con 191 ofertas emitidas sobre 30 posiciones de una vacante cada una, el denominador no representa el universo de contrataciones posibles sino los intentos por cupo fijo. Si una posición emite seis ofertas y solo puede incorporar a una persona, las cinco restantes no pueden concretarse con independencia del comportamiento del candidato.

| Indicador | Fórmula | Valor | Lectura |
|---|---|---|---|
| Aceptación de ofertas (actual) | Contrataciones / Ofertas emitidas | 12,0% | Aparente crisis de atracción |
| Cobertura de vacantes (propuesto) | Cubiertas / Abiertas | 76,7% | Desempeño mejorable, no crítico |
| Ofertas por contratación (propuesto) | Ofertas / Contrataciones | 8,3 | Ineficiencia del proceso |

### 2. La lentitud del proceso individual no explica el rechazo

| Decisión | n | Media (días) | Mediana | Desvío |
|---|---|---|---|---|
| Aceptó | 23 | 17,0 | 15,0 | 8,2 |
| Rechazó | 168 | 17,9 | 17,0 | 7,4 |

Diferencia de 0,9 días. El resultado se mantiene incluso en el subgrupo que declaró explícitamente la lentitud como motivo de salida (18,5 días de media). La hipótesis más disponible se descarta empíricamente.

### 3. Existe un umbral de viabilidad en los 70 días

| Días abierta la requisición | Posiciones | Cubiertas | Tasa de éxito |
|---|---|---|---|
| 0 – 35 | 7 | 7 | 100% |
| 36 – 55 | 6 | 6 | 100% |
| 56 – 70 | 8 | 8 | 100% |
| 71 – 90 | 9 | 2 | 22% |

Correlación entre días abiertos y éxito de la búsqueda: **-0,658**. Las 7 posiciones canceladas o vencidas promediaron 82 días abiertas y consumieron 54 ofertas —el 28% del total del trimestre— sin concretar una sola contratación.

La lentitud sí es un problema, pero opera en un nivel distinto al supuesto: no deteriora la decisión del candidato individual, sino que agota la búsqueda como sistema.

### 4. El filtro temprano es deficiente

503 candidatos (50,8% del total ingresado) se descartan por competencias no coincidentes. Ese volumen consume capacidad de entrevista propia y del cliente, dilata la requisición y la aproxima al umbral de fracaso.

Progresión del embudo:

| Etapa | Candidatos | Conversión de etapa | Acumulada |
|---|---|---|---|
| Revisión de perfil | 990 | — | 100,0% |
| Screening de TA | 886 | 89,5% | 89,5% |
| Entrevista Hiring Manager | 778 | 87,8% | 78,6% |
| Envío al cliente | 535 | 68,8% | 54,0% |
| Entrevista con el cliente | 441 | 82,4% | 44,5% |
| Oferta emitida | 191 | 43,3% | 19,3% |
| Contratado | 23 | 12,0% | 2,3% |

### 5. El canal más efectivo está infrautilizado

| Fuente | Candidatos | Ofertas | Contrataciones | Conversión oferta→hire |
|---|---|---|---|---|
| Sourced (búsqueda activa) | 311 (31%) | 57 | 10 | 17,5% |
| Referral | 341 (34%) | 72 | 8 | 11,1% |
| Applied (postulación espontánea) | 338 (34%) | 62 | 5 | 8,1% |

La organización concentra su volumen en el canal menos eficiente. Un canal de mayor conversión reduce la cantidad de tandas de candidatos necesarias y, con ello, la duración total de la requisición.

## Conclusión

No hay un problema de aceptación de ofertas sino de diseño de proceso y de medición. El indicador que concentra la atención del área desvía el diagnóstico hacia una causa inexistente, mientras el factor efectivamente asociado al fracaso —la duración de la requisición— permanece sin intervención específica.

## Recomendaciones

| Recomendación | Indicador de seguimiento |
|---|---|
| Reemplazar el KPI de aceptación por cobertura de vacantes y ofertas por contratación | Cobertura ≥ 90% |
| Alerta temprana a los 55 días con escalamiento obligatorio | % de requisiciones > 70 días |
| Reforzar filtro de competencias con criterios acordados con hiring manager y clientes | % descartes por competencias < 30% |
| Reasignar volumen hacia el canal sourced | Participación de sourced ≥ 45% |
| Revisar con el negocio la viabilidad de perfiles en búsquedas canceladas | Canceladas por trimestre = 0 |

## Limitaciones

- El dataset no contiene información salarial ni sobre la propuesta económica, lo que impide descartar de manera concluyente un componente de competitividad retributiva.
- No se dispone de marcas temporales por etapa del embudo, solo de fecha de inicio y fin del proceso del candidato. Ello impide localizar con precisión dónde se concentra la demora.
- El período corresponde a un único trimestre: no es posible evaluar estacionalidad ni tendencia.
- Los motivos de salida son categorías autodeclaradas y registradas por el reclutador, sujetas a sesgo de atribución.

## Metodología

1. **Recolección** — Integración de datos del ATS y del sistema de requisiciones.
2. **Modelado** — Limpieza, cálculo de variables del embudo y formulación de medidas en DAX para seguimiento de SLA.
3. **Visualización** — Tablero en Power BI para monitoreo de fricción, tiempos de cobertura y SLA.
4. **Insights** — Interpretación para proponer iniciativas estratégicas.

## Stack

Power BI · DAX · Análisis exploratorio y de correlación

## Contenido del repositorio

```
├── README.md
├── informe/
│   └── TIF_Caso_ITBA_Talent.pdf     Informe completo
└── presentacion/
    └── TIF_Presentacion.pdf         Presentación ejecutiva
```

## Autoría

Trabajo grupal — Arancibia Bárbara · Corbo Agustina · Amoruso Ignacio Facundo · Lopez Almeida Gabriela Fredzaida · Rodriguez Julia · Spina Ailen · Carreras Julieta

Julio 2026 · ITBA Escuela de Innovación

