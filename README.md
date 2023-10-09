# GMT BASICS FOR GEOMATICS ENGINEERING

Generic Mapping Tools (GMT) is open-source software that provides command-line tools for working with geographic and cartesian data. It offers features like data manipulation, map projection support, data visualization, and the creation of high-quality maps and illustrations. GMT includes geospatial data, supports various map projections, and allows for customization. It is widely used in scientific and geographic applications.

<p align = "center">
<img src="https://www.generic-mapping-tools.org/_static/gmt-logo.png" width="500" height="300">
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






