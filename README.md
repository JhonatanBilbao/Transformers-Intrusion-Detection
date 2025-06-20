# 🛡️ Sistema de Detección de Intrusos en Redes (NIDS) con TabTransformer

Este proyecto implementa un sistema de detección de intrusos basado en aprendizaje profundo utilizando el modelo **TabTransformer** sobre el conjunto de datos **CIC-IDS-2017**. Se presentan resultados tanto en **Google Colab (con GPU)** como en una **PC local con CPU**, detallando adaptaciones realizadas para ejecutar en entornos con recursos limitados.

---

## 🎯 Objetivo del Proyecto

- Clasificar el tráfico de red como **Benigno** o **Ataque**.
- Aplicar técnicas de preprocesamiento, balanceo de clases, entrenamiento y evaluación.
- Comparar el rendimiento entre ejecución en Google Colab y entorno local (Windows 10).
- Demostrar cómo adaptar un modelo complejo a hardware sin GPU.

---

## 🧠 Dataset

Se utiliza el dataset [CIC-IDS-2017](https://www.unb.ca/cic/datasets/ids-2017.html), un conjunto de datos realista y etiquetado que simula tráfico de red con múltiples tipos de ataques.  
> ⚠️ Para optimizar el procesamiento, los archivos `.csv` fueron previamente convertidos a formato `.parquet`.

---

## ⚙️ Especificaciones del Entorno Local (Windows 10)

| Componente        | Especificación                                 |
|-------------------|-------------------------------------------------|
| Procesador        | Intel Core i5-10400F @ 2.90GHz (6 núcleos)     |
| RAM               | 8 GB                                            |
| Almacenamiento    | SSD 250 GB (Kingston) + HDD 1 TB               |
| Sistema Operativo | Windows 10 Pro (v10.0.19045.5854)              |
| GPU               | No compatible con CUDA (CPU-only)              |

---

## 📚 Librerías Utilizadas

- **Procesamiento y Visualización**: `pandas`, `numpy`, `matplotlib`, `seaborn`
- **Preprocesamiento y ML**: `scikit-learn`, `imbalanced-learn`
- **Deep Learning**: `PyTorch`, `tab-transformer-pytorch`

---

## 🔁 Comparativa de Implementación

| Característica             | Google Colab (GPU)                   | PC Local (CPU)                          |
|----------------------------|--------------------------------------|-----------------------------------------|
| Plataforma                 | Basado en navegador, GPU disponible  | CPU Intel i5                           |
| Lectura de datos           | Desde Google Drive (.csv/.parquet)  | Desde disco local (`D:\...`)           |
| Balanceo de clases         | `BorderlineSMOTE` completo           | `BorderlineSMOTE` + `sample(frac=0.25)` para reducir uso de memoria |
| Instalación de librerías   | `!pip install`                       | `pip install` en entorno virtual/local |
| Velocidad de entrenamiento | Rápido                               | Más lento (sin GPU)                    |
| Visualización              | En notebook                          | Igual, con `matplotlib` / `seaborn`    |

---

## 📊 Métricas de Evaluación

### ✅ Resultados en Google Colab

| Métrica           | Valor     |
|-------------------|-----------|
| **Accuracy**       | **98.56%** |
| Precision         | 97.38%    |
| Recall            | 99.80%    |
| F1 Score          | 98.58%    |
| MCC               | 0.9714    |
| AUC-ROC           | **0.9987** |

[🔗 GitHub del proyecto en Colab](https://github.com/JhonatanBilbao/Tesis-articulos)

---

### 🖥️ Resultados en PC Local

| Métrica           | Valor     |
|-------------------|-----------|
| **Accuracy**       | **98.21%** |
| Precision         | 96.65%    |
| Recall            | 99.87%    |
| F1 Score          | 98.23%    |
| MCC               | 0.9647    |
| AUC-ROC           | **0.9977** |

> El rendimiento fue excelente incluso con recursos limitados, demostrando la viabilidad de modelos complejos como TabTransformer en entornos modestos.

---

## 🛠️ Adaptaciones Realizadas para la PC Local

1. **Cambio de rutas para lectura local**
```python
data_path = r"D:\Jhonatan\Nueva carpeta\CIC-IDS-20177-PAQUET"

```



2. **Evitar MemoryError con muestreo:**
```python
df = df.sample(frac=0.25, random_state=42)
```

3. **Cambio de tipo de dato para ahorrar RAM:**
```python
X = X.astype(np.float32)
```

4. **Desactivación de CUDA:**
```python
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
```




