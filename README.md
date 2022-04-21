# **Redes en Humanidades. Gephi**

☞ Esquema del curso

- [Objeto de trabajo](#objeto-de-trabajo-redes-en-humanidades)
- [Redes](#redes)
- [Formalización y formatos](#formalización-y-formatos)
- [Métricas](#métricas)
- [Herramientas](#herramientas)
- [Datos](#datos)
- [Prácticas paso a paso](#prácticas-paso-a-paso)
- [Tutoriales, manuales, bibliografía](#tutoriales-manuales-bibliografía)

# Objeto de trabajo: redes en humanidades

## _Showcase_

- Redes de caracteres:
    - Coaparición en escena: [Dracor](https://dracor.org)
    - Coaparición en novelas: [_Les Miserables_](https://bost.ocks.org/mike/miserables/)
    - Dinámicas: [Visualising the dynamics of character networks](https://maladesimaginaires.github.io/intnetviz/)
    - Paratextos: [Proyecto Bieses](https://www.bieses.net/editorial.html)
- Redes Textuales:
    - [Estilometría de obras teatrales](https://editio.github.io/grafos/teatro)
- Redes Históricas:
    - [Mapping the archives of the League of Nations ICIC (1919-1927)](https://grandjeanmartin.github.io/intellectual-cooperation)
- Redes espaciales:
    - [Centro y periferia en la novela bizantina](https://editio.github.io/mapping.literature/spatialnet.html#persiles_core_vs_periphery)
- Redes Bibliográficas:
    - Citación: [Vosviewer](https://tinyurl.com/y36v4cb3)
    - Similitud de contenido: [Connected Papers](https://www.connectedpapers.com/main/3149a915f738f044778e3decdb4278e2bad17808/Gephi%3A-An-Open-Source-Software-for-Exploring-and-Manipulating-Networks/graph)
- Redes culturales:
    - [Premios y premiados](https://w.wiki/52Ju) 



# Redes

- Método de representación de patrones de conexión o interacción entre partes de un sistema.

- El concepto de red supone una estructura relacional que puede ser estudiada (1) de forma lógica y matemática: Teoría de grafos (disciplina). Historia: [Euler y los siete puentes de Königsberg](https://medium.com/@satoshihgsn/seven-bridges-of-königsberg-can-this-diagram-be-drawn-in-a-single-stroke-e261980711a1).
- (2) Exploración por medio de la visualización.

## Conceptos básicos. Nodos y enlaces

- Red: puntos unidos por líneas.
- Puntos: **nodos** o vértices (_nodes_ o _vertices_).
- Líneas: **aristas** o enlaces (_edges_ o _links_).
- Atributos: información extra sobre nodos o aristas
- Tipos de redes:
    - Definen los nodos: [bipartitas](https://mathworld.wolfram.com/BipartiteGraph.html), [simples](https://mathworld.wolfram.com/SimpleGraph.html), [desconectadas](https://mathworld.wolfram.com/DisconnectedGraph.html)
    - Definen las aristas: [múltiples](https://mathworld.wolfram.com/Multigraph.html), [dirigidas](https://mathworld.wolfram.com/DirectedGraph.html), ...

## Red simple

![](images/terms_simple.png)

## Red bipartita  

![](images/terms_bipartita.png)
 
## Red múltiple 

![](images/terms_multiple.png) 

# Formalización y formatos

## Formalización

Lista de aristas, matrices, lista de adyacencia, ...

**Lista de aristas (_edgelist_)**: es conjunto de datos estructurados que contiene como mínimo dos columnas: una columna de nodos que son el origen de una conexión (_source_) y otra columna de nodos que son el destino de la conexión (_target_). El resto de columnas corresponden a los atributos.

|source |target|weight|lang|type|
|-------|------|----|-----|----|
|Juan|Elena |4 |esp     |undirected|
|Juan|Hans  |2  |de     |undirected|
|Juan|Marta  |1 |eng     |undirected|
|Juan|Marek |1  |de     |undirected|
|...|... |... |...|...|

**Matriz de adyacencia ([Adjacency matrix](https://mathworld.wolfram.com/AdjacencyMatrix.html))**: una matriz cuadrada (igual número de columnas y filas)

| |Juan|Hans|Elena|Marta|Marek|
|--|--|------|----|-----|----|
|**Juan**|0|1|1|1|1|
|**Hans**|1|0|0|1|1|
|**Elena**|1|0|0|0|0|
|**Marta**|1|1|0|0|0|
|**Marek**|1|1|0|0|0|

[...]

## Formatos

- ```CSV```. Lista de aristas en CSV:

```
source,target,lengua,weight
Juan,Elena,esp,4
Juan,Hans,de,2
Juan,Marta,eng,1
Juan,Marek,de,1
Juan,Marek,esp,1
Juan,Marek,pol,5
Hans,Marta,eng,1
Hans,Marek,de,1
```

- ```CSV```. Lista de Aristas + Nodos en CSV:

```
source,target
1,4
1,2
1,3

id,Label
1,Juan
2,Hans
3,Marta
4,Elena
```
Es recomendable guardar los datos estructurados en CSV, aunque Gephi acepta tablas en Excel.

- ```gexf``` (XML)

```xml
[...]
      <node id="Marek" label="Marek">
        <attvalues>
          <attvalue for="att1" value="2.0"/>
        </attvalues>
        <viz:size value="4.0"/>
        <viz:position x="-22.013721" y="26.080078"/>
        <viz:color r="255" g="99" b="71"/>
      </node>
    </nodes>
    <edges>
      <edge id="0" source="Juan" target="Hans" weight="2.0"/>
      <edge id="1" source="Juan" target="Elena" weight="4.0"/>
      <edge id="2" source="Juan" target="Marta"/>
      <edge id="3" source="Juan" target="Marek" weight="7.0"/>
      <edge id="4" source="Hans" target="Marta"/>
      <edge id="5" source="Hans" target="Marek"/>
    </edges>
  </graph>
</gexf>
```

- [Más formatos](https://gephi.org/users/supported-graph-formats/) (reconocidos por Gephi)

# Visualización (_spatialization_)

Misma red, distinta disposición.

![](images/network_viz.png)

Red bipartita

![](images/terms_bipartita_layout.png)

## Algoritmos para dibujar el grafo

![](images/network_layouts.png)

- Clásicos en Gephi: _Force Atlas_, _Fruchterman Reingold_,...

# Métricas

![](images/terms_metrics.png)

- _Degree centrality_: nº de conexiones.
- _Betweenness centrality_: nodos puente. 
- _Eigenvector centrality_: nodos conectados a nodos bien conectados.
- _Modularity_ (Louvain, Leiden algorithms): agrupaciones de nodos.
- ...

![degree-distribution](images/degree-distribution.png)

# Herramientas

Flujo de trabajo: del dato a la visualización.

![work flow](images/workflow.png)

- Lenguajes de programación (flujo completo) : R, Python, JavaScript,...
- OpenRefine, Table2net,...
- Tableau, Nodegoat,...
- Gephi, Cytoscape, VOSviewer,...

## Gephi. Open Graph Viz Platform

Gephi acaba de ser actualizado a la versión 0.9.4 (last release: 16/04/2022). Se puede descargar desde su página <https://gephi.org>.

Una de las ventajas de la nueva versión es que viene ya con Java (lenguaje de programación y entorno de ejecución para programas como Gephi). Más sobre la instalación en <https://gephi.org/users/install/>

## Interfaz: Panel _Overview_

![](images/gephi_interfaz.png)

## Plugins en Gephi: 

Se encuentran en Tools > Plugin. Añaden a Gephi funcionalidades extra (métricas, importación, exportación, espacializaciones, ...). 

- _Multimode networks transformation_: Proyecta una red bipartita a una simple.

- _Sigma exporter_: Exporta el grafo para visualizarlo dinámicamente usando javascript y html.

- _Leiden algorithm_: Algoritmo de modularidad.

# Datos

Los archivos en formato CSV y GEXF se encuentran en la carpeta ```/data``` de este repositorio.

## Teatro

Redes de caracteres de coaparición en el teatro. La fuente es <http://www.dracor.org>, desde donde se pueden descargar; los añado a ```/data``` como respaldo.

  - ```calderon_VidaEsSueno_ezlinavis.csv```
  - ```span000014-valle-luces.gexf```

## Premios literarios

35 premios literarios y 1325 autores premiados: datos obtenidos de Wikidata. Tabla en CSV con 3 variables: premios, premiados y género (masc./fem.); red bipartita y redes simples en formato gexf.

- ```autoresypremios.csv```
- ```autoresypremios.gexf```
- ```autores.gexf```
- ```premios.gexf```

El set de datos (+ listas de nodos y aristas) está en [editio/premios-literarios](https://github.com/editio/premios-literarios) y Zenodo: José Luis Losada (2022) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.6464417.svg)](https://doi.org/10.5281/zenodo.6464417)

## Estilometría

Red de estilometría de obras teatrales del Siglo de Oro. Los nodos representan obras teatrales unidos según su cercanía estilística. Análisis realizado usando el árbol de consenso (2000-5000 MFW) y la distancia Delta con el paquete de R, stylo (Eder, Rybicki y Kestemont, 2016), sobre un corpus de aproximadamente 700 obras y 50 autores. Visualización interactiva en: [Estilometría de obras teatrales](https://editio.github.io/grafos/teatro)

- ```estilometria_teatro.gexf```

# Prácticas paso a paso
 
## Red de caracteres

☞ Practicar los fundamentos de una lista de aristas, cómo cargarla en Gephi y realizar los primeros pasos de visualización y métricas.

1. Dracor > tools > https://ezlinavis.dracor.org > Examples > Calderón > descarga _edge list_.
2. Gephi > Import spreadsheet (CSV) > next > finish.
- Layout: Fruchterman Reingold.
- Tamaño de nodos según el _degree_: Appearance > nodes > size [icono círculos] > Ranking > Choose an attribute > Degree [min. 10 - max. 50].
- Etiquetas de los nodos (_label_): "copy data to other column" (_Data laboratory_). Alternativa: "select attributes to display as labels" (_Overview_).
- Medidas de centralidad (Betweenness/Eigenvector): Segismundo frente a Clarín (statistics > Network Diameter; Eigenvector Centrality).

☞ Conocer el archivo en formato gexf, abrir en Gephi, atributos de los nodos (masculino/femenino).

1. Dracor > corpora > [Spanish Drama Corpus](https://dracor.org/span) > Valle Inclán, _Luces de bohemia_ > Downloads > Archivo en gexf.
2. Gephi > open > [sin cambios] > ok.
- Exploración de datos: _label_, _gender_ (_Data laboratory_).
- Appearance > nodes > color [icono paleta] > Partition > Choose an attribute > gender
- Layout: Force Atlas 2 [Prevent overlap, Disuade Hubs, Scaling = 40] > run|stop.

## De los datos a la red: premios y premiados

☞ Pasar de datos estructurados (tabla de datos) a una formalización de una lista de aristas (gexf)

1. Materiales en Github > data > ```autoresypremios.csv```
2. [table2net](https://medialab.github.io/table2net/) (conversión en el navegador).
3. Load table > Type of Network > Nodes > Build the network > Download.

  - 3.1 Tipo de red: bipartita.
  - 3.2 Nodos 1: autores | atributo: masc/fem.
  - 3.3 Nodos 2: premios.

## Red de premios y premiados (1)

☞ Explorar redes bipartitas.

1. Gephi > open ```autoresypremios.gexf```.
- Layout: Force Atlas 2 > run|stop; > Prevent overlap > run|stop; Zoom
- Appearance > nodes > color [icono paleta] > Partition > Choose an attribute > Type
- Appearance > nodes > size [icono círculos] > Ranking > Choose an attribute > Degree [min. 10 - max. 50] (nº de autores por premio).
- Nodes Labels: Show node Labels; More settings > Labels > Hide non-selected. 
- [reset colors] > Appearance > nodes > color [icono paleta] > Partition > Choose an attribute > sexlabel. 

## Red de premios y premiados (2)

☞ Explorar redes simples (premios, autores). 

Los archivos ya están listos en ```/data/premios.gexf```; ```/data/autores.gexf```. Se pueden asimismo crear desde la tabla de datos ([table2net](https://medialab.github.io/table2net/)) o usando una transformación desde la red bipartita (☞ _vide infra_).

1. Gephi > open ```premios.gexf```
  - Layout: Force atlas 2 [Prevent overlap, Disuade Hubs, Scaling = 50]
  - Appearance > nodes > size [icono círculos] > Ranking > Choose an attribute > Degree [min. 5 - max. 30].
  - Modularidad: Community detection > Modularity > run.
  - Appearance > nodes > color [icono paleta] > Partition > Choose an attribute > Modularity Class.

  - Comprobar centralidad:
      - statistics > eigenvector Centrality.
      - Appearance > nodes > size [icono círculos] > Ranking > Choose an attribute > eigenvector Centrality.

2. Gephi > open ```autores.gexf```
  - Layout: Layout: Fruchterman Reingold.
  - Appearance > nodes > color [icono paleta] > Partition > Choose an attribute > sexlabel.
  - Appearance > nodes > size [icono círculos] > Ranking > Choose an attribute > Degree [min. 5 - max. 30].

☞ Pasar de un tipo de red a otro (proyeción). 

1. Plugin: multimode networks transformation.
  
  - Red bipartita.
  - Load attributes > type:
    - Premio > Autor / Autor > Premio (Red simple de premios)
    - Autor > Premio / Premio > Autor (Red simple de autores)
  - Remove nodes, edges.
  - Run.

## Estilometría

☞ Explorar redes textuales

1. Gephi > open ```estilometria_teatro.gexf```.
- Layout: Force atlas 2 [Prevent overlap, Disuade Hubs, Scaling = 200].
- Appearance > nodes > color [icono paleta] > Partition > Choose an attribute > Classes (autores) > Palette > Generate [Limit number of colors: unchecked] > generate.
- Appearance > nodes > size [icono círculos] > Unique > size = 20.
- Nodes Labels: Show node Labels; More settings > Labels > Hide non-selected.  

Contrastar con la modularidad:

- Modularidad: Community detection > Modularity > run.
- Appearance > nodes > color [icono paleta] > Partition > Choose an attribute > Modularity Class.

## Red espacial

☞ Explorar redes espaciales

1. Gephi > open ```homero_odisea.gexf```.
2. Plugin: Geo Layout



## Formatos de publicación

☞ Formas de representación estática y dinámica de los grafos.

1. Panel _Overview_: Screeshot (izquierda), More settings (derecha)...
1. Panel _Preview_: exportar svg, png, pdf.
2. Plugin: _Sigma Exporter_. Crea una carpeta con las librerías, datos y ficheros para mostrar el grafo de forma interactiva en un navegador. Es necesario subirlo a un servidor web, por ejemplo, usando [Github Pages](https://pages.github.com). Se puede lanzar un servidor web local para realizar pruebas en local: [Instrucciones](http://phc.uni.wroc.pl/interreg/w/losada/trans.html#web-server-in-your-computer).


# Tutoriales, manuales, bibliografía

- Albert-László Barabási, [Network Science](http://networksciencebook.com), 2016.
- Gephi, [Learn how to use Gephi](https://gephi.org/users/).
- Martin Grandjean, [Gephi: Introduction to Network Analysis and Visualization](http://www.martingrandjean.ch/gephi-introduction), 14/10/2015.
- Clément Levallois, [Gephi tutorials](https://seinecle.github.io/gephi-tutorials/), Last update: 2022.
- Mark Newman, _Networks: An Introduction_, Oxford University Press, 2010.
- Katherine Ognyanova, [Static and dynamic network visualization with R](https://kateto.net/network-visualization), 2021
- Katharina A. Zweig, _Network Analysis Literacy: A Practical Approach to the Analysis of Networks_, Springer, 2016.