## 1.	Estructura de carpetas
Dashboard es el componente que se encarga de cargar todos los datos provenientes del backend y de renderizar las gráficas y todos los componentes. En la carpeta services se encuentra metricsService, el cual se encarga de realizar las solicitudes de datos al backend y proporcionar la información necesaria mediante la función getMetricData().

## 2.	Componentes principales
Hay 4 secciones, Total commits, Promedio diario, Máximo y la gráfica que muestra la evolución de los commits. Las primeras tres muestran métricas calculadas a partir de los datos obtenidos de la API mediante componentes MetricCard. La última sección utiliza Chart.js para representar visualmente el comportamiento de los commits a lo largo del tiempo, facilitando el análisis de tendencias.

## 3.	Manejo del estado con Hooks
Para el manejo de los estados, se utiliza useEffect() para cargar todos los datos de los commits solicitados de la base de datos una sola vez. Y useState para almacenar estos datos desde la API.

## 4.	Consumo de APIs
El consumo de la API se realiza importando getMetricData desde el archivo metricsService, el cual está en la carpeta services. Este tiene la función getmetricData(), encargada de realizar la solicitud de información al backend y devolver los datos requeridos. Posteriormente, estos datos son almacenados en el estado mediante setData(result) para que puedan ser utilizados en el cálculo de métricas y la generación de la gráfica.

## 5.	Flujo de datos entre componentes
El flujo de datos en el frontend empezaría con la API, que mandaría los datos solicitados al dashboard, este se encargaría de transformarlos, hacer los cálculos solicitados y finalmente desplegarlos.

## 6.	Implementación de gráficas o visualizaciones
La aplicación utiliza Chart.js junto con react-chartjs-2 para generar una gráfica de líneas que muestra la evolución de los commits a lo largo del tiempo. Los datos de la gráfica se construyen dinámicamente a partir de la información obtenida de la API, utilizando las etiquetas como eje horizontal y los valores como eje vertical. Esta visualización permite identificar tendencias y cambios en la actividad de manera más clara y sencilla.

## 7.	Identificación de posibles mejoras
El problema más grande que existe actualmente y que mejoraría considerablemente el rendimiento solucionarlo, es que actualmente para cada render se recalculan todos los datos, esto se podría solucionar fácilmente utilizando un useMemo().
En cuestión de visuales, los colores están muy mal implementados porque muchos elementos tales como algunos títulos y datos se pierden en el fondo. Además de que se podría agregar más descripciones para los datos mostrados para dar aun más contexto.