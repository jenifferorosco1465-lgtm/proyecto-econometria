# Proyecto Final de Econometría

## Factores asociados a la probabilidad de trabajar en Ecuador: aplicación de modelos Logit y Probit

**Autora:** Jeniffer Orosco
**Universidad:** Universidad Técnica de Cotopaxi
**Carrera:** Economía
**Asignatura:** Econometría II
**Docente:** Eco. Vinicio Arcos 


---

## 1. Descripción del proyecto

Este proyecto analiza los factores asociados con la probabilidad de que una persona se encuentre trabajando en Ecuador, utilizando modelos econométricos de respuesta binaria **Logit y Probit**.

El análisis utiliza información de la **Encuesta de Condiciones de Vida (ECV6R)** del Instituto Nacional de Estadística y Censos (INEC).

Los resultados se interpretan como asociaciones estadísticas y no como relaciones causales.

---

## 2. Pregunta de investigación

¿Qué factores se encuentran asociados con la probabilidad de que una persona se encuentre trabajando?

---

## 3. Objetivo

Analizar los factores asociados con la probabilidad de trabajar mediante modelos econométricos de respuesta binaria Logit y Probit.

---

## 4. Fuente de información

La información utilizada proviene de la **Encuesta de Condiciones de Vida (ECV6R)** del Instituto Nacional de Estadística y Censos (INEC) de Ecuador.

La unidad de observación corresponde a personas.

Se utilizó el factor de expansión de la encuesta como parte del tratamiento de la información, reconociendo que esto no equivale necesariamente a incorporar todos los componentes del diseño muestral complejo.

---

## 5. Variables utilizadas

### Variable dependiente

**trabaja**

* 1 = trabaja
* 0 = no trabaja

### Variables explicativas

| Variable | Descripción                        |
| -------- | ---------------------------------- |
| `hombre` | 1 = hombre; 0 = mujer              |
| `EDAD`   | Edad de la persona en años         |
| `edad2`  | Edad al cuadrado                   |
| `urbano` | 1 = área urbana; 0 = área rural    |
| `FEXP`   | Factor de expansión de la encuesta |

La variable `edad2` se incorpora para representar una posible relación no lineal entre la edad y la probabilidad de trabajar.

---

## 6. Metodología

Se estimaron dos modelos de respuesta binaria:

* Modelo Logit.
* Modelo Probit.

Posteriormente se compararon sus resultados mediante:

* Pseudo R².
* AIC.
* Log-verosimilitud.
* Efectos marginales promedio.
* Capacidad predictiva.
* AUC.
* Matriz de confusión.
* Accuracy.
* Factor de Inflación de la Varianza (VIF).

---

## 7. Resultados principales

La muestra utilizada para la estimación final estuvo conformada por **85.950 observaciones**.

### Modelo Logit

* Pseudo R² = **0.2748**
* AIC = **83.332,02**
* Log-verosimilitud = **-41.661,01**

Los coeficientes estimados fueron estadísticamente significativos.

El coeficiente de `hombre` fue positivo, mientras que `urbano` presentó un coeficiente negativo. La edad presentó un efecto no lineal debido a la inclusión de `edad2`.

### Modelo Probit

* Pseudo R² = **0.2745**
* AIC = **83.371,11**
* Log-verosimilitud = **-41.680,55**

Los resultados del modelo Probit presentan signos y conclusiones similares a los obtenidos mediante Logit.

---

## 8. Efectos marginales promedio

Los efectos marginales promedio obtenidos fueron:

| Variable |   Logit |  Probit |
| -------- | ------: | ------: |
| hombre   |  0.2017 |  0.2035 |
| EDAD     |  0.0461 |  0.0464 |
| edad2    | -0.0005 | -0.0005 |
| urbano   | -0.1443 | -0.1435 |

En el modelo Logit, manteniendo las demás variables constantes en el sentido del cálculo de efectos marginales promedio, la variable `hombre` presenta un efecto marginal promedio de aproximadamente **0.2017**, mientras que `urbano` presenta un efecto marginal promedio de **-0.1443**.

La edad presenta un componente positivo y su término cuadrático uno negativo, lo que es consistente con una relación no lineal entre edad y probabilidad de trabajar.

Los resultados del Probit son muy similares, lo que muestra estabilidad en las conclusiones generales.

---

## 9. Capacidad predictiva

El modelo Logit obtuvo:

* **AUC = 0.8341**
* **Accuracy = 0.7713**

### Matriz de confusión

```text
[[21547 11912]
 [ 7749 44742]]
```

El AUC de **0.8341** indica una capacidad de discriminación adecuada del modelo para distinguir entre las observaciones clasificadas como trabajadoras y no trabajadoras.

El Accuracy de **0.7713** indica que aproximadamente el 77,13 % de las observaciones fueron clasificadas correctamente utilizando el criterio de clasificación empleado.

---

## 10. Diagnóstico de multicolinealidad

El diagnóstico mediante VIF presentó los siguientes resultados:

| Variable |     VIF |
| -------- | ------: |
| hombre   |  1.0006 |
| EDAD     | 16.8969 |
| edad2    | 16.9013 |
| urbano   |  1.0052 |

Los valores elevados de VIF para `EDAD` y `edad2` están relacionados con la inclusión simultánea de la edad y su cuadrado en el modelo. Esto debe considerarse al interpretar el diagnóstico de multicolinealidad.

Las variables `hombre` y `urbano` presentan valores cercanos a 1, por lo que no muestran problemas relevantes de colinealidad.

---

## 11. Comparación Logit y Probit

| Modelo | Pseudo R² |       AIC | Log-Likelihood |
| ------ | --------: | --------: | -------------: |
| Logit  |    0.2748 | 83.332,02 |     -41.661,01 |
| Probit |    0.2745 | 83.371,11 |     -41.680,55 |

Los dos modelos producen resultados muy similares en términos de signos, significancia y efectos marginales.

El modelo Logit presenta ligeramente menor AIC y una log-verosimilitud menos negativa, por lo que, bajo estos criterios, presenta un ajuste ligeramente superior al Probit.

---

## 12. Estructura del repositorio

```text
proyecto-econometria/
│
├── dashboard/
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
├── outputs/
│   ├── figures/
│   ├── tables/
│   └── results/
│
├── paper/
│   └── minipaper.md
│
├── prompts/
│   └── registro_uso_ia.md
│
├── src/
│   ├── obtener_datos.py
│   ├── limpiar_datos.py
│   ├── estimar_modelo.py
│   └── generar_resultados.py
│
├── .gitignore
├── LICENSE
├── README.md
└── requirements.txt
```

---

## 13. Productos del proyecto

### Repositorio GitHub

https://github.com/jenifferorosco1465-lgtm/proyecto-econometria

### Dashboard

https://proyecto-econometria-eight.vercel.app

### Mini paper

El documento completo del análisis se encuentra en:

```text
paper/minipaper.md
```

---

## 14. Tecnologías utilizadas

* Python
* Jupyter Notebook
* Pandas
* NumPy
* Statsmodels
* Scikit-learn
* Matplotlib
* OpenPyXL
* Git
* GitHub
* Vercel

---

## 15. Conclusiones

Los modelos Logit y Probit permiten analizar la asociación entre determinadas características individuales y del área de residencia y la probabilidad de trabajar.

Los resultados muestran una relación positiva entre la variable `hombre` y la probabilidad de trabajar, mientras que la variable `urbano` presenta una asociación negativa en la especificación estimada. La edad presenta una relación no lineal debido a la incorporación de su término cuadrático.

Los modelos Logit y Probit presentan resultados muy similares. El modelo Logit muestra ligeramente mejores indicadores de ajuste según el AIC y la log-verosimilitud.

El modelo Logit presenta además un AUC de **0.8341** y un Accuracy de **0.7713**, lo que evidencia una capacidad predictiva adecuada dentro de la muestra analizada.

Estos resultados deben interpretarse como **asociaciones estadísticas y no como efectos causales**.

---

## 16. Limitaciones

Entre las principales limitaciones se encuentra el tratamiento del diseño muestral de la encuesta. La utilización del factor de expansión no implica necesariamente la incorporación completa de todos los componentes del diseño complejo de la ECV6R.

Asimismo, la inclusión simultánea de `EDAD` y `edad2` genera valores elevados de VIF asociados a la relación matemática entre ambas variables.

Por estas razones, los resultados deben interpretarse considerando las características y limitaciones de la información utilizada.

---

## 17. Uso de inteligencia artificial

Durante el desarrollo de este proyecto se utilizaron herramientas de inteligencia artificial como apoyo para la revisión de código, organización del repositorio, documentación y mejora de la redacción.

La estudiante verificó los procedimientos, estimaciones, referencias e interpretaciones y asume la responsabilidad sobre el contenido presentado.

El registro del uso de inteligencia artificial se encuentra en:

```text
prompts/registro_uso_ia.md
```

---



