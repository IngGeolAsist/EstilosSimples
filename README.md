# Estilos Simples
Hemos visto como cargar capas vectoriales, sin embargo, esto no es muy útil si no se tiene una representación cartográfica adecuada. En los siguientes tutoriales, veremos como añadir estilos mas complejos, pero por el momento, nos enfocaremos en los elementos de un estilo simple. 
## Para empezar, cargaremos una nueva capa, que serán los contactos de las litologías. Así que seguiremos el procedimiento completo que realizamos con los Geojsons. 
``` html

	<!-- -----CAPAS JSON------ -->
	
	<script type="text/javascript" src="DATA/json/Geología_PeñaDe Bernal_GCS.js"></script>
	<script type="text/javascript" src="DATA/json/contact.js"></script>

```
## Después, entre las líneas de código que incluyen las Características del Mapa y las de las Capas Base, incluiremos un nuevo apartado que contendrá los Estilos Capas Vectoriales.

``` html

<!-- ------ CARACTERISTICAS DEL MAPA------ -->
 var map = L.map('mapDIV', {
		center:[20.83748 , -99.71396],
		zoom:11
	});
	
	var scale = L.control.scale({
		'imperial':false
	});
	scale.addTo(map);
	
<!-- ------ ESTILOS PARA CAPAS VECTORIALES ------ -->
	
	var contact_style = {
		color: "#000000",
		weight: 2,
		opacity: 1,
	};
	
<!-- ------CAPAS BASE------ -->
	
	var osm = L.tileLayer('http://a.tile.openstreetmap.org/{z}/{x}/{y}.png',
	{attribution: 'Map Data &copy; OpenStreetMap contributors'
	});
	osm.addTo(map);
	
	var topo = L.tileLayer('https://{s}.tile.opentopomap.org/{z}/{x}/{y}.png', {
	maxZoom: 17,
	attribution: 'Map data: &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, <a href="http://viewfinderpanoramas.org">SRTM</a> | Map style: &copy; <a href="https://opentopomap.org">OpenTopoMap</a> (<a href="https://creativecommons.org/licenses/by-sa/3.0/">CC-BY-SA</a>)'
	}); 
	topo.addTo(map);
	
	var sat = L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}', {
	attribution: 'Tiles &copy; Esri &mdash; Source: Esri, i-cubed, USDA, USGS, AEX, GeoEye, Getmapping, Aerogrid, IGN, IGP, UPR-EGP, and the GIS User Community'
	});


```

## Cada nuevo estilo estará declarado como una variable, nuevamente al nombrar la variable procura usar un nombre que te sea familiar, como en el ejemplo. 
Hay multiples atributos que se pueden ser editados según el tipo de geometría. Para las líneas, como es el caso tenemos:
``` html
<script>
  	var contact_style = {
		color: "#000000",
		weight: 2,
		opacity: 1,
	};
 </script>
```

*COLOR*: Nos ayuda a editar el color que tendrá el vector, puede ser expresado en hexagesimal o utilizar uno de los colores que ya vienen precargados en las estilos de leaflet.
*WEIGHT*: Se utiliza para editar el grosor de la línea, admite números enteros.
*OPACITY*: Controla la transparencia con la que se representa el vector. Admite números decimales.

## En el mismo nivel en el que declaramos la información del ejemplo anterior, escribiremos las sigientes lineas de codigo. Si te das cuenta, el estilo que declaramos es llamado para efectuar su función hasta este punto.

``` html
<script>
<!-- ----- CAPAS VECTORIALES------	 -->
	var geology = L.geoJson(geology).addTo(map);
	
	var contact = L.geoJson(contact,{
		style: contact_style
		}).addTo (map);
 </script>
```

## Al final el codigo debería parecerce al siguiente
``` html
<html>
<head>
	<meta charset="utf-8">
	<title>Mapa E14C17_2</title>
	
	<!-- -----LIBRERIAS-------- -->
	<link rel="stylesheet" href="https://unpkg.com/leaflet@1.6.0/dist/leaflet.css"
	integrity="sha512-xwE/Az9zrjBIphAcBb3F6JVqxf46+CDLwfLMHloNu6KEQCAWi6HcDUbeOfBIptF7tcCzusKFjFw2yuvEpDL9wQ=="
	crossorigin=""/>
	<script src="https://unpkg.com/leaflet@1.6.0/dist/leaflet.js"
	integrity="sha512-gZwIG9x3wUXg2hdXF6+rVkLF/0Vi9U8D2Ntg4Ga5I5BZpVkVxlJWbSQtXPSiUTtC0TjtGOmxa1AJPuV0CPthew=="
	crossorigin=""></script>
	
	
	<!-- -----CAPAS JSON------ -->
	
	
	<script type="text/javascript" src="DATA/json/Geología_PeñaDe Bernal_GCS.js"></script>
	<script type="text/javascript" src="DATA/json/contact.js"></script>
	
	
	
	
	<!-- -----ESTILOS DEL MAPA------ -->
	<style>
	#mapDIV {
	height: 100%;
	width: 100%;
	border: solid 2px black;
	}
	</style>
</head>

<body>
<div id="mapDIV"></div>

 <script>	
 <!-- ------ CARACTERISTICAS DEL MAPA------ -->
 var map = L.map('mapDIV', {
		center:[20.83748 , -99.71396],
		zoom:11
	});
	
	var scale = L.control.scale({
		'imperial':false
	});
	scale.addTo(map);
	
<!-- ------ ESTILOS PARA CAPAS VECTORIALES ------ -->
	
	var contact_style = {
		color: "#000000",
		weight: 2,
		opacity: 1,
	};
	
<!-- ------CAPAS BASE------ -->
	
	var osm = L.tileLayer('http://a.tile.openstreetmap.org/{z}/{x}/{y}.png',
	{attribution: 'Map Data &copy; OpenStreetMap contributors'
	});
	osm.addTo(map);
	
	var topo = L.tileLayer('https://{s}.tile.opentopomap.org/{z}/{x}/{y}.png', {
	maxZoom: 17,
	attribution: 'Map data: &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, <a href="http://viewfinderpanoramas.org">SRTM</a> | Map style: &copy; <a href="https://opentopomap.org">OpenTopoMap</a> (<a href="https://creativecommons.org/licenses/by-sa/3.0/">CC-BY-SA</a>)'
	}); 
	topo.addTo(map);
	
	var sat = L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}', {
	attribution: 'Tiles &copy; Esri &mdash; Source: Esri, i-cubed, USDA, USGS, AEX, GeoEye, Getmapping, Aerogrid, IGN, IGP, UPR-EGP, and the GIS User Community'
	});

<!-- ----- CONTROLADOR DEL MAPA------	 -->
	var basemaps = {
		"OSM": osm,
		"Topografía": topo,										
		"Satélite": sat
		};
	L.control.layers(basemaps).addTo(map);
	
<!-- ----- CAPAS VECTORIALES------	 -->
	var geology = L.geoJson(geology).addTo(map);
	
	var contact = L.geoJson(contact,{
		style: contact_style
		}).addTo (map);
	 
 </script>
</body>
</html>
```

## De esta manera debería visualizarse el mapa al ejecutarlo en el navegador.

![screenshot](https://raw.githubusercontent.com/sampach95/EstilosSimples/master/img/Imagen1.png )

Siguiente Tutorial https://github.com/IngGeolAsist/CategorizarElementosAPartirDeUnaPropiedad

Haz click en el siguiente enlace para volver a la pagina inicial https://github.com/IngGeolAsist/ComoCrearMapasEnLaWebConLeaflet





