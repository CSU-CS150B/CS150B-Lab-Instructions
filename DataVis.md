# Lab 13: Visualizing data using matplotlib

## Introduction
In this lab, you will be using the skills you gained in the last lab to read in a dataset to python and then use the new libraries matplotlib and seaborn to visualize what is happening in that dataset.

Keep in mind that the way that this lab is structured, it won't run without error until all steps of the lab have been completed, so if you're having trouble running your program initially, don't panic!

## Accessing the dataset (Step 1)

The first thing we need to do is to load in the **mpg** dataset to our development environment. Pandas has already been imported so the only necessary step is to call the correct pandas method to read a csv file. If you are struggling with this step try looking back at lab 12. Remember that pandas is being imported into our program under the name **pd**.
```
//Remember the syntax to call a method is
import pandas as pd
mpg = pd.*method call goes here*
```
Once this is completed the dataset should be imported and stored in the variable **mpg**.

_HINT: if you are having trouble knowing what to do, review reading 12.1!_

## Create new dataframe (Step 2)

Now that we've imported the dataset we need to create the dataframe that we will use to store the data we want to visualize. The dataset is currently stored as **mpg** and we want to create a new dataframe that contains only a subset of the total data (specifically the columns **weight** and **mpg**).
```
//Remember the syntax to access a pandas dataframe uses square brackets
mpgSmall = mpg[[*col1*, *col2*]]
```

## Create visualization using matplotlib (Step 3)

For this step, we will using functions from matplotlib(plt) and seaborn(sns) to create a scatterplot of **weight** vs **mpg**.
i.e we want **mpg** to be the Y value and **weight** to be the X value:
```
//define a scatterplot using
p = sns.scatterplot(*method arguments go here*)
p.set_xlabel(*method arguments go here*)
p.set_ylabel(*method arguments go here*)
```

_HINT: Reading 13.2 will be very helpful!_


