# BERTopic en español: Don Quijote

El proyecto está completo en **[analisis_quijote.ipynb](analisis_quijote.ipynb)**: corpus, segmentación, embeddings, dos configuraciones, nombres, ejemplos y análisis de las gráficas.

Se analiza la primera parte de *Don Quijote de la Mancha* (1605), de [Project Gutenberg](https://www.gutenberg.org/ebooks/2000). Es un texto distinto de las reseñas de Letterboxd del [repositorio de referencia](https://github.com/ErikJajan/BERTopic).

## Cómo ejecutarlo

Usa Python 3.12 y ejecuta desde esta carpeta:

```bash
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

En Windows, activa el entorno con `.venv\Scripts\activate`.
Abre el notebook en VS Code, selecciona el intérprete de `.venv` y pulsa **Ejecutar todo**.
La primera ejecución requiere Internet para descargar el modelo; después reutiliza los pesos locales.
Los embeddings se recalculan al ejecutar el notebook.

## Archivos

```text
analisis_quijote.ipynb   Todo el código y el análisis
requirements.txt        Dependencias
README.md               Estas instrucciones
data/                   Texto original y stopwords españolas
results/                Tablas, ejemplos, figuras e informe
```

No hay carpeta de tests ni scripts auxiliares. El notebook solo conserva comprobaciones básicas del número de segmentos y del límite de tokens.

## Resultados incluidos

Se procesan 52 capítulos, con un párrafo por documento y división de los párrafos que exceden 512 tokens. Se quitan textos de menos de cinco palabras y duplicados: quedan **2,046 segmentos**, con una media de **88.57 palabras**.

| Configuración | Tópicos | Outliers |
|---|---:|---:|
| A | 16 | 18.43% |
| B | 9 | 25.51% |

El encoder es `intfloat/multilingual-e5-small`, con soporte de español. Ambas configuraciones comparten embeddings y fijan `random_state=42` en UMAP. Los outliers se conservan como −1.

El [informe](results/informe.md) resume la ejecución incluida. Los catálogos [A](results/catalogo_A.md) y [B](results/catalogo_B.md) contienen tres ejemplos por tópico. El notebook regenera tablas, catálogos y figuras; si modificas el corpus o los parámetros, revisa también los nombres y las conclusiones del notebook y del informe.

Los nombres y las interpretaciones se elaboraron con asistencia de IA a partir de resultados reales. No representan una validación independiente por especialistas en literatura. La reproducción exacta depende también de la plataforma y las versiones.
