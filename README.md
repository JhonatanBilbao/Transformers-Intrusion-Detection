# 🛡️ Sistema de Detección de Intrusos en Redes (NIDS) usando TabTransformer

Este proyecto implementa un sistema de detección de intrusos en redes basado en aprendizaje profundo (TabTransformer) utilizando el conjunto de datos CIC-IDS-2017. Se parte de una versión inicial ejecutada en Google Colab y se adapta a un entorno local (Windows 10), mostrando comparativas de rendimiento y personalizaciones necesarias.

---

## 📌 Objetivo del Proyecto

- Clasificar el tráfico de red como **Benigno** o **Ataque** usando un modelo basado en **TabTransformer**.
- Aplicar técnicas de preprocesamiento, balanceo de clases, entrenamiento y evaluación del modelo.
- Adaptar el código para ejecutarse en una **PC personal con recursos limitados**.

---

## 🧠 Dataset

Se utiliza el dataset [CIC-IDS-2017](https://www.unb.ca/cic/datasets/ids-2017.html), convertido previamente de `.csv` a `.parquet` para optimizar lectura y procesamiento.

---

## ⚙️ Especificaciones de la PC Local (Windows 10)

| Componente     | Especificación                               |
|----------------|-----------------------------------------------|
| Procesador     | Intel(R) Core(TM) i5-10400F @ 2.90GHz (6 núcleos) |
| RAM            | 8 GB                                          |
| Disco SSD      | 250 GB (Kingston SNVS250G)                    |
| Disco HDD      | 1 TB (WDC WD10EZEX-00BBHA0)                   |
| Sistema Operativo | Windows 10 Pro - v10.0.19045.5854          |
| GPU            | No compatible con CUDA (CPU-only)            |

---

## 🧪 Librerías utilizadas

- `pandas`, `numpy`, `matplotlib`, `seaborn`
- `scikit-learn`, `imbalanced-learn`
- `torch`, `tab-transformer-pytorch`

---

## 🔄 Comparativa de Implementación

| Elemento                        | Google Colab                           | PC Local (Windows 10)                    |
|---------------------------------|----------------------------------------|------------------------------------------|
| Plataforma                      | Google Colab (GPU disponible)          | PC con CPU Intel                         |
| Dataset                         | Montado desde Google Drive             | Lectura directa desde `D:\...`           |
| Balanceo de clases              | `BorderlineSMOTE` sin restricciones    | `BorderlineSMOTE` + `sample(frac=0.25)` para evitar MemoryError |
| Librerías                       | Instaladas vía `!pip`                  | Instaladas vía `pip install` local       |
| Entrenamiento                   | Rápido (aceleración GPU)               | Más lento (solo CPU)                     |
| Visualización                   | Interactiva, gráficos en notebook      | Igual, usando `matplotlib` y `seaborn`   |

---

## 📊 Métricas de Evaluación

### ✅ Resultados en Google Colab ([GitHub del proyecto](https://github.com/JhonatanBilbao/Tesis-articulos))

| Métrica           | Valor                 |
|-------------------|-----------------------|
| Accuracy          | **98.56%**            |
| Precision         | 97.38%                |
| Recall            | 99.80%                |
| F1 Score          | 98.58%                |
| MCC               | 0.9714                |
| AUC-ROC           | **0.9987**            |

**Reporte de clasificación**:



