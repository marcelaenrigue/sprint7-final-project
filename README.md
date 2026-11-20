# sprint7-final-project

# Análisis de clientes de ConnectaTel

## Objetivo del proyecto

Analizar el comportamiento de los clientes de **ConnectaTel**, una empresa de telecomunicaciones con operaciones en México y Colombia, a partir de sus registros de llamadas y mensajes.

El proyecto busca identificar patrones de consumo, valores atípicos y segmentos de usuarios que ayuden a proponer mejoras en la oferta comercial. El análisis se enfoca en la información disponible hasta **2024**.

## Datasets utilizados

| Archivo | Contenido |
|---|---|
| `plans.csv` | Planes disponibles, precios, minutos, GB y costos por consumo adicional. |
| `users_latam.csv` | Datos de clientes: identificador, edad, ciudad, fechas de registro y cancelación, y plan contratado. |
| `usage.csv` | Registros de llamadas y mensajes por usuario, con fechas, duración o longitud según la actividad. |

## Etapas del análisis

1. **Carga y exploración:** lectura de los archivos CSV y revisión de dimensiones, columnas y tipos de datos.
2. **Diagnóstico de calidad:** identificación de valores nulos, valores *sentinel* e inconsistencias en fechas y registros de actividad.
3. **Limpieza:** tratamiento de edades inválidas, ciudades sin identificar y fechas fuera del período; revisión de los nulos de duración y longitud según el tipo de actividad.
4. **Estadísticas por usuario:** agrupación de llamadas, mensajes y minutos de llamadas por `user_id`, y combinación con los datos de clientes.
5. **Visualizaciones y outliers:** histogramas, diagramas de caja (*boxplots*) y detección de valores atípicos mediante el método IQR.
6. **Segmentación:** clasificación de clientes por edad (`Joven`, `Adulto`, `Adulto Mayor`) y nivel de actividad (`Bajo uso`, `Uso medio`, `Alto uso`); visualización de los segmentos.
7. **Análisis ejecutivo:** interpretación de los resultados y recomendaciones comerciales.

## Principales hallazgos

- El **uso medio** es el segmento predominante entre los clientes analizados.
- Los clientes de los planes **Basico** y **Premium** presentan patrones de llamadas y mensajes relativamente similares.
- Se identificaron valores atípicos de consumo que conviene conservar para investigar posibles necesidades diferenciadas de los usuarios.

## Cómo ejecutar el notebook en Google Colab

1. Descarga el notebook `S7 Version-Estudiante-Project-ConnectaTel (1).ipynb` y los tres archivos CSV indicados arriba.
2. Abre [Google Colab](https://colab.research.google.com/) y selecciona **Archivo → Subir notebook** para abrir el archivo `.ipynb`.
3. En el panel **Archivos** de Colab, sube `plans.csv`, `users_latam.csv` y `usage.csv`.
4. **Actualiza las rutas** de la celda de carga de datos: el notebook utiliza originalmente `/datasets/`, pero los archivos subidos a Colab suelen quedar en `/content/`. Usa:

   ```python
   plans = pd.read_csv('/content/plans.csv')
   users = pd.read_csv('/content/users_latam.csv')
   usage = pd.read_csv('/content/usage.csv')
   ```

5. Ejecuta las celdas **en orden, de arriba hacia abajo** (menú **Entorno de ejecución → Ejecutar todas**).
6. Revisa las tablas, gráficos, resultados de segmentación y conclusiones del análisis ejecutivo.

**Nota:** Los archivos cargados directamente en Colab pueden desaparecer al reiniciar la sesión. Si eso ocurre, vuelve a subir los CSV. No se necesita cambiar el código de análisis, solo las rutas de lectura cuando corresponda.

## Guía breve de reproducción

- Mantén juntos el notebook y los tres CSV originales al guardar el proyecto en GitHub.
- Utiliza un entorno con **Python 3**, `pandas`, `matplotlib` y `seaborn` (disponibles habitualmente en Google Colab).
- Ejecuta el notebook desde el principio, sin saltarte las celdas de limpieza, agregación y segmentación: las variables posteriores dependen de los pasos anteriores.
- Comprueba que se hayan generado las columnas `cant_mensajes`, `cant_llamadas`, `cant_minutos_llamada`, `grupo_uso` y `grupo_edad`.
- Si ejecutas el notebook fuera de Colab, adapta las rutas de `pd.read_csv()` a la ubicación de los CSV en tu equipo.

## Archivos para GitHub

```text
connectatel/
├── README.md
├── S7 Version-Estudiante-Project-ConnectaTel (1).ipynb
├── plans.csv
├── users_latam.csv
└── usage.csv
```

*Proyecto académico de análisis de datos con Python.*
