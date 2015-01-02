Lab 2: Basic arcpy operations and vector analysis
=================================================
for GEOG 410/510 winter term 2015


**Overview**

Lab 2 consists of two parts, and each part requires a separate script.
The overall goal of this lab is to import some existing data layers in shapefile
and .img raster file formats from the Data folder into a geodatabase (Part 1),
and to use the geodatabase feature class layers for a short analysis (Part 2).


**Part 1: Importer Script**

The importer should create a file geodatabase, and import the shapefiles and
raster files in the Data folder into the new geodatabase. The raster files should
be moved into a feature dataset named "Rasters", and should have the spatial
reference ___________.
If the importer fails to import a file for some reason, the script should not
fail, but should continue after reporting the error to the user in a useful manner.


**Part 2: Analysis Script**

The analysis script will use the feature classes imported into the geodatabase
created in Part 1, but should be implemented in such a way that changing the
analysis geodatabase is trivial (e.g. use a constant). The analysis should perform
the following steps:

1. Check to ensure the analysis geodatabase has the required layers:
    - at least one point layer
    - at least one line layer
    - a layer named "study_area"

2. Buffer each point layer in the geodatabase.
   Only features in a layer with the field "buff_enabled" set to "True" should be buffered.
   The buffer distance should be set using the values in the "buff_dist" field.

3. Merge all buffer polygon layers into a single polygon layer. It does not matter
   if the features are dissolved into a single feature, or remain separated.

4. Buffer each point layer in the geodatabase.
   Only buffer lines greater than 250 feet in length that also fall within
   the polygons in the "study_area" feature class.
   The buffer distance should be 1,000 feet, and should be on both sides of the lines,
   and should cap the ends of the lines.

5. The buffer layers from the line features should be merged into a single feature
   class. The features should not be dissolved together, but should remain separate.

6. Erase the merged point buffers layer from the merged line buffers layer.

7. Create a fishnet grid with a 200-foot by 200-foot cell size.
   Intersect the grid with the erase results, and find the centroids of the
   resulting polygons. Report the number of centroids to the user.

The script should output two and only two feature classes to the analysis geodatabase:

- The results of the erase operation from step 6

- The centroid feature class from step 7


**Tips and Hints

- Don't forget a try/except in part 1

- Make good use of the ArcGIS `in_memory` workspace for intermediate files

- Feature layers are required for some selection tools in arcpy


**What to submit**

You need only submit your completed .py files. See the general lab instructions
(README in the 410Labs repo) for submission instructions.


**Lab Grading**

This lab is worth a total of 23 points. Following the grading breakdown outlined
in the code guidelines for the course, comments, format/style/readability,
variable names, and the user interface are each worth up to 3 points. Proper
programming structures and logic are worth up to 5 points. Meeting the assignment
requirements outlined above is worth an additional
6 points (2 points Part 1, 4 points Part 2).

Failure to make a reasonable attempt to complete one of the parts of the lab  will result
in an automatic loss of all points for that part (Part 1: 10.5 points, Part 2: 12.5 points).
Code that does not make a reasonable attempt to address any part of the lab will get an automatic 0.
