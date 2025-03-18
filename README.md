## Predicción del tratamiento farmacológico óptimo mediante modelo de clasificación de árbol de decisión

## Autor ✒️
**Georgina Casillas Rosano**

* [LinkedIn](https://www.linkedin.com/in/georgina-casillas-rosano-data-science)
* [Portafolio](https://github.com/Georgina-Casillas/Proyecto_Arbol_Decision)

* Instalación 💻: Este proyecto requiere de instalar Python.

## Objetivos del proyecto: 🎯
* Desarrollar un modelo de clasificación supervisado para averiguar qué medicamento podría ser apropiado para un futuro paciente con la misma enfermedad. 

* Entrenar un conjunto de datos para construir un árbol de decisión, y luego utilizarlo para predecir la clase de un nuevo paciente.

* Identificar la importancia de las características como son: la edad, el sexo, la presión arterial y el colesterol de los pacientes y como influenciaron en la forma en la que cada paciente respondió al fármaco.

## Dataset 🧾
El conjunto de datos reúne el fármaco al que respondieron 200 pacientes durante sus tratamientos médicos. La variable clave, `Drug`, es una variable categórica ordinal con cinco niveles:

*   0: drugA
*   1: drugB
*   2: drugC
*   3: drugX
*   4: drugY

Adicionalmente se incluyen variables de cada paciente como son la edad , el sexo, la presión arterial (BP),  el colesterol y los niveles de sodio- potasio:

*   `age`:  Integer
*   `sex`:  Binary (0: Female, 1: Male)
*   `BP`:  Categorical (1:LOW , 2:NORMAL ,3:HIGH)
*   `Cholesterol`:  Binary (0: Normal , 1:High)

## Estructura del Proyecto y Metodología 📈

1. **Carga de datos y Preprocesamiento:**
    * La base de datos se carga usando la librería Pandas. 
    * Se codifican apropiadamente las variables categóricas (`sex`, `BP`, `Cholesterol`) en variables numéricas para poder procesarlas.
    * La variable edad se deja como una variable numérica ya que el modelo puede encontrar los mejores puntos de corte por sí mismo sin necesidad de agrupar manualmente.

2. **Preprocesamiento de datos:**
   * Se cambian las variables de cadenas a numéricas como son `Drug`, `BP`, `Sex`, `Cholesterol`.


3. **Análisis Exploratorio de Datos (EDA) y Análisis de Correlación Spearman:**
   * Se comprueba el balance del dataset y si existen faltantes. 
   * Se utilizan estadísticas descriptivas y visualizaciones (histogramas, gráficos de barras) para comprender la distribución de las variables individuales.


4. **Prueba de Hipótesis Estadística:**
   * **Prueba de Kruskal-Wallis:**, que es una prueba no paramétrica para comparar medianas entre múltiples grupos de variables numéricas/ordinales en los diferentes niveles de «Drug». La prueba de Dunn se    utiliza para comparaciones por pares cuando la prueba de Kruskal-Wallis es significativa. 
   * **Prueba de Chi-cuadrada:** Se utiliza para evaluar la asociación entre «Drug» y variables categóricas. La prueba V de Cramer se calcula para medir la fuerza de esa asociación.
   * Estas pruebas confirman la significancia estadística de varias asociaciones, incluso con correlaciones débiles, lo que destaca la importancia de las pruebas inferenciales.

   * **Prueba de Correlación de rangos de Spearman:** * Se aplican métodos no paramétricos como la correlación de Spearman para medir la correlación entre la variable ordinal ´Drug´ y otros predictores numéricos/ordinales. Esto proporciona una indicación inicial de posibles asociaciones. *Se encontró* que la correlación de Spearman de la variable ´Na_to_K´ es la más prometedora para predecir el tipo de fármaco a utilizar. El resto de las variables presentaron correlaciones débiles indicando que estas variables por sí solas no predicen con firmeza el tipo de tratamiento.


5. **Entrenamiento y Evaluación del Modelo:**
   * El conjunto de datos se divide en conjuntos de Entrenamiento ´train´ y Prueba ´test´.
   * Se entrenan y evalúa el modelo de árboles de decisión y posteriormente se optimizan los hiperparámetros para encontrar la mejor combinación.

## Hallazgos Clave 🔎
* **El modelo de clasificación junto con las pruebas estadísticas** indican que las variables BP, Na_to_K, y Colesterol son clave para diferenciar los grupos de medicamentos.
* **DrugY:** parece indicado para pacientes con niveles elevados de sodio a potasio, lo que podría sugerir desbalances electrolíticos severos.
* **DrugX:** Niveles menores de 14.83 de potasio y sodio y para pacientes con presión arterial baja o normal y colesterol controlado.
* **DrugA:** Niveles menores de 14.83 de potasio y sodio para pacientes jóvenes (menores 50 años) con presión arterial elevada (mayor 2.5).
* **DrugB:** Niveles menores de 14.83 de potasio y sodio. Indicado para pacientes mayores de 50 años con presión arterial elevada (mayor 2.5).
* **DrugC:** Niveles menores de 14.83 de potasio y sodio. Indicado para pacientes con colesterol alto (mayor 0.5) y presión arterial baja o normal.
* Las pruebas estadísticas validan que las diferencias observadas en el modelo son significativas, respaldando la solidez de los resultados.


## Rendimiento del modelo ⚙️
* El modelo muestra un buen desempeño en términos de precisión, recall y F1-score, con una precisión general del 0.9938. Esto indica que el modelo clasificó correctamente el 99.38% de las muestras en promedio durante el proceso de validación cruzada.

