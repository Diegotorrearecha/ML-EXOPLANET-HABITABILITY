# MountAdapt — Interactive Climate-Health Dashboard (Prototype)

## 🚀 Quickstart

### 1. Clona el repositorio
```bash
git clone https://github.com/<your-user>/mountadapt.git
cd mountadapt
```

### 2. Entorno virtual e instalación
```bash
python.exe -m venv .venv
# Windows (PowerShell)
.\.venv\Scripts\Activate.ps1
# macOS / Linux
# source .venv/bin/activate

pip install -r requirements.txt
```

---

## 📦 Requirements

### Minimal dependencies
- streamlit  
- pandas  
- numpy  
- scikit-learn  
- matplotlib  
- seaborn  
- statsmodels   # SARIMAX  
- shap  
- lime  
- reportlab     # PDF export  
- PyPDF2  

> **Nota:** guarda estas dependencias en `requirements.txt` para instalación rápida (`pip install -r requirements.txt`).

---

## 📊 Outputs (what the app produces)

La aplicación genera los siguientes artefactos y visualizaciones de forma dinámica, en función de los datos cargados por el usuario:

### Correlation Analysis
- Matriz de correlación (heatmap) sobre dataset original.
- **Augmented Correlations**: misma matriz aplicada al dataset con Data Augmentation (Gaussian Noise + Mixup), con comparación lado a lado.

### IA Models
- Tabla comparativa de modelos (R², MAE, RMSE) para:
  - Linear Regression
  - Random Forest
  - Gradient Boosting
  - SVR
  - MLPRegressor (configuración mostrada)
- Visualización de **y_test vs y_pred** para el mejor modelo (scatter + línea ideal).
- Exportable a CSV/PNG.

### Explainability
- Importancia global de variables con **SHAP** (summary plot, bar plot).
- Explicación local de predicciones concretas con **LIME** (sustituye al SHAP dependence plot).
- Descarga de imágenes explicativas.

### Forecasting (series temporales)
- Modelo SARIMAX para la variable seleccionada.
- Predicción a 5 años vista con intervalos de confianza.
- Gráficos interactivos: histórico vs forecast + componentes (trend/seasonal/resid).

### Data handling & App features
- Upload de CSVs personalizados: fusión automática con dataset base y validaciones (missing values, formato de fecha).
- Login/registro de usuarios (con fondo configurable y logos).
- Export dinámico a **PDF**: informe generado con los resultados y figuras vistas en pantalla (personalizado por usuario y dataset).
- Logs y resumen reproducible (WBS/Gantt/risks) para entrega académica.

---

## 🛠 Uso (run)

- Para lanzar la app Streamlit:
```bash
streamlit run app.py --server.port 8501
```

- Para lanzar tests / notebooks:
```bash
jupyter notebook
# o
python -m pytest tests/
```

---

## ℹ️ Notas importantes para entrega / TFG
- Indicar en la memoria: número de capas del `MLPRegressor` (ej. `hidden_layer_sizes=(100,75,50,25)`).
- Incluir tabla con parámetros de cada modelo (hiperparámetros usados).
- Reproducibilidad: añadir seed global (`np.random.seed(...)`, `torch.manual_seed(...)` si procede) y registrar versiones (`pip freeze > requirements_freeze.txt`).
- Asegurar que la pestaña Forecasting y Export report son dinámicas respecto a variables subidas por el usuario.

---

## ✍️ Licencia
Indica aquí la licencia de tu trabajo (por ejemplo, MIT) y cualquier atribución necesaria.

---

¿Quieres que adapte el texto de **Outputs** para que describa exactamente los nombres de tus ficheros/plots (por ejemplo `correlation_augmented.png`, `ytest_ypred_bestmodel.png`, `forecast_sarimax_5y.csv`) y así poder pegarlos ya en el `app.py` y en la memoria? Si quieres, te lo dejo con nombres exactos y ejemplos de snippet para generar y guardar cada figura.
