# 🚚 Predicción de Retrasos en Envíos

## 📌 Descripción
Este proyecto utiliza **Machine Learning** para predecir si un envío llegará con retraso o no, a partir de un dataset con información de pedidos, clientes, productos y modos de envío.  
El objetivo es **apoyar la toma de decisiones logísticas**, identificando factores que influyen en los retrasos y construyendo un modelo confiable para anticiparlos.

---

## 🎯 Objetivos
- Analizar las variables más relacionadas con retrasos (producto, país, ciudad, modo de envío).  
- Probar diferentes algoritmos de clasificación (Random Forest, Gradient Boosting, XGBoost, LightGBM).  
- Manejar el desbalance de clases con técnicas como **class_weight** y **SMOTE**.  
- Ajustar el **umbral de decisión** para encontrar el mejor equilibrio entre precisión y recall.  
- Seleccionar el modelo final más estable y práctico para producción.

---

## 📊 Exploración de datos
Durante el análisis exploratorio se identificaron patrones clave:
- El **modo de envío Second Class** concentra más retrasos que otros.  
- Algunos **productos y ciudades** presentan mayor proporción de demoras.  
- El dataset está **desbalanceado**, con más casos de retraso que de no retraso.  

Estas observaciones guiaron la selección de variables y el diseño de los modelos.

---

## 🤖 Modelos probados
Se entrenaron y evaluaron distintos algoritmos:

- **Random Forest** → Accuracy: 0.57, ROC-AUC: 0.69. Buen recall en retrasos, bajo en otras clases.  
- **Gradient Boosting** → Accuracy: 0.56, ROC-AUC: 0.70. Mejor sensibilidad, pero precisión baja.  
- **XGBoost** → Accuracy: 0.56, ROC-AUC: 0.70. Potente, pero afectado por el desbalance.  
- **XGBoost + SMOTE** → Accuracy: 0.56, ROC-AUC: 0.69. Mejor recall en minoritarias, pero más falsos positivos.  
- **LightGBM (multiclase)** → Accuracy: 0.52, ROC-AUC: 0.70. Balance más estable que XGBoost.  
- **LightGBM + RandomizedSearchCV** → ROC-AUC: 0.70. Ajuste fino de hiperparámetros, mejora ligera.  
- **LightGBM binario (reagrupación de clases)** → Accuracy: 0.68, ROC-AUC: 0.72. Mejor modelo final.

---

## 📈 Ajuste de umbral y curva Precision‑Recall
El modelo final (LightGBM binario) se evaluó con distintos umbrales:  
- **Umbrales bajos (0.3–0.4)** → más recall, menos precisión.  
- **Umbrales altos (0.55–0.6)** → más precisión, menos recall.  
- **Umbral óptimo: 0.55** → Precisión: 0.81, Recall: 0.58, F1-score: 0.68.  

La curva Precision‑Recall confirmó que este punto logra el mejor equilibrio entre **detecciones confiables** y **sensibilidad razonable**.

---

## 🧩 Conclusiones
- El **LightGBM binario con umbral 0.55** es el modelo recomendado.  
- Ofrece un balance sólido entre precisión y recall, con alta confiabilidad en la detección de retrasos.  
- El proyecto demuestra cómo el análisis exploratorio y el ajuste de umbrales pueden transformar un modelo en una herramienta práctica para la operación logística.

---

## 🚀 Uso del proyecto
1. Clonar el repositorio.  
2. Instalar dependencias (`requirements.txt`).  
3. Ejecutar el notebook principal para entrenar y evaluar los modelos.  
4. Ajustar el umbral según las necesidades operativas.  

---

## 📂 Estructura del repositorio
- `Envios.md` → Notebook principal con exploración, modelos y resultados.  
- `data/` → Dataset de ejemplo.  
- `images/` → Gráficas de análisis y curvas de evaluación.  
- `README.md` → Presentación del proyecto.  

---

## 👤 Autor
Proyecto desarrollado por **Roberto González Espinosa de los Monteros**  
💼 Clinical Logistic Specialist | 📊 Data Scientist en formación  
