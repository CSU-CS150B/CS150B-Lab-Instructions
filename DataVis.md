# Lab 12: Cleaning Data

## Introduction
In this lab, you will be using the Pandas Library to read a csv dataset into a dataframe, and then cleaning the data in two different ways to see how they affect the total average of our data.

Keep in mind that the way that this lab is structured, it won't run without error until all steps of the lab have been completed, so if you're having trouble running your program initially, don't panic!

## Reading a CSV File into a Dataframe (Step 1)

To start off, we first need to read our csv file, **hmeq_small.csv** into a dataframe!<br>
At the very start of your program, you will notice the line:
```
import pandas as pd
```
This line is importing the Pandas wrangling library into our program under the name **pd**.<br>To initially use the methods that Pandas provides, we will have to use our methods on the variable **pd** much like lst.append(), where we used the .append() method to add to the list variable lst.<br><br>
For this step specifically, we want to use the method to read csv files as a dataframe on **pd** and store that returned dataframe in the variable **hmeq**.

_HINT: if you are having trouble knowing what to do, review reading 12.1!_

## Removing Rows with Missing Data (Step 2)

Now that we've read our dataframe, for all future steps of this lab we will want to use our methods on the dataframe variables rather than the pd library itself, so that we can perform specific modifications to the existing dataframes themselves. 

Here, we want to **clean** our data by taking our dataframe **hmeq** and removing, otherwise known as **dropping**, all rows with missing data from it, storing the resulting dataframe in the variable **hmeqDelete**.

## Filling Rows of Missing Data (Step 3)

For this step, instead of dropping all rows that have missing data, we will want to use a method on **hmeq** to fill all its missing data with a mean value, and then store that resulting dataframe in the variable **hmeqReplace**. Keep in mind that it's possible to have a method call within a method call, for instance:
```
lst = [0,1,2,3]
lst.append(lst.pop(0))

# lst is now equal to [1,2,3,0]
```
So for our purposes, it would be possible to use a method that fills empty row values in your dataset, and provide a separately method calculated mean as the value for the fill method.

## Comparing Our Results! (Step 4)

For the last part of this lab, you will just need to edit the provided print statements to print the mean value of **hmeqDelete** and **hmeqReplace** respectively.

Once you've finished adding to the print statements, run your program and look at the resulting means and how they differ!<br>You should notice some relatively substantial differences, which really shows how much your methodology in your treatment of data can warp results.

Though this lab was pretty simple, going into your practical project with even this knowledge and experience with Pandas will be extremely beneficial!
