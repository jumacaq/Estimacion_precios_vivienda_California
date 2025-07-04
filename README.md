
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

- 📊 **Análisis de multicolinealidad**: Se evalua la multicolinealidad  de las variables usando los métodos Pearson y Spearman para medir el grado de correlación, esta evaluación se hizo  separando el dataset en dos: uno para variables geoespaciales y otra de variables socio-económicas.

  Se eliminan columnas irrelevantes tras la evaluación para asegurar que los modelos tengan un rendimiento 

## 📅 **Modelado**  
Se entrenan varios modelos de machine learning, entre ellos:

- **XGBoost**: Enfoque avanzado de predicción que utiliza boosting de gradiente para optimizar el rendimiento y manejar datos complejos de manera eficiente.
- **lightgbm**: Algoritmo de boosting basado en gradiente que se utiliza para establecer una línea base de predicción, destacando por su rapidez y capacidad de manejo de grandes volúmenes de datos.

Los modelos se evalúan utilizando métricas como el RMSE (Root Mean Squared Error), MAE (Mean Absolute Error) y el coeficiente de determinación R². 

🌐 **Visualización Geoespacial**  
Se crean mapas interactivos para visualizar cómo los precios de las viviendas varían geográficamente utilizando las coordenadas de latitud y longitud.

📝 **Conclusiones**  
Este proyecto ofrece un marco sólido para la predicción de precios de vivienda en California. A través de modelos avanzados y visualizaciones geoespaciales, se proporciona un análisis profundo de las variables que influyen en los precios del mercado inmobiliario.
