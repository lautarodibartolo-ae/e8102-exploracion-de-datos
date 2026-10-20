# Los pingüinos de Palmer

`pinguinos_palmer.csv` tiene 344 pingüinos de tres especies, medidos entre 2007 y 2009 en tres islas
del archipiélago Palmer, en la Antártida, por Kristen Gorman (Palmer Station LTER). Una fila es un
pingüino.

| Columna | Qué es | Valores |
|---|---|---|
| `especie` | la especie | `Adelia`, `papúa`, `barbijo` |
| `isla` | la isla donde se lo midió | `Biscoe`, `Dream`, `Torgersen` |
| `largo_pico_mm` | el largo del pico, en milímetros | 32,1 a 59,6 |
| `alto_pico_mm` | el alto del pico, en milímetros | 13,1 a 21,5 |
| `largo_aleta_mm` | el largo de la aleta, en milímetros | 172 a 231 |
| `masa_g` | la masa corporal, en gramos | 2.700 a 6.300 |
| `sexo` | el sexo | `hembra`, `macho` |
| `año` | el año de la medición | 2007, 2008, 2009 |

## Cuidado con

- Dos pingüinos no tienen ninguna medida, y once no tienen el sexo.
- En esta base los barbijos se midieron solo en Dream, y los papúa solo en Biscoe: la tabla de
  `especie` por `isla` tiene casillas en cero. Las frecuencias esperadas pasan igual el mínimo de 5.
- No hay mediciones apareadas: no sirve para Wilcoxon.

## Qué columna sirve para cada punto

| Punto | Columnas posibles |
|---|---|
| 2, media | `masa_g` o cualquiera de las medidas |
| 2, proporción | `sexo` |
| 3 | una medida, comparada entre hembras y machos |
| 4 | proporciones: la proporción de hembras, Biscoe contra Dream; ANOVA: `masa_g` según `especie` |
| 5 | `largo_aleta_mm` y `masa_g` |
| 6 | `especie` e `isla`, o `isla` y `sexo` |
| 7 | Kruskal-Wallis con `especie`, Mann-Whitney con `sexo` |

## Qué cambió respecto del original

Las columnas y las especies están en castellano (Adelie es `Adelia`, Chinstrap es `barbijo`, Gentoo
es `papúa`), y los `NA` son celdas vacías.

## Fuente

- Página: <https://allisonhorst.github.io/palmerpenguins/>
- Archivo original: <https://raw.githubusercontent.com/allisonhorst/palmerpenguins/main/inst/extdata/penguins.csv>
- Licencia: [CC0](https://creativecommons.org/publicdomain/zero/1.0/), dominio público.
- Cita: Horst, A. M., Hill, A. P. y Gorman, K. B. (2020). *palmerpenguins: Palmer Archipelago
  (Antarctica) penguin data*. <https://doi.org/10.5281/zenodo.3960218>. Los datos son de Gorman, K.
  B., Williams, T. D. y Fraser, W. R. (2014), *PLoS ONE* 9(3): e90081.
