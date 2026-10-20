# Los datos del bloque 3

Los dos archivos de esta carpeta son los datos de la ejercitación del bloque 3. Salen de la
[Encuesta Permanente de Hogares](https://www.indec.gob.ar/indec/web/Institucional-Indec-BasesDeDatos)
del INDEC, la misma del bloque 2. La ejercitación usa además el relevamiento de los apuntes, que va
adentro del notebook; su copia publicada está en
[la carpeta del bloque 1](../../bloque-1-probabilidad-y-variables-aleatorias/datos/).

| Archivo | Filas | Una fila es |
|---|---|---|
| `eph_2t2025_ocupados.csv` | 20.374 | una persona ocupada encuestada en el segundo trimestre de 2025 |
| `eph_panel_2025.csv` | 4.950 | una persona ocupada encuestada en el primer y en el segundo trimestre de 2025 |

## Los ocupados

Son los ocupados del archivo de personas del bloque 2, con los mismos `id_hogar`. La ejercitación
trata a los 16.709 que declararon su ingreso como una población completa.

| Columna | Qué es |
|---|---|
| `id_hogar` y `componente` | el hogar, con el mismo número que en el bloque 2, y la persona dentro del hogar |
| `region` | la región del aglomerado |
| `sexo` | `varón` o `mujer` |
| `edad` | años cumplidos |
| `nivel_educativo` | el máximo nivel alcanzado; siete categorías |
| `categoria_ocupacional` | `patrón`, `cuenta propia`, `obrero o empleado` o `trabajador familiar sin remuneración` |
| `horas_semanales` | horas trabajadas en la semana en la ocupación principal |
| `ingreso` | ingreso mensual de la ocupación principal, en pesos corrientes |

Tres cambios respecto del [archivo de personas del bloque 2](../../bloque-2-distribuciones-y-analisis-de-datos/datos/):
no está la columna `condicion_actividad`, porque todos son ocupados; la columna del ingreso se llama
`ingreso`, y no `ingreso_ocupacion_principal`; y el `999` de las horas, que quiere decir "no sabe o
no responde", ya está convertido en celda vacía: son 33 casos.

El ingreso conserva el `-9` de la no respuesta, 3.665 casos, porque el ejercicio 1 define la
población a partir de él. Los ceros son datos: en el ingreso, 449 ocupados que no cobraron nada por
esa ocupación en el mes; en las horas, 331 que esa semana no trabajaron.

## El panel

La EPH encuesta a cada vivienda en dos trimestres seguidos, no la encuesta en los dos siguientes y
la vuelve a encuestar en otros dos. Este archivo cruza las bases del primer y del segundo trimestre
de 2025 por la vivienda, el hogar y el número de persona, y se queda con las personas que
estuvieron ocupadas y declararon su ingreso en los dos trimestres.

| Columna | Qué es |
|---|---|
| `id_persona` | un número corto para cada persona |
| `region` y `sexo` | como en los ocupados |
| `edad` | la edad en el segundo trimestre |
| `ingreso_1t` e `ingreso_2t` | el ingreso de la ocupación principal en cada trimestre, en pesos corrientes |

De las 5.718 personas ocupadas con ingreso en los dos trimestres, el cruce descarta 768 en las que
el sexo cambia, la edad baja, o la edad sube más de un año. Puede ser otra persona del hogar con el
mismo número, o la misma persona con la edad mal anotada; el archivo no las distingue y las saca a
todas.

## Lo que estos números no son

No son estimaciones para la población del país. La EPH es una muestra, y las cifras oficiales se
calculan con factores de expansión que estos archivos no traen. La ejercitación usa a los
encuestados como una población de laboratorio, para poder comparar cada estimación contra el valor
verdadero.

## De dónde salen

Las bases usuarias de la EPH del primer y del segundo trimestre de 2025, y su
[diseño de registro](https://www.indec.gob.ar/ftp/cuadros/menusuperior/eph/EPH_registro_2T2025.pdf).
Fuente: INDEC, Encuesta Permanente de Hogares.
