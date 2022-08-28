# Pronósticos de demanda para el Sistema Eléctrico Nacional (SEN) de Chile con redes neuronales artificiales.   

**IMPORTANTE**: Dado problemas de compatibilidad en las versiones utilizadas de las librerías Numpy y Tesorflow, es necesario iniciar la primera celda (instalación de Numpy) del Jupyter Notebook y reiniciar el entorno de ejecución. Hecho lo anterior, podrá ejecutar el código sin problemas.   

## Contenido   

En este proyecto se podrán encontrar 3 archivos:
1. demanda_electrica_diaria.csv   
2. SEN_dmax.ipynb   
3. SEN_dmin.ipynb   

El primer archivo corresponde a un csv que contiene la información de demanda eléctrica en MW (Mega Watts) de los sistemas eléctricos SIC (Sistema Interconectado Central), SING (Sistema Interconectado del Norte Grande) y SEN (Sistema eléctrico Nacional). La data fue obtenida de la página de Energía Abierta (energiaabierta.cl - Comisión Nacional de Energía).   
Los primeros 2 sistemas (SIC y SING) ya no se encuentran operando, dada su unión definitiva en el año 2018 (proyecto anunciado en el año 2010), dando origen a SEN. Por lo que se tiene:   
- SIC y SING --> Enero 2006 hasta Diciembre 2017   
- SEN --> Enero 2018 hasta Septiembre 2021   
  
Dada la menor presencia de datos outliers y la actualidad de estos, se prosiguió a trabajar con la data de SEN para el estudio en cuestión.   

Los archivos 2 y 3 contienen el análisis de los sistemas mencionados y preparación de la data de SEN para los modelos de redes neuronales junto a su predicción. Se encuentran separados, dado que se posee la información de la demanda mínima y la demanda máxima, por lo que se prosiguió a crear, entrenar y predecir con los modelos por separado.   

Se crearon 5 modelos para cada caso y ver quién es el que mejor predice:   
- MLP (Multi Layer Perceptron)   
- LSTM (Long Short-Term Memory)   
- GRU (Gated Recurrent Neuronal)   
- Hibrido 1 (LSTM y Conv1D)   
- Hibrido 2 (GRU y Conv1D)    

El entrenamiento y predicción de los modelos está configurado para tomar 30 días atrás y predecir el siguiente día. Para poder predecir en el tiempo, se agrego el valor predicho al siguiente vector para predecir en base a este último y se prosiguió así sucesivamente según la cantidad de días en el tiempo a predecir.   
En este estudio se realizaron predicciones de 1, 2, 3 y 4 semanas del mes de septiembre de 2021 para la demanda mínima y máxima. Las predicciones fueron evaluadas a traves del MAE (Mean Absolute Error), MSE (Mean Square Error) y MAPE (Mean Absolute Percentage Error).
