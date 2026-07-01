# MCDI501 - Estadística Computacional para la Toma de Decisiones

Repositorio del Grupo 2 para las actividades formativas y sumativas del curso MCDI501.

## Integrantes

- Enzo Pinilla
- Claudio Alarcón
- Luis Rodrigo Espinoza

## Docente

Dr. Jean Paul Maidana González

## Avance actual

### Evaluación Formativa 1: EDA e inferencia

- Análisis exploratorio e inferencial: [`notebooks/F1_Definicion.ipynb`](notebooks/F1_Definicion.ipynb).
- Informe fuente: [`formativa-1-eda-inferencia/formativa-1-eda-inferencia.tex`](formativa-1-eda-inferencia/formativa-1-eda-inferencia.tex).
- Informe compilado: [`formativa-1-eda-inferencia/formativa-1-eda-inferencia.pdf`](formativa-1-eda-inferencia/formativa-1-eda-inferencia.pdf).
- Datos originales: `data/raw/weatherAUS.csv`.
- Datos procesados: `data/processed/weatherAUS.csv`.
- Figuras generadas localmente: `results/figures/`.

### Evaluación Sumativa 1: análisis exploratorio e inferencial

- Análisis reproducible: [`notebooks/S1_Definicion.ipynb`](notebooks/S1_Definicion.ipynb).
- Informe fuente: [`sumativa-1-analisis-exploratorio-inferencial/sumativa-1-analisis-exploratorio-inferencial.tex`](sumativa-1-analisis-exploratorio-inferencial/sumativa-1-analisis-exploratorio-inferencial.tex).
- Informe compilado: [`sumativa-1-analisis-exploratorio-inferencial/sumativa-1-analisis-exploratorio-inferencial.pdf`](sumativa-1-analisis-exploratorio-inferencial/sumativa-1-analisis-exploratorio-inferencial.pdf).
- Figuras del análisis: `results/figures/fig01_*.png` a `results/figures/fig05_*.png`.

## Estructura

- `data/raw/`: datasets originales.
- `data/processed/`: datasets procesados.
- `notebooks/`: análisis exploratorio, inferencial y modelamiento.
- `src/`: funciones reutilizables.
- `results/figures/`: figuras generadas por los notebooks.
- `results/reports/`: reportes generados.
- `docs/`: documentación adicional.
- `formativa-*` y `sumativa-*`: fuentes y entregables de cada evaluación.

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

### 2. Ejecutar el notebook

Iniciar JupyterLab desde la raíz del repositorio:

```bash
python -m jupyter lab
```

Abrir el notebook correspondiente y seleccionar **Kernel → Restart Kernel and Run All Cells**:

- Formativa 1: `notebooks/F1_Definicion.ipynb`.
- Sumativa 1: `notebooks/S1_Definicion.ipynb`.

Al finalizar se generan:

- Los datos procesados en `data/processed/weatherAUS.csv`.
- Las figuras utilizadas por LaTeX en `results/figures/`.

### 3. Compilar el informe LaTeX

Se requiere una distribución LaTeX:

- **macOS:** [MacTeX](https://www.tug.org/mactex/).
- **Windows:** [MiKTeX](https://miktex.org/download) o [TeX Live](https://www.tug.org/texlive/).
- **Linux (Ubuntu/Debian):** `sudo apt install texlive-latex-extra latexmk`.

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

La primera compilación genera los archivos auxiliares; la segunda actualiza el índice y las referencias internas. LaTeX incorpora las figuras existentes en `results/figures/`, pero no las genera.

### 4. Abrir el PDF generado

Usar el nombre del PDF correspondiente. Por ejemplo, para la Sumativa 1:

```bash
# macOS
open sumativa-1-analisis-exploratorio-inferencial.pdf

# Linux
xdg-open sumativa-1-analisis-exploratorio-inferencial.pdf

# Windows (PowerShell)
Start-Process sumativa-1-analisis-exploratorio-inferencial.pdf
```
