# 🦠 Proyecto ETL: Datos COVID-19 en EE.UU.

Este proyecto implementa un pipeline ETL completo (Extract, Transform, Load) utilizando una API pública de datos de COVID-19. El objetivo es practicar habilidades de ingeniería de datos, incluyendo consumo de APIs, limpieza de datos, transformación, validaciones y carga en una base de datos relacional.


## 🎯 Objetivo del proyecto

Desarrollar un pipeline ETL real que:

- Consuma datos diarios de casos COVID-19 en EE.UU. desde una API pública.
- Transforme los datos: limpieza, conversión de tipos y generación de métricas derivadas.
- Almacene la información transformada en una base de datos SQLite.
- Sirva como proyecto de portafolio para mostrar competencias clave como ingeniero de datos.


## 🧪 Dataset y fuente

- **Fuente oficial**: [COVID Tracking Project](https://covidtracking.com/)
- **API utilizada**: `https://api.covidtracking.com/v1/us/daily.json`
- **Frecuencia**: Datos diarios por país (EE.UU.)
- **Formato**: JSON

---

## ⚙️ Tecnologías usadas

| Herramienta | Propósito |
|-------------|-----------|
| Python 3.x  | Lenguaje de programación principal |
| Pandas      | Manipulación y análisis de datos |
| Requests    | Consumo de API REST |
| SQLite3     | Base de datos relacional embebida |
| Google Colab | Desarrollo en entorno basado en la nube |
| Matplotlib (opcional) | Visualización de datos |

---

## 🔄 Flujo ETL

### 1. 🔍 Extracción

- Se hace un request HTTP a la API pública del COVID Tracking Project.
- Se obtiene un JSON con los registros diarios de COVID-19 en EE.UU.

### 2. 🧹 Transformación

- Se convierte el JSON a un DataFrame de Pandas.
- Se seleccionan columnas clave: fecha, casos positivos, negativos, muertes, hospitalizaciones, recuperados, etc.
- Se convierten tipos de datos (fechas, numéricos).
- Se eliminan o transforman valores nulos y negativos.
- Se calcula la **tasa de positividad** (`positives / totalTestResults`).
- Se ordenan los datos cronológicamente y se valida la calidad.

### 3. 💾 Carga

- Se guarda el DataFrame limpio en una base de datos SQLite (`covid_us.db`).
- Se reemplaza la tabla si ya existía (`if_exists='replace'`).


## 📦 Estructura del proyecto

ETL_Covid/
├── ETL-Covid.ipynb # Notebook con el pipeline completo
├── covid_us.db # Base de datos SQLite con los datos cargados
└── covid_us_clean # Csv limpio

