# Los estudiantes secundarios de Portugal

`estudiantes_portugal.csv` tiene 649 alumnos de Lengua Portuguesa de dos escuelas secundarias
públicas de Portugal, en 2005-2006. Las notas salen de las escuelas, y el resto, de una encuesta.
Una fila es un alumno. Las notas van de 0 a 20 y se aprueba con 10.

| Columna | Qué es | Valores |
|---|---|---|
| `escuela` | la escuela | `Gabriel Pereira`, `Mousinho da Silveira` |
| `sexo` | el sexo | `mujer`, `varón` |
| `edad` | años cumplidos | 15 a 22 |
| `domicilio` | dónde vive | `urbano`, `rural` |
| `tamaño_familia` | cuántas personas tiene la familia | `hasta 3`, `más de 3` |
| `padres` | si los padres viven juntos | `juntos`, `separados` |
| `educacion_madre` y `educacion_padre` | el máximo nivel alcanzado | `ninguna`, `primaria (hasta 4.º año)`, `5.º a 9.º año`, `secundaria`, `superior` |
| `trabajo_madre` y `trabajo_padre` | el área de trabajo | `docente`, `salud`, `servicios públicos`, `en el hogar`, `otro` |
| `motivo_escuela` | por qué eligió la escuela | `cercanía`, `reputación`, `oferta de cursos`, `otro` |
| `tutor` | quién es el tutor | `madre`, `padre`, `otro` |
| `tiempo_viaje` | el tiempo de viaje a la escuela | `menos de 15 min`, `15 a 30 min`, `30 min a 1 h`, `más de 1 h` |
| `estudio_semanal` | las horas de estudio por semana | `menos de 2 h`, `2 a 5 h`, `5 a 10 h`, `más de 10 h` |
| `materias_repetidas` | cuántas materias desaprobó antes; la fuente agrupa 3 o más | 0 a 3 |
| `inasistencias` | la cantidad de faltas | 0 a 32 |
| `nota_1` | la nota del primer período | 0 a 20 |
| `nota_2` | la nota del segundo período | 0 a 20 |
| `nota_final` | la nota final | 0 a 20 |

Ocho columnas valen `sí` o `no`: `apoyo_escolar` y `apoyo_familiar` (si recibe apoyo educativo de
la escuela o de la familia), `clases_pagas` (clases particulares de la materia), `actividades_extra`,
`jardin_infantes`, `quiere_estudios_superiores`, `internet` (en la casa) y `en_pareja`.

Seis columnas son una escala de 1 a 5, de muy poco o muy malo a mucho o muy bueno:
`relacion_familiar`, `tiempo_libre`, `salidas` (con amigos), `alcohol_dias_habiles`,
`alcohol_fin_de_semana` y `salud`.

## Cuidado con

- No hay celdas vacías, pero quince alumnos tienen 0 de nota final, y siete de ellos también en el segundo período. Puede ser
  un alumno que dejó la materia: miralo en el punto 1 y decidí qué hacer.
- Las columnas de 1 a 5 son escalas, no mediciones: decí si las tratás como categorías ordenadas o
  como números.

## Qué columna sirve para cada punto

| Punto | Columnas posibles |
|---|---|
| 2, media | `nota_final` |
| 2, proporción | `internet`, `quiere_estudios_superiores` o cualquier columna de `sí` y `no` |
| 3 | `nota_final` según `sexo`, `escuela` o `domicilio` |
| 4 | proporciones: la proporción con `internet`, `urbano` contra `rural`; ANOVA: `nota_final` según `estudio_semanal` o `educacion_madre` |
| 5 | `nota_1` y `nota_final` |
| 6 | `estudio_semanal` y `sexo`, o `domicilio` e `internet` |
| 7 | Wilcoxon con `nota_1` y `nota_2`, que son del mismo alumno |

## Qué cambió respecto del original

Las columnas y las categorías están en castellano, y los niveles educativos, el tiempo de viaje y las horas de estudio van escritos en vez de códigos. El original
trae también un archivo de Matemática, que no se usa.

## Fuente

- Página: <https://archive.ics.uci.edu/dataset/320/student+performance>
- Archivo original: `student-por.csv`, dentro de
  <https://archive.ics.uci.edu/static/public/320/student+performance.zip>
- Licencia: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
- Cita: Cortez, P. (2008). *Student Performance* [base de datos]. UCI Machine Learning Repository.
  <https://doi.org/10.24432/C5TG7T>
