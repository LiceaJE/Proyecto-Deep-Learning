# Bone Fracture Detection Using YOLOv8 and Transfer Learning

Este proyecto aplica técnicas de aprendizaje profundo para la detección automática de fracturas óseas en radiografías, utilizando modelos de detección de objetos (YOLOv8) y comparando distintos enfoques: modelo base, modelo con data augmentation y un modelo ajustado mediante transferencia de aprendizaje (fine-tuning de pesos preentrenados).

El objetivo es analizar el impacto de las distintas configuraciones de entrenamiento en el desempeño del modelo.

---

## Tabla de Contenidos
- Introducción  
- Dataset  
- Modelos entrenados  
- Conclusiones  

---

## Introducción

La detección automática de fracturas óseas en radiografías es un problema relevante en el diagnóstico médico asistido por computadora. En este proyecto se entrenan y comparan distintas variantes del modelo YOLOv8 para detectar fracturas en diferentes regiones anatómicas del miembro superior.

Se desarrollaron tres modelos:

1. Modelo 1: YOLOv8n base sin augmentations.  
2. Modelo 2: YOLOv8n con data augmentation y early stopping.  
3. Modelo 3: Modelo preentrenado descargado externamente y ajustado (fine-tuning) al dataset.  

El desempeño de cada modelo se evalúa mediante las métricas estándar de detección: precisión, recall, mAP50 y mAP50-95.

---
## Requerimientos
Este proyecto utiliza las siguientes dependencias, listadas en el archivo requirements.txt:

ultralytics
matplotlib
Pillow
numpy

Para instalarlas, ejecutar:

pip install -r requirements.txt

## Dataset

El dataset utilizado es:

**Bone Fracture Detection (YOLOv8 Format)**  
Autor: Pk Darabi  
Fuente: Kaggle

Enlace:  
https://www.kaggle.com/datasets/pkdarabi/bone-fracture-detection-computer-vision-project

El conjunto de datos contiene radiografías clasificadas en siete categorías:

| ID | Clase               |
|----|----------------------|
| 0  | elbow positive       |
| 1  | fingers positive     |
| 2  | forearm fracture     |
| 3  | humerus fracture     |
| 4  | humerus              |
| 5  | shoulder fracture    |
| 6  | wrist positive       |

---

## Modelos entrenados

### Modelo 1 — YOLOv8 Base
- Entrenado desde cero con configuración mínima.
- Sin data augmentation.
- Evidencia de sobreajuste en etapas finales.

### Modelo 2 — YOLOv8 con Data Augmentation
- Se aplicaron técnicas como Blur, MedianBlur, GrayScale, CLAHE y flip horizontal.
- Early stopping con paciencia de 20.
- Mejor generalización que el modelo base.

### Modelo 3 — Modelo Preentrenado + Fine-Tuning
- Se utilizó un modelo preentrenado externo especializado en fracturas.
- Se aplicó una tasa de aprendizaje más baja.
- Mejor desempeño en mAP general.

---

## Conlcusiones

Efectividad del Fine-Tuning: Se demostró que el Fine-Tuning fue exitoso para adaptar un modelo externo al dominio específico del proyecto, elevando su Recall de ~0.01 a ~0.27. Sin embargo, no superó a los modelos entrenados desde cero.

Superioridad del Data Augmentation: El Modelo 2 demuestra ser la arquitectura más equilibrada. El aumento de datos permitió al modelo generalizar mejor, logrando la mejor Precisión y el mejor mAP del grupo.

Limitación del Hardware/Datos: El hecho de que los tres modelos se estanquen en un mAP de ~0.24 sugiere que el problema ya no se resuelve con hiperparámetros. La resolución de entrada (640px) y la arquitectura pequeña (Nano) son cuellos de botella físicos que impiden detectar las fracturas más finas.

## Modelos
En la carpeta models se encuentran los 3 modelos ya entrenados que se usaron en el colab, el model.pt es el YOLOv8 nano, que no tenía un early stopping, y tampoco data augmentation, el model2.pt es el modelo con early stopping y data augmentation, y el model3.pt es un modelo ya pre-entrenado en fracturas, vuelto a entrenar específicamente para este dataset.
