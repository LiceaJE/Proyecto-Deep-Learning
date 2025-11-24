# Proyecto-Deep-Learning

En este repositorio se encuentra el proyecto final de la materia Deep Learning, acerca de intentos de identificar fracturas mediante modelos YOLO en imágenes de radiografías.

## Descripción del Proyecto

Este proyecto explora el rendimiento de diferentes modelos YOLO (You Only Look Once) con diversos hiperparámetros para la detección automática de fracturas en imágenes de radiografías. El análisis se realiza en un Jupyter Notebook interactivo que compara múltiples arquitecturas y configuraciones.

## Contenido del Repositorio

- **`model_exploration.ipynb`**: Notebook principal con exploración completa de modelos y hiperparámetros
- **`requirements.txt`**: Dependencias de Python necesarias
- **`dataset.yaml`**: Plantilla de configuración para el dataset YOLO
- **`.gitignore`**: Archivos y directorios excluidos del control de versiones

## Inicio Rápido

### 1. Clonar el repositorio
```bash
git clone https://github.com/LiceaJE/Proyecto-Deep-Learning.git
cd Proyecto-Deep-Learning
```

### 2. Instalar dependencias
```bash
pip install -r requirements.txt
```

### 3. Preparar los datos
Crear la siguiente estructura de directorios:
```
data/
├── train/
│   ├── images/
│   └── labels/
├── val/
│   ├── images/
│   └── labels/
└── test/
    ├── images/
    └── labels/
```

### 4. Configurar dataset.yaml
Editar el archivo `dataset.yaml` con las rutas correctas de tu dataset.

### 5. Ejecutar el notebook
```bash
jupyter notebook model_exploration.ipynb
```

## Características del Notebook

### Modelos Evaluados
- YOLOv5 (nano, small, medium)
- YOLOv8 (nano, small, medium)

### Hiperparámetros Explorados
- Learning rate (0.001 - 0.01)
- Batch size (8, 16, 32)
- Image size (416, 640, 1280)
- Epochs (50, 100)
- Optimizers (SGD, Adam)

### Análisis Incluidos
- Comparación de arquitecturas YOLO
- Exploración de hiperparámetros
- Visualización de métricas (mAP, Precision, Recall)
- Matrices de correlación
- Análisis de trade-offs
- Configuración óptima recomendada

## Resultados

El notebook genera:
- Gráficos comparativos de rendimiento
- Tablas de resultados detalladas
- Archivo CSV con resultados completos
- Configuración óptima en formato JSON
- Visualizaciones de trade-offs

## Requisitos

- Python 3.9+
- CUDA (opcional, para entrenamiento con GPU)
- 8GB+ RAM recomendado
- Espacio en disco para datasets y modelos

## Uso del Notebook

El notebook incluye dos modos de operación:

1. **Modo Demostración**: Genera datos sintéticos para explorar la estructura y visualizaciones
2. **Modo Entrenamiento Real**: Descomentar las secciones de entrenamiento para ejecutar con datos reales

Para entrenamiento real, descomentar las líneas indicadas en las secciones 5 y 6 del notebook.

## Contribuciones

Este es un proyecto académico de la materia Deep Learning. Las sugerencias y mejoras son bienvenidas.

## Licencia

Este proyecto es parte de un trabajo académico en Deep Learning.

## Autores

Jesús Emiliano Licea Román
