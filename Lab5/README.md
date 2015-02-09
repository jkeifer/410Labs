Lab 5: Vector operations with OGR
=================================
for GEOG 410/510 winter term 2015


**Lab Overview**

This lab is about getting experience with ORG vector fucntions
and data stored in the geojson format. Provided is a geojson
file in the data directory. The file contains some 15,155 points
distributed across the US and Canada.

The task for this lab is much simpler than in labs past,
due to the greater difficulty of using OGR over arcpy.
What is required is simply this:

1. Copy all points in the geojson file that, according to the
   `store` field are in Arizona, to a shapefile with the
   WGS 1984 GCS (WKID 4326). Include all attributes.

2. Open the created shapefile again and find the extent of 
   the points in the file. Create a new shapefile that is
   polygon type and write that extent polygon to the new
   shapefile. Use the USA Contiguous Albers Equal Area
   Conic USGS version CRS for the output CRS. (To find the
   definition of this CRS, please search the internet for
   SR-ORG 6703, find the page on spatialreference.org, and
   get the OGC WKT string.)

3. Look at the results. What is the problem? Please answer this
   question briefly in the comments at the beginning of your
   .py file. (Natural Earth polygons for North American admin
   boundaries level 1 (states and provinces) are included in the
   data directory to facilitate your visaul analysis of the results.)


**Tips and Hints**

- Use the `json` module to load the data in the geojson file.
  Remember that json data loads in a form that works just
  like a python dictionary. Also, note that the geojson file
  provided is of type FeatureCollection, so to get the
  individual features you will need to look at the
  `features` key (hint: features, being plural, holds a list,
  and each element in the list is a geojson feature of type point).

- Selecting the points in AZ does not require OGR, just some
  good dictionary/for loop/string comparison skills (do take
  a look at the contents of the `store` attributes to ascertain
  the pattern that will allow this selection).

- You can import a WKT projection string using the
  `ImportFromWKT(wkt_string)` method of an
  osr.spatialReference instance.

- Be sure to transform the extent geometry before writing it
  to the polygon shapefile.

- Don't forget to write a .prj file to go with any created
  shapefiles, containing the WKT of the spatial reference of
  the shapefile geometry.

- Follow the code guideline for the course.


**What to submit**

For this lab you must submit your completed .py file.
See the general lab instructions (README in the 410Labs repo) for submission instructions.


**Lab Grading**

This lab is worth a total of
30 points.
Following the grading breakdown outlined in the code guidelines for the course,
comments, format/style/readability, variable names, and the user interface are
each worth 12.5 percent of the points. Proper programming structures and logic
are worth 25 percent of the total. Meeting the assignment
requirements outlined above is worth an additional 25 percent.

Code that does not make a reasonable attempt to address
any part of the requirements above will get an automatic 0.
