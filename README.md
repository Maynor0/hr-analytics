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

> Nota: En caso de publicar el repositorio de forma pública, los datos reales deben anonimizarse o sustituirse por una muestra. 

## Flujo de trabajo

### 1. Limpieza y preparación en Excel y Power Query
- Ordenación y limpieza inicial de la base.
- Tipificación de columnas.
- Tratamiento de valores nulos.
- Estructuración de la tabla para análisis posterior.

### 2. Análisis en Python
- Carga y transformación con `pandas`.
- Creación de variables derivadas.
- Estadística descriptiva.
- Pruebas t, ANOVA, Pearson y chi-cuadrado.
- Visualización con `matplotlib` y `seaborn`.

### 3. Dashboard en Power BI
- Construcción del modelo de datos.
- Creación de medidas DAX.
- Diseño de páginas interactivas.
- Análisis de RRHH por departamento, género, sueldo, evaluación y edad.

## Resultados destacados

- Se observa el reparto de la plantilla por género y departamento, identificando áreas con mayor concentración de personal. 
- La evaluación media por departamento permite detectar equipos con mejor desempeño y aquellos con margen de mejora. 
- El análisis de la distribución salarial muestra el rango, la mediana y posibles sueldos atípicos, facilitando el estudio de la política retributiva. 
- El scatter sueldo–evaluación, junto con la correlación, ayuda a comprobar la coherencia entre salario y rendimiento. 
- La parte demográfica (edad aproximada y agrupación por rangos) aporta contexto sobre la estructura generacional de la empresa. 

## Tecnologías utilizadas

- **Excel** para la revisión y preparación inicial de los datos.
- **Power Query** para la transformación y estandarización.
- **Python**:
  - `pandas` para manipulación de datos.
  - `numpy` para operaciones numéricas.
  - `scipy` para análisis estadístico.
  - `matplotlib` y `seaborn` para visualización.
- **Power BI** para el dashboard interactivo.
- **DAX** para medidas y cálculos dentro del modelo.

## Cómo ejecutar

1. Clonar el repositorio.  
2. Abrir el notebook o script de Python (`analisis_empleados.py` / `.ipynb`) y ejecutar las celdas; se requiere tener instaladas las librerías `pandas`, `numpy`, `matplotlib` y `seaborn`.  
3. Abrir `dashboard_empleados.pbix` en Power BI Desktop para explorar las visualizaciones y las medidas DAX. 
---

Puedes cambiar el nombre del proyecto, el archivo `.pbix` y el script según cómo los guardes, pero esta estructura ya está lista para pegar como `README.md` en tu repo.