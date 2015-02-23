Lab 6: Raster operations with GDAL
==================================
for GEOG 410/510 winter term 2015


**Lab Overview**

Most of the functions need for this lab should be available
in Exercise 4, greatly simplfying the coding for this assignment.

The scenario for this lab is that you are working with a
government agency doing environmental sampling in a mountainous
region in Washington State. You already have three sampling
stations in your study area, but preliminary results are showing
that you need to add a fourth station in a specific elevation
band to capture different results.

Additionally, you need to ensure that the sampling site can
transmit its data back to your base of operations. Only one
of your current sample sites is at a high enough elevation
to make clear radio contact, so you must ensure that your
new sample station in at a location with clear visiblity
of the highest station, so you can use it as a relay for
the wireless data transmission.

From aerial imagery you were able to digitze five possible
sample sites located in areas clear of obstructions.
However, due to this method of site selection, you are unable
to know whether the sample site candidates are within
the required elevation range or have clear line of sight
to the main station without further GIS analysis.

Thus, you need to write a script using GDAL to perform the
required analysis. You have already generated a raster with
values corresponding to the visibility of each of your
existing sample stations, you have a raster of elevation
in the area, and you have your possible sample site points
in a shapefile. Your script will need to open these three
data sources, find the areas that are both within the
viewshed of your main station and the required elevation
range, then check whether or not each point is within a
suitable area, printing the results to the screen or
optionally to a text file (if printing to the screen,
please include the results as a comment at the top of
your script).


**Analysis Specifics**

The visibilty raster is not just a viewshed. It is a
raster representing the combined station visibilty of
each cell. More specifically:

- A cell of value 0 is has no visible stations
- A cell of value 1 can see station 1 only
- A cell of value 2 can see station 2 only
- A cell of value 3 can see station 1 and 2 but not 3
- A cell of value 4 can see station 3 only
- A cell of value 5 can see station 1 and 3 but not 2
- A cell of value 6 can see station 2 and 3 but not 1
- A cell of value 7 can see all three stations

For the purposes of this analysis, you will accept all cells
that can see station 2 as suitable. Therefore you need to
find all cells with a value of 2, 3, 6, or 7.

Acceptable elevations are between 1000 and 1400 meters, inclusive.


**Tips and Hints**

- Your output report printed to the screen or a text file
  needs to be something like `<point_id> <suitable_or_not>`.
  For example, for the point of ID 1 you could print
  `1 True`.

- Read in your rasters as arrays. As your elevation and visibility
  rasters are registered with one another and have the same
  dimensions, numpy array operations will allow you to perform the
  required overlay analysis using a similar syntax to arcpy map
  algebra.

- Take liberally from Exercise 4 and any other helpful sources,
  but be sure any borrowed code is well-documented and your
  sources are cited.

- Include some means of parsing arguments from the command line
  adequate to run this analysis for up to 5 points extra credit.

- Follow the code guideline for the course.


**What to submit**

For this lab you must submit your completed .py file (and your text report, if created).
See the general lab instructions (README in the 410Labs repo) for submission instructions.


**Lab Grading**

This lab is worth a total of
15 points (plus an additional 5 points of possible extra credit).
Following the grading breakdown outlined in the code guidelines for the course,
comments, format/style/readability, variable names, and the user interface are
each worth 12.5 percent of the points. Proper programming structures and logic
are worth 25 percent of the total. Meeting the assignment
requirements outlined above is worth an additional 25 percent.

Code that does not make a reasonable attempt to address
any part of the requirements above will get an automatic 0.
