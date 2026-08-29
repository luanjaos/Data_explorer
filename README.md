# Explorador automático de datos

Aplicación web en Streamlit para cargar archivos tabulares y ejecutar un análisis exploratorio de datos de forma automática, interactiva y sin datasets predeterminados.

## Funcionalidades

- Carga de archivos desde el navegador y procesamiento en memoria.
- Limpieza de espacios en nombres de columnas y detección prudente de fechas por nombre.
- Filtros interactivos para fechas, categorías y variables numéricas.
- Indicadores de filas, columnas, duplicados y valores faltantes.
- Resumen de tipos Pandas y tipos analíticos.
- Inspección de duplicados y análisis de valores faltantes.
- Estadísticas descriptivas numéricas y categóricas.
- Histogramas, diagramas de caja y frecuencias categóricas con Plotly.
- Correlaciones Pearson, Spearman y Kendall.
- Detección de valores atípicos mediante rango intercuartílico.
- Tabla interactiva ordenable y selección de columnas visibles.
- Descarga en CSV UTF-8 con BOM de datos filtrados y valores atípicos.

## Formatos admitidos

- CSV
- XLSX, mediante `openpyxl`
- XLS, mediante `xlrd`

> El archivo debe contener una tabla legible en la primera hoja si se trata de Excel.

## Estructura del repositorio

```text
explorador-automatico-datos/
├── app.py
├── requirements.txt
└── README.md
```

No se incluye ningún dataset.

## Instalación

Se recomienda Python 3.12.

```bash
python -m venv .venv
```

Activación en Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

Activación en macOS o Linux:

```bash
source .venv/bin/activate
```

Instale las dependencias:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

## Ejecución local

Desde la raíz del repositorio:

```bash
streamlit run app.py
```

Streamlit mostrará la dirección local en la terminal. Abra la aplicación, cargue un archivo compatible y utilice las pestañas del análisis.

## Despliegue en Streamlit Community Cloud

1. Cree un repositorio en GitHub.
2. Suba `app.py`, `requirements.txt` y `README.md` a la raíz.
3. Inicie sesión en Streamlit Community Cloud con GitHub.
4. Seleccione **Create app**.
5. Elija el repositorio, la rama y `app.py` como archivo de entrada.
6. En la configuración avanzada, seleccione Python 3.12.
7. Pulse **Deploy**.

La aplicación no requiere secretos, claves ni variables de entorno.

## Privacidad y uso responsable

Los datos se procesan durante la sesión de la aplicación. No cargue información personal, confidencial o sensible en una instancia pública. El análisis exploratorio no reemplaza la interpretación de una persona experta. Una correlación no implica causalidad y un valor atípico no necesariamente representa un error.

## Limitaciones conocidas

- Los archivos muy grandes pueden superar la memoria o los límites de carga del entorno de despliegue.
- Solo se analiza la primera hoja de los libros de Excel.
- Los CSV con estructuras irregulares, varias tablas o separadores ambiguos pueden requerir preparación previa.
- La detección de fechas se intenta únicamente en columnas cuyo nombre contiene `fecha` o `date`, y exige una proporción mínima de valores reconocibles.
- La clasificación entre variable categórica y texto usa una regla heurística basada en cardinalidad.
- El método IQR puede no ser apropiado para todas las distribuciones o áreas de conocimiento.
- La correlación requiere al menos dos variables numéricas con observaciones suficientes.
- Los filtros categóricos no incluyen los valores faltantes como categoría seleccionable.
