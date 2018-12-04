
.. raw:: html

   <div class="alert alert-block alert-info" style="margin-top: 20px">

.. raw:: html

   <h1 align="center">

 Link

.. raw:: html

   </h1>

.. raw:: html

   <h1 align="center">

Data Analysis with Python

.. raw:: html

   </h1>

Module 1 Introduction
=====================

Welcome!
~~~~~~~~

In this section you will learn how to approach data acquisition in
various ways, and obtain necessary insights from a dataset. By the end
of this lab, you will successfully load the data into Jupyter Notebook,
and gain some fundamental insights via Pandas Library.

Table of contents
-----------------

.. raw:: html

   <div class="alert alert-block alert-info" style="margin-top: 20px">

.. raw:: html

   <li>

Data Acquisition

.. raw:: html

   <li>

Basic Insight of Dataset

.. raw:: html

   </li>

.. raw:: html

   <p>

.. raw:: html

   </p>

Estimated Time Needed: 10 min

.. raw:: html

   </div>

.. raw:: html

   <hr>

 # Data Acquisition There are various formats for a dataset, .csv,
.json, .xlsx etc. The dataset can be stored in different places, on your
local, machine or sometimes online. In this section, you will learn how
to load a dataset into our Jupyter Notebook. In our case, the Automobile
Dataset is an online source, and it is in CSV (comma separated value)
format. Let's use this dataset as an example to practice data reading.
Data source:
https://archive.ics.uci.edu/ml/machine-learning-databases/autos/imports-85.data
data type: csv The Pandas Library is a useful tool that enables us to
read various datasets into a data frame. Our Jupyter notebook platforms
have a built-in **Pandas Library** so that all we need to do is import
Pandas without installing.

.. code:: python

    # import pandas library
    import pandas as pd

Read Data
---------

We use **"pandas.read\_csv()"** function to read the csv file. In the
bracket, we put the file path along with a quotation mark, so that
pandas will read the file into a data frame from that address. The file
path can be either a URL or your local file address. Because the data
does not include headers, we can add an argument **" header = None"**
inside the **"read\_csv()"** method, so that pandas will not
automatically set the first row as a header. You can also assign the
dataset to any variable you create.

.. code:: python

    # import pandas library
    import pandas as pd
    # read the online file by the URL provides above, and assign it to variable "df"
    path="https://archive.ics.uci.edu/ml/machine-learning-databases/autos/imports-85.data"
    
    df = pd.read_csv(path,header=None)
    print("Done")

After reading the dataset, we can use the **``dataframe.head(n)``**
method to check the top 'n' rows of the dataframe, where n is an
integer. Contrary to **``dataframe.head(n)``**,
**``dataframe.tail(n)``** will show you the bottom n rows of the
dataframe.

.. code:: python

    # show the first 5 rows using dataframe.head() method
    df.head(5)

.. raw:: html

   <div class="alert alert-danger alertdanger" style="margin-top: 20px">

.. raw:: html

   <h1>

Question #1:

.. raw:: html

   </h1>

Check the bottom 10 rows of data frame "df":

.. raw:: html

   </div>


.. raw:: html

   <div class="alert alert-danger alertdanger" style="margin-top: 20px">

.. raw:: html

   <h1>

Question #1 Answer:

.. raw:: html

   </h1>

Run the code below! Did you get the right code?

.. raw:: html

   </div>

.. raw:: html

   <div align="right">

Click here for the solution

.. raw:: html

   </div>

.. raw:: html

   <div id="q2" class="collapse">

::

    df.tail(10)

.. raw:: html

   </div>

Add Headers
-----------

Take a look at our dataset; pandas automatically set the header by an
integer from 0.

.. raw:: html

   <div>

To better describe our data we can introduce a header. This information
is available at: https://archive.ics.uci.edu/ml/datasets/Automobile

.. raw:: html

   </div>

.. raw:: html

   <p>

.. raw:: html

   </p>

.. raw:: html

   <div>

Thus, we have to add headers manually.

.. raw:: html

   </div>

.. raw:: html

   <div>

Firstly, we create a list "headers" that includes all column names in
order.

.. raw:: html

   </div>

.. raw:: html

   <div>

Then, we use **``dataframe.columns = headers``** to replace the headers
by the list we created.

.. raw:: html

   </div>

.. code:: python

    # create headers list
    headers = ["symboling","normalized-losses","make","fuel-type","aspiration", "num-of-doors","body-style",
             "drive-wheels","engine-location","wheel-base", "length","width","height","curb-weight","engine-type",
             "num-of-cylinders", "engine-size","fuel-system","bore","stroke","compression-ratio","horsepower",
             "peak-rpm","city-mpg","highway-mpg","price"]
    headers

We replace headers and recheck our data frame:

.. code:: python

    df.columns = headers
    df.head(10)

We can drop missing values along the column "price" as follows:

.. code:: python

    df.dropna(subset=["price"], axis=0)

Now, we have successfully read the raw dataset and add the correct
headers into the data frame.

.. raw:: html

   <div class="alert alert-danger alertdanger" style="margin-top: 20px">

.. raw:: html

   <h1>

Question #2:

.. raw:: html

   </h1>

Find the name of the columns of the dataframe:

.. raw:: html

   </div>


.. raw:: html

   <div align="right">

Click here for the solution

.. raw:: html

   </div>

.. raw:: html

   <div id="q3" class="collapse">

::

    df.columns

.. raw:: html

   </div>

Save Dataset
------------

Correspondingly, Pandas enables us to save the dataset to csv by using
the **``dataframe.to_csv()``** method. You can add the file path and
name along with quotation marks in the brackets.

For example, if you would save the dataframe "df" as "automobile.csv" to
your local machine, you may use the syntax below:
:sub:`:sub:`:sub:`:sub:` df.to\_csv("automobile.csv") ````

We can also read and save other file formats, and we can use similar
functions to **``pd.read_csv()``** and **``df.to_csv()``** for other
data formats. The functions are listed in the following table:

Read/Save Other Data Formats
----------------------------

+----------------+-----------------------+---------------------+
| Data Formate   | Read                  | Save                |
+================+=======================+=====================+
| csv            | ``pd.read_csv()``     | ``df.to_csv()``     |
+----------------+-----------------------+---------------------+
| json           | ``pd.read_json()``    | ``df.to_json()``    |
+----------------+-----------------------+---------------------+
| excel          | ``pd.read_excel()``   | ``df.to_excel()``   |
+----------------+-----------------------+---------------------+
| hdf            | ``pd.read_hdf()``     | ``df.to_hdf()``     |
+----------------+-----------------------+---------------------+
| sql            | ``pd.read_sql()``     | ``df.to_sql()``     |
+----------------+-----------------------+---------------------+
| ...            | ...                   | ...                 |
+----------------+-----------------------+---------------------+

 # Basic Insight of Dataset After reading data into Pandas dataframe, it
is time for us to explore the dataset. There are several ways to obtain
essential insights of the data to help us better understand our dataset.

Data Types
----------

Data has a variety of types. The main types stored in Pandas dataframes
are ``object``, ``float``, ``int``, ``bool``, and ``datetime64``. In
order to better learn about each attribute, it is always good for us to
know the data type of each column. In Pandas: :sub:`:sub:`:sub:`:sub:`
dataframe.dtypes ```` Returns a Series with the data type of each
column.

.. code:: python

    # check the data type of data frame "df" by .dtypes
    df.dtypes

As a result, as shown above, it is clear to see that the data type of
"symboling" and "curb-weight" are ``int64``, "normalized-losses" is
``object``, and "wheel-base" is ``float64``, etc. These data types can
be changed, and we will learn how to accomplish this in a later module.

Describe
--------

If we would like to get a statistical summary of each column, such as
count, column mean value, column standard deviation, etc, then we use
the describe method: :sub:`:sub:`:sub:`:sub:` dataframe.describe() ````
This method will provide various summary statistics, excluding ``NaN``
(Not a Number) values:

.. code:: python

    df.describe()

This shows the statistical summary of all numeric-typed (int, float)
columns. For example, the attribute "symboling" has 205 counts, the mean
value of this column is 0.83, the standard deviation is 1.25, the
minimum value is -2, the 25th percentile is 0, 50th percentile is 1,
75th percentile is 2, and the maximum value is 3.

However, what if we would also like to check all the columns including
those that are of type object?

You can add an argument ``include = "all"`` inside the bracket. Let's
try it again:

.. code:: python

    # describe all the columns in "df" 
    df.describe(include = "all")

Now it provides the statistical summary of all the columns, including
object-typed attributes. We can now see how many unique values there
are, (top row), and the frequency of the top value in the third row.
Some values in the table above show as "NaN", this is because those
numbers are not available regarding a particular column type.

.. raw:: html

   <div class="alert alert-danger alertdanger" style="margin-top: 20px">

.. raw:: html

   <h1>

Question #3:

.. raw:: html

   </h1>

.. raw:: html

   <p>

You can select the columns of a data frame by indicating the name of
each column. For example, you can select the three columns as follows:

.. raw:: html

   </p>

.. raw:: html

   <p>

.. raw:: html

   </p>

.. raw:: html

   <p>

dataframe[[' column 1 ',column 2', 'column 3'] ]

.. raw:: html

   </p>

.. raw:: html

   <p>

.. raw:: html

   </p>

.. raw:: html

   <p>

Where "column" is the name of the column, you can apply the method
".describe()" to get the statistics of those columns as follows:

.. raw:: html

   </p>

.. raw:: html

   <p>

.. raw:: html

   </p>

.. raw:: html

   <p>

dataframe[[' column 1 ',column 2', 'column 3'] ].describe()

.. raw:: html

   </p>

.. raw:: html

   <p>

.. raw:: html

   </p>

Apply the method to ".describe()" to the columns 'length' and
'compression-ratio'.

.. raw:: html

   </div>

.. raw:: html

   <div align="right">

Click here for the solution

.. raw:: html

   </div>

.. raw:: html

   <div id="q4" class="collapse">

::

     df[['length','compression-ratio']].describe()

.. raw:: html

   </div>

Info
----

Another method you can use to check your dataset is:
:sub:`:sub:`:sub:`:sub:` dataframe.info ```` It provides a concise
summary of your DataFrame.

.. code:: python

    # look at the info of "df"
    df.info

Here we are able to see the information of our dataframe, with the top
30 rows and the bottom 30 rows.

It also shows us the whole data frame has 205 rows and 26 columns in
total.

you can also use the method info as follows

.. code:: python

    df.info()

Excellent! You have just completed the Introduction Notebook!
=============================================================

About the Authors:
~~~~~~~~~~~~~~~~~~

This notebook was written by `Mahdi Noorian
PhD <https://www.linkedin.com/in/mahdi-noorian-58219234/>`__ ,\ `Joseph
Santarcangelo PhD <https://www.linkedin.com/in/joseph-s-50398b136/>`__,
Bahare Talayian, Eric Xiao, Steven Dong, Parizad , Hima Vsudevan and
`Fiorella Wenver <https://www.linkedin.com/in/fiorellawever/>`__.

Copyright © 2017
`cognitiveclass.ai <cognitiveclass.ai?utm_source=bducopyrightlink&utm_medium=dswb&utm_campaign=bdu>`__.
This notebook and its source code are released under the terms of the
`MIT License <https://bigdatauniversity.com/mit-license/>`__.

.. raw:: html

   <div class="alert alert-block alert-info" style="margin-top: 20px">

.. raw:: html

   <h1 align="center">

 Link

.. raw:: html

   </h1>

