Lab 3: Editing attributes and geometries with arcpy
===================================================
for GEOG 410/510 winter term 2015


**Lab 3 Overview**

Lab 3 is all about working with cursors and geometry objects.
The data for this lab comes from two sources: the centroid points
created from Lab 2 (but use the version in the Data folder to
ensure you have the correct data), and a text file of Lat/Long
coordinates in the WGS84 GCS.

Your job is to update the attributes of the centroids using an update
cursor for some given conditions. Once that is complete, you can filter
the centroid points as specified. Using the filtered points, you will
build a line geometry by finding the nearest points and conencting them.

Once the line is completed, you'll need to import the Lat/Lot coordinates
in the text file as point objects, then see which of the points are within
100 feet of the line object you created. The script will output the coordinates
of each point on a separate line, also indicating whether the points is within
the given distance of the line.

**Updating the Centroid Attributes**

You must use a cursor to update the attributes of the points in
the centroids feature class. But first, you will need to add a new
nullable text field to the feature class.

The new field is what you will update depending on the following conditions:

- If the OID is divisible by 3, write `Fizz` to the new field

- If the OID is divisible by 5, write `Buzz` to the new field

- If the OID is divisible by 3 AND 5, write `FizzBuzz` to the new field

- If none of the above condition have been met, but the _____________________, write `BuzzFizz` to the new field


**Filtering the Centroid Points**

Once you have updated the attributes of the centroid features,
filter them by keeping all points that are not null in the field
you added. That is, if the added field of a point contains
`Fizz`, `Buzz`, `FizzBuzz`, or `BuzzFizz`, then select that point.


**Build a line**

Using the selected point features above, create a polyline geometry object.
Perhaps a dict of point geometry objects would be good for this
exercise...Remember that point geometry objects have methods that
may prove useful.


**Import the Text Point Features**

The points stored in the text file are in Lat/Long format, separated by a space:

    43.5667 -132.5544

Import these coordinates as point geometry obejcts (remember they are WGS84).
See which fall within 100 feet of the constructed polyline object.
For each point, the script should output its coordinates and whether it is
within the given distance, like so:

    Lat: 43.5667, Long: -132.5544, Within Specified Distance: True (or False)


**Tips and Hints**

- There are many ways to accomplish these tasks.
  Some are better than others,
  but as long as your code is readable and understandable,
  any way that works is sufficient.

- You do not need to output any feature classes; you only need to modify the centroid feature class.

- Geometry objects have methods.

- Follow the code guideline for the course.


**What to submit**

You need only submit your completed .py file.
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
