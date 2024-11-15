Práctica de desarrollo 3. PD03. Morfometría de Cuencas y Procesos
Fluviales, análisis pormenorizados<small><br>Geomorfología
(GEO-114)<br>Universidad Autónoma de Santo Domingo (UASD)<br>Semestre
2024-02</small>
================
El Tali
2024-11-11

<!-- README.md se genera a partir de README.Rmd. Por favor, edita ese archivo. -->

Versión HTML (quizá más legible),
[aquí](https://geomorfologia-master.github.io/sistema-fluvial-morfometria-cuenca-avanzada/README.html)

# Fecha/hora de entrega

**18 de noviembre de 2024, 11:59 pm.**

# Objetivos

1.  **Aplicar herramientas de análisis morfométrico en GRASS GIS y R**
    para obtener morfométricos de una cuenca hidrográfica en la
    cordillera Central, cordillera Oriental o la sierra de Yamasá de la
    República Dominicana, utilizando un modelo digital de elevación
    (DEM) de resolución media.

2.  **Desarrollar habilidades en la manipulación de datos
    geoespaciales** mediante la integración de múltiples fuentes de
    datos (DEM, geoides, imágenes satelitales) y el uso de software de
    código abierto (QGIS, RStudio, GRASS GIS) para la generación y
    análisis de redes hidrográficas.

3.  **Redactar un manuscrito científico reproducible** siguiendo
    estándares de formato y redacción académica, integrando la
    presentación de resultados obtenidos con un análisis crítico y el
    uso de referencias bibliográficas según el estilo APA.

# Mandato

1.  **Acepta la asignación, genera tu repositorio personalizado y
    clónalo en tu cuenta del servidor RStudio**. Este paso sigue el
    procedimiento estándar que aprendiste en PD anteriores. De todas
    formas, te lo refresco de forma resumida. Primero ve al [portal de
    la asignatura](https://github.com/geomorfologia-202402), haz clic en
    el enlace de la PD04 y acepta la asignación. Se creará un
    repositorio personalizado en la [organización
    geomorfologia-202402](https://github.com/geomorfologia-202402). El
    nombre de tu repo personalizado normalmente será algo tal que: “base
    del repo” + “tu nombre de usuario de GitHub” (como sufijo). Clona tu
    repositorio personalizado en el servidor RStudio. Para ello, deberás
    acceder al servidor con tus credenciales, copiar la ruta en GitHub
    de tu repo personalizado (botón verde `Code` en GitHub) y realizar
    el procedimiento estándar de nuevo proyecto con control de versiones
    en RStudio.

2.  **REPRODUCE EL VÍDEO DE APOYO** para comprender el código de Python
    y sus resultados. Tienes un vídeo de apoyo exclusivo para esta
    práctica, cuyo enlace encontrarás en el párrafo de asignación de
    esta PD03 en el [portal de la
    asignatura](https://github.com/geomorfologia-202402). El vídeo
    explica cómo realizar, y en qué consisten, los análisis necesarios
    para obtener los parámetros básicos de morfometría de una cuenca
    pequeña usando GRASS GIS y R.

3.  Elige una cuenca pequeña, de entre 50 y 100 km<sup>2</sup> en
    cualquiera de los sistemas montañosos mencionados arriba. Esta fase
    es de exploración, así que usa por ejemplo Google Earth o QGIS (con
    fondo de por ejemplo OpenTopoMas) para calcular el área aproximada
    cuenca. Podrías hacer la medición de múltiples maneras, para
    eficientizar, te recomiendo que crees una capa poligonal en QGIS en
    EPSG:4326, digitalices el límite de una cuenca (de los sistemas
    montañosos mencionados arriba) que entiendas tiene superificie entre
    50 y 100 km<sup>2</sup> (no tiene que ser preciso, de hecho, mejor
    ligeramente más grande que la cuenca), y luego presiona
    `Vectorial > Herramientas de geometría > Agregar atributos de geometría`.
    Cuando encuentres una cuenca del tamaño requerido, exporta el
    vectorial sólo con dicha cuenca (`botón derecho a la capa>Exportar`)
    en formato KML o o GeoJSON, pues lo usarás más adelante.

4.  **IMPORTANTE**. Anuncia tu elección en el foro; si ya está elegida,
    o si el Tali te desaconseja usarla, deberás elegir otra.

5.  Desde [Alaska Satellite Facility
    (ASF)](https://search.asf.alaska.edu/) (necesitarás una cuenta),
    descarga un DEM ALOS PALSAR de 12.5 m de modo “haz fino” de doble
    polarización (FBD), de resolución (preferiblemente, el de fecha más
    reciente que encuentres), de que abarque la cuenca que elegiste. Si
    tu cuenca elegida cae sobre más de una escena, tendrás que
    descargarlas todas y después unirlas (*mosaicking*); también puedes
    cambiar de cuenca si no quieres unir escenas.

6.  Descomprime el contenido obtenido desde ASF. Concéntrate en un
    archivo con este patrón “AP\_#####*FBD*\#####\_RT1.dem.tif”. La
    parte “dem” es lo que te indica que se trata de una fuente de
    elevaciones.

7.  En el servidor RStudio, dentro del repo de la asignación, sube el
    archivo DEM a tu clon del repo de esta PD03 y reproduce, para tu
    cuenca, los mismos resultados obtenidos en el preprint titulado
    “Generación de red hidrográfica densa de República Dominicana a
    partir de modelo digital de elevaciones de resolución media”
    (Martínez-Batlle y Izzo-Gioiosa, 2023), disponible
    [aquí](https://preprints.scielo.org/index.php/scielo/preprint/view/7056/version/7462).
    Para ello, necesitarás consultar y adaptar el código fuente, que se
    encuentra tanto en la información suplementaria del propio preprint,
    así como en [este repo de
    GitHub](https://github.com/geofis/red-hidrografica-densa-rd). Tu
    código deberá ser reproducible.

Algunas notas:

- Umbral de acumulación. Elegirás uno, pero tendrá que ser de 120 celdas
  o menos.

- Puedes reproducir el código del *preprint* pero, lógicamente, tendrás
  que adaptarlo a tu caso, y necesitarás depurar errores. Tienes dos
  opciones para ejecutar los algoritmos de GRASS GIS:

  - Directamente en la consola terminal de Bash (en el servidor de
    RStudio, panel inferior, pestaña nombrada `Terminal`, justo al lado
    de la nombrada `Console`, que es la del intérprete de R). El código
    que funcione lo deberás transcribir a la sección “Información
    suplementaria” del manuscrito de ejemplo con el flag `eval=F` en el
    encabezado del bloque de código, lo cual te permitirá tejer el
    cuaderno.

  - EN R, usando el paquete `rgrass`.

- Para la parte correspondiente a obtener alturas pseudo-ortométricas,
  necesitarás subir un geoide al servidor. Puedes usar
  [este](https://drive.google.com/file/d/1tLHhD1xcFKAJE0rfulVDDm-hiGVoDLnx/view),
  que fue descargado y recortado desde la web de Metashape, Agisoft, y
  pertenece a [Office of Geomatics de la USA
  NGA](https://earth-info.nga.mil/).

8.  Revisa bibliografía sobre los algoritmos empleados. No puedes usar
    estos algoritmos sin saber de qué tratan, aunque no tienes por qué
    entrar en los detalles. Los parámetros de configuración de los
    algoritmos (por ejemplo, umbral de acumulación, que en la ayuda de
    GRASS GIS suele aparecer como “*threshold*”), son extremadamente
    importantes. Eso sí, te recomiendo que consultes tanto libros como
    artículos científicos con casos de uso.

9.  **Finalmente, redacta un manuscrito**. Para el procesamiento de tu
    texto y la redacción de tus análisis, usa la plantilla
    `manuscrito-sistema-fluvial-morfometria-cuenca-avanzada.Rmd`, que se
    encuentra en este mismo repositorio. Con esta plantilla generarás un
    PDF que tejeras a usando RStudio. Deberás usar estilos de formato
    (los títulos debidamente escritos, el texto normal también,
    siguiendo lo aprendido en las PD anteriores), referencias
    bibliográficas, referencias cruzadas a figuras y tablas (es decir,
    necesitarás que las figuras y tablas tengan título o “*caption*”).
    No podrás desarrollar tu redacción usando listas de viñetas ni
    listas numeradas. Debes usar la plantilla mencionada en RStudio,
    preferiblemente en mi servidor, tal como hiciste en las PD
    anteriores. Cuando termines tu manuscrito con tus análisis
    reproducibles, y lo tejas a PDF, no olvides hacer commit\>push de
    todos tus cambios para subirlos a GitHub. Necesitarás citar
    bibliografía, no lo podrás evitar, tanto en la introducción, como en
    la metodología y la discusión. No olvides citar los datos fuente.

Distribuye tu texto en las siguientes secciones:

- **Introducción** (tamaño recomendado: 3 párrafos). Desde lo amplio,
  puedes comenzar escribiendo sobre los modelos de elevación y su
  potencial, el modelo de ALOS-PALSAR, y el análisis morfométrico de
  cuencas y de redes de drenaje, pero muy desdelo general. Puedes
  mencionar el repo de hidrografía nacional y su aporte como base para
  este trabajo, pero también cualquier otro trabajo que se haya
  realizado en el país sobre hidrografía nacional, especialmente si hay
  algunos sobre morfometría. Puedes a continuación mencionar tu cuenca
  elegida y lo poco estudiada que se encuentra (todas las cuencas
  pequeñas dominicanas están “poco estudiadas”).

A continuación, explica en qué consiste (algo más detalladamente que en
el párrafo anterior) el análisis morfométrico, destacando la importancia
de estos análisis, por qué son útiles estos y que los hace especiales.
Plantea tu o tus objetivos, que en este caso están algo acotados. Cierra
con la importancia que reviste la morfometría de tu cuenca elegida
respecto del conjunto de la ciencia.

- Dentro de esta sección, debes incluir al menos cinco citas. Los
  conceptos y afirmaciones ajenas, deben citarse bibliográficamente, y
  nunca deberás usar cita textual, pues se considera plagio. Las citas
  bibliográficas que incluyas, deberán estar respaldadas por su
  correspondiente lista referencias, la cual deberá aparecer en la
  sección final (Referencias); el propio tejido de RMarkdown debería
  generarla por ti, siempre que sigas las instrucciones correspondientes
  (vuelve al vídeo de la PD01 para refrescar). Las citas y la lista de
  referencias, deberán seguir el estándar APA 7ma edición (APA7), que es
  el que la propia plantilla tiene configurado por defecto; en
  principio, no tendrás que ocuparte de todos los detalles de sintaxis
  del formato APA7, pero no debes confiar ciegamente en lo que hace
  RMarkdown.

- En esta sección (o en la siguiente de “Materiales y métodos”) debes
  incluir la descripción del ámbito geográfico del estudio, ya sea
  dentro de un subtítulo o como párrafo debidamente integrado en el
  texto donde lo insertes. Con independencia de dónde lo incluyas, lo
  importante es que no omitas dicho texto. En un manuscrito del área de
  geografía, no puede omitirse la descripción del área o territorio
  estudiado, en este caso, tu cuenca hidrográfica y su entorno.

- **Materiales y métodos** (tamaño recomendado: cuatro párrafos).
  Explica cómo obtuviste los datos que usaste (e.g. el DEM, el geoide, y
  todos los demás que hayas usado como fuentes), y documenta en qué
  consiste la fuente. Debes igualmente citar el software y hardware
  usado, y las referencias sobre la técnica o algoritmo empleados. Ten
  presente que la bibliografía sobre cuencas es muy pero que muy densa
  (aunque la de morfometría es algo ligera), así que deberás hacer una
  selección apropiada. Si incluyes un diagrama de flujo metodológico
  (“metodología gráfica”), te resultará más fácil explicar tu
  metodología. **No adelantes resultados, sólo escribe qué fuentes y
  herramientas usaste (materiales), qué técnicas concretas o algoritmos
  utilizaste (métodos), y qué configuraciones aplicaste a los
  algoritmos**. Toda figura y tabla que insertes debe citarse con
  referencia cruzada, para lo cual dispones de una guía con ejemplos al
  final de la plantilla de manuscrito (archivo:
  `manuscrito-sistema-fluvial-morfometria-cuenca-avanzada.Rmd`).

- **Resultados** (tamaño recomendado: 4 párrafo). Los análisis
  morfométricos realizados, los descriptores básicos de estos análisis,
  los patrones espaciales de las variables obtenidas (en genera, la
  morfometría produce atributos de la cuenca y de la red, que en
  conjunto podemos considerar como “variables”). Describe estos patrones
  usando orientaciones cardinales y referencias geográficas. No hagas
  valoraciones en esta sección, simplemente incluye los resultados
  obtenidos.

- **Discusión** (tamaño recomendado: 4 párrafos). Abre la discusión
  indicando si alcanzaste tus objetivos. Describe por qué era importante
  alcanzarlos.

Comenta sobre las limitaciones, de cualquier tipo, ya sea las
limitaciones de los datos, de la técnicas, de los objetivos de
aprendizaje. Cierra indicando qué desafíos futuros quedan abiertos tras
este trabajo. Interpreta por qué las variables morfométricas obtenidas
tienen el patrón espacial que tienen, o la relación que tienen con otras
variables (e.g. geología, topografía, etc.). Comenta sobre las
limitaciones, de cualquier tipo, ya sea las limitaciones de los datos,
de las técnicas o de los objetivos de aprendizaje. Cierra indicando qué
desafíos futuros quedan abiertos tras este trabajo.

- **Referencias**. Las referencias que hayas citado en el texto, se
  incluirán automáticamente en la sección “Referencias”. No obstante,
  debes verificar la integridad de las mismas.

> **RECUADRO: recomendaciones básicas de redacción**
>
> Usa una voz (activa o pasiva) de forma consistente, pero sólo ten
> presente que la redacción de manuscritos científicos a menudo se
> utilizan ambas voces, dependiendo del contexto y el mensaje que el/la
> autor/a quiera transmitir. Veamos algunos ejemplos:
>
> **Voz activa en manuscrito científicos:**
>
> - **Analicé** los datos utilizando el lenguaje de programación Python.
>
> - El experimento **mostró** que la temperatura afecta directamente la
>   tasa de reacción.
>
> - Los investigadores **encontraron** una correlación significativa
>   entre las dos variables.
>
> La voz activa puede hacer que la redacción parezca más directa y
> clara, y es especialmente útil cuando el/la autor/a quiere enfatizar
> quién llevó a cabo una acción o cuándo se desea hacer una afirmación
> fuerte.
>
> **Voz pasiva en artículos científicos:**
>
> - Los datos **fueron analizados** utilizando el lenguaje de
>   programación Python.
>
> - **Se observó** que la temperatura afecta directamente la tasa de
>   reacción.
>
> - Una correlación significativa **fue encontrada** entre las dos
>   variables.
>
> La voz pasiva es común en la redacción científica porque a menudo se
> prefiere un tono más impersonal, enfocando la atención en los
> resultados y procedimientos en lugar de en quienes llevaron a cabo la
> investigación. También puede ser útil cuando no se quiere o no es
> relevante especificar quién realizó la acción.
>
> **En todas mis prácticas, está completamente permitido usar IA
> (e.g. chatGPT), pero te recomiendo que la uses más como tutor que como
> redactor**. Tal como te sugerí arriba, no le pidas que te resuelva los
> problemas del mandato. Pídele que te dé ideas, y que luego tú las
> mejores o las descartes. No abuses tampoco del texto, pues mucha
> redacción no siempre es mejor; en redacción de ensayos “menos es más”.
> Cruza las redacciones que te ofrezca con tu conocimiento, y revisa si
> los términos o conceptos usados son descabellados (toda IA se inventa
> cosas, cuidate de no caer en esa trampa). Nunca le pidas referencias
> bibliográficas, porque se va equivocar.

# Referencias

<div id="refs" class="references csl-bib-body hanging-indent"
entry-spacing="0" line-spacing="2">

<div id="ref-Martinez-Batlle_Gioiosa_2023" class="csl-entry">

Martínez-Batlle, J.-R. y Izzo-Gioiosa, M. (2023). Generación de red
hidrográfica densa de República Dominicana a partir de modelo digital de
elevaciones de resolución media. *SciELO Preprints*.
<https://doi.org/10.1590/SciELOPreprints.7056>

</div>

</div>
