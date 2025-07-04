
# 🏡 **Proyecto de Predicción de Precios de Vivienda en California**

## 📈 **Problema de Negocio**  
Este proyecto tiene como objetivo predecir los precios de las viviendas en California utilizando datos geoespaciales y características de las propiedades. Se exploran modelos de machine learning para ayudar a comprender cómo varían los precios según la ubicación y las características de las viviendas.

  
## 🚀 **Configuración del Ambiente**  
Asegúrate de tener las siguientes bibliotecas instaladas:

```bash
pip install numpy pandas seaborn matplotlib sklearn xgboost lightgbm folium
```
  **Estructura del proyecto**

```bash
california-housing-prediction/
├── data/
|   └── California_Houses.csv
├── Images/       # Contiene los gráficos de evaluación de los modelos            
├── notebooks/
│   └── Prediccion_precios_CA.ipynb
├── maps/
│   └── mapa_precios_california.html
├── README.md
├── requirements.txt
└── .gitignore
  
```
📥 **Obtención y Tratamiento de Datos**  
- **Cargando la Base de Datos**: Los datos provienen del conjunto de datos de California Housing, disponible en formato CSV.

  El dataset contiene 20640 filas y 14 columnas.
  
## 🧹 **Tratamiento de Datos**  
Durante el preprocesamiento se realizan las siguientes operaciones:

- 🧽 **Manejo de Valores Faltantes**: El dataset no contiene valores faltantes ni duplicados.
  
- 📉 **Manejo de Outliers**: Se utilizan técnicas de truncamiento con el percentil 0.97 para gestionar valores atípicos en el precio de las viviendas.
      Se prefirió este método al de rango interquantilico(IQR) debido a que este no se adapta bien a distribuciones asimétricas como en este caso donde hay variables con un sesgo muy           a la derecha. Esto puede llevar a descartar valores grandes válidos como "valores atípicos".

- 📊 **Análisis de multicolinealidad**: Se evalua la multicolinealidad  de las variables respecto a la variable dependiente 'Median_House_Value' usando los métodos Pearson y Spearman para medir el grado de correlación, un coeficiente de correlación mide el grado en que dos variables tienden a cambiar al mismo tiempo.

  Heatmap de la matriz de correlación para variables geoespaciales.

  ![](https://github.com/jumacaq/Estimacion_precios_vivienda_California/blob/main/Images/geospacial_correlation.png)

  Heatmap de la matriz de correlación para variables socio-económicas.

   ![](https://github.com/jumacaq/Estimacion_precios_vivienda_California/blob/main/Images/social_economic_correlation.png)

**Conceptos Relacionados**

- La correlación de Pearson evalúa la relación lineal entre dos variables continuas. Una relación es lineal cuando un cambio en una variable se asocia con un cambio proporcional en la      otra variable.
- La correlación de Spearman evalúa la relación monótona entre dos variables continuas u ordinales. En una relación monótona, las variables tienden a cambiar al mismo tiempo, pero no   necesariamente a un ritmo constante.
- En este caso específico se determina que es mejor usar los valores entregados por el método Spearman ya que por ejemplo las propiedades cercanas a la costa en general tienden a tener más valor, pero hay otras variables como el ingreso promedio o el número de habitaciones, que también son importantes, por lo que no existe una relación lineal entre el precio de la propiedad y las demas variables en general, esto se corrobora mirando la matriz de correlación donde Spearman tiene valores más altos como se observa en los gráficos Heatmaps.
- Luego de este análisis se decide eliminar las columnas ['Distance_to_San_Francisco','Tot_Bedrooms', 'Households'] por alta correlación y no aportar al modelo.
   

## 📅 **Modelado**  
Se entrenan dos modelos de machine learning:

- **XGBoost**: Enfoque avanzado de predicción que utiliza boosting de gradiente para optimizar el rendimiento y manejar datos complejos de manera eficiente.
- **Lightgbm**: Algoritmo de boosting basado en gradiente que se utiliza para establecer una línea base de predicción, destacando por su rapidez y capacidad de manejo de grandes volúmenes de datos.

Los modelos se evalúan utilizando métricas como el RMSE (Root Mean Squared Error), MAE (Mean Absolute Error) y el coeficiente de determinación R². 

Aqui se muestran los gráficos de comparación entre los outputs obtenidos en entrenamiento y validación con XGBoost luego de aplicar optimización de parámetros con GridSearchCV.

![](https://github.com/jumacaq/Estimacion_precios_vivienda_California/blob/main/Images/training_validation_xgboost_gridsearch.png)

Este esta gráfica se observa la importancia de las variables con XGBoost luego de aplicar optimización de parámetros con GridSearchCV.

![](https://github.com/jumacaq/Estimacion_precios_vivienda_California/blob/main/Images/feature_importance_xgboost_gridsearch.png)

Aqui se muestran los gráficos de comparación entre los outputs obtenidos en entrenamiento y validación con Lightgbm luego de aplicar optimización de parámetros con GridSearchCV

![](https://github.com/jumacaq/Estimacion_precios_vivienda_California/blob/main/Images/training_validation_lightgbm_gridsearch.png)

Este esta gráfica se observa la importancia de las variables con Lightgbm luego de aplicar optimización de parámetros con GridSearchCV.

![](https://github.com/jumacaq/Estimacion_precios_vivienda_California/blob/main/Images/feature_importance_lightgbm_gridsearch.png)


🌐 **Visualización Geoespacial**  
Se crean mapas interactivos para visualizar cómo los precios de las viviendas varían geográficamente utilizando las coordenadas de latitud y longitud.

📝 **Conclusiones**  
Este proyecto ofrece un marco sólido para la predicción de precios de vivienda en California. A través de modelos avanzados y visualizaciones geoespaciales, se proporciona un análisis profundo de las variables que influyen en los precios del mercado inmobiliario.
