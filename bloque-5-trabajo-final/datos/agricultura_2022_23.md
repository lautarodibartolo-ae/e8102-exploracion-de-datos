# Las estimaciones agrícolas de la campaña 2022/23

`agricultura_2022_23.csv` tiene la superficie, la producción y el rendimiento de soja, maíz, trigo
y girasol por departamento en la campaña 2022/23, la de la sequía en la región pampeana. Son estimaciones de la Secretaría de Agricultura, Ganadería y Pesca de la Nación. Una fila
es un cultivo en un departamento: 1.041 filas.

| Columna | Qué es | Valores |
|---|---|---|
| `provincia` | la provincia | 15 provincias |
| `region` | la región de la provincia | `Pampeana` (Buenos Aires, Córdoba, Entre Ríos, La Pampa y Santa Fe), `Noroeste`, `Noreste`, `Cuyo` (31 filas, solo San Luis) |
| `departamento` | el departamento, o el partido en Buenos Aires | |
| `cultivo` | el cultivo | `maíz`, `soja`, `trigo`, `girasol` |
| `superficie_sembrada_ha` | la superficie sembrada, en hectáreas | 0 a 743.500 |
| `superficie_cosechada_ha` | la superficie cosechada, en hectáreas | 0 a 743.500 |
| `produccion_t` | la producción, en toneladas | 0 a 1.891.147 |
| `rendimiento_kg_ha` | la producción por hectárea cosechada, en kg | 0 a 10.900 |
| `rendimiento_2021_22_kg_ha` | el rendimiento de la campaña 2021/22 en el mismo departamento y cultivo, en kg por hectárea | 0 a 12.000 |

## Cuidado con

- En 10 filas el rendimiento de 2022/23 es 0 (en 2021/22, en 6). Son datos, no faltantes, pero pesan
  mucho en una media: decidí qué hacer con ellos.
- En 22 filas `rendimiento_2021_22_kg_ha` está vacío: la fuente no tiene la estimación de ese cultivo en ese departamento en 2021/22.
- La superficie y la producción son muy asimétricas (mediana sembrada de 12.224 ha, máximo de
  743.500). En el punto 5 mirá la dispersión antes de ajustar la recta, y probá con logaritmos.
- Una hectárea de maíz rinde mucho más que una de soja: casi siempre conviene elegir un cultivo.

## Qué columna sirve para cada punto

| Punto | Columnas posibles |
|---|---|
| 2, media | `rendimiento_kg_ha` de un solo cultivo |
| 2, proporción | si el rendimiento de 2022/23 es menor que el de 2021/22, o región pampeana contra el resto |
| 3 | `rendimiento_kg_ha` de un cultivo, región pampeana contra el resto |
| 4 | proporciones: la proporción de departamentos donde el rendimiento cayó, soja contra maíz; ANOVA: `rendimiento_kg_ha` según `cultivo`, o el de un cultivo según `region` |
| 5 | `superficie_sembrada_ha` y `produccion_t` |
| 6 | `cultivo` y `region`, o `cultivo` y si el rendimiento cayó |
| 7 | Wilcoxon con `rendimiento_2021_22_kg_ha` y `rendimiento_kg_ha`, que son del mismo departamento y cultivo |

## Qué cambió respecto del original

El original tiene 160.499 filas, con 41 cultivos desde 1969/70. La soja y el trigo son las filas
`soja total` y `trigo total`, y se agregaron `region` y `rendimiento_2021_22_kg_ha`.

## Fuente

- Página: <https://datos.gob.ar/dataset/estimaciones-agricolas>
- Archivo original:
  <https://datos.magyp.gob.ar/dataset/9e1e77ba-267e-4eaa-a59f-3296e86b5f36/resource/95d066e6-8a0f-4a80-b59d-6f28f88eacd5/download/estimaciones-agricolas-2026-03.csv>
- Licencia: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
- Cita: Secretaría de Agricultura, Ganadería y Pesca de la Nación. *Estimaciones agrícolas*. Datos
  Argentina.
