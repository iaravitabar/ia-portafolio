---
title: "Featrure Engineering Simple + Modelo Base ⚙️"
date: 12-08-2025
---

# Feature Engineering Simple + Modelo Base ⚙️

Para esta segunda práctica retomamos la práctica anterior sobre el dataset del Titanic para documentar el proceso de caracteristicas simple y la creacion del modelo de lasificacion base para el dataset. 

## Contexto 🤔💭

El objetivo de esta práctica es tomar un conjunto de datos (el del Titanic), y aplicar técnicas básicas de Feature Engineering para mejorar la calidad y las predicciones, para entrenar un modelo simple de Regresión Logística. Fundamentalmente, se busca establecer un modelo base (baseline) para tener una referencia clara del rendimiento y asegurar que nuestro modelo es útil.

### Actividad 0: Investigación Teórica
Antes de seguir con la implementación, me gustaría dejar registrada la actividad 0 como huella teórica. Me sirvió para entender componentes clave que se usarán. Las preguntas guía fueron:

??? tip "Investigación de Scikit-learn"
    ###`LogisticRegression`:
    - **¿Qué tipo de problemas resuelve?**
        Resuelve problemas de clasificación.  Estima prob de que una instancia sea de una clase específica. Mapea la salida en prob entre 1 y 0
    - **`C`**
        parámetro de regularzación. Inverso a fuerza refularización, valores más pequeños indican una regularización más fuerte
    - **`penalty`:** 
        especifica la norma de regularización a usar ('l2'mas comun) mientras que 'l1' puede llevar a la selección de características (algunos coeficientes se vuelven cero)
    - **`solver`:** 
        algoritmo a usar en el problema de optimización. La elección depende del tamaño del dataset y la penalización elegida
    - **`liblinear`** 
        es una buena opción para **datasets pequeños**. Funciona bien con penalizaciones L1 y L2
    - Para **datasets grandes**, solvers como `sag`, `saga`son más rápidos. No todos los solvers soportan todas las penalizaciones (`lbfgs` solo soporta 'l2')

    ###`DummyClassifier`:
    - **¿Para qué sirve exactamente?**
      - Sirve para crear un **baseline o pto de referencia**.clasificador muy simple que no aprende de los datos, sino hace predicciones basadas en estrategias triviales
    - **¿Qué estrategias de baseline ofrece?**
      -`most_frequent`: siempre predice la clase más común en el conjunto de entrenamiento
      -`stratified`: hace predicciones aleatorias pero manteniendo la distribución de clases del conj de entrenamiento
      -`uniform`: predice clases de forma aleatoria con = probabilidad para cada una
    - **¿Por qué es importante tener un baseline?**
      -importancia baseline: **contextualizar el rendimiento** del modelo. Si un modelo complejo no supera significativamente a un baseline simple, significa que el modelo no está             aprendiendo patrones útiles o que el problema es muy difícil. Nos dice si nuestro esfuerzo está valiendo la pena
          
    ###`train_test_split`:
    - **¿Qué hace `stratify`?**
      - hace que la división de los datos mantenga la **misma proporción de cada clase** que en el conjunto de datos original. Es fundamental en problemas con clases                            desbalanceadas para que tanto el conjunto de entrenamiento como el de prueba sean representativos
    - **Por qué usar `random_state`?**
      - para garantizar la **reproducibilidad**. Al fijar un `random_state` (cualquier num entero), la div de los datos será siempre la misma cada vez que se     ejecute el                     código.clave para depurar y comparar el rendimiento de diferentes modelos de manera justa
    - **¿Qué porcentaje de test es recomendable?**
      - No hay regla única, pero las divisiones comunes son **80/20** o **70/30** (entrenamiento/prueba). Para datasets muy grandes, el porcentaje de prueba puede ser menor. Un                 20% es un buen punto de partida 
        
    ###`métricas de evaluación`:
    - **¿Qué significa cada métrica en `classification_report`?**
      - `precision`: De todas las veces que el modelo predijo una clase, ¿QUE porcentaje fue correcto? (Mide calidad de las predicciones positivas)
      - `recall` (sensibilidad): De todos los ejemplos reales de una clase, ¿qué porcentaje detectó el modelo? (Mide capacidad del modelo para encontrar todos los pos)
      - `f1-score`: Es la media de `precision` y `recall`. Es una métrica única que balancea las dos, útil cuando nos importan tanto los falsos positivos como los falsos negativos
      - `support`: número de muestras reales de cada clase en los datos

    - **¿Cómo interpretar la matriz de confusión?**
      -Es una tabla que resume los aciertos y errores. Para una clasificación binaria:
      - **Diagonal principal (arriba-izq a abajo-der)**: Los aciertos (Verdaderos Nega, Verdaderos Posi)
      - **Fuera de la diagonal**: Los errores (Falsos Posi, Falsos Nega)

    - **¿Cuándo usar `accuracy` vs otras métricas?**
      - `accuracy` (precisión global) cuando las **clases están balanceadas**
      - `precision`, `recall` y `f1-score` cuando las **clases están desbalanceadas**. `accuracy` puede ser tricky, xq un modelo puede tener una alta precisión solo                              prediciendo siempre la clase mayoritaria


## Objetivos 

## Actividades

## Desarrollo

## Evidencias
- resulta2

## Reflexiones

## Ref
