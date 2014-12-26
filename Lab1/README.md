Lab 1: General File Operations
==============================
for GEOG 410/510 winter term 2015


**Lab Overview**

Inside the Lab1 directory is a folder named data containing a number of files.
Some of the files are shapefiles (made up of several files of the same name with different extensions),
some are rasters of format .img (again, with multiple files), some are tables in .dbf and .csv format,
and some are .txt files with text.

The assignment consists of two parts:

1) Create three directories within the data folder, named shapefiles, rasters, and tables.
Move all the shapefiles, rasters, and tables in the data directory into the respective
subfolder you have created. You should not use any GIS libraies to find or move these files
(i.e., don't use arcpy or anything like it).

2) The .txt files in the data directory are composed of multiple lines of data which needs to be concatenated in order. The first data line in a file will be a number. All following data lines will be strings, and should be concatenated in order, with a space as a separator. Some lines in the file may be comments, and marked as such by beginning with a double backslash (//). You will need to open each of the files and read the lines, filtering out any comment lines. Again, the first non-comment line is a number. This number indicates the order of the data in the file, and the number should not be concatenated with the string data. That is, the data in a file with the number 1 comes before the data in the file with the number 2, and the data from the file with 3 would follow both of these. Concatentate each of the file strings in order, separated by a space character, and print that string.

Here is an example of two .txt files, and what would be output from these files:

> .txt file 1:

> ```
// this is a text file
// lines like these are comments
2
// the number above is the order of the data when concatenated
once. And then he jumped into the air,
falling into
the darkness.
// yet another comment
```

> .txt file 2:

> ```
1
I saw Batman
// comment
on a roof
```

> What would be output from these two files:

> ```
I saw Batman on a roof once. And then he jumped into the air, falling into the darkness.
```

**Tips and Hints**

- Don't reinvent the wheel: standard library modules have functions that will help you.

- Shapefiles and .img raster files are made up of multiple files of the same name. Be sure to move ALL the files corresponding to the .shp or .img files.

- Be sure to safely close the text files.
