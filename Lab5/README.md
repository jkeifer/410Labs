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
   `store` field, are in Arizona to a shapefile with the
   WGS 1984 GCS (EPSG 4326). Include all attributes.

2. Open the created shapefile again and find the extent of 
   the points in the file. Create a new shapefile that is
   polygon type and write that extent polygon to the new
   shapefile. Include a field called `AREA_MI22` and write the
   area of the extent to that field **in square miles**.
   Use the NAD 83 Albers US CRS for this polygon file (EPSG 5070).

3. Look at the results in ArcMap. Add the extent polygon to the map
   doc first, to use its CRS. What problems do you notice? What do you
   think are the reasons for these problems? Please answer this
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

- OGR has a function to create a geometry from JSON. However,
  this function assumes all strings will be in native python
  byte encoding, not unicode encoding. Unfortuately, it is commom
  to get unicode strings when reading JSON from a file. You
  can try to play around with the json module arguments for
  its load function to see if you can get non-unicode strings
  so you can use the CreateGeometryFromJSON function in OGR if
  you are feeling adventurous. The easy approach would be to get
  the coords from the dictionary yourself, and pass those in as the
  two required arguments to the AddPoint method on an OGR point
  geometry object.

- I am requiring you to "re-open" the shapefile created in step
  1 for step 2. You would not need to do this to get the
  extent of the points in the file, as you should have the points
  without open the file (after all, how did you create it?).
  However, opening a shapefile in OGR is important to know,
  so I am requiring you to do it.

- OGR refers to extent as envelope. The function to get this
  requires a geometry collection. The function will return a
  tuple of four values, like this: `(xmin, xmax, ymin, ymax)`.
  You should be able to create a polygon geometry from these
  points, but remember to make a ring to add the polygon object.

- Be sure to transform the extent geometry before calculating
  the area or writing it to the polygon shapefile.

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
