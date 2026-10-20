# Los pacientes cardíacos de Cleveland

`corazon_cleveland.csv` tiene 303 pacientes que la Cleveland Clinic Foundation, en Estados Unidos,
estudió por sospecha de enfermedad coronaria en la década de 1980. La angiografía confirma o
descarta la enfermedad. Una fila es un paciente.

| Columna | Qué es | Valores |
|---|---|---|
| `edad` | años cumplidos | 29 a 77 |
| `sexo` | el sexo | `varón`, `mujer` |
| `dolor_pecho` | el tipo de dolor de pecho | `angina típica`, `angina atípica`, `dolor no anginoso`, `asintomático` |
| `presion_reposo` | la presión arterial en reposo, en mm Hg | 94 a 200 |
| `colesterol` | el colesterol en sangre, en mg/dl | 126 a 564 |
| `glucemia_ayunas_alta` | si la glucemia en ayunas supera los 120 mg/dl | `sí`, `no` |
| `ecg_reposo` | el resultado del electrocardiograma en reposo | `normal`, `anomalía ST-T` (4), `hipertrofia ventricular` |
| `frecuencia_maxima` | la frecuencia cardíaca máxima en la prueba de esfuerzo, en latidos por minuto | 71 a 202 |
| `angina_ejercicio` | si la prueba de esfuerzo le provocó angina | `sí`, `no` |
| `depresion_st` | cuánto baja el segmento ST del electrocardiograma con el esfuerzo; la fuente no da la unidad | 0 a 6,2 |
| `pendiente_st` | la pendiente del segmento ST en el pico del esfuerzo | `ascendente`, `plana`, `descendente` |
| `vasos_coloreados` | cuántos vasos principales se ven en la fluoroscopía | 0 a 3 |
| `talio` | el resultado del estudio con talio | `normal`, `defecto fijo`, `defecto reversible` |
| `diagnostico` | el resultado de la angiografía: 0 si ningún vaso principal se estrecha más del 50 %; de 1 a 4, alguno se estrecha más | 0 a 4 |
| `enfermedad` | si la angiografía confirma la enfermedad (`diagnostico` mayor que 0) | `sí` (139), `no` (164) |

## Cuidado con

- La fuente no explica la diferencia entre los valores 1 a 4 de `diagnostico`: usá `enfermedad`.
- Faltan `vasos_coloreados` en cuatro pacientes y `talio` en dos.
- En `ecg_reposo`, `anomalía ST-T` tiene 4 pacientes: en una tabla de contingencia deja
  frecuencias esperadas menores que 5.
- No hay mediciones apareadas: no sirve para Wilcoxon.

## Qué columna sirve para cada punto

| Punto | Columnas posibles |
|---|---|
| 2, media | `colesterol`, `presion_reposo` o `frecuencia_maxima` |
| 2, proporción | `enfermedad` o `sexo` |
| 3 | `frecuencia_maxima` o `colesterol` según `enfermedad` o `sexo` |
| 4 | proporciones: la proporción con `enfermedad`, varones contra mujeres; ANOVA: `frecuencia_maxima` según `dolor_pecho` |
| 5 | `edad` y `frecuencia_maxima` |
| 6 | `dolor_pecho` y `enfermedad`, o `sexo` y `enfermedad` |
| 7 | Mann-Whitney con `enfermedad`, Kruskal-Wallis con `dolor_pecho` |

## Qué cambió respecto del original

Las categorías, que en el original son números, están en castellano. `enfermedad` sale de
`diagnostico`, y los `?` son celdas vacías.

## Fuente

- Página: <https://archive.ics.uci.edu/dataset/45/heart+disease>
- Archivo original: `processed.cleveland.data`, dentro de
  <https://archive.ics.uci.edu/static/public/45/heart+disease.zip>
- Licencia: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
- Cita: Janosi, A., Steinbrunn, W., Pfisterer, M. y Detrano, R. (1989). *Heart Disease* [base de
  datos]. UCI Machine Learning Repository. <https://doi.org/10.24432/C52P4X>
