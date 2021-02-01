# Python Review
Professor Ron Smith  
Data Science Program  
William & Mary

0. Do some basic operations in Python
1. Import a data file
2. Do some basic processing with the file
3. Main goal: Be comfortable working with data using the pandas library


```python

```


```python

```


```python

```


```python

```

### Logical Operators

Working with data can often require making logical comparisons, either to find specific data we are looking for, or to 
filter out rows of data, etc.  


```python

```


```python

```

Which is greater, $4^6$ or $6^4$? _(BTW - don't forget that exponentiation in Python is different than some other languages)_


```python

```

AND: Both A and B are true.


```python

```

Inclusive OR:  Either A or B, or both, is true.


```python

```

Exclusive OR (XOR).  Either A or B, but not both, is true.


```python

```

Logical negation (NOT):


```python

```

**Special note about NaN!**

Next up is something you should definitely be aware of!  NaN ("not a number") **is not equal to itself**!  It is also the ONLY value for which this is the case!

This is important, because missing records in a data set are often treated as NaN, and you will sometimes need to be careful about how you handle them.  It may not happen very often, but it will happen eventually and can cause confusion if you're not aware of it.


```python

```


```python

```

From the results of the logical comparison, you could conclude that x must be NaN.  This may show up at some time in the future, don't forget it!  There's also usually special operations for checking if something is NaN.  In Python:


```python

```


```python

```

The benefit of this approach becomes apparant when you have a list of values. Here's how you can make a list:


```python

```

Here's how you can extract the individual elements of the list (this is called "indexing"):


```python

```

What if we wanted to check if any values in y are NaN? Since y is a list, the output here will not be what we want:


```python

```

This is because y is a list, and we just asked whether the list is equal to itself, which is True. To test the individual values in the list we could write a loop:


```python

```

Which you could also do in a single line (in Python, this is referred to as "list comprehension"):


```python

```

Or, if you want to save yourself some typing:


```python

```

Last but not least, you might want to identify which values in a list match some criteria, and then perhaps remove/keep those elements from the list.  Let's suppose that we wanted to remove the NaN values from y:


```python
# First, identify the elements in the list that match your criteria.  

```


```python
# We can negate all of these boolean values like so:

```


```python
# We can use the inverted boolean array to index y, but first we'll need to make y into an array.  
# A bit annoying, but lists and arrays are handled differently, and this will not work with a list:

```


```python

```


```python

```

### The pandas library and DataFrames

The first thing you'll usually do when writing Python code is to import any libraries that you'll need. When working with data files, the pandas library offers all sorts of convenient functionality.


```python
# You can also give the library a shorter name (alias) in the process using "as", 
# that'll save typing later on:

```

Next, let's get our file imported.  First, open up the file in the text editor and take a look at it.  You'll notice that there are tabs between each value in the file.  In other words, it's a tab-separated file.  We'll need to let pandas know this when we import it because, by default, it's going to assume a comma-separated file.


```python
# I usually like to do this in two steps.  First, specify where the file is located:

# Now import the file, but let's suppose we forgot about the whole tab-separated thing:

```

It's important to learn how to troubleshoot errors like this.  As you can see, we receive quite a long error from what we know is a very simple problem.  Usually, you'll want to start at the bottom of the error message, and then work your way to the top.


```python

```

'data' is now an object called a DataFrame, and it contains an array-like representation of our data.  Important to note here that DataFrames are not arrays - they have a lot of additional built-in functionality. 

If we just enter the name of the DataFrame, it'll print the top and bottom:


```python

```


```python
# You can also look at just the top, or just the bottom, using .head() and .tail()

```


```python

```


```python

```

To check the size of your data, you can use the .size and .shape commands


```python
# .shape will return the number of rows and number of columns.  
# Note that the first column (the one in bold) is called the index of the DataFrame,
# and does not count as an actual column.
#
# Also, the header row, if there is one, does not count as an actual row of data

```


```python
# .size will return the number of individual cells in the DataFrame

```


```python
# ...which is equivalent to the number of rows * the number of columns

```


```python
# To get a quick summary of the names of the columns, as well as what type of data...

```


```python
# Or if you just want a quick list of the column names:

```


```python

```


```python
# ... even better:

```


```python
# Here's a quick way to get a summary of your numerical data:

```


```python
# Let's extract all the data for Asia and store it in a new DataFrame

```


```python

```


```python
# Oops!  Wrong column.  Good thing we checked.

```


```python
# What if we only wanted the data for the most recent year, from Asia?

```


```python

```


```python

```


```python
# You could, of course, have done that all in one step, but...

```


```python
# The error occurred because _____________.

```

Even though the results above are what we wanted, the logic we used is not equivalent to what we were originally trying to do.  For example, if there were no records for Asia for 2007, then we would have gotten back an empty DataFrame.


```python
# So, here's a better way. First, I would write down what I want to do:

#   Goal: Specify a continent, and extract the most recent data from that continent

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
