# 🏦 Optimización de Campañas de Marketing Bancario: Un Enfoque KDD

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Status](https://img.shields.io/badge/Status-Finalizado-success)
![Course](https://img.shields.io/badge/Curso-Minería_de_Datos-orange)

> **Proyecto Final - Minería de Datos con Python**
>
> **Pontificia Universidad Católica de Chile**

## 📄 Descripción del Proyecto

Este proyecto aplica la metodología **KDD (Knowledge Discovery in Databases)** para resolver un problema de ineficiencia en campañas de telemarketing bancario. Utilizando el dataset *Bank Marketing* del UCI Machine Learning Repository, desarrollamos un flujo completo de Ciencia de Datos para predecir la suscripción de depósitos a plazo.

El objetivo principal es pasar de un enfoque de llamadas masivas aleatorias a una **estrategia de focalización inteligente**, identificando los segmentos de clientes más rentables y propensos a la compra.

## 🛠️ Tecnologías y Librerías

El proyecto fue desarrollado en **Python** utilizando las siguientes librerías clave:

* **Pandas & NumPy:** Manipulación y limpieza de datos.
* **Scikit-Learn:** Preprocesamiento, PCA, K-Means, Random Forest y Regresión Logística.
* **PyGAM:** Implementación de Modelos Aditivos Generalizados (GAM) para análisis no lineal.
* **Matplotlib & Seaborn:** Visualización de datos (EDA).

## 📊 Metodología (Proceso KDD)

El trabajo sigue estrictamente las fases del proceso KDD:

1.  **Selección:** Dataset de 45.211 registros con 17 variables iniciales.
2.  **Preprocesamiento:**
    * Detección de desbalance de clases (11.7% de éxito).
    * Limpieza de anomalías en la variable `pdays`.
3.  **Transformación:**
    * Ingeniería de variables (`fue_contactado_antes`).
    * One-Hot Encoding aumentando la dimensionalidad a 44 variables.
4.  **Minería de Datos (Unsupervised & Supervised):**
    * Reducción de dimensionalidad con **PCA** (31 componentes explican el 90% de varianza).
    * Segmentación de clientes con **K-Means**.
    * Predicción con modelos lineales y de ensamble.

## 🚀 Resultados Clave

### 1. Perfilamiento de Clientes (Clustering)
Mediante K-Means (k=3), descubrimos un segmento de alto valor denominado **"Cluster 0"**:
| Cluster | Saldo Promedio (€) | Tasa de Conversión | Perfil |
| :---: | :---: | :---: | :--- |
| **0** | **1.556** | **23%** | **Alto Valor ("Oro")** |
| 1 | 1.138 | 5% | Bajo Interés |
| 2 | 1.457 | 11% | Promedio |

### 2. Modelos Predictivos (Supervisado)
Se evaluaron tres modelos utilizando la métrica **ROC-AUC** debido al desbalance de clases. El **Random Forest** demostró ser el más robusto, seguido de cerca por el modelo GAM.

| Ranking | Modelo | ROC-AUC | Observación |
| :---: | :--- | :---: | :--- |
| 🥇 | **Random Forest** | **0.9250** | Mejor capacidad de generalización. |
| 🥈 | **GAM (pygam)** | 0.9121 | Confirma relaciones no lineales. |
| 🥉 | Regresión Logística | 0.8949 | Línea base. |

## 📉 Variables Más Influyentes
Según el modelo ganador, las variables determinantes para la predicción son:
1.  **Duration:** Duración de la llamada.
2.  **Balance:** Saldo en cuenta del cliente.
3.  **Age:** Edad del cliente.

## 🏁 Conclusión de Negocio

La estrategia propuesta para el banco es **híbrida y jerarquizada**:
1.  **Filtro Primario:** Priorizar clientes pertenecientes al **Cluster 0** (Alto saldo y conversión histórica).
2.  **Filtro Secundario:** Dentro de ese grupo, aplicar el modelo **Random Forest** para ordenar las llamadas por probabilidad de éxito.

Esta metodología permite maximizar el retorno de inversión (ROI) de la campaña, reduciendo drásticamente los costos operativos de contactar a clientes del Cluster 1 (bajo interés).

## 💻 Instalación y Uso

Para replicar este análisis, clona el repositorio e instala las dependencias:

```bash
git clone [https://github.com/crimen-cl/Proyecto-Miner-a-de-Datos-con-Python.git](https://github.com/crimen-cl/Proyecto-Miner-a-de-Datos-con-Python.git)
pip install pandas numpy matplotlib seaborn scikit-learn pygam plotly
```

Ejecuta el archivo principal en Jupyter Notebook:

```bash
jupyter notebook script.ipynb
```

Autor: Cristian Méndez Fuenzalida

Profesor: Pedro Luiz Ramos
