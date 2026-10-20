# La Encuesta Permanente de Hogares

Los tres archivos de esta carpeta son los datos de la ejercitación del bloque 2. Salen de la
[Encuesta Permanente de Hogares](https://www.indec.gob.ar/indec/web/Institucional-Indec-BasesDeDatos)
del INDEC, que releva cada trimestre entre 43.700 y 49.100 personas en 32 aglomerados urbanos del
país. La base de personas tiene 235 columnas con códigos numéricos (177 hasta el tercer trimestre de 2023) y la de hogares, 98; acá quedan las pocas que usa
la ejercitación, con las categorías escritas en castellano.

| Archivo | Filas | Una fila es |
|---|---|---|
| `eph_2t2025_personas.csv` | 46.086 | una persona encuestada en el segundo trimestre de 2025 |
| `eph_2t2025_hogares.csv` | 16.169 | un hogar del mismo trimestre |
| `eph_trimestres.csv` | 12 | un trimestre, de 2023 a 2025 |

## Las personas

| Columna | Qué es | Valores |
|---|---|---|
| `id_hogar` | el hogar de la persona, el mismo número que en el archivo de hogares | 1 a 16.169 |
| `componente` | el número de la persona dentro del hogar | 1, 2, 3, … |
| `region` | la región del aglomerado | seis regiones |
| `sexo` | sexo declarado | `varón`, `mujer` |
| `edad` | años cumplidos | 0 a 103 |
| `nivel_educativo` | el máximo nivel alcanzado | siete categorías, de `sin instrucción` a `superior o universitario completo` |
| `condicion_actividad` | la situación en el mercado de trabajo | `ocupado`, `desocupado`, `inactivo`, `menor de 10 años`, `entrevista individual no realizada` |
| `categoria_ocupacional` | solo para ocupados | `patrón`, `cuenta propia`, `obrero o empleado`, `trabajador familiar sin remuneración` |
| `horas_semanales` | solo para ocupados: horas trabajadas en la semana en la ocupación principal | 0 a 140, y `999` |
| `ingreso_ocupacion_principal` | solo para ocupados: ingreso mensual de la ocupación principal, en pesos corrientes | 0 a 30.000.000, y `-9` |

Las tres últimas columnas están vacías en las 25.712 personas que no están ocupadas, porque la
pregunta no les corresponde.

**Los códigos de INDEC quedaron como están, a propósito.** Tratarlos es parte de la ejercitación, y
el diseño de registro de la encuesta dice qué es cada uno:

| Columna | Valor | Qué es | Casos entre los 20.374 ocupados |
|---|---|---|---|
| `ingreso_ocupacion_principal` | `-9` | no respuesta: un centinela | 3.665 |
| `ingreso_ocupacion_principal` | `0` | "sin ingresos": no cobró nada por esa ocupación en el mes de referencia; es un ingreso real de cero | 449 |
| `horas_semanales` | `999` | no sabe o no responde: un centinela | 33 |
| `horas_semanales` | `0` | un ocupado que esa semana no trabajó, por ejemplo por licencia | 331 |

Es la misma distinción entre vacío, centinela y cero de la sección 2.1 de la unidad 4.

Dos cambios respecto de la base original. La EPH anota `-1` en la edad de los menores de un año,
y acá figura como `0`. Y el par de claves `CODUSU` y `NRO_HOGAR`, que identifica al hogar, se
reemplazó por el número corto `id_hogar`.

## Los hogares

| Columna | Qué es |
|---|---|
| `id_hogar` | el mismo número del archivo de personas |
| `region` | la región del aglomerado |
| `miembros` | la cantidad de personas del hogar, de 1 a 18 |
| `tenencia_vivienda` | si el hogar es propietario, inquilino u ocupante de la vivienda; nueve categorías |

Diez hogares no tienen el dato de tenencia.

## Los trimestres

Un resumen de las doce bases de 2023 a 2025, calculado sobre los ocupados que declararon su
ingreso, es decir sin los `-9`:

| Columna | Qué es |
|---|---|
| `periodo`, `anio`, `trimestre` | el trimestre, escrito de tres maneras |
| `personas_encuestadas` | todas las personas de la base |
| `ocupados` | las personas ocupadas |
| `ocupados_con_ingreso_declarado` | los ocupados sin el `-9` en el ingreso |
| `ingreso_mediano` y `ingreso_medio` | la mediana y la media del ingreso de la ocupación principal, en pesos corrientes |

Los pesos son corrientes: no están corregidos por inflación, y entre el primer trimestre de 2023 y
el último de 2025 la mediana se multiplica por diez.

## Lo que estos números no son

**No son estimaciones para la población.** La EPH es una muestra, y cada persona trae un factor de
expansión, `PONDERA`, que dice a cuántas personas del aglomerado representa. Las cifras oficiales
de INDEC se calculan con esos factores. Este archivo no los incluye, y la ejercitación describe
**a las personas encuestadas**, que es lo que corresponde a la unidad 4. Pasar de la muestra a la
población es inferencia, y empieza en la unidad 5.

Por eso la media del ingreso de este archivo no tiene por qué coincidir con la que publica INDEC.

## De dónde salen

Las bases usuarias de la EPH del INDEC, del primer trimestre de 2023 al cuarto de 2025, y su
[diseño de registro](https://www.indec.gob.ar/ftp/cuadros/menusuperior/eph/EPH_registro_2T2025.pdf).
Los archivos se arman con un script que descarga las bases, se queda con estas columnas y escribe
las etiquetas. Fuente: INDEC, Encuesta Permanente de Hogares.
