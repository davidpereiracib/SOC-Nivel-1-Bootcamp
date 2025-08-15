Fuentes de Datos: Windows - Registros de Ejecución:

| Artefacto Forense        | Descripción Breve                                                                 | Herramienta Recomendada                                 | Enlace Oficial |
|--------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------|----------------|
| **Amcache**              | Base de datos de Windows que registra programas ejecutados, ubicación de archivos y metadatos, útil para determinar la primera ejecución. | AmcacheParser (Eric Zimmerman)                         | [🔗 Descargar](https://ericzimmerman.github.io/#!index.md) |
|                          |                                                                                   | AmcacheParser (Python - Willi Ballenthin)               | [🔗 GitHub](https://github.com/williballenthin/python-amcache) |
| **ShimCache**            | Registro en el SYSTEM hive (AppCompatCache) que almacena información de ejecución de programas, incluso si ya no existen en disco. | AppCompatCacheParser (Eric Zimmerman)                   | [🔗 Descargar](https://ericzimmerman.github.io/#!index.md) |
|                          |                                                                                   | ShimCacheParser (Python - FireEye)                      | [🔗 GitHub](https://github.com/mandiant/ShimCacheParser) |
| **RecentFileCache**      | Archivo que guarda referencias recientes a ejecutables para compatibilidad de aplicaciones, útil para identificar software usado. | RecentFileCacheParser (Python - Corey Harrell)           | [🔗 GitHub](https://github.com/keydet89/Tools/blob/master/RecentFileCacheParser.py) |
|                          |                                                                                   | WindowsSCOPE (Visualizador forense)                      | [🔗 Sitio Web](https://www.windowsscope.com/) |
