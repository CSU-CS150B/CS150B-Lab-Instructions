# Colorado Pollution Data
## Intro
 The data for this project was obtained from [The EPA Website](https://www.epa.gov/outdoor-air-quality-data/download-daily-data) using the filters: 
 - Pollutant: CO
 - Year: 2020
 - Geographic Area: Colorado
 - Monitor Site: All Sites

The columns of the dataset we will use are
  1. Site ID (Id of the site surveyed), Index: 2
  2. Daily Max 8-hour CO Concentration, Index: 4 
  3. DAILY_AQI_VALUE (Daily Air Quality Index Value), Index: 6
  4. PERCENT (Percentage of required monitoring days having valid 8-hour data), Index: 9
## Overview
This project asks you to sort through a dataset of CO values at different Colorado sites to find the Maximum, Minimum and Average values for the Daily Max Co Concentration, The Daily AQI value, and the Percentage of days that had valid data.
To do so you will make several functions to read the file, filter it by the Site ID provided through the input and extract different statistics from the data.

## Step 1: readCSV(file)
This function takes in the name of a file and reads in a csv file from that filename. 

__You will need to skip the Header__. Use the next(csv_reader) method to skip a row when reading in a file to do so.

If you are using lists to complete this project, this function should return a list of lists, where each row is a line of the file and each column a different entry in that line.

If you are using pandas to complete this project, this function should return a dataframe. Remember that pandas automatically skips the header.

## Step 2: filterCSV(data, filterby)
For using lists:
This function takes in a list of lists returned from the readCSV() function and selects rows from it based on what the filterby is.

To do so, loop through the data and compare the Site ID column to filterby, if they are equal, add that row to a empty list and move to the next row.

This function returns a list of lists where the Site ID of each list is equal to filterby.

 For using pandas:
 This function takes a dataframe returned from the readCSV() function and selects rows from it based  on what filterby is.

 To do so, grab the Site ID column from the dataframe and check for each row that matches filterby.   You do not need a loop to do this in pandas! Dataframes can be filtered by lists of boolean values.  This means you can make a list of all rows where the Site ID matches filterby and then index the    dataframe by that list to filter it! df[column_name] == var, will return a list of boolean values where the all rows whose column_name value matches var is True. You can then use this to index the dataframe.

 This function should return a filtered dataframe where only the rows whose Site ID matches filterby are present.

## Step 3: calcAllMaxs(data)
This function takes in filtered data and returns the maximum value for three separate columns.
  1. Daily Max 8-hour CO Concentration, Index: 4 
  2. DAILY_AQI_VALUE (Daily Air Quality Index Value), Index: 6
  3. PERCENT (Percentage of required monitoring days having valid 8-hour data), Index: 9

To do so, it is useful to use the helper function calcMax.

This function returns a tuple in the order (Daily Max, Daily AQI, Percent).
#### calcMax(data, column_index)
This is a helper function that takes in data, and the number of one specific column and finds the maximum value in that column.

For both lists and pandas, it may be useful to loop through the data and keep track of the max then return it at the end.

## Step 4: calcAllMins(data)
This function takes in filtered data and returns the minimum value for three separate columns.
  1. Daily Max 8-hour CO Concentration, Index: 4 
  2. DAILY_AQI_VALUE (Daily Air Quality Index Value), Index: 6
  3. PERCENT (Percentage of required monitoring days having valid 8-hour data), Index: 9

To do so, it is useful to use the helper function calcMin.

This function returns a tuple in the order (Daily Max, Daily AQI, Percent).
#### calcMin(data, column_index)
This is a helper function that takes in data, and the number of a specific column and finds the minimum value in that column.

For both lists and pandas, it may be useful to loop through the data and keep track of the min then return it at the end. When checking for a minimum value in a list or dataframe, you will want a min_val variable to check each value against. It is typical to set this value to a huge number like 90 thousand.

## Step 5: calcAllAvgs(data)
This function takes in filtered data and returns the Average value for three separate columns.
  1. Daily Max 8-hour CO Concentration, Index: 4 
  2. DAILY_AQI_VALUE (Daily Air Quality Index Value), Index: 6
  3. PERCENT (Percentage of required monitoring days having valid 8-hour data), Index: 9

To do so, it is useful to use the helper function calcAvg.

This function returns a tuple in the order (Daily Max, Daily AQI, Percent).
#### calcAvg(data, column_index)
This is a helper function that takes in data, and the number of a specific column and finds the average value in that column.

For both lists and pandas, it may be useful to loop over the data and keep track of the total, then return the average value. Remember that the total of a list (and each column is a list!) divided by the number of entries in the list will give you the average value of that list.

## Step 6: print_stats(user_input, stat_type, stats)
This function takes in the ID of the site that was used for filtering, the type of statistic to display, and the numbers for that statistic.
It then prints out the statistics for each part of the stats.
__Remember that [index] can be used to access parts of a tuple__

All Statistics should be printed as formatted strings, with only two decimals using {:.2f}.

For example If the function is called like:

```python3
print_stats("080310027", "Maximum", calcAllMaxs(filtered))
```

Then the output would be:

```
Site 080310027: Maximum for Daily Max is 1.90
Site 080310027: Maximum for Daily AQI is 22.00
Site 080310027: Maximum for Percent Complete is 1.90
```

However if the function is called like:

```python3
print_stats("080310027", "Average", calcAllAvgs(filtered))
```
The output would be:

```
Site 080310027: Average for Daily Max is 0.64
Site 080310027: Average for Daily AQI is 7.47
Site 080310027: Average for Percent Complete is 0.64
```

## Step 7: Main()
This is the driver of your program, it will call your other functions and is where you will do most of your testing.

In this function you should 
- read in the CSV file using your readCSV() function
- filter the result of the last step using your filterCSV() function
- Calculate the maximums, minumums and Averages using your calcAllMaxs, calcAllMins, and calcAllAvgs functions.
- Use your print stats functions with the statistics from the earlier steps to print out each set of statistic.
