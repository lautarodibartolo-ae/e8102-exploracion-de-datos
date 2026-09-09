# E8102 — Exploración de datos

Asignatura de 48 horas de cursada, repartidas en cuatro bloques de cuatro clases. Cada bloque trae
el apunte de sus unidades en PDF, un notebook de ejemplos interactivos por unidad, la consigna de la
ejercitación en PDF y un notebook de Google Colab para resolverla. Los botones abren los notebooks
en Colab, sin instalar nada.

| Bloque | Unidades | Ejemplos interactivos | Ejercitación |
|---|---|---|---|
| 1 — Probabilidad y variable aleatoria | 1 y 2 | [![Unidad 1](https://img.shields.io/badge/Colab-Unidad_1-F9AB00?logo=googlecolab&logoColor=white)](https://colab.research.google.com/github/lautarodibartolo-ae/e8102-exploracion-de-datos/blob/main/bloque-1-probabilidad-y-variables-aleatorias/u1_ejemplos_probabilidad.ipynb) [![Unidad 2](https://img.shields.io/badge/Colab-Unidad_2-F9AB00?logo=googlecolab&logoColor=white)](https://colab.research.google.com/github/lautarodibartolo-ae/e8102-exploracion-de-datos/blob/main/bloque-1-probabilidad-y-variables-aleatorias/u2_ejemplos_variable_aleatoria.ipynb) | [![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lautarodibartolo-ae/e8102-exploracion-de-datos/blob/main/bloque-1-probabilidad-y-variables-aleatorias/ejercitacion_bloque_1.ipynb) |
| 2 — Distribuciones y análisis de datos | 3 y 4 | — | [![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lautarodibartolo-ae/e8102-exploracion-de-datos/blob/main/bloque-2-distribuciones-y-analisis-de-datos/ejercitacion_bloque_2.ipynb) |
| 3 — Muestreo e inferencia | 5, 6 y 7 | — | [![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lautarodibartolo-ae/e8102-exploracion-de-datos/blob/main/bloque-3-muestreo-y-inferencia/ejercitacion_bloque_3.ipynb) |
| 4 — Regresión e inferencia no paramétrica | 8 y 9 | — | [![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lautarodibartolo-ae/e8102-exploracion-de-datos/blob/main/bloque-4-regresion-y-no-parametricos/ejercitacion_bloque_4.ipynb) |

El material se publica bloque por bloque, antes de que empiece cada uno.

Los notebooks de ejemplos no piden escribir código. Cada bloque del notebook resume una sección del
apunte y abre un formulario con deslizadores y listas: se mueve un valor y el gráfico se vuelve a
dibujar. Sirven para ver qué le pasa a una probabilidad, a una esperanza o a una kurtosis cuando
cambia el dato que la produce.

## De qué se trata

Exploración de datos es la primera asignatura de la Especialización en Inteligencia de Datos para
la Gestión Estratégica. Trata la estadística que se usa para describir un conjunto de datos y para
decidir qué se puede afirmar a partir de una muestra.

La asignatura sigue a los dos talleres de nivelación, T8001 Pre-procesado de datos y T8002
Representación de datos. En ellos el conjunto de datos quedó limpio y con una estructura que se
puede consultar. Acá empieza el análisis: qué dice cada variable, cuánto varía, y qué parte de lo
que se observa en una muestra vale para la población de la que salió.

El eje es la interpretación del resultado y no el cálculo. Un intervalo de confianza o un valor p
se obtienen con una línea de código, y lo que se evalúa es qué conclusión admite ese número y cuál
no. La asignatura no supone conocimientos previos de estadística.

Las herramientas son `pandas` y `matplotlib`, las mismas del T8001, más `scipy.stats` para las
distribuciones y los tests. Acá una librería de estadística no esconde el concepto: la
distribución **es** el concepto, y calcularla a mano con tablas impresas no agrega nada.

## Cómo está organizado

Cada bloque son cuatro clases de tres horas, siempre en el mismo orden:

1. **Asincrónica** — lectura del apunte de las unidades del bloque.
2. **Sincrónica** — encuentro virtual teórico-práctico, 18:00 a 21:00.
3. **Sincrónica** — encuentro virtual teórico-práctico, 9:00 a 12:00.
4. **Asincrónica** — ejercitación de repaso del bloque.

La ejercitación no se entrega y no se corrige: sirve para practicar los contenidos del bloque antes
de pasar al siguiente. La única entrega de la asignatura es un trabajo práctico integrador de las
nueve unidades, al final del cursado.

## Contenidos

- **Bloque 1** — Azar, experimento y espacio muestral. Enfoques clásico, empírico y subjetivo.
  Probabilidad marginal, condicional, compuesta y total. Variable aleatoria: esperanza, varianza,
  desvío standard, asimetría y kurtosis.
- **Bloque 2** — Distribuciones binomial, hipergeométrica, de Poisson y normal. Teorema de
  Bernoulli y teorema central del límite. Distribuciones t de Student, chi cuadrado y F.
  Series de frecuencia, medidas de posición y de variabilidad, y representaciones gráficas.
- **Bloque 3** — Población y muestra. Muestreo aleatorio simple, estratificado y por
  conglomerados. Parámetro y estimador. Intervalos de confianza y tamaño de muestra. Test de
  hipótesis, valor p y errores tipo I y II.
- **Bloque 4** — Covarianza y gráfico de dispersión. Mínimos cuadrados. Regresión lineal simple y
  múltiple. Correlación y coeficiente de determinación. Test de Mann-Whitney, de Wilcoxon, de
  Kruskal Wallis y chi cuadrado.

El programa completo, el cronograma con fechas y la bibliografía están en
[E8102_Presentacion_Exploracion_de_Datos_2026.pdf](E8102_Presentacion_Exploracion_de_Datos_2026.pdf).

## Licencia

Este material se publica bajo [CC BY 4.0](LICENSE): se puede usar, copiar y adaptar libremente,
con atribución.
