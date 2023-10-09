# GMT BASICS FOR GEOMATICS ENGINEERING

Generic Mapping Tools (GMT) is open-source software that provides command-line tools for working with geographic and cartesian data. It offers features like data manipulation, map projection support, data visualization, and the creation of high-quality maps and illustrations. GMT includes geospatial data, supports various map projections, and allows for customization. It is widely used in scientific and geographic applications.

<p align = "center">
<img src="https://www.generic-mapping-tools.org/_static/gmt-logo.png" width="500" height="300" alt="GMT Logo">
</p>

GMT can be utilized across various programs or programming languages, including Python, MATLAB, Octave, Julia, and via the terminal using its original syntax rules. Thanks to GMT, it becomes possible to visualize a wide range of data types such as grids, netCDF4, and point data. GMT finds extensive applications in geomatics engineering, particularly in geodesy, due to its support for different projection types and its simplicity in visualizing spatial data.

## GMT SYNTAX

GMT has a different and complex syntax in terms of other programming languages such as Python or C#; because. In order to use GMT on Linux, first of all a shell (.sh) file have to be created, and afterwards that file should be started with #!/bin/bash comment in order to specifiy which shell a .sh script will be executed with and ensures the script's portability and executability in a broader context. So the heading a shell file should be seen like below.

```
#!/bin/bash
```

The second step is specifying the starting and ending places of code. It is _gmt begin_ and _gmt end_ commands for GMT. Other codes that are used for visualizing the data are written between those commands.

```
gmt begin my_first_plot
  #Other codes are written in here with an indentation.
gmt end show
```

In above code, after _gmt begin_ command the section name should be written. It is used for giving name to output of code. Also in order to show output of code _show_ command should be writtern after _gmt end_. Lastly, in order to get different types of outputs such as _png_ or _pdf_, after _gmt begin <section_name>_ _pdf_ or _png_ commands could be writtern. For example below code returns the output as a pdf file:

```
gmt begin output_types pdf
  #Codes
gmt end show
```
## GMT PROJECTIONS

As previously mentioned, GMT is frequently used by geomatics engineering for the visualization of spatial data because it has many different features. In this section, more than one projection is mentioned and examples are created. Firstly, projection means the presentation of curves or surfaces on a map with using geometric and mathematical equalities. Those projections could be geographic or non-geographic. Geographic projections are used for geodesy; however, non-geographic projections cannot be used for geodesy. They are created in order to obtaining a presentation of Earth with a general perspective. Also projection processing is done via surfaces which are flattenable such as conic, cyclinder or plane.

### Mercator Projection
Mercator Projection uses a azimuthal cylinder. That cylinder wrap Earth from its equator line.

<p align = "center">
<img src=https://cdn.britannica.com/55/109155-050-9FE4B08C/simple-cylindrical-projection-earth-map-globe-mercator.jpg height="300" alt="Mercator Projection">
</p>

In order to create a map with Mercator projection below code of GMT should be written.

```
#!/bin/bash

gmt begin mercator pdf

	gmt coast -R25/45/35/44 -Jm0.8 -Dh -Ggray -Slightblue -Wthinnest -B2.5g2.5 -B+t"Türkiye Map with Mercator Projection" -N1 -Ia/79/148/205 -Tdg43.8/43+w0.4i+f1+jcm+l,,,,
	
	echo 43.8 43.7 N | gmt text  -F+f7p,Helvetica,black

gmt end show
```

Its output is in the below:

<p align = "center">
<img src="https://github.com/felsenfest7/GMT_Examples/assets/92101782/13bb0c9f-f646-4250-ab5d-686f825f3d43" width="700" height=500" alt="Mercator Map">
</p>

In above code:
* ***gmt coast***: It is used for plotting continents, countries, shorelines, rivers, and borders.
* ***-R***: It describes the region of that will be drawn. It uses as -Rlower_long/higher_long/lower_lat_higher_lat.
* ***-J***: It is used for describing the projection type. In that example Mercator projection is used and because of that -J has a additional later _m_ to describe Mercator projection. Also _0.8_ means scale along paralels.
* ***-D***: It is resolution of map objects (the lands). It could be used with _l (lower), _i (intermediate)_, _h (high_ or _f_ (full).
* ***-G***: It is color of lands.
* ***-S***: It is color of water objects.
* ***-W***: It is proporties of pen that uses to draw coasts.
* ***-B***: It is the boundaries of map. In that example 2.5/2.5 latitude and longitude spacing are used and they are drawed with _g_ command.
* ***-B+t"text"***: It is used for giving a title of map.
* ***-N***: It is used for drawing political boundaries. It could be also used with other options. For example, _1_ for political boundaries, _2_ for state boundaries within the Americas, _3_ for marine boundaries, and _a_ for all boundaries.
* ***-I***: It is used for drawing rivers and has lots of properties. _a_ means all rivers and canals and _79/148/205_ is the RGB color code for rivers and canals.
* ***-Td***: It could be used for drawing shapes like north arrow in the map. First attributes are the location of shape, _+w_ for width of shape, _+f_ for orientations of shape, _+j_ for justification, _+l,,,,_ for label the cardinal points.

### Transversal Mercator (Gauss-Krüger) Projection

Transversal Mercator (Gauss-Krüger) Projection uses a cylinder that is horizontal and wrap earth with tangent to a meridian. That projection system is widely used by many countries such as Türkiye. The output coordinate system is describing as X-Y. As a result of the application of this projection, the world turns into 3 degree slices.

<p align = "center">
<img src=https://gisgeography.com/wp-content/uploads/2016/05/Universe-Transverse-Mercator-Cylinder.png height="300" alt="Transversal Mercator Projection">
</p>

In order to create a map with Mercator projection below code of GMT should be written.

```
#!/bin/bash

gmt begin transversal_mercator pdf

	gmt coast -R25/45/35/44 -Jt35/0.3i -Dh -Ggray -Slightblue -Wthinnest -B2.5g2.5 -B+t"Türkiye Map with Mercator Projection" -N1 -Ia/79/148/205 
	
gmt end show
```
Its output is in the below:

<p align = "center">
<img src="https://github.com/felsenfest7/GMT_Examples/assets/92101782/d79cbc92-78ea-4bb8-9fa5-8ba6d2f1308d" width="700" height=500" alt="Mercator Map">
</p>

In above code, the projection system is identified with _-Jt35/0.3i_. The _t_ describes the projection type, _35_ describes the central meridian in order to project the Earth and _0.3i_ is the scale.

### Universal Transversal Mercator (UTM) Projection

Universal Transversal Mercator also used a horizontal cylinder and that cylinder again tangent to a meridian. It is used in order to project the wider areas of Earth. THe output coordinate system is called as (Easting-Norting, in Turkish Sağa-Yukarı). As a result of the application of this projection, the world turns into 6 degree slices.

In order to create a map with Mercator projection below code of GMT should be written.

```
#!/bin/bash

gmt begin transversal_mercator pdf

	gmt coast -R25/45/35/44 -Ju35/0.3i -Dh -Ggray -Slightblue -Wthinnest -B2.5g2.5 -B+t"Türkiye Map with Mercator Projection" -N1 -Ia/79/148/205 
	
gmt end show
```

Its output is in the below:

<p align = "center">
<img src="https://github.com/felsenfest7/GMT_Examples/assets/92101782/4faa8aae-3235-4893-9b6d-e24183d88665" width="700" height=500" alt="Mercator Map">
</p>
