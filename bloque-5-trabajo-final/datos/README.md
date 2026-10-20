# Las bases del trabajo final

Cada base de esta carpeta sale de una fuente abierta, y con cualquiera de ellas se pueden resolver
los siete puntos del trabajo final. Cada una tiene un archivo `.csv` con los datos y un archivo `.md` con su
descripción: qué es una fila, qué quiere decir cada columna, qué cambió respecto del original, qué
columna sirve para cada punto, y la fuente con su link, su licencia y cómo citarla.

| Base | Tema | Filas | Una fila es | Wilcoxon |
|---|---|---|---|---|
| [`factores_de_riesgo_2018`](factores_de_riesgo_2018.md) | salud, Argentina | 2.000 | una persona | sí |
| [`agricultura_2022_23`](agricultura_2022_23.md) | agricultura, Argentina | 1.041 | un cultivo en un departamento | sí |
| [`arbolado_buenos_aires`](arbolado_buenos_aires.md) | arbolado urbano, Argentina | 2.000 | un árbol | no |
| [`pinguinos_palmer`](pinguinos_palmer.md) | biología, Antártida | 344 | un pingüino | no |
| [`estudiantes_portugal`](estudiantes_portugal.md) | educación, Portugal | 649 | un alumno | sí |
| [`vinos_portugal`](vinos_portugal.md) | vinos, Portugal | 6.497 | una muestra de vino | no |
| [`corazon_cleveland`](corazon_cleveland.md) | salud, Estados Unidos | 303 | un paciente | no |
| [`bicicletas_washington`](bicicletas_washington.md) | transporte, Estados Unidos | 731 | un día | sí |
| [`autos_1970_1982`](autos_1970_1982.md) | autos, Estados Unidos, Europa y Japón | 398 | un modelo de auto | no |

La última columna dice si la base tiene dos mediciones sobre las mismas unidades, que es lo que
pide el test de Wilcoxon. El punto 7 pide al menos uno de los tres tests no paramétricos, así que
una base sin mediciones apareadas sirve igual: se usa el de Mann-Whitney o el de Kruskal-Wallis.

## El formato de los archivos

Los CSV están en UTF-8, separados por comas y con punto decimal. Las celdas vacías son datos
faltantes. Las categorías están escritas en castellano, con tildes.

En R y en Python se leen directo: `read.csv("archivo.csv")` en R, `pd.read_csv("archivo.csv")` en
Python.

En Excel no conviene abrirlos con doble clic. Con la configuración regional de Argentina, Excel
espera punto y coma entre columnas y coma decimal, y lee mal el archivo: pone todo en una columna,
o convierte un 12.5 en 125. La forma segura es esta:

1. Abrir un libro en blanco.
2. Ir a `Datos` → `Obtener datos` → `Desde un archivo` → `Desde texto/CSV`, y elegir el archivo.
3. En la ventana que se abre, elegir `65001: Unicode (UTF-8)` como origen del archivo y `Coma` como
   delimitador.
4. Hacer clic en `Transformar datos`. En el editor que se abre, ir a `Archivo` → `Opciones y
   configuración` → `Opciones de consulta` → `Libro actual` → `Configuración regional`, y elegir
   `Inglés (Estados Unidos)`.
5. En la pestaña `Inicio` del editor, hacer clic en `Cerrar y cargar`.

En el paso 4 hay que hacer clic en `Transformar datos` y no en `Cargar`: con `Cargar`, Excel usa la
configuración regional de la computadora. Las opciones del paso 4 pueden no estar en Excel para Mac.

Después de cargar, revisar una columna con decimales contra el CSV: el valor tiene que ser el
mismo.
