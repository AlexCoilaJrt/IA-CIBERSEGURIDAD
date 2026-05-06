# IA en Ciberseguridad: Guía Práctica y Pipeline Integrado

Este repositorio contiene una serie de cuadernos interactivos (Jupyter Notebooks) que cubren la implementación de soluciones de Inteligencia Artificial aplicadas a la Ciberseguridad. El proyecto abarca desde la configuración inicial del entorno hasta la creación de un pipeline de seguridad end-to-end con monitoreo de deriva de datos.

## 🚀 Contenido del Proyecto

El proyecto está estructurado de forma modular para facilitar el aprendizaje y la implementación paso a paso de diversas técnicas de IA en el ámbito de la seguridad:

| Orden | Notebook | Descripción y Técnicas |
| :--- | :--- | :--- |
| **01** | `01_entorno_setup.ipynb` | Configuración de Python, creación de entorno virtual e instalación de bibliotecas críticas (TensorFlow, Scikit-Learn, SHAP, etc.). |
| **02** | `02_deteccion_amenazas.ipynb` | Detección de anomalías en tráfico de red utilizando algoritmos como **Isolation Forest** y **Autoencoders**. |
| **03** | `03_deteccion_malware.ipynb` | Clasificación de archivos ejecutables (PE) mediante modelos de aprendizaje supervisado (**Árboles de Decisión** y **Random Forest**). |
| **04** | `04_respuesta_incidentes.ipynb` | Automatización de la respuesta ante incidentes (**SOAR**) y triaje automático de alertas con **SVM**. |
| **05** | `05_analisis_comportamiento.ipynb` | Análisis de Comportamiento de Usuarios y Entidades (**UBA/UEBA**) para la detección de amenazas internas. |
| **06** | `06_explicabilidad_xai.ipynb` | Implementación de **SHAP** y **LIME** para proporcionar transparencia y explicabilidad a las decisiones de la IA. |
| **07** | `07_ataques_adversariales.ipynb` | Estudio de la robustez de los modelos frente a **ataques adversariales** y técnicas de defensa proactiva. |
| **08** | `08_pipeline_integrado.ipynb` | Integración final de todos los módulos en un **Pipeline de Seguridad** unificado con detección de deriva de datos. |

## 🛠️ Requisitos e Instalación

### Requisitos previos
- **Python 3.9 o superior** (Se recomienda Python 3.11 para garantizar la compatibilidad de todas las bibliotecas).

### Configuración del Entorno

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/AlexCoilaJrt/IA-CIBERSEGURIDAD.git
   cd IA-CIBERSEGURIDAD
   ```

2. **Crear y activar un entorno virtual:**
   ```bash
   # En Windows:
   python -m venv ai_security_env
   .\ai_security_env\Scripts\activate

   # En Linux/macOS:
   python3 -m venv ai_security_env
   source ai_security_env/bin/activate
   ```

3. **Instalar dependencias:**
   Puedes instalar las dependencias ejecutando la celda correspondiente en el notebook `01_entorno_setup.ipynb` o usando pip:
   ```bash
   pip install numpy==1.26.4 tensorflow==2.16.2 scikit-learn pandas matplotlib seaborn pefile shap==0.44.1 lime scipy joblib imbalanced-learn
   ```
   *Nota: Las versiones de `numpy` y `tensorflow` están fijadas para evitar conflictos conocidos.*

## 🏗️ Arquitectura del Pipeline Integrado

El módulo final (`08_pipeline_integrado.ipynb`) implementa una clase `PipelineSeguridad` que simula un flujo de trabajo real en un SOC (Security Operations Center):

1. **Ingesta y Preprocesamiento:** Normalización de características de tráfico de red y extracción de atributos de archivos.
2. **Detección de Deriva (Data Drift):** Utiliza el test estadístico de **Kolmogorov-Smirnov** para alertar si los datos de entrada en producción difieren significativamente de los datos de entrenamiento.
3. **Análisis Multicapa:**
   - **Capa de Anomalías:** Identifica comportamientos sospechosos en la red (detección no supervisada).
   - **Capa de Malware:** Clasifica archivos como benignos o maliciosos (detección supervisada).
4. **Persistencia:** Capacidad para guardar (`save`) y cargar (`load`) el pipeline completo entrenado para su despliegue inmediato.

## 📊 Tecnologías Principales
- **Machine Learning:** Scikit-learn (SVM, Random Forest, Isolation Forest).
- **Deep Learning:** TensorFlow & Keras (Autoencoders).
- **Explicabilidad:** SHAP & LIME.
- **Análisis de Archivos:** `pefile` para el análisis estático de binarios Windows.
- **Estadística:** Scipy para el monitoreo de deriva.

---
*Este proyecto ha sido diseñado con fines educativos para demostrar el potencial de la Inteligencia Artificial en la automatización y fortalecimiento de las tareas de ciberseguridad.*
