# Los vinos verdes de Portugal

`vinos_portugal.csv` tiene 6.497 muestras de vino verde portugués (1.599 tintos y 4.898 blancos),
analizadas entre 2004 y 2007. Cada una tiene once mediciones de laboratorio y una nota de calidad, la
mediana de por lo menos tres catadores. Una fila es una muestra.

| Columna | Qué es | Unidad |
|---|---|---|
| `tipo` | `tinto` o `blanco` | |
| `acidez_fija` | la acidez fija | g de ácido tartárico por litro |
| `acidez_volatil` | la acidez volátil | g de ácido acético por litro |
| `acido_citrico` | el ácido cítrico | g por litro |
| `azucar_residual` | el azúcar que queda después de la fermentación | g por litro |
| `cloruros` | los cloruros | g de cloruro de sodio por litro |
| `dioxido_azufre_libre` | el dióxido de azufre libre | mg por litro |
| `dioxido_azufre_total` | el dióxido de azufre total | mg por litro |
| `densidad` | la densidad | g por cm³ |
| `ph` | el pH | |
| `sulfatos` | los sulfatos | g de sulfato de potasio por litro |
| `alcohol` | la graduación alcohólica | % del volumen |
| `calidad` | la nota de los catadores | 0 a 10; en la base va de 3 a 9 |

## Cuidado con

- No hay celdas vacías, pero hay 1.177 filas repetidas en todas las columnas. La fuente no dice si
  son muestras distintas o la misma muestra cargada dos veces.
- Las notas 3 y 9 tienen 30 y 5 muestras: sin agruparlas, una tabla de contingencia deja
  frecuencias esperadas menores que 5.
- Con 6.497 filas casi cualquier diferencia da un valor p chico: acompañá cada test
  con la diferencia estimada y su intervalo.
- No hay mediciones apareadas: no sirve para Wilcoxon.

## Qué columna sirve para cada punto

| Punto | Columnas posibles |
|---|---|
| 2, media | `alcohol` o `ph` |
| 2, proporción | `tipo`, o una calidad de 7 o más contra el resto |
| 3 | `alcohol` o `ph` según `tipo` |
| 4 | proporciones: la proporción con calidad de 7 o más, tintos contra blancos; ANOVA: `alcohol` según `calidad`, agrupando las notas de los extremos |
| 5 | `alcohol` y `densidad`, o `azucar_residual` y `densidad` |
| 6 | `tipo` y `calidad`, agrupando las notas de los extremos |
| 7 | Mann-Whitney con `tipo`, Kruskal-Wallis con `calidad` |

## Qué cambió respecto del original

Los tintos y los blancos, que en el original están en dos archivos, van juntos con la columna `tipo`.

## Fuente

- Página: <https://archive.ics.uci.edu/dataset/186/wine+quality>
- Archivos originales: `winequality-red.csv` y `winequality-white.csv`, dentro de
  <https://archive.ics.uci.edu/static/public/186/wine+quality.zip>
- Licencia: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
- Cita: Cortez, P., Cerdeira, A., Almeida, F., Matos, T. y Reis, J. (2009). *Wine Quality* [base de
  datos]. UCI Machine Learning Repository. <https://doi.org/10.24432/C56S3T>
