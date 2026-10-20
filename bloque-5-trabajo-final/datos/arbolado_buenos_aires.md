# Los árboles de los parques de Buenos Aires

`arbolado_buenos_aires.csv` tiene 2.000 árboles de parques y plazas de la Ciudad de Buenos Aires,
del relevamiento del Gobierno de la Ciudad. Es una muestra aleatoria simple de 400 árboles de cada
una de las cinco especies más comunes. Una fila es un árbol.

| Columna | Qué es | Valores |
|---|---|---|
| `id_arbol` | el número del árbol en la base original | |
| `especie` | el nombre común | `Eucalipto`, `Tipa blanca`, `Jacarandá`, `Palo borracho rosado`, `Casuarina` |
| `nombre_cientifico` | el nombre científico | |
| `familia` | la familia botánica | |
| `origen` | si la especie es nativa de la región o no | `nativo` (tipa, jacarandá, palo borracho), `exótico` (eucalipto, casuarina) |
| `altura_m` | la altura total, en metros | 1 a 45 |
| `diametro_cm` | el diámetro del tronco, en centímetros; la fuente no dice a qué altura se midió | 2 a 213 |
| `inclinacion_grados` | la inclinación del tronco, en grados | 0 a 57 |
| `espacio_verde` | el parque o la plaza | |

## Cuidado con

- 191 árboles no tienen `espacio_verde`.
- Casi dos de cada tres árboles tienen una inclinación de 0 grados.
- El muestreo fijó la cantidad por especie: esa proporción no dice nada sobre la ciudad.
- No hay mediciones apareadas: no sirve para Wilcoxon.

## Qué columna sirve para cada punto

| Punto | Columnas posibles |
|---|---|
| 2, media | `altura_m` |
| 2, proporción | `origen`, o los árboles inclinados contra los rectos |
| 3 | `altura_m` según `origen`, o jacarandá contra tipa blanca |
| 4 | proporciones: la proporción de árboles inclinados, nativos contra exóticos; ANOVA: `altura_m` según `especie` |
| 5 | `diametro_cm` y `altura_m`, mejor dentro de una sola especie |
| 6 | `especie` y si el árbol está inclinado |
| 7 | Kruskal-Wallis con `especie`, Mann-Whitney con `origen` |

## Qué cambió respecto del original

La base original tiene 51.502 árboles de más de 300 especies. La muestra usa una semilla fija, se
corrigieron letras mal codificadas (`Denominaci¢n` por `Denominación`) y los `S/D` son celdas vacías.

## Fuente

- Página: <https://data.buenosaires.gob.ar/dataset/arbolado-espacios-verdes>
- Archivo original:
  <https://cdn.buenosaires.gob.ar/datosabiertos/datasets/ministerio-de-espacio-publico-e-higiene-urbana/arbolado-espacios-verdes/arbolado-en-espacios-verdes.csv>
- Licencia: [CC BY 2.5 AR](https://creativecommons.org/licenses/by/2.5/ar/)
- Cita: Gobierno de la Ciudad de Buenos Aires. *Arbolado en espacios verdes*. Buenos Aires Data.
