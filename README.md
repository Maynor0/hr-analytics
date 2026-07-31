# HR Analytics – Análisis de empleados (BD_Mo)

Proyecto de análisis de datos de empleados que combina preparación de datos en Excel y Power Query, análisis exploratorio en Python y visualización interactiva en Power BI.

## Objetivo

El objetivo del proyecto es analizar la plantilla de una empresa desde la perspectiva de RRHH: composición por género y departamento, distribución salarial, evaluación del desempeño, estructura jerárquica y características demográficas (edad). A partir de estos análisis se construye un dashboard que facilita la toma de decisiones. 

## Datos

El dataset principal se encuentra en el archivo `BD_Mo.xlsx` (hoja `Tabla1`) y contiene 194 registros con las siguientes columnas: 
- `ID_Empleado`
- `Nombre`, `Apellido`
- `Estado`
- `Nacimiento`
- `Genero`
- `Departamento`
- `Posicion`
- `Nombre_Jefe`
- `Evaluación`
- `Sueldo`

## Flujo de trabajo

1. **Excel y Power Query**  
   - Ordenación y limpieza inicial de la base.  
   - Tipificación de columnas (fechas, números, texto).  
   - Tratamiento de valores nulos y estructuración de la tabla para análisis posterior. 

2. **Análisis en Python**  
   Script principal: `analisis_empleados.py` (o notebook equivalente). 
   - Carga de datos con `pandas` desde `BD_Mo.xlsx`.  
   - Revisión básica: `head()`, `info()`, `shape`, `columns`, `isna().sum()`.  
   - Conversión de tipos: `Nacimiento` a fecha, `Evaluación` y `Sueldo` a numérico.  
   - Perfil del personal:
     - distribución por `Genero`, `Departamento`, `Posicion` y `Estado`.  
   - Distribución salarial:
     - estadísticas descriptivas (`describe()`),
     - detección de sueldos atípicos mediante IQR.  
   - Evaluación del rendimiento:
     - evaluación media por departamento, posición y jefe.  
   - Relación sueldo–evaluación:
     - correlación entre ambas variables.  
   - Estructura jerárquica:
     - número de empleados por jefe.  
   - Demografía:
     - año de nacimiento y edad aproximada, agrupaciones por género. 

3. **Visualización en Python**

   Gráficos generados con `matplotlib` y `seaborn`: 

   - Empleados por género (`countplot` sobre `Genero`).  
   - Empleados por departamento (`countplot` sobre `Departamento`).  
   - Evaluación media por departamento (`barplot` con `estimator=np.mean`).  
   - Distribución salarial (`boxplot` de `Sueldo`).  
   - Relación sueldo–evaluación (`scatterplot` de `Evaluación` vs `Sueldo` con color por `Genero`).  

   Estos gráficos permiten responder preguntas como:
   - ¿Cómo se distribuye la plantilla por género y departamento?  
   - ¿Qué departamentos presentan mejor evaluación media?  
   - ¿Cómo se distribuyen los sueldos y dónde hay valores atípicos?  
   - ¿Existe relación entre el nivel salarial y la evaluación del desempeño? 

4. **Dashboard en Power BI**

   Archivo: `dashboard_empleados.pbix`. 

   Principales elementos:

   - **Medidas DAX** (ejemplos):
     - `Total Sueldo = SUM('Tabla1'[Sueldo])`
     - `Promedio Evaluación = AVERAGE('Tabla1'[Evaluación])`
     - `Empleados = COUNTROWS('Tabla1')`
     - `Sueldo Promedio = AVERAGE('Tabla1'[Sueldo])`
     - Medidas por departamento y jefe usando `CALCULATE` y `ALLEXCEPT`.  
     - Clasificación de evaluación (`Estado Evaluación`) con `SWITCH(TRUE(), ...)`.  
     - Agrupación de edad (`Edad Grupos`) a partir de una columna calculada de edad. 

   - **Páginas del dashboard**:
     - **Resumen RRHH**: tarjetas (empleados, total sueldo, sueldo promedio, evaluación media) y barras por departamento, con segmentadores por género, estado y departamento. 
     - **Evaluación**: evaluación media por jefe y por posición, estado de evaluación y matriz con detalle por empleado (jefe, sueldo, edad, estado de evaluación). 
     - **Sueldos**: sueldo por posición, sueldo promedio por departamento y scatter sueldo–evaluación por empleado. 
     - **Demografía**: agrupación de edad por departamento y género, tarjeta de edad media y mapa con distribución geográfica. 

## Resultados destacados

- Se observa el reparto de la plantilla por género y departamento, identificando áreas con mayor concentración de personal. 
- La evaluación media por departamento permite detectar equipos con mejor desempeño y aquellos con margen de mejora. 
- El análisis de la distribución salarial muestra el rango, la mediana y posibles sueldos atípicos, facilitando el estudio de la política retributiva. 
- El scatter sueldo–evaluación, junto con la correlación, ayuda a comprobar la coherencia entre salario y rendimiento. 
- La parte demográfica (edad aproximada y agrupación por rangos) aporta contexto sobre la estructura generacional de la empresa. 

## Tecnologías utilizadas

- **Excel** y **Power Query** para limpieza y transformación inicial de la base. 
- **Python** (`pandas`, `numpy`, `matplotlib`, `seaborn`) para análisis exploratorio y visualización básica. 
- **Power BI** y **DAX** para construir el modelo de datos y el dashboard interactivo. 

## Cómo ejecutar

1. Clonar el repositorio.  
2. Abrir el notebook o script de Python (`analisis_empleados.py` / `.ipynb`) y ejecutar las celdas; se requiere tener instaladas las librerías `pandas`, `numpy`, `matplotlib` y `seaborn`.  
3. Abrir `dashboard_empleados.pbix` en Power BI Desktop para explorar las visualizaciones y las medidas DAX. 
---

Puedes cambiar el nombre del proyecto, el archivo `.pbix` y el script según cómo los guardes, pero esta estructura ya está lista para pegar como `README.md` en tu repo.
