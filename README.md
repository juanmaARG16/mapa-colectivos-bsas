🗺️ Mapa Interactivo de Transporte Público — Ciudad de Buenos Aires

📋 Descripción del proyecto
Este proyecto visualiza la red completa de transporte público de colectivos de la Ciudad Autónoma de Buenos Aires (CABA) en un mapa web interactivo. Permite explorar recorridos y paradas de todas las líneas, filtrar por número de línea mediante checkboxes, y consultar información detallada de cada tramo y parada mediante popups. El mapa fue generado a partir de datos geoespaciales oficiales en formato Shapefile, procesados con Python y publicado como página estática en GitHub Pages.

🗃️ Fuente de datos
DatasetNombre oficialURLFecha de descargaRecorridosRecorridos de Colectivos — CABAdata.buenosaires.gob.arMayo 2025ParadasParadas de Colectivos — CABAdata.buenosaires.gob.arMayo 2025
Proveedor: Gobierno de la Ciudad Autónoma de Buenos Aires
Licencia: Datos Abiertos — uso libre con atribución
Formato original: Shapefile (.shp, .dbf, .shx, .prj)
Sistema de coordenadas original: POSGAR / WGS84 → reproyectado a EPSG:4326

🛠️ Tecnologías utilizadas
TecnologíaRol en el proyectoPython 3.xLenguaje principal de procesamientoGeoPandasLectura, reproyección y manipulación de archivos ShapefileFoliumGeneración del mapa HTML a partir de datos geoespacialesLeaflet.jsMotor de renderizado del mapa interactivo en el navegador (incluido por Folium)JavaScript (vanilla)Lógica del panel de checkboxes, filtrado dinámico y zoom automáticoOpenStreetMapCapa base del mapa (tiles gratuitos)HTML / CSSEstructura y estilos del panel lateral, leyenda y popupsGitHub PagesHosting estático gratuito para la publicación de la URL públicaJupyter NotebookEntorno de desarrollo y documentación del proceso

🔍 Observaciones analíticas
1. 📍 Saturación de recorridos en el corredor central Norte–Sur
Al visualizar todas las líneas simultáneamente, se observa una marcada concentración de trazados sobre el eje que une el Microcentro con los barrios de Palermo, Belgrano y Núñez. Avenidas como Santa Fe, Corrientes, Callao y Pueyrredón concentran una superposición de 15 o más líneas distintas operando en el mismo tramo, lo que sugiere redundancia de oferta en ese corredor mientras otras zonas quedan subatendidas. Esta concentración es especialmente visible al activar el filtro de líneas nacionales versus líneas jurisdicción CABA.
2. 🏘️ Brecha de cobertura en las comunas del sur (8 y 9)
Las comunas 8 (Villa Soldati, Villa Lugano, Villa Riachuelo) y 9 (Liniers, Mataderos, Parque Avellaneda) muestran una densidad de paradas notablemente inferior al promedio de la ciudad. Al filtrar las líneas que sirven esas zonas, se comprueba que los recorridos son de mayor longitud, menor frecuencia de paradas intermedias y menor variedad de opciones de transbordo. Esto evidencia una brecha de accesibilidad estructural en el sur de CABA que contrasta con la saturación de servicios en el corredor central.
3. 🔄 Asimetría geométrica entre recorridos de ida y vuelta
Al filtrar una misma línea y alternar entre sentido ida (rojo) y vuelta (azul), se observa que los trazados frecuentemente no son simétricos: utilizan calles distintas en cada sentido para adaptarse al sentido único del tránsito urbano. En algunos casos la diferencia supera los 400 metros de desvío entre ambos sentidos en un mismo tramo, lo que implica que una parada puede tener servicio en un sentido pero no en el opuesto en un radio caminable. Este fenómeno es especialmente pronunciado en la zona de Microcentro y en los accesos a las terminales de cabecera.

▶️ Instrucciones para correr el proyecto localmente
Requisitos previos

Python 3.8 o superior instalado
Git instalado
Google Chrome instalado (para captura automática de pantalla)
Cuenta de GitHub con token de acceso personal

Paso 1 — Clonar el repositorio
bashgit clone https://github.com/TU_USUARIO/mapa-transporte-bsas.git
cd mapa-transporte-bsas
Paso 2 — Instalar dependencias
bashpip install geopandas folium fiona pyproj shapely selenium pillow webdriver-manager
O usando el archivo de requerimientos:
bashpip install -r requirements.txt
Paso 3 — Verificar los datos
Asegurate de que los archivos Shapefile estén en la carpeta /data:
data/
├── recorrido-colectivo-zip.shp
├── recorrido-colectivo-zip.dbf
├── recorrido-colectivo-zip.shx
├── recorrido-colectivo-zip.prj
├── Paradas_Colectivos.shp
├── Paradas_Colectivos.dbf
├── Paradas_Colectivos.shx
└── Paradas_Colectivos.prj
Si no los tenés, descargalos desde:

Recorridos
Paradas

Paso 4 — Ejecutar el notebook
bashjupyter notebook src/generar_mapa.ipynb
Ejecutá las celdas en orden de arriba hacia abajo. El proceso completo tarda entre 2 y 5 minutos dependiendo del hardware.
Paso 5 — Abrir el mapa localmente
Al finalizar la ejecución, el archivo index.html se genera en la raíz del proyecto. Abrilo directamente en el navegador:
bash# En Windows
start index.html

# En Mac
open index.html

# En Linux
xdg-open index.html
Paso 6 — Publicar en GitHub Pages (opcional)

Subí el repositorio a GitHub
Ir a Settings → Pages
En Branch seleccionar main y carpeta / (root)
Guardar — la URL pública estará disponible en 1–3 minutos


📁 Estructura del repositorio
mapa-transporte-bsas/
│
├── index.html              # Mapa interactivo (abrí esto en el navegador)
├── README.md               # Este archivo
├── requirements.txt        # Dependencias Python
│
├── data/                   # Archivos fuente Shapefile (no modificar)
│   ├── recorrido-colectivo-zip.shp
│   ├── Paradas_Colectivos.shp
│   └── ...
│
├── src/                    # Código fuente
│   └── generar_mapa.ipynb  # Notebook con todo el proceso
│
└── assets/                 # Recursos estáticos
    └── mapa_preview.png    # Captura de pantalla del mapa

📄 Licencia
Datos: © Gobierno de la Ciudad Autónoma de Buenos Aires — Licencia de Datos Abiertos.
Código: MIT License — libre uso, modificación y distribución con atribución.

Proyecto desarrollado como parte de la Misión 1 — Análisis de Transporte Urbano CABA


