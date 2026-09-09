# El relevamiento de hogares

`relevamiento_plano.csv` es el conjunto de datos de los dos apuntes del bloque: **45 filas y 12
columnas**. Es el relevamiento de hogares que el T8001 dejó limpio y que el T8002 usó como tabla
plana, copiado sin cambios desde
[ese repositorio](https://github.com/lautarodibartolo-ae/t8002-representacion-de-datos/tree/main/clase-1-bases-y-claves/datos).

Las 45 filas son visitas, no hogares. Son **37 hogares**, y ocho de ellos recibieron una segunda
visita en junio. En tres de esos ocho, los hogares 1, 20 y 30, la cantidad de personas cambió
entre visita y visita.

Los apuntes trabajan con la **primera visita de cada hogar**: 37 filas, una por hogar. Con esa
regla salen todos los números de las dos unidades:

| Qué | Valor | Dónde |
|---|---|---|
| Hogares por localidad | Concepción 11, Córdoba 11, Ramallo 15 | U1 · 6.5 |
| Con cobertura, sin cobertura, sin dato | 14, 13, 10 | U1 · 6.5 |
| Personas por hogar: valores | 1, 2, 3, 4, 5, 6, 7 y 12 | U2 · 3.5 |
| Esperanza de personas por hogar | 3,7838 | U2 · 4.5 |
| Varianza y desvío | 4,2776 y 2,0682 | U2 · 5.2 y 5.4 |
| Coeficiente de variabilidad | 54,66 % | U2 · 6.1 |
| Asimetría y kurtosis | 1,7200 y 7,4836 | U2 · 7.2 y 8.2 |

Si se tomara la segunda visita, el hogar 30 pasaría de 7 a 8 personas y el hueco entre 7 y 12 se
achicaría a 9, 10 y 11. Los notebooks de ejemplos permiten elegir una u otra visita para ver esa diferencia.

Los notebooks llevan el archivo adentro, como texto, así que funcionan sin conexión y no leen esta
copia. El archivo está acá para poder mirarlo y para citarlo por su dirección web.
