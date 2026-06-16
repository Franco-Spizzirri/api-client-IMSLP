api-client-IMSLP

Este worker está creado con el objetivo de consumir información pública del sitio IMSLP (International Music Score Library Project) para obtener metadatos asociados a obras musicales y compositores, procesar las respuestas obtenidas y almacenarlas utilizando las tablas assets y assets_history provistas.

Los datos se obtendrán mediante requests HTTP a páginas públicas de IMSLP y/o mediante consultas a la API MediaWiki utilizada internamente por el sitio. A partir de esto, se obtendrá información (metadatos) relacionada con obras musicales, compositores y partituras en formato JSON.
La aplicación procesará dichos datos utilizando técnicas de parsing y scraping mediante BeautifulSoup, permitiendo extraer información relevante del contenido obtenido.

Los datos recuperados serán almacenados en la tabla assets, y el mapeo de campos sería el siguiente:

asset_uri --> URL de la obra o compositor en IMSLP

title --> título de la obra musical

entity --> compositor o nombre de la obra

provider --> IMSLP

meta_payload --> JSON o estructura completa obtenida desde IMSLP (además de los mencionados, también pueden incluirse descripción, instrumentación, opus, género musical, fecha de composición, categorías, enlaces de descarga, etc).

La aplicación funcionará realizando consultas GET sobre páginas públicas de IMSLP, utilizando parámetros de búsqueda asociados al nombre de una obra o compositor.
En caso de utilizar la API MediaWiki de IMSLP, se accederá a endpoints públicos que devuelven información estructurada en formato JSON.

La documentación de IMSLP y MediaWiki especifica que gran parte de la información pública puede ser consultada sin autenticación, por lo que no será necesario utilizar tokens, logins ni otros métodos de autenticación para acceder a contenido público.

Documentación:

https://imslp.org/
https://www.mediawiki.org/wiki/API:Main_page
