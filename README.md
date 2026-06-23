# Análisis Exploratorio de Datos (EDA) - Accidentes de Tráfico en Madrid

![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=flat&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/matplotlib-%23ffffff.svg?style=flat&logo=matplotlib&logoColor=black)

## 📌 Metadatos del Proyecto
* **Origen de los Datos:** [Portal de Datos Abiertos del Ayuntamiento de Madrid](https://datos.madrid.es/)
* **Dataset utilizado:** [Accidentes de tráfico detalle CSV](https://datos.madrid.es/egob/catalogo/300228-28-accidentes-trafico-detalle.csv)
* **Documentación de la estructura:** [Estructura del Conjunto de Datos](https://datos.madrid.es/FWProjects/egob/Catalogo/Seguridad/Ficheros/Estructura_ConjuntoDatos_Accidentesv2dfpdfp)

---

## 🎯 Objetivos del Proyecto
1. **Análisis General:** Realizar un análisis exploratorio riguroso para comprender la naturaleza de los siniestros viales en la ciudad de Madrid durante el año 2024.
2. **Preparación para ML:** Tratar valores nulos, corregir tipos de datos y estructurar la información para su posterior integración en un modelo predictivo de **Machine Learning**.
3. **Resolución de Pregunta de Negocio:** 
   > *“¿En qué franja horaria se producen los accidentes con mayor gravedad (ingreso superior a 24 horas o fallecidos) y qué condiciones (estado meteorológico, tipo de accidente, etc.) pueden influir en ello?”*

---

## 🛠️ Tecnologías y Librerías Utilizadas
* **Python** (Core del análisis)
* **Pandas** & **NumPy** (Manipulación y limpieza de datos)
* **Matplotlib** & **Seaborn** (Visualización estadística)

---

## 📊 Fases del Análisis Implementadas

### 1. Inspección y Entendimiento General
* Carga del dataset (`49,340` registros y `19` columnas originales).
* Identificación de tipos de variables (categóricas, numéricas, temporales y espaciales).

### 2. Limpieza de Datos y Tratamiento de Nulos
Se aplicaron criterios lógicos e institucionales (siguiendo la documentación técnica) para evitar sesgos o invención de datos:
* **`tipo_accidente`**: Eliminación de filas con registros nulos debido a su baja frecuencia (5 casos).
* **`estado_meteorológico`**: Agrupación de nulos bajo la nueva categoría *"Desconocido"*.
* **`tipo_vehiculo`**: Imputación de valores faltantes como *"Sin_info"*.
* **`lesividad` y `cod_lesividad`**: Mapeo y conversión de códigos numéricos hacia una nueva variable estructurada llamada **`gravedad`** (Categorías: *LEVE, GRAVE, FALLECIDO, Sin asistencia sanitaria, Desconocido*).
* **Coordenadas UTM**: Eliminación de registros sin geolocalización por inviabilidad de invención de coordenadas.
* **`positiva_alcohol` & `positiva_droga`**: Clasificación estricta de valores booleanos/nulos para reflejar los controles no registrados o negativos de forma correcta (`0` y `Desconocido`).

### 3. Análisis Univariado y Control de Duplicados
* Implementación de filtros para mitigar el impacto del **doble conteo de accidentes** causado por la presencia de múltiples implicados en un mismo expediente (`num_expediente`).

---

## 🏗️ Estructura del Proyecto
```
madrid-traffic-accidents-eda/
│
├── data/
│   └── accidentalidad_2024.csv
│
├── notebooks/
│   └── 01_accidentes_madrid_eda.ipynb
│
├── images/
│   ├── accidentes por estado meteo.png
│   ├── accidentes por distrito.png
│   ├── tipo accidente.png
│   └── distribucion de la hora.png
    ├── correlacion variables numericas.png
    └── evolucion de accidentes.png
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## 🚀 Próximos Pasos
* Regresión Logística.
* Modelos de Machine Learning.
* Predicción de gravedad de accidentes.
* Predicción de resultados positivos en alcohol.
* Análisis geoespacial mediante mapas interactivos.


---

## 🛡️ Licencia
Este proyecto está bajo la Licencia MIT. Eres libre de usar, modificar y compartir este proyecto con la atribución correspondiente.
