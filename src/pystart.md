# Python Review
Professor Ron Smith  
Data Science Program  
William & Mary  

## Some basic operations  

First lets do some basic operations in Python.  See if you can execute the following tasks.

- add 1 + 1
- print 'Hello World!'
- create a variable x that is equal to 1
- create a variable x that is equal to x + 1

Logical operators can be important when working with data that requires us to assess logical comparisons, such as equality, greater than or less than.  Logical operators can be used to find specific data we are looking for, or perhaps to filter out rows of data that we may need.

## Practicing with logical operators

Now let's practice comparing values using some of the logical operators available in Python.

- write a logical operation that compares the sum of 1 + 1 with the numerical value 2
- compare the character values of the words 'cat' and 'dog'
- write a logical expression that determines whether 4^6 is greater than 6^4
- write an inclusive "or" statement (use the pipe which is the **|** character as the "or" operator) evaluating both the character values of the words 'cat' and 'dog' AND whether 2 is greater than or less than 1 -- in this case either A or B, or both is true
- write an exclusive "or" statement evaluating both the character values of the words 'cat' and 'dog' AND whether 2 is greater than or less than 1 -- in this case either A or B, but not both is true

Next up is something you should definitely be aware of!  NaN ("not a number") **is not equal to itself**!  It is also the ONLY value for which this is the case!  This is important, because missing records in a data set are often treated as NaN, and you will sometimes need to be careful about how you handle them.  It may not happen very often, but it will happen eventually and can cause confusion if you're not aware of it.

Try assigning `float('nan')` to the variable `x` and then evaluating that same variable with itself in an equality statement (using the `==` logical operator).  Also try using the not equal logical operator (in this case !=) to evaluate `x` with itself. 

From the results of the logical comparison, you could conclude that x must be NaN.  This may show up at some time in the future, don't forget it!  There's also usually special operations for checking if something is NaN.  Use the `import()` to load the `math` library of functions into your PyCharm work session.  Now evaluate `x` with the command `math.isnan()`.  Also try running the same command from the `numpy` library by again first using the `import()` library command and then using the `isnan()` command.  To distinguish the two similarly named functions from the two different libraries, specify the library in the command itself `numpy.isnan()`.

### Evaluating Lists and Subscripting with an Index

If we attempt a similar approach where we evaluate each term in a list, we might not obtain the expected results.  For example try the following.

```python
y = [1,2,float('nan'),4,5,float('nan')]
y
```
First we could extract one of the values in the list by using a subscripting operator such as `y[2]`.  Notice that Python indexes values in a list starting with 0, thus the `2` will in essence retrieve the third value in the list.  Also, consider the evaluation of `y == y`, which is evaluating the equality of two lists rather than two float objects as in our previous example.  To isolate and evaluate individual values within the list we could evaluate each term as part of a loop, one by one.

```python
for yi in y:
    print(yi==yi)
```
To simplify the command in a single line of code, use "list comprehension" syntax.

```python
[yi==yi for yi in y]
```

An even simpler approach is to evaluate the list `y` using the `np.isnan()` command.

Last but not least, you might want to identify which values in a list match some criteria, and then perhaps remove or keep those elements from the list.  Let's suppose that we wanted to remove the NaN values from y.  To do this, first, identify the elements in the list that match your criteria by creating an object `idx` and then assigning the output from `y` using the `np.isnan()` command.  You can negate boolean values using the `~` preceding the object (in this case `idx`).

To isolate and drop our `Nan` values we start by assigning the output from `np.array(y)` command back to the `y` object and essentially writing over and replacing that object.  Now use the inverted values to retain those values that have true records in the list by subscripting the index like this `y[~idx]`.  Go ahead and assign those values to a new object named `y_filtered`.

### Using the pandas library and DataFrames

The first thing you'll usually do when writing Python code is to import any libraries that you'll need. When working with data files, the pandas library offers all sorts of convenient functionality.  You can also give the library a shorter name (alias) in the process using "as" like this `import pandas as pd`.

Next, let's get our file imported.  First, open up the file in the text editor and take a look at it.  You'll notice that there are tabs between each value in the file.  In other words, it's a tab-separated file.  We'll need to let pandas know this when we import it because, by default, it's going to assume a comma-separated file.

First, specify where the file is located by creating an object named `path_to_data` and then assign the path of your tab separated values file to that object.  If your `gapminder.tsv` file is in your project folder, then you only need to specify the name of the file itself.  Don't forget to nest the file name in `''` quotes.


To import the data use the `read_csv()` command from the pandas library of functions with the `path_to_data` object you already created.  In order to specify that command first use the library alias followed by the command itself, `pd.read_csv()`.  Assign the output from reading your `gapminder.tsv` file to a new object that is simply named `data`.  Finally, in order to inform Python that our data is in a tab separated format, we need to add an additional argument following the `path_to_data` object.  Use the `\t` specification in your argument to execute the command as follows.

```python
new_object = library_name.function_name(path_to_file_object, sep = '\t')
```

To interrogate the new data frame object we just created, you can start by simply typing `data` in the console.  You can also look at just the top, or just the bottom, using `data.head()` and `data.tail()`.  To further specify the number of lines from the data object you would like printed in the console add that number as a value within the `.head()` or `.tail()` command.  

You can check the number of rows and columns in your data frame with the `.shape` command or if you would like to have the number of total cells returned you can use `.size`.  If you would like to manually confirm the number of cells, you can subscript the first and second values from the shape of the data.  Keep in mind that the first value is in the 0 place while the second value is in the 1 place.

```python
data.shape[0]*data.shape[1]
```

To get a quick summary of the names of the columns, as well as what type of data use `data.info()` or if you just want a quick list of the column names use `data.columns`.  If you check the your `data.columns` output with the `type()` command, you will find that the columns themselves within your pandas data frame are an Index.  To return a list of just the column names, instead use `list(data.columns)`.  Using the `.describe()` command is a good way for Python to return descriptive statistics about your data frame.

## Subsetting our data frame


Let's extract all the data for Asia and store it in a new DataFrame

Oops!  Wrong column.  Good thing we checked.

What if we only wanted the data for the most recent year, from Asia?

You could, of course, have done that all in one step, but...

The error occurred because _____________.

Even though the results above are what we wanted, the logic we used is not equivalent to what we were originally trying to do.  For example, if there were no records for Asia for 2007, then we would have gotten back an empty DataFrame.

 So, here's a better way. First, I would write down what I want to do:



Goal: Specify a continent, and extract the most recent data from that continent

# Next, do one operation at a time to get to the desired result:


```


```python
# And if this was something I thought I would be using a lot, I might even write a function:

```


```python

```

Back to the original dataset - can we get a list of all the countries that exist in the data?


```python

```

How many countries are in that list?  It's a little long to count manually.


```python

```

What if we wanted to know how many records there are for each individual country?


```python

```

Is there a way to see the entire list?


```python

```

Can we sort the list by the country name?

Yes - but we need to understand what type of object we are working with first...


```python

```

This is a series object.  A Series is basically a column of a DataFrame, and just like a DataFrame, it is a special type of object that has all sorts of built-in functionality.

The column with the country names is the index of the Series.  Just like with DataFrames, the index is not an actual column.  If you want to sort by it, then you would need to use the sort_index() function.


```python

```

### Indexing DataFrames

There are several ways to extract individual rows from a DataFrame, usually you will be using .loc or .iloc.

Let's identify the record with the largest GDP per capita:


```python

```


```python

```


```python
# If this were an array, you might try this:

```

Instead, use .loc.  What we want to do here is extract the row with the label (index) 853.


```python

```

.iloc is a little different.  To see why, let's look at the Asia data:


```python

```


```python

```


```python

```

iloc is fetching the row by it's integer position, whereas loc is fetching the row by its label.  In this case, the first row of the data (starting counting at 0) has the label 11.

Sometimes, you might want to reset the index so that the rows are labeled sequentially again:


```python

```


```python

```


```python

```


```python

```

### Exercises

**1)** Get a list of all the years in this data, without any duplicates.  How many unique values are there, and what are they?


```python

```

**2)** What is the largest value for population (pop) in this data?  When and where did this occur?


```python

```


```python

```


```python

```

**3)** Extract all the records for Europe.  In 1952, which country had the smallest population, and what was the population in 2007?


```python

```


```python

```
