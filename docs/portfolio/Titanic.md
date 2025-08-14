---
title: "EDA del Titanic 🚢"
date: 12-08-2025
---

# Análisis Exploratorio de Datos (EDA) del Titanic 🚢

Como primera actividad, se nos presentó la idea de investigar sobre un datasaet muy famoso en la cienda de datos. 

## Contexto
El dataset del Titanic contiene ciertos datos de los pasajeros a bordo del barco, dividido en un conjunto de "entrenamiento" y otro de prueba. El objetivo del ejercicio de Kaggle es usar esta información para construir un modelo de Machine Learning que pueda predecir con precisión quiénes sobrevivieron al naufragio en el conjunto de prueba. Todo esto como un desafío de clasificación para familiarizarnos en el ciclo de vida de un proyecto de cienca de datos.

## Objetivos
**Inverstigar** sobre la estructura y significado de las variables del dataset
**Visualizar las relaciones** entre las variables importantes (sexo, edad, clase) y la supervivencia.

## Actividades (con tiempos estimados)
- Investigación y comprensión del dataset, las variables y el problema
- Configuración de Colab y conexión a Drive
- Carga de Datos
- Visualización de datos clave en patrones de supervivencia
- Documentación

## Desarrollo
El proceso se llevó a cabo en un notebook de Google Colab.

???+ info "Ver el desarrollo técnico paso a paso"

    ### 1. Configuración del Entorno
    El primer paso fue importar las librerías y configurar el entorno para guardar los resultados
    
    !!! tip "Google Drive"
        Configurar Google Drive en Colab permite persistir los datos, resultados y el propio notebook entre sesiones, evitando perder trabajo.

    ```python
    import pandas as pd
    import numpy as np
    import matplotlib.pyplot as plt
    import seaborn as sns
    from pathlib import Path

    # Google Drive para persistencia
    try:
        from google.colab import drive
        drive.mount('/content/drive')
        ROOT = Path('/content/drive/MyDrive/IA-UT1-Titanic')
    except Exception:
        ROOT = Path.cwd() / 'IA-UT1-Titanic'

    RESULTS_DIR = ROOT / 'results'
    RESULTS_DIR.mkdir(parents=True, exist_ok=True)
    print(f'Los resultados se guardarán en: {RESULTS_DIR}')
    ```
    ### 2. Cargar datos desde Kaggle
    Usamos la API de Kaggle para descargar el dataset directamente en el entorno de Colab.

    ```python linenums="1"
    # Configuración de la API de Kaggle
    !pip -q install kaggle
    from google.colab import files
    files.upload() # Subir el archivo kaggle.json
    !mkdir -p ~/.kaggle && cp kaggle.json ~/.kaggle/ && chmod 600 ~/.kaggle/kaggle.json

    # Descargar y descomprimir el dataset
    !kaggle competitions download -c titanic -p data
    !unzip -o data/titanic.zip -d data

    train_df = pd.read_csv('data/train.csv')
    test_df = pd.read_csv('data/test.csv')
    ```
    ### 3. Valores nulos
    Una vez cargados los datos, necesitaba saber en dónde podía encontrar valores nulos
    
    ```python
    print("Dimensiones del dataset de entrenamiento:", train_df.shape)
    train_df.info()

    # valores nulos
    print("\nValores nulos x columna:")
    print(train_df.isna().sum().sort_values(ascending=False))
    ```
    Este paso expuso que las columnas `Age`, `Cabin` y `Embarked` contienen valores faltantes


## Evidencias
El análisis visual a continuación dejó una representación clarísima sobre los patrones y factores de supervivencia.

![Panel de Visualizaciones del EDA del Titanic] 

## Reflexión
- Qué aprendiste, qué mejorarías, próximos pasos

## Referencias
- Fuentes consultadas con enlaces relativos cuando corresponda


---

## Guía de formato y ejemplos (MkDocs Material)

Usá estos ejemplos para enriquecer tus entradas. Todos funcionan con la configuración del template.

### Admoniciones

!!! note "Nota"
    Este es un bloque informativo.

!!! tip "Sugerencia"
    Considerá alternativas y justifica decisiones.

!!! warning "Atención"
    Riesgos, limitaciones o supuestos relevantes.

### Detalles colapsables

???+ info "Ver desarrollo paso a paso"
    - Paso 1: preparar datos
    - Paso 2: entrenar modelo
    - Paso 3: evaluar métricas

### Código con resaltado y líneas numeradas

```python hl_lines="2 6" linenums="1"
def train(
    data_path: str,
    epochs: int = 10,
    learning_rate: float = 1e-3,
) -> None:
    print("Entrenando...")
    # TODO: implementar
```

### Listas de tareas (checklist)

- [ ] Preparar datos
- [x] Explorar dataset
- [ ] Entrenar baseline

### Tabla de actividades con tiempos

| Actividad           | Tiempo | Resultado esperado               |
|---------------------|:------:|----------------------------------|
| Revisión bibliográfica |  45m  | Lista de fuentes priorizadas     |
| Implementación      |  90m   | Script ejecutable/documentado    |
| Evaluación          |  60m   | Métricas y análisis de errores   |

### Imágenes con glightbox y atributos

Imagen directa (abre en lightbox):

![Diagrama del flujo](../assets/placeholder.png){ width="420" }

Click para ampliar (lightbox):

[![Vista previa](../assets/placeholder.png){ width="280" }](../assets/placeholder.png)

### Enlaces internos y relativos

Consultá también: [Acerca de mí](../acerca.md) y [Recursos](../recursos.md).

### Notas al pie y citas

Texto con una afirmación que requiere aclaración[^nota].

[^nota]: Esta es una nota al pie con detalles adicionales y referencias.

### Emojis y énfasis

Resultados destacados :rocket: :sparkles: y conceptos `clave`.
