# La Encuesta Nacional de Factores de Riesgo 2018

`factores_de_riesgo_2018.csv` tiene 2.000 personas de la Encuesta Nacional de Factores de Riesgo
2018 (INDEC y Secretaría de Gobierno de Salud), que releva a personas de 18 años o más de localidades
de 5.000 habitantes o más. Una fila es una persona. Es una muestra aleatoria simple de las 16.425 personas a
las que les midieron peso, altura, cintura y presión. No trae los factores de expansión: los
resultados describen a la muestra, no al país, y el informe tiene que decirlo.

| Columna | Qué es | Valores |
|---|---|---|
| `id` | el número de la persona en la base original | |
| `provincia` | la provincia | las 24 jurisdicciones |
| `region` | la región del INDEC | `Metropolitana`, `Pampeana`, `Noroeste`, `Noreste`, `Cuyo`, `Patagónica` |
| `sexo` | el sexo | `mujer`, `varón` |
| `edad` | años cumplidos | 18 a 97 |
| `nivel_educativo` | el máximo nivel alcanzado | `hasta primario incompleto`, `hasta secundario incompleto`, `secundario completo y más` |
| `quintil_ingreso` | el quintil del ingreso del hogar por unidad consumidora | 1 (el 20 % de menor ingreso) a 5 (el de mayor ingreso) |
| `tabaco` | la condición de fumador | `fumador`, `ex fumador`, `no fumador` |
| `salud_percibida` | cómo dice la persona que es su salud | `excelente`, `muy buena`, `buena`, `regular`, `mala` |
| `peso_declarado_kg` | el peso que la persona dice tener, en kg | 30 a 190 |
| `altura_declarada_cm` | la altura que la persona dice tener, en cm | 130 a 198 |
| `peso_medido_kg` | el peso medido por el encuestador, en kg | 34 a 190 |
| `altura_medida_cm` | la altura medida, en cm | 132 a 197 |
| `cintura_cm` | el perímetro de la cintura medido, en cm | 51 a 206 |
| `imc` | el índice de masa corporal, con el peso y la altura medidos | 15,05 a 54,48 |
| `presion_sistolica` | la presión sistólica: el promedio de la segunda y la tercera medición, en mm Hg | 84,5 a 241 |
| `presion_diastolica` | la presión diastólica, calculada igual, en mm Hg | 31 a 154,5 |
| `presion_elevada` | si la sistólica es de 140 o más, o la diastólica de 90 o más | `sí` (765), `no` (1.187) |

## Cuidado con

- Hay celdas vacías: 75 personas no declararon su peso y 147 su altura; a 48 no les midieron la
  presión (tampoco tienen `presion_elevada`), 21 no aceptaron la medición de la cintura, y 1 la de
  la altura (tampoco tiene `imc`).
- El valor 99 aparece en algunas columnas numéricas, como el peso o la cintura, y es una medición
  real: el código de "no sabe o no contesta" del original no quedó en esta base.

## Qué columna sirve para cada punto

| Punto | Columnas posibles |
|---|---|
| 2, media | `presion_sistolica` o `imc` |
| 2, proporción | `presion_elevada` |
| 3 | `presion_sistolica` según `sexo` |
| 4 | proporciones: la proporción con `presion_elevada`, varones contra mujeres; ANOVA: `imc` según `region` o `nivel_educativo` |
| 5 | `peso_medido_kg` y `cintura_cm`, o `edad` y `presion_sistolica` |
| 6 | `tabaco` y `sexo`, o `nivel_educativo` y `presion_elevada` |
| 7 | Wilcoxon con `peso_declarado_kg` y `peso_medido_kg`, que son de la misma persona |

## Qué cambió respecto del original

La base original tiene 29.224 personas y 287 columnas con códigos. Esta muestra usa una semilla
fija y tiene 18 columnas en castellano.

## Fuente

- Página: <https://www.indec.gob.ar/indec/web/Institucional-Indec-BasesDeDatos>, en la sección de la
  Encuesta Nacional de Factores de Riesgo.
- Archivo original: <https://www.indec.gob.ar/ftp/cuadros/menusuperior/enfr/ENFR2018_baseusuario.zip>
- Diccionario de la base original:
  <https://www.indec.gob.ar/ftp/cuadros/menusuperior/enfr/diccionario_registros_enfr2018.xls>
- Licencia: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.es), según el pie
  de cada página del INDEC y su [política de difusión](https://www.indec.gob.ar/ftp/cuadros/publicaciones/politica_difusion_indec.pdf).
  Una obra que modifica estos datos se tiene que publicar con la misma licencia.
- Cita: Fuente: INDEC, Encuesta Nacional de Factores de Riesgo 2018. La política de difusión pide
  citar la fuente y decir qué cambió.
