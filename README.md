# Trabajo Fin de Máster Universitario de Ciencia de Datos

Código fuente del TFM **'Minority Report en Londres: un análisis de los sesgos en los datos policiales'**.

## Resumen

La inteligencia artificial es una de las tecnologías con mayor previsión de crecimiento en los próximos años y con un uso cada vez más extensivo en todos los sectores de actividad. Su aplicación en ámbitos especialmente sensibles, con gran impacto en la sociedad, está generando preocupación después de que varios estudios hayan puesto de manifiesto que los resultados obtenidos por algunos de estos algoritmos son injustos y discriminatorios.

A diferencia de estudios anteriores, enfocados fundamentalmente en datos y algoritmos norteamericanos, este trabajo emplea datos pertenecientes al Reino Unido, a Londres en concreto, para crear un modelo de policía predictiva con el objetivo de mostrar los sesgos en los que incurren este tipo de sistemas.

La construcción del modelo se realiza siguiendo un proceso común y ampliamente utilizado en los proyectos de ciencia de datos, denominado KDD, y partiendo de las mismas premisas y similares fuentes de datos que otros modelos de vigilancia predictiva.

Una vez analizados los resultados del modelo creado e identificados sus sesgos, puede concluirse que el uso indiscriminado y generalizado de este tipo de sistemas sin intervención o revisión humana, no hace sino perpetuar y aumentar las desigualdades existentes actualmente en nuestra sociedad. 

Es necesario establecer un marco de trabajo que facilite el conocimiento sobre el funcionamiento interno de este tipo de sistemas y aplique garantías para su uso dependiendo de la criticidad e impacto de su ámbito de actuación.

## Código

### 0_creacion_dataset
Construcción del conjunto de datos empleado para el modelo de policía predictiva. Recoge información sobre las actuaciones policiales de tipo 'detención y registro' de la web <a href='https://data.police.uk/'>data.police.uk</a> sobre las fuerzas policiales que operan en Londres. También obtiene, empleando la librería <a href='https://geopy.readthedocs.io/en/stable/'>Geopy</a> y el servicio de geolocalización <a href='https://nominatim.org/'>Nominatim</a> la dirección completa de las cooordenadas facilitadas por el *dataset* anterior incluyendo el distrito en que han tenido lugar dichas intervenciones.

### 1_analisis_exploratorio
Carga de los datos de actuaciones policiales obtenidos previamente junto con la información relativa a sus ubicaciones y realización de un análisis exploratorio y algunas operaciones de preprocesamiento tales como la eliminación de valores perdidos o la homogeneización de datos.

### 2_construccion_modelo
Creación del modelo de predicción de actuaciones policiales de detención y registro de personas y/o vehículos. El objetivo es obtener un algoritmo que permita identificar qué actuaciones son más probables que finalicen con resultado positivo, es decir, con indicios de delito que requieren de una actuación policial o judicial posterior.    

### 3_explicabilidad_modelo
Aplicación de técnicas de explicabilidad agnósticas del modelo (<a href='https://github.com/marcotcr/lime'>LIME</a> y <a href='https://github.com/slundberg/shap'>SHAP</a>) para entender mejor el comportamiento del modelo construido. Para revisar si presenta sesgos no deseados, se emplea además la librería <a href='http://www.datasciencepublicpolicy.org/projects/aequitas/'>Aequitas</a>, que permite calcular fácilmente diversas métricas de equidad y realizar una comparativa visual.

### 99_graficas_apoyo
Creación de gráficas adicionales a las existentes en el análisis exploratorio de datos surgidas durante la elaboración de la memoria del TFM.

### 99_tecnicas_oversampling
Aplicación de varias técnicas de aumento de datos sobre un modelo base para intentar resolver los problemas de precisión encontrados para la clase minoritaria y que lastran el rendimiento global de los modelos diseñados.

## Ficheros de datos
En la carpeta datasets pueden encontrarse los datos empleados para la realización del proyecto:
* 042017-022021.zip: conjunto de registros extraído de <a href='https://data.police.uk/'>data.police.uk</a> con los datos de actuaciones policiales en Londres.
* ethnic_ratios_all_ages.csv: distribución poblacional por etnias a nivel de MSOA según el <a href='https://www.nomisweb.co.uk/census/2011'>censo de 2011</a>.
* modelled-household-income-estimates-borough.csv: estadísticas sobre los ingresos familiares por distritos según la *Greater London Authority*.

## Recursos adicionales
El archivo 3_imagen_arbol.png contiene una imagen a mayor resolución del árbol mostrado en el *notebook* de explicabilidad.   
El archivo libs_config.txt contiene el listado de librerías y versiones utilizadas durante el proyecto.   
En la carpeta maps se encuentran varios ficheros con información geográfica que son necesarios para visualizar los mapas de Londres.
