Lab 4: Raster analysis with arcpy
=================================
for GEOG 410/510 winter term 2015

**Lab 4 Overview**

Imagine you are a GIS professional working for
Mountain Man Housing Intl, LLC. In a typical day you respond
to many requests from mountain men around the country looking
for suitable locations for thier mountain shacks. Currently, you
complete all of the required analysis manually, but given some
recent python classes you believe a python script could
automate many of the standard requests you encounter from your
mountain man clients.

In thinking through the design of such a python script, your first
thought is that it would be good to organize your data in a file
geodatabase. Normally you find all the data sources required for an
analysis, and drop them in a folder in shapefile and .img formats.
Thus, you recognize you will need to write a script to import all
the data files for each analysis in to a geodatabase.

Once you have a database with all the analysis layers, you can
run your suitability analysis. As this is a first pass, you
recognize that it would be best to keep the analysis simple,
covering the most basic requests you get, reserving more advanced
approaches for future updates.

To that end, you compile a list of things your basic clients request:

- Proximity to water: even mountain men need to hydrate
  (but not bathe, oh no).

- Elevation range: some mountain men are more mountain than others.

- Slope: a mountain man isn't a mountain man if his shack slides
  off the mountain into a valley.

- Soil: the required soil types will depend on the dietary needs
  of the mountain man and what he will want to grow.

Lastly, the area of the combination of all these factors must meet
the size of shack and garden the mountain man is seeking to find.


**A Less-Silly Look at Part 1: Importing the Data (5 Points)**

The requirements for the importer script are as below:

> The importer should create a file geodatabase in the output folder,
> and import the shapefiles and raster files in the data folder into the new geodatabase.
> If the importer fails to import a file for some reason, the script should not
> fail, but should continue after reporting the error to the user in a useful manner.

You should recognize that these requirements are copied
verbatim from the importer instructions from Lab 2.
Therefore, you should be able simple use your code from Lab 2,
assuming it works correctly.


**A Less-Silly Look at Part 2: Shack Site Selection (25 Points)**

In the Lab Overview we identified five criteria that are common
to basic mountain man shack site selection: distance to water,
elevation, slope, soil, and the area of a plot of land meeting
these requriements. Because each mountain man has different
requirements, you will need to develop a script that can perform
this analysis given different critera without requiring the user
to edit any code. That is, your script must take these five
critera as arguments. More specifically, your script will have
the following arguments:

- Analysis geodatabase path: the file path to the geodatabase;
  required

- Distance to water: integer representing the maximum allowable
  distance from a water source; required

- Elevation minimum: integer representing the minimum elevation
  to consider; optional

- Elevation maximum: integer representing the maximum elevation
  to consider; optional

- Slope: float of the highest allowable slope in degrees;
  optional, default is 4.5

- Soil: each soil type is represented by an integer code in the
  soil raster data, and it is important to note that multiple
  types of soils all be adaquate; this argument should be an
  integer representing an allowable soil code in the soil raster;
  this argument is required, and should allow multiple values

- Area: a float representing the minimum size of a parcel meeting
  the above requirements; required

The data in your geodatabase can be assumed to always have the same
names (i.e., make the required layer names constants). Your analysis
should, after getting the user arguments, check to make sure the
specified geodatabase exists and has all the required layers (unlike
Lab 2, no need to check FCs by type, simply if each of the required
FCs exists). If there is an error, a useful message should be presented
to the user, and the script should exit.

After validating all the required layers are present, the script should
proceed with the analysis, finding any areas that meet all of the
requirements. For the purpose of this assignment, you should use the
following values to produce the final output:

- Max water distance:

- Minimum elevation:

- Maximum elevation:

- Maximum slope:

- Suitable soil types: 1, 4 and 5

- Minimum site area:

The final output of the script should be a feature class
containing polygons of all suitable areas. All intermediate layers should
be considered temporary and should not persist after the completion of
the script.

You will also need to make a map of the resultant suitable area,
including the relevant layers that contributed to the analysis:
elevation (DEM; can be hillshade if desired), water sources,
and soil (try transparency on top of the elevation layer). Follow
good cartographic principles. Produce the map in PDF format for
your submission.


**Tips and Hints**

- Your Lab 2 importer *should* have handled import errors elegantly,
  such that program execution would not be interrupted. However,
  the Lab 2 data did not actually have any problems. This lab
  *will* have an error that you will need to ensure your importer
  handles correctly.

- The argparse module will allow effective and easy parsing of
  the user's command line arguments, including allowing defaults,
  type checking, optional arguments, and multiple values.

- If you are unsure how to approach building a query from a list
  of unknown length, perhaps check the example in Demo 1...

- The only output of your final script should be your suitable
  area feature class. All other layers/datasets produced during
  your analysis should exist only in memory.

- Follow the code guideline for the course.


**What to submit**

For this lab you must submit your
completed .py files
a map of your suitable site (following good cartographic principles)
in a zip folder named <lastname><firstname>_lab4.zip.
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
