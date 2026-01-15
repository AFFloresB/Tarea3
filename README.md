# Predicción de Riesgo en Créditos Hipotecarios

## 📌 Descripción del Proyecto

Este proyecto implementa un flujo de trabajo de Ciencia de Datos para predecir el incumplimiento de pago en solicitudes de crédito de **Home Credit**. Se aborda el problema técnico del desbalanceo de clases y la calidad de datos inconsistente mediante un análisis exploratorio profundo y modelos de Machine Learning supervisados.

## 🚀 Instalación y Configuración

### 1. Clonar y Preparar el Entorno

Primero, asegúrate de tener instaladas todas las dependencias necesarias ejecutando el siguiente comando:

```bash
pip install -r requirements.txt

```

### 2. Configuración de API de Kaggle (`.env`)

Para que el notebook descargue automáticamente el dataset desde [Home Credit Default Risk](https://www.kaggle.com/competitions/home-credit-default-risk/), cada usuario debe configurar su propio token.

1. Ve a tu perfil de Kaggle -> Settings -> API -> **Create New Token**.
2. Se descargará un archivo `kaggle.json`.
3. Crea un archivo llamado `.env` en la raíz de este proyecto.
4. Agrega tu clave siguiendo este formato:

```env
KAGGLE_API_TOKEN=TU_KEY_PERSONAL_AQUI

```

---

## 📊 Contenido del Análisis (`tarea3.ipynb`)

El desarrollo sigue una metodología rigurosa dividida en las siguientes etapas:

### I. Ingesta y ETL Automático

* El código detecta si el archivo `application_train.csv` existe localmente.
* Si no existe, utiliza la API de Kaggle para descargar y descomprimir los datos de la competición automáticamente.

### II. Análisis del Target

* **Diagnóstico de Balanceo:** Se identifica una fuerte desproporción (92% Clase 0 / 8% Clase 1).
* **Ratio de Desbalance:** Se calcula un ratio de **1 a 11.4**, fundamental para justificar el uso de SMOTE.

### III. Diagnóstico de Calidad de Datos

Siguiendo los requerimientos de la auditoría de datos, el notebook reporta:

* **Valores Nulos:** Porcentaje de ausencia de datos por columna y distribución por fila.
* **Inconsistencias:** Detección de errores lógicos en `DAYS_EMPLOYED`.
* **Outliers:** Identificación de valores atípicos en variables financieras mediante Boxplots.
* **Integridad:** Eliminación de variables constantes (sin varianza) y registros duplicados.

### IV. Ingeniería de Características y Balanceo

* **Limpieza:** Imputación de nulos y codificación de variables categóricas.
* **SMOTE:** Aplicación de sobremuestreo sintético para equilibrar el set de entrenamiento, permitiendo que el modelo aprenda a identificar correctamente los casos de incumplimiento (Clase 1).

### V. Modelado y Evaluación

Comparativa de tres algoritmos de clasificación:

1. **Regresión Logística**
2. **Gaussian Naive Bayes**
3. **Árbol de Decisión**

Se evalúa el rendimiento mediante **Matrices de Confusión** y **Curvas ROC (AUC)** para determinar la capacidad de discriminación del riesgo.

---

## 🛠️ Instrucciones de Uso

1. Instala las librerías: `pip install -r requirements.txt`.
2. Configura tu `.env` con tu token de Kaggle.
3. Abre el notebook `tarea3.ipynb` y ejecuta todas las celdas.
4. El sistema se encargará de la gestión de archivos y la generación de reportes visuales interactivos de forma automática.

---