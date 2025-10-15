# Books Eater - Audiolibros Dominicanos

Herramienta especializada para buscar y catalogar audiolibros de literatura dominicana disponibles en YouTube.

## ¿Qué es Books Eater?

Books Eater es una aplicación de Python que busca audiolibros de autores dominicanos en YouTube, recopila información sobre cada video encontrado y genera un dataset completo en formato Excel.

## Características

 - **Búsqueda automática** de audiolibros en YouTube
 - **Catálogo de literatura dominicana** con autores clásicos
 - **Metadata de videos**: duración, URL, tipo de contenido
 - **Exportación a Excel/CSV** con estadísticas completas
 - **Dataset predefinido** de libros dominicanos importantes
 - **Scraping sin API key** - sin límites de búsqueda

## Estructura del Proyecto

```
books-eater/
├── src/
│   ├── clients/
│   │   └── youtube_client.py      # Cliente para buscar en YouTube
│   ├── models/
│   │   └── book.py                # Modelo de datos del libro
│   ├── services/
│   │   └── audiobook_service.py   # Lógica de procesamiento
│   └── utils/
│       ├── config.py              # Configuración
│       ├── file_handler.py        # Manejo de archivos
│       └── dominican_books.py     # Dataset de libros dominicanos
├── main.py                        # Punto de entrada
├── books_list.txt                 # Lista de libros a buscar (opcional)
├── requirements.txt               # Dependencias
└── README.md                      # Este archivo
```

## Instalación

1. **Clonar/crear el directorio**
   ```bash
   cd workspace
   cd books-eater
   ```

2. **Instalar dependencias**
   ```bash
   pip install -r requirements.txt
   ```

## Uso

### Ejecución básica
```bash
python main.py
```

### Opciones de búsqueda

El programa incluye un dataset predefinido de literatura dominicana organizado por autor:

- **Juan Bosch**: La Mañosa, El Oro y la Paz, Camino Real, etc.
- **Pedro Mir**: Hay un País en el Mundo, Contracanto a Walt Whitman, etc.
- **Salomé Ureña**: Poesías Completas, A la Educación, etc.
- **Manuel de Jesús Galván**: Enriquillo
- **Y muchos más autores dominicanos...**

### Resultado

El programa genera un archivo `dominican_audiobooks.xlsx` con:

| Columna | Descripción |
|---------|-------------|
| **Número** | ID secuencial |
| **Título Libro** | Título completo de la obra |
| **Autor** | Autor dominicano |
| **Año** | Año de publicación original |
| **URL YouTube** | Enlace directo al video |
| **Duración** | Duración del video |
| **Tipo Contenido** | Clasificación del contenido |
| **Disponibilidad** | ENCONTRADO/PARCIAL/NO ENCONTRADO |

### Archivo books_list.txt (Opcional)

Puedes crear tu propia lista de búsqueda:

```txt
# Formato: Título | Autor | Año
La Mañosa | Juan Bosch | 1936
Enriquillo | Manuel de Jesús Galván | 1882
Hay un País en el Mundo | Pedro Mir | 1949
```

## Tipos de Contenido Detectados

- **Lectura Completa**: Audiobook completo profesional
- **Dramatización**: Adaptación teatral o dramatizada
- **Narración Profesional**: Narrado por profesionales
- **Lectura Amateur**: Personas leyendo el libro
- **Fragmentos**: Solo partes del libro
- **Análisis/Reseña**: Videos sobre el libro (no lectura)

## Estadísticas

Al finalizar, el programa muestra:

```
Resultados de la búsqueda:
   Total procesado: 50
   Encontrados: 32 (64%)
   Parciales: 10 (20%)
   No encontrados: 8 (16%)
```

## Configuración

Modifica `src/utils/config.py` para ajustar:

```python
SEARCH_TIMEOUT = 30          # Timeout de búsqueda
VIDEOS_PER_SEARCH = 3        # Videos a analizar por búsqueda
OUTPUT_FILE = "dominican_audiobooks.xlsx"
```

## Dependencias

- `scrapetube`: Búsqueda en YouTube sin API
- `pandas`: Procesamiento de datos
- `openpyxl`: Exportación a Excel
- `python-dotenv`: Variables de entorno (opcional)

## Autores Dominicanos Incluidos

- Juan Bosch (1909-2001)
- Pedro Mir (1913-2000)
- Salomé Ureña (1850-1897)
- Manuel de Jesús Galván (1834-1910)
- Manuel del Cabral (1907-1999)
- Aida Cartagena Portalatín (1918-1994)
- Hilma Contreras (1907-1996)
- Marcio Veloz Maggiolo (1936-)
- Y muchos más...

## Notas Importantes

Este proyecto es para uso educativo y de investigación. Verifica siempre los derechos de autor de los contenidos encontrados.

## Licencia

Proyecto educativo - Uso académico
