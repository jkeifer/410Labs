Lab 3: Editing attributes and geometries with arcpy
===================================================
for GEOG 410/510 winter term 2015


**Lab 3 Overview**

Lab 3 is all about working with cursors and geometry objects.
The data for this lab comes from two sources: the centroid points
created from Lab 2 (but use the version in data.gdb in the data
folder to ensure you have the correct data), and a text file of
Lat/Long coordinates in the WGS84 GCS.

Your job is to update the attributes of the centroids using an update
cursor for some given conditions. Once that is complete, you can filter
the centroid points as specified. Using the filtered points, you will
build a line geometry by finding the nearest points and connecting them.

Once the line is completed, you'll need to import the Lat/Lot coordinates
in the text file as point objects, then see which of the points are within
1 mile of the line object you created. The script will output the coordinates
of each point on a separate line, also indicating whether the points is within
the given distance of the line.

**Updating the Centroid Attributes**

You must use a cursor to update the attributes of the points in
the centroids feature class. But first, you will need to add a new
nullable text field to the feature class.

The new field is what you will update depending on the following conditions:

- If the OID is divisible by 31,
  write `Fizz` to the new field

- If the OID is divisible by 33,
  write `Buzz` to the new field

- If the OID is divisible by 31 AND 33,
  write `FizzBuzz` to the new field

- If none of the above condition have been met,
  choose a random integer between 0 and 99.
  If that integer is equal to 57,
  write `BuzzFizz` to the new field


**Filtering the Centroid Points**

Once you have updated the attributes of the centroid features,
filter them by keeping all points that are not null in the field
you added. That is, if the added field of a point contains
`Fizz`, `Buzz`, `FizzBuzz`, or `BuzzFizz`, then select that point.
Please have your script print the number of points after filtering,
and record that number. Then, add that number as a comment in your
script's intro comment block so I can see it when grading, formatted
something like this:

    # Filtered point count: <the count>

**Build a Line**

Using the selected point features above, create a polyline geometry
object. The line you create should connect each point to the nearest
point, never reusing a point. If two or more points are the same
distance apart, you can choose which to use. Start your line
with the northern-most point (measured using the CRS of the centroids FC).

Remember that point geometry objects have methods that may prove useful.
You must use geometry objects for this task.
Do not use any toolbox tools that might do something similar.

Once you have constructed your line object, use `CopyFeatures_management()`
to output your line as a feature class in data.gdb. Additionally,
have your script print the length of your line; record this length
and add it at the top of your script in the intro comments like:

    # Line length: <your line's length>


**Import the Text Point Features**

Each point stored in the text file has its ID, Longitude,
and Latitude, separated by a comma:

    1,-132.5544,43.2556

Import these coordinates as point geometry obejcts (remember they are WGS84).
See which fall within 1 Mile of the constructed polyline object.
Your script should produce a new text file reporting the results.
For each point, the script should create a new line in the text file with the
ID of the point and an indication of whether or not it falls within the given
distance, like so:

    1 True (or False)

You may not use any toolbox tools, such as `Buffer_analysis`,
to accomplish this task.


**Tips and Hints**

- There are many ways to accomplish these tasks.
  Some are better than others,
  but as long as your code is readable and understandable,
  any way that works is sufficient.

- Check out the `random` module for choosing a random integer.

- Your only output should be a copy of your line and the text report;
  the centroid feature class should be modified in place.

- Geometry objects have methods.

- When importing the points from the text file, ensure the coordinates
  are in the correct order, i.e., (x, y).

- A dictionary may be useful when importing the text file points.

- Recursion may be a useful approach to building the line.

- Follow the code guideline for the course.


**What to submit**

For this lab you must submit your completed .py file, your data.gdb, and your output report.
See the general lab instructions (README in the 410Labs repo) for submission instructions.


**Lab Grading**

This lab is worth a total of
32 points.
Following the grading breakdown outlined in the code guidelines for the course,
comments, format/style/readability, variable names, and the user interface are
each worth 12.5 percent of the points. Proper programming structures and logic
are worth 25 percent of the total. Meeting the assignment
requirements outlined above is worth an additional 25 percent.

Code that does not make a reasonable attempt to address
any part of the requirements above will get an automatic 0.
