# 🤖 challenge_Telecom-X (Parte 2: Machine Learning)

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Banner del Proyecto](https://img.shields.io/badge/Data_Science-Python-blue?style=for-the-badge&logo=python)
![Alura Latam](https://img.shields.io/badge/Alura%20Latam-00447B?style=for-the-badge&logo=target&logoColor=white)
![Oracle ONE](https://img.shields.io/badge/Oracle%20ONE-F80000?style=for-the-badge&logo=oracle&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
> **Nota:** Este proyecto es la continuación directa del análisis exploratorio. 
> Puedes ver la **Fase 1 (EDA,Limpieza y transformación de datos)** aquí: [Repositorio Parte 1](https://github.com/Harold-dev-code/challenge_Telecom-X_parte_uno)
---

## 📝 Descripción del Proyecto

Tras la fase exploratoria, me integro al equipo de **Machine Learning** de Telecom X. El objetivo es construir un pipeline robusto de clasificación para predecir qué clientes tienen mayor probabilidad de cancelar sus servicios (Churn), permitiendo a la empresa actuar de forma preventiva.

---

## ⚙️ Instalación y Uso
Para replicar este análisis y probar los modelos predictivos, sigue estos pasos:

1. **Clonar el repositorio:**
    ```bash
    git clone https://github.com/Harold-dev-code/TelecomX_Parte2_Tercer-Challenge.git
    ```
2. Carga de Datos:
   - El proyecto utiliza el archivo datos_telecomX_procesados.csv incluido en este repositorio, el cual ya cuenta con la limpieza inicial de la Fase 1.
3. Abrir el Notebook:
   - Sube el archivo challenge_telecom_x_parte_dos.ipynb a Google Colab o ábrelo en tu entorno local de Jupyter Notebook.
4. Ejecutar las celdas:
   - Ejecuta todas las celdas en orden para replicar el proceso

## 🛠️ Pipeline de Trabajo

### 1. Preprocesamiento y Feature Engineering
* **Limpieza Técnica:** Se estandarizaron tipos de datos (como `TotalCharges` a float) y se eliminaron registros inconsistentes.
* **Encoding Estratégico:** * Simplificación de variables: Se detectó que "No internet service" y "No phone service" eran funcionalmente equivalentes a "No".
    * Aplicación de **One-Hot Encoding** para variables categóricas.
* **Tratamiento de Desbalance:** Utilicé **SMOTE** (Synthetic Minority Over-sampling Technique) para equilibrar la clase minoritaria (Churn=1), que representaba menos del 30% de los datos.

### 2. Selección de Variables (Optimización)
Realicé un análisis de correlación para evitar la **multicolinealidad**:
* Se eliminó `account.Charges.Total` por su alta correlación (0.83) con `tenure`.
* Se descartaron variables con correlación casi nula con el Churn (como `gender` y `PhoneService`) para simplificar el modelo sin perder potencia predictiva.


### 3. Modelado y Comparación
Entrené y evalué tres algoritmos distintos: **Regresión Logística**, **Random Forest** y **XGBoost**.

| Métrica | Regresión Logística (Final) | Random Forest | XGBoost |
| :--- | :---: | :---: | :---: |
| **Recall (Churn=1)** | **0.69** | 0.51 | 0.54 |
| **AUC-ROC** | **0.8351** | 0.8126 | 0.8127 |
| **F1-Score** | **0.62** | 0.55 | 0.56 |

## 🏆 Modelo Seleccionado: Regresión Logística
Aunque los modelos de ensamble (RF y XGBoost) son más complejos, la **Regresión Logística con datos estandarizados** resultó ser la ganadora para este caso de negocio:
* **Capacidad de Detección:** Logra un **Recall del 69%**, superando significativamente a los modelos basados en árboles. En Churn, es preferible un falso positivo que perder a un cliente por no detectarlo.
* **Simplicidad:** Logramos los mismos resultados reduciendo el número de variables de 38 a 33.


## 📈 Conclusiones Estratégicas
1. **Antigüedad (Tenure):** Es el predictor más fuerte. Los clientes nuevos tienen una probabilidad drásticamente mayor de abandonar.
2. **Cargos Mensuales:** Los clientes que cancelan tienen, en promedio, cargos mensuales más altos ($74.44 vs $61.26).
3. **Punto Crítico:** La matriz de confusión del modelo final muestra que logramos capturar correctamente a 387 clientes en riesgo de Churn en el set de prueba.


## 💻 Tecnologías Utilizadas
* **Python** (Pandas, NumPy)
* **Scikit-Learn** (Modelado y Escalado)
* **Imbalanced-learn** (SMOTE)
* **Matplotlib & Seaborn** (Visualización de métricas)


## 👤 Autor

Desarrollado por [Harold-dev-code](https://github.com/Harold-dev-code).
Dentro del programa de formación ONE - Oracle Next Education de Oracle y Alura Latam https://www.oracle.com/latam/education/oracle-next-education/

## ⚖️ Licencia

Este proyecto está bajo la Licencia MIT - mira el archivo [LICENSE](LICENSE) para más detalles.

