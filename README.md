# Tecnologías de la Explotación de la Información (T.E.I.)

Implementación computacional y metodológica de modelos de Explotación de la Información, Minería de Datos, Aprendizaje Automático y Descubrimiento de Conocimiento (KDD) mediante notebooks de Jupyter. Cada notebook desarrolla la formulación matemática rigurosa, el diseño algorítmico de la resolución, la verificación numérica y computacional mediante Python, y la representación gráfica de las métricas de evaluación, estructuras jerárquicas, topologías de red y reglas de comportamiento descubiertas.

## Contenido por notebook

| Notebook | Contenido |
| :--- | :--- |
| `01-tdidt.ipynb` | Inducción de árboles de decisión (TDIDT): algoritmos ID3 y C4.5, medidas de información (entropía de Shannon, ganancia y ratio de ganancia) y extracción de reglas |
| `02-redes-bayesianas.ipynb` | Redes bayesianas discretas: formulación en grafos dirigidos acíclicos (DAG), estimación paramétrica de probabilidades condicionales (CPTs) e inferencia exacta por enumeración |
| `03-som.ipynb` | Mapas autoorganizados de Kohonen (SOM): aprendizaje no supervisado, cuantización vectorial, preservación topológica, U-Matrix y mapas de activación |
| `04-descubrimiento-reglas.ipynb` | Flujo integral de descubrimiento de conocimiento (KDD): agrupamiento no supervisado con SOM, inducción de reglas de pertenencia con TDIDT y ponderación probabilística con redes bayesianas |
| `05-mineria-web.ipynb` | Minería Web (*Web Mining*): minería de contenido textual con TF-IDF, similitud coseno y agrupamiento K-Means, y minería de estructura de enlaces mediante PageRank y HITS |

## Tabla de contenidos detallada

Cada fila indica el tema central del notebook y los subtemas tratados en su marco teórico, formulación analítica e implementación práctica.

| Notebook | Tema | Subtemas |
| :--- | :--- | :--- |
| `01-tdidt.ipynb` | Inducción de árboles de decisión (TDIDT) | Entropía de Shannon e impureza de nodos; ganancia de información; información de partición (*Split Info*) y razón de ganancia (*Gain Ratio*); algoritmo ID3 recursivo; extensiones de C4.5 para sesgo de atributos multievaluados; supuestos y sesgo inductivo; complejidad computacional; extracción y formalización de reglas de decisión Si-Entonces; evaluación de exactitud y matriz de confusión sobre el conjunto meteorológico de tenis (`dataset_tenis.csv`) |
| `02-redes-bayesianas.ipynb` | Modelos gráficos probabilísticos | Grafos dirigidos acíclicos (DAG) e independencia condicional; factorización de la distribución de probabilidad conjunta; regla de la cadena y regla del producto; teorema de Bayes y actualización de creencias; aprendizaje paramétrico mediante estimación por máxima verosimilitud (MLE) de CPTs; inferencia exacta por enumeración; análisis del impacto de evidencia observada; validación del modelo frente a frecuencias empíricas sobre el conjunto climático (`weather.csv`) |
| `03-som.ipynb` | Redes neuronales autoorganizadas (SOM) | Arquitectura de retículo bidimensional; vector de pesos y distancia euclídea; neurona ganadora o BMU (*Best Matching Unit*); funciones de vecindad gaussiana y decaimiento temporal ($\sigma$ y $\eta$); regla de adaptación de pesos de Kohonen; normalización Min-Max; métricas de evaluación: error de cuantización (QE) y error topológico (TE); sensibilidad al suelo de vecindad (*floor*); visualizaciones: U-Matrix, matrices de hits y proyección PCA sobre conjuntos multiclase (`breast.txt` y `cars.xls`) |
| `04-descubrimiento-reglas.ipynb` | Descubrimiento de conocimiento (KDD) | Integración metodológica no supervisada, supervisada y probabilística; saneamiento y tipificación de datos sociolaborales (`AdultosyJovenesDatosTrab.xls`); partición latente del hiperespacio con MiniSom (grilla 2×3); caracterización sociodemográfica de clústeres; entrenamiento de árbol TDIDT con codificación ordinal entera; extracción exhaustiva de reglas Si-Entonces legibles con conteo de soporte real y pureza; modelado gráfico bayesiano con regularización Dirichlet/BDeu mediante `pgmpy`; inferencia por eliminación de variables; cálculo de probabilidades a priori y posteriores de pertenencia a grupos; ganancia evidencial |
| `05-mineria-web.ipynb` | Minería de Contenido y Estructura Web | Taxonomía de minería web; extracción del árbol DOM mediante *BeautifulSoup*; persistencia determinística del corpus (`web_mining_corpus.json`); cálculo de riqueza léxica (TTR); vectorización TF-IDF con n-gramas; matriz de similitud coseno; agrupamiento semántico no supervisado K-Means; proyección 2D por PCA; modelado del grafo dirigido $G=(V, E)$; formulación analítica de PageRank (iteración de potencias con amortiguamiento $d=0.85$); algoritmo HITS (autoridades y concentradores); contraste cuantitativo y representación topológica del grafo web |

## Requisitos previos

Python 3.14 o superior, disponible en el PATH del sistema. Un intérprete de comandos. Las instrucciones siguientes se indican para PowerShell; en sistemas POSIX los nombres de los ejecutables carecen del sufijo `.ps1` y las rutas emplean `/` como separador.

## Configuración del entorno virtual

El proyecto se aísla en un entorno virtual propio de modo que las dependencias no se propagan al intérprete del sistema. Desde la raíz del repositorio:

```powershell
# 1. Crear el entorno virtual en .venv
python -m venv .venv

# 2. Activar el entorno
.\.venv\Scripts\Activate.ps1

# 3. Actualizar el gestor de paquetes
python -m pip install --upgrade pip
```

Si el intérprete bloquea la ejecución de scripts en Windows, se levanta la restricción para la sesión en curso antes de activar el entorno:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

## Instalación de dependencias

Con el entorno activo, las dependencias declaradas en `requirements.txt` se instalan con:

```powershell
python -m pip install -r requirements.txt
```

El manifiesto fija las versiones con las que se verificó la ejecución completa de los cinco notebooks:

| Grupo | Paquetes |
| :--- | :--- |
| Bibliotecas de computación científica, aprendizaje automático y minería de datos | `numpy 2.5.4`, `scipy 1.18.1`, `pandas 3.1.0`, `scikit-learn 1.9.1`, `minisom 2.3.6`, `pgmpy 1.1.2`, `networkx 3.7`, `python-calamine 0.9.0` |
| Minería web y recolección automatizada | `requests 2.34.2`, `beautifulsoup4 4.15.0` |
| Bibliotecas de visualización | `matplotlib 3.11.2`, `seaborn 0.13.2` |
| Ejecución de notebooks | `ipykernel 7.4.0`, `jupyterlab 4.6.5`, `nbconvert 7.17.2` |

La correspondencia entre notebook y dependencias es la siguiente:

| Notebook | Dependencias |
| :--- | :--- |
| `01-tdidt.ipynb` | `pandas`, `matplotlib` |
| `02-redes-bayesianas.ipynb` | `numpy`, `pandas`, `matplotlib`, `networkx` |
| `03-som.ipynb` | `numpy`, `pandas`, `matplotlib`, `python-calamine` |
| `04-descubrimiento-reglas.ipynb` | `numpy`, `pandas`, `matplotlib`, `seaborn`, `networkx`, `scikit-learn`, `minisom`, `pgmpy`, `python-calamine` |
| `05-mineria-web.ipynb` | `requests`, `beautifulsoup4`, `numpy`, `pandas`, `matplotlib`, `seaborn`, `networkx`, `scikit-learn` |

Los módulos estándar como `math`, `collections`, `itertools`, `re`, `unicodedata` y `warnings` se distribuyen directamente con el intérprete de Python y no requieren instalación independiente. El motor `python-calamine` se utiliza para la lectura eficiente de archivos de hoja de cálculo en formato Excel (`.xls`), evitando dependencias heredadas incompatibles.

Para regenerar el entorno desde cero en otra máquina, basta con repetir los pasos anteriores: la creación del entorno virtual y la instalación del manifiesto reproducen fielmente el estado verificado.

## Ejecución de los notebooks

### Interfaz interactiva

```powershell
python -m jupyter lab
```

El servidor abre el árbol de directorios en el navegador. Se selecciona el kernel Python 3 (asociado al entorno virtual) y se ejecutan las celdas en orden mediante *Run All*. Los notebooks están entregados con las salidas ya almacenadas, de modo que las tablas, métricas y figuras son visibles sin necesidad de reejecutarlos.

### Ejecución por lotes

Para reejecutar un notebook de punta a punta y escribir las salidas en el propio archivo, sin pasar por la interfaz gráfica:

```powershell
python -m jupyter nbconvert --to notebook --execute --inplace 01-tdidt.ipynb
python -m jupyter nbconvert --to notebook --execute --inplace 02-redes-bayesianas.ipynb
python -m jupyter nbconvert --to notebook --execute --inplace 03-som.ipynb
python -m jupyter nbconvert --to notebook --execute --inplace 04-descubrimiento-reglas.ipynb
python -m jupyter nbconvert --to notebook --execute --inplace 05-mineria-web.ipynb
```

El tiempo límite de ejecución por celda se controla con el parámetro `--ExecutePreprocessor.timeout`, expresado en segundos.

### Verificación del kernel

Para comprobar que Jupyter apunta al entorno correcto:

```powershell
python -m jupyter kernelspec list
```

Si el entorno virtual no figura entre los kernels disponibles, se registra con:

```powershell
python -m ipykernel install --user --name python3 --display-name "Python 3"
```

## Estructura del repositorio

```
.
├── 01-tdidt.ipynb                  # Inducción de árboles de decisión (ID3 y C4.5)
├── 02-redes-bayesianas.ipynb        # Modelado e inferencia exacta en redes bayesianas
├── 03-som.ipynb                    # Mapas autoorganizados de Kohonen (SOM)
├── 04-descubrimiento-reglas.ipynb  # Flujo integral de descubrimiento de reglas (SOM + TDIDT + Bayes)
├── 05-mineria-web.ipynb            # Minería de contenido (TF-IDF) y estructura web (PageRank y HITS)
├── data/                           # Conjuntos de datos de entrenamiento y evaluación
│   ├── AdultosyJovenesDatosTrab.xls # Datos sociolaborales para descubrimiento de reglas
│   ├── breast.txt                  # Registros clínicos para agrupamiento con SOM
│   ├── cars.xls                    # Especificaciones automotrices multiclase
│   ├── dataset_tenis.csv           # Atributos meteorológicos para clasificación TDIDT
│   ├── Parcial_Damian_Piazza.tdm   # Esquema de minería de datos y metadatos
│   ├── weather.csv                 # Red bayesiana discreta del dominio climático
│   └── web_mining_corpus.json      # Corpus web estructurado de Wikipedia (10 artículos y red de enlaces)
├── requirements.txt                # Dependencias fijadas del entorno
├── .gitignore                      # Reglas de exclusión de versionamiento
└── README.md                       # Este documento
```

## Notas sobre reproducibilidad

- **Aritmética y precisión**: Todos los cálculos de medidas de información (entropía, ganancia), similitud coseno y vectores de probabilidad estacionaria de PageRank se computan bajo aritmética de doble precisión IEEE 754.
- **Determinismo estocástico**: Los algoritmos con componentes estocásticas (inicialización de retículos SOM, partición K-Means, proyecciones de grafos) fijan de manera explícita la semilla pseudoaleatoria (`SEMILLA = 42`), garantizando reproducibilidad determinística.
- **Respaldo local y conectividad**: En `05-mineria-web.ipynb`, la rutina de web scraping cuenta con un respaldo serializado (`data/web_mining_corpus.json`), permitiendo la reejecución completa y sin fallas incluso en ausencia de conexión a Internet.
- **Generación autónoma**: Todas las tablas analíticas, dendrogramas/árboles y figuras gráficas se generan íntegramente a partir de celdas de código ejecutables sin depender de artefactos binarios externos.
- **Persistencia de versiones**: Las dependencias del entorno se encuentran fijadas en `requirements.txt`. El uso de estas versiones previene divergencias en cálculos numéricos o interfaces de librerías especializadas (como `pgmpy`, `scikit-learn` o `networkx`).
