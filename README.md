# MCDI501 - Estadística Computacional para la Toma de Decisiones

Repositorio del Grupo 2 para las actividades formativas y sumativas del curso MCDI501.

## Integrantes

* Enzo Pinilla
* Claudio Alarcón
* Luis Rodrigo Espinoza

## Docente

Dr. Jean Paul Maidana González

## Avance actual

### Evaluación Formativa 1: EDA e inferencia

* Análisis exploratorio e inferencial: [`notebooks/F1_Definicion.ipynb`](notebooks/F1_Definicion.ipynb).
* Informe fuente: [`formativa-1-eda-inferencia/formativa-1-eda-inferencia.tex`](formativa-1-eda-inferencia/formativa-1-eda-inferencia.tex).
* Informe compilado: [`formativa-1-eda-inferencia/formativa-1-eda-inferencia.pdf`](formativa-1-eda-inferencia/formativa-1-eda-inferencia.pdf).
* Datos originales: `data/raw/weatherAUS.csv`.
* Datos procesados: `data/processed/weatherAUS.csv`.
* Figuras generadas localmente: `results/figures/`.

### Evaluación Sumativa 1: análisis exploratorio e inferencial

* Análisis reproducible: [`notebooks/S1_Definicion.ipynb`](notebooks/S1_Definicion.ipynb).
* Informe fuente: [`sumativa-1-analisis-exploratorio-inferencial/sumativa-1-analisis-exploratorio-inferencial.tex`](sumativa-1-analisis-exploratorio-inferencial/sumativa-1-analisis-exploratorio-inferencial.tex).
* Informe compilado: [`sumativa-1-analisis-exploratorio-inferencial/sumativa-1-analisis-exploratorio-inferencial.pdf`](sumativa-1-analisis-exploratorio-inferencial/sumativa-1-analisis-exploratorio-inferencial.pdf).
* Figuras del análisis: `results/figures/fig01_*.png` a `results/figures/fig05_*.png`.

### Evaluación Sumativa 2: validación, simulación y remuestreo

* Validación reproducible: [`notebooks/S2_Validacion.ipynb`](notebooks/S2_Validacion.ipynb).
* Informe fuente: [`sumativa-2-validacion-simulacion-remuestreo/sumativa-2-validacion-simulacion-remuestreo.tex`](sumativa-2-validacion-simulacion-remuestreo/sumativa-2-validacion-simulacion-remuestreo.tex).
* Informe compilado: [`sumativa-2-validacion-simulacion-remuestreo/sumativa-2-validacion-simulacion-remuestreo.pdf`](sumativa-2-validacion-simulacion-remuestreo/sumativa-2-validacion-simulacion-remuestreo.pdf).
* Figuras del análisis: `results/figures/fig_s2_*.png`.
* Reportes generados: `results/reports/`.

La Sumativa 2 valida y profundiza los resultados obtenidos en la Sumativa 1 mediante técnicas de simulación y remuestreo. En particular, incorpora:

* Bootstrap no paramétrico con 10.000 remuestras.
* Intervalos de confianza por método percentil y BCa.
* Comparación con intervalos clásicos obtenidos en S1.
* Test de permutación con 10.000 permutaciones.
* Evaluación de estabilidad de correlaciones mediante bootstrap.
* Simulación Monte Carlo basada en parámetros estimados en S1.
* Análisis de robustez frente a outliers y supuestos estadísticos.
* Síntesis de resultados validados para la preparación de S3.

Además, esta evaluación incorpora explícitamente el feedback recibido en S1:

* Revisión de la colinealidad entre `MaxTemp` y `Temp3pm`.
* Consideración de faltantes relevantes en `Sunshine` y `Evaporation`.
* Análisis del desbalance de la variable objetivo `RainTomorrow`.
* Validación bootstrap de variables con colas pesadas como `Rainfall` y `WindGustSpeed`.
* Tratamiento cuidadoso de `Rainfall` mediante `log1p`, winsorización y análisis de robustez.
* Recomendaciones para S3 sobre imputación, métricas sensibles a clase minoritaria y partición temporal o por `Location`.

### Evaluación Formativa 2: modelamiento predictivo

* Modelamiento reproducible: [`notebooks/F2_Modelamiento_Predictivo.ipynb`](notebooks/F2_Modelamiento_Predictivo.ipynb).
* Informe fuente: [`formativa-2-modelamiento-predictivo/F2_Modelamiento_Predictivo_WeatherAUS.tex`](formativa-2-modelamiento-predictivo/F2_Modelamiento_Predictivo_WeatherAUS.tex).
* Informe compilado: [`formativa-2-modelamiento-predictivo/F2_Modelamiento_Predictivo_WeatherAUS.pdf`](formativa-2-modelamiento-predictivo/F2_Modelamiento_Predictivo_WeatherAUS.pdf).
* Figuras del modelamiento: `results/figures_f2/`.

La Formativa 2 integra los resultados de S1 y S2 en una primera línea base de clasificación para predecir `RainTomorrow`. Incluye preparación de datos, imputación sin fuga de información, transformación `log1p` de `Rainfall`, regresión logística, odds ratios, diagnóstico VIF, matriz de confusión, métricas de clasificación y curva ROC-AUC.

## Estructura

* `data/raw/`: datasets originales.
* `data/processed/`: datasets procesados.
* `notebooks/`: análisis exploratorio, inferencial, validación, simulación y modelamiento.
* `src/`: funciones reutilizables.
* `results/figures/`: figuras generadas por los notebooks.
* `results/figures_f2/`: figuras generadas por el notebook de Formativa 2.
* `results/reports/`: reportes generados.
* `docs/`: documentación adicional.
* `formativa-*` y `sumativa-*`: fuentes y entregables de cada evaluación.

## Orden de ejecución

### 1. Preparar el entorno de Python

```bash
# macOS y Linux
python3 -m venv .venv

# Windows
py -m venv .venv
```

Activar el entorno virtual:

```bash
# macOS y Linux
source .venv/bin/activate

# Windows (PowerShell)
.\.venv\Scripts\Activate.ps1
```

Instalar las dependencias:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 2. Ejecutar los notebooks

Iniciar JupyterLab desde la raíz del repositorio:

```bash
python -m jupyter lab
```

Abrir el notebook correspondiente y seleccionar **Kernel → Restart Kernel and Run All Cells**:

* Formativa 1: `notebooks/F1_Definicion.ipynb`.
* Sumativa 1: `notebooks/S1_Definicion.ipynb`.
* Sumativa 2: `notebooks/S2_Validacion.ipynb`.
* Formativa 2: `notebooks/F2_Modelamiento_Predictivo.ipynb`.

Al finalizar se generan:

* Los datos procesados en `data/processed/weatherAUS.csv`.
* Las figuras utilizadas por LaTeX en `results/figures/`.
* Las figuras de Formativa 2 en `results/figures_f2/`.
* Los reportes y tablas auxiliares en `results/reports/`.

### 3. Compilar los informes LaTeX

Se requiere una distribución LaTeX:

* **macOS:** [MacTeX](https://www.tug.org/mactex/).
* **Windows:** [MiKTeX](https://miktex.org/download) o [TeX Live](https://www.tug.org/texlive/).
* **Linux (Ubuntu/Debian):** `sudo apt install texlive-latex-extra latexmk`.

Una vez instalada y después de ejecutar el notebook correspondiente, compilar desde la raíz del repositorio.

Formativa 1:

```bash
cd formativa-1-eda-inferencia
pdflatex formativa-1-eda-inferencia.tex
pdflatex formativa-1-eda-inferencia.tex
```

Sumativa 1:

```bash
cd sumativa-1-analisis-exploratorio-inferencial
pdflatex sumativa-1-analisis-exploratorio-inferencial.tex
pdflatex sumativa-1-analisis-exploratorio-inferencial.tex
```

Sumativa 2:

```bash
cd sumativa-2-validacion-simulacion-remuestreo
pdflatex sumativa-2-validacion-simulacion-remuestreo.tex
pdflatex sumativa-2-validacion-simulacion-remuestreo.tex
```

Formativa 2:

```bash
cd formativa-2-modelamiento-predictivo
pdflatex F2_Modelamiento_Predictivo_WeatherAUS.tex
pdflatex F2_Modelamiento_Predictivo_WeatherAUS.tex
```

La primera compilación genera los archivos auxiliares; la segunda actualiza el índice y las referencias internas. LaTeX incorpora las figuras existentes en `results/figures/`, `results/figures_s2/` o `results/figures_f2/`, pero no las genera.

### 4. Abrir el PDF generado

Usar el nombre del PDF correspondiente.

Formativa 1:

```bash
# macOS
open formativa-1-eda-inferencia.pdf

# Linux
xdg-open formativa-1-eda-inferencia.pdf

# Windows (PowerShell)
Start-Process formativa-1-eda-inferencia.pdf
```

Sumativa 1:

```bash
# macOS
open sumativa-1-analisis-exploratorio-inferencial.pdf

# Linux
xdg-open sumativa-1-analisis-exploratorio-inferencial.pdf

# Windows (PowerShell)
Start-Process sumativa-1-analisis-exploratorio-inferencial.pdf
```

Sumativa 2:

```bash
# macOS
open sumativa-2-validacion-simulacion-remuestreo.pdf

# Linux
xdg-open sumativa-2-validacion-simulacion-remuestreo.pdf

# Windows (PowerShell)
Start-Process sumativa-2-validacion-simulacion-remuestreo.pdf
```

Formativa 2:

```bash
# macOS
open F2_Modelamiento_Predictivo_WeatherAUS.pdf

# Linux
xdg-open F2_Modelamiento_Predictivo_WeatherAUS.pdf

# Windows (PowerShell)
Start-Process F2_Modelamiento_Predictivo_WeatherAUS.pdf
```

## Notas de reproducibilidad

* Ejecutar siempre los notebooks desde la raíz del repositorio.
* Verificar que exista el archivo `data/raw/weatherAUS.csv`.
* Ejecutar `Kernel → Restart Kernel and Run All Cells` antes de compilar los informes.
* No editar manualmente las figuras generadas por los notebooks.
* Mantener las salidas de `results/figures/`, `results/figures_s2/`, `results/figures_f2/` y `results/reports/` sincronizadas con la versión final del notebook.
* La Sumativa 2 depende explícitamente de los resultados de la Sumativa 1, por lo que debe ejecutarse después de S1.
* La Formativa 2 depende de los hallazgos de S1 y S2, por lo que conviene ejecutarla después de ambas evaluaciones.
