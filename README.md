# Proyecto: Network Intrusion Detection System con TabTransformer

Este proyecto implementa un modelo de detección de intrusos en redes basado en aprendizaje profundo (TabTransformer) utilizando el dataset **CIC-IDS 2017**. El código original fue diseñado para ejecutarse en **Google Colab** con recursos en la nube, y posteriormente fue adaptado para funcionar en **una PC local con Windows 10**.

---

## 📌 Objetivos

- Clasificar tráfico de red como **Benigno** o **Ataque**.
- Aplicar técnicas de preprocesamiento, balanceo de clases, y entrenamiento con un modelo TabTransformer.
- Evaluar el desempeño del modelo y visualizar métricas clave.

---

## ⚙️ Especificaciones de la PC local

| Recurso         | Detalle                              |
|-----------------|--------------------------------------|
| CPU             | Intel(R) Core(TM) i5-10400F @ 2.90GHz (6 núcleos) |
| RAM             | 8 GB                                 |
| Disco SSD       | 250 GB (Kingston SNVS250G)           |
| Disco HDD       | 1 TB (WDC WD10EZEX-00BBHA0)          |
| Sistema Operativo | Windows 10 Pro (Versión 10.0.19045.5854) |
| GPU             | No especificada (no compatible con CUDA) |

---

## 🧠 Librerías y Frameworks

- `pandas`, `numpy`, `seaborn`, `matplotlib`
- `scikit-learn`, `imbalanced-learn`
- `torch` (PyTorch)
- `tab-transformer-pytorch`

---

## 🧪 Dataset

Se utilizaron archivos `.parquet` generados a partir de los `.csv` del dataset **CIC-IDS-2017**. El preprocesamiento incluyó:

- Eliminación de duplicados.
- Codificación binaria de la columna `Label` (`Benign = 0`, `Attack = 1`).
- Normalización de características.
- Balanceo de clases con `BorderlineSMOTE`.

---

## 🧬 Comparativa de Implementación

| Elemento                   | Versión Google Colab                           | Versión Local (PC Windows)                     |
|----------------------------|-----------------------------------------------|------------------------------------------------|
| Plataforma                 | Google Colab (cloud, GPU disponible)          | PC local (CPU-only)                            |
| Dataset                    | `/content/drive/MyDrive/...`                  | `D:\Jhonatan\Nueva carpeta\CIC-IDS-20177-PAQUET` |
| Librerías instaladas       | `!pip install ...`                            | Instalación manual con `pip install`           |
| Lectura de datos           | Google Drive montado                          | Acceso directo a disco local                   |
| Manejo de memoria          | ~12 GB de RAM en Colab                        | 8 GB en local → requiere `df.sample()`         |
| Balanceo                   | SMOTE completo                                | `BorderlineSMOTE` sobre 25% del dataset        |
| Entrenamiento              | GPU acelerado (rápido)                        | CPU solamente (más lento)                      |
| Visualización              | Interactiva en notebook                       | Igual, con `matplotlib` y `seaborn`            |

---

## 💻 Adaptaciones necesarias para entorno local

1. **Ruta de datos modificada:**

```python
data_path = r"D:\Jhonatan\Nueva carpeta\CIC-IDS-20177-PAQUET"
