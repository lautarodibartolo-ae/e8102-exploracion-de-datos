# Las bicicletas compartidas de Washington

`bicicletas_washington.csv` tiene los 731 días de 2011 y 2012 del sistema de bicicletas compartidas
Capital Bikeshare, de Washington D.C.: los viajes y el clima de cada día. Una fila es un día.

| Columna | Qué es | Valores |
|---|---|---|
| `fecha` | la fecha, en formato año-mes-día | 2011-01-01 a 2012-12-31 |
| `año` y `mes` | el año y el mes de la fecha | |
| `estacion` | la estación del año, en el hemisferio norte | `invierno`, `primavera`, `verano`, `otoño` |
| `dia_semana` | el día de la semana | `lunes` a `domingo` |
| `feriado` | si es feriado | `sí`, `no` |
| `dia_laboral` | si no es fin de semana ni feriado | `sí`, `no` |
| `clima` | el clima del día | `despejado o parcialmente nublado`, `neblina o nublado`, `lluvia o nieve leve` (21) |
| `temperatura_c` | la temperatura, en °C | 2,4 a 35,3 |
| `sensacion_termica_c` | la sensación térmica, en °C | 4,0 a 42,0 |
| `humedad_pct` | la humedad relativa, en % | 0 a 97,2 |
| `viento_kmh` | la velocidad del viento, en km/h | 1,5 a 34,0 |
| `usuarios_ocasionales` | los viajes de usuarios sin abono | 2 a 3.410 |
| `usuarios_registrados` | los viajes de usuarios con abono | 20 a 6.946 |
| `usuarios_total` | la suma de las dos columnas anteriores | 22 a 8.714 |

## Cuidado con

- No hay celdas vacías, pero la humedad del 10 de marzo de 2011 es 0, un valor imposible para
  Washington: probablemente es un dato faltante cargado como cero.
- Un día se parece al anterior, así que las observaciones no son del todo independientes.
  Mencionalo como una limitación.

## Qué columna sirve para cada punto

| Punto | Columnas posibles |
|---|---|
| 2, media | `usuarios_total` |
| 2, proporción | `dia_laboral`, o los días con lluvia contra el resto |
| 3 | `usuarios_total` o `usuarios_ocasionales` según `dia_laboral`, o según `año` |
| 4 | proporciones: la proporción de días con más de 5.000 viajes, 2011 contra 2012; ANOVA: `usuarios_total` según `estacion` o `clima` |
| 5 | `temperatura_c` y `usuarios_total` |
| 6 | `estacion` y `clima` |
| 7 | Wilcoxon con `usuarios_ocasionales` y `usuarios_registrados`, que son del mismo día |

## Qué cambió respecto del original

El clima está en °C, % y km/h, no dividido por su máximo, y las categorías en castellano. El
`Readme.txt` del archivo original llama primavera a la estación 1, pero va del 21 de diciembre al 20
de marzo: acá es `invierno`, como dice la página de la fuente. La conversión del clima sigue ese
`Readme.txt`: temperatura por 41, sensación térmica por 50, humedad por 100 y viento por 67.

## Fuente

- Página: <https://archive.ics.uci.edu/dataset/275/bike+sharing+dataset>
- Archivo original: `day.csv`, dentro de
  <https://archive.ics.uci.edu/static/public/275/bike+sharing+dataset.zip>
- Licencia: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
- Cita: Fanaee-T, H. (2013). *Bike Sharing* [base de datos]. UCI Machine Learning Repository.
  <https://doi.org/10.24432/C5W894>
