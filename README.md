
🏡 **Proyecto de Predicción de Precios de Vivienda en California**

📈 **Problema de Negocio**  
Este proyecto tiene como objetivo predecir los precios de las viviendas en California utilizando datos geoespaciales y características de las propiedades. Se exploran modelos de machine learning para ayudar a comprender cómo varían los precios según la ubicación y las características de las viviendas.

❓ **Preguntas Clave**  
- 🔍 **Análisis Inicial**: ¿Qué insights podemos obtener del análisis exploratorio inicial del conjunto de datos?
- 🛠️ **Transformaciones**: ¿Qué preprocesamiento es necesario para preparar los datos correctamente?
- 🌍 **Influencia Geográfica**: ¿Cómo afecta la ubicación (latitud, longitud, distancia a la costa) a los precios de las viviendas?
- 🏠 **Características de las Viviendas**: ¿Qué características como el número de habitaciones o el tamaño de las viviendas influyen más en los precios?
  
🚀 **Configuración del Ambiente**  
Asegúrate de tener las siguientes bibliotecas instaladas:

```bash
pip install numpy pandas seaborn matplotlib sklearn xgboost geopy folium
```

📥 **Obtención y Tratamiento de Datos**  
- **Cargando la Base de Datos**: Los datos provienen del conjunto de datos de California Housing, disponible en formato CSV.
  
🧹 **Tratamiento de Datos**  
Durante el preprocesamiento se realizan las siguientes operaciones:

- 🧽 **Manejo de Valores Faltantes**: Se imputa o elimina cualquier valor faltante en las variables clave.
- 🚫 **Eliminación de Duplicados**: Se identifican y eliminan filas duplicadas en el conjunto de datos.
- 📉 **Manejo de Outliers**: Se utilizan técnicas como el rango intercuartílico (IQR) para gestionar valores atípicos en el precio de las viviendas.
- 🏷️ **Codificación de Variables Categóricas**: Las variables categóricas se transforman en numéricas mediante codificación one-hot.

📊 **Normalización de Datos**  
Se eliminan columnas irrelevantes y se normalizan las variables para asegurar que los modelos tengan un rendimiento óptimo.

🔍 **Modelado**  
Se entrenan varios modelos de machine learning, entre ellos:

- **XGBoost**: Enfoque avanzado de predicción que utiliza boosting de gradiente para optimizar el rendimiento y manejar datos complejos de manera eficiente.
- **lightgbm**: Algoritmo de boosting basado en gradiente que se utiliza para establecer una línea base de predicción, destacando por su rapidez y capacidad de manejo de grandes volúmenes de datos.

Los modelos se evalúan utilizando métricas como el RMSE (Root Mean Squared Error), MAE (Mean Absolute Error) y el coeficiente de determinación R². 

🌐 **Visualización Geoespacial**  
Se crean mapas interactivos para visualizar cómo los precios de las viviendas varían geográficamente utilizando las coordenadas de latitud y longitud.

📝 **Conclusiones**  
Este proyecto ofrece un marco sólido para la predicción de precios de vivienda en California. A través de modelos avanzados y visualizaciones geoespaciales, se proporciona un análisis profundo de las variables que influyen en los precios del mercado inmobiliario.
