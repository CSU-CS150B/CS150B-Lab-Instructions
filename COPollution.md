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

__You will need to skip the Header__ Use the next(csv_reader) method to skip a row when reading in a file to do so.

This function returns a list of lists where each row is a line of the file and each column a different entry in that line.

## Step 2: filterCSV(data, filterby)
This function takes in a list of lists returned from the readCSV() function and selects rows from it based on what the filterby is.

To do so, loop through the data and compare the Site ID column to filterby, if they are equal, add that row to a empty list and move to the next row.

This function returns a list of lists where the Site ID of each list is equal to filterby.

## Step 3: calcAllMaxs(data)
This function takes in filtered data and returns the maximum value for three seperate columns.
  1. Daily Max 8-hour CO Concentration, Index: 4 
  2. DAILY_AQI_VALUE (Daily Air Quality Index Value), Index: 6
  3. PERCENT (Percentage of required monitoring days having valid 8-hour data), Index: 9
To do so, it is useful to use the helper function calcMax.
To find the max you should loop through the file and keep a variable that keeps track of the maximum for each column, updating it whenever there is a larger value.
This function returns a tuple in the order (Daily Max, Daily AQI, Percent).
#### calcMax(data, column_index)
This is a helper function that takes in data, and the number of a specific column and finds the maximum value in that column.

It may be useful to loop through the data and keep track of the max then return it at the end.

## Step 4: calcAllMins(data)
This function takes in filtered data and returns the minimum value for three seperate columns.
  1. Daily Max 8-hour CO Concentration, Index: 4 
  2. DAILY_AQI_VALUE (Daily Air Quality Index Value), Index: 6
  3. PERCENT (Percentage of required monitoring days having valid 8-hour data), Index: 9
To do so, it is useful to use the helper function calcMin.
To find the min you should loop through the file and keep a variable that keeps track of the minimum for each column, updating it whenever there is a smaller value.
This function returns a tuple in the order (Daily Max, Daily AQI, Percent).
#### calcMin(data, column_index)
This is a helper function that takes in data, and the number of a specific column and finds the minimum value in that column.

It may be useful to loop through the data and keep track of the min then return it at the end.

## Step 5: calcAllAvgs(data)
This function takes in filtered data and returns the Average value for three seperate columns.
  1. Daily Max 8-hour CO Concentration, Index: 4 
  2. DAILY_AQI_VALUE (Daily Air Quality Index Value), Index: 6
  3. PERCENT (Percentage of required monitoring days having valid 8-hour data), Index: 9
To do so, it is useful to use the helper function calcAvg.
To find the max you should loop through the file and keep a variable that keeps track of the total for each column, dividing it by the number of rows at the end.
This function returns a tuple in the order (Daily Max, Daily AQI, Percent).
#### calcAvg(data, column_index)
This is a helper function that takes in data, and the number of a specific column and finds the average value in that column.

It may be useful to loop through the data and keep track of the max then return it at the end.

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

## Step 6: Main()
This is the driver of your program, it will call your other functions and is where you will do most of your testing.

In this function you should 
- read in the CSV file using your readCSV() function
- filter the result of the last step using your filterCSV() function
- Calculate the maximums, minumums and Averages using your calcAllMaxs, calcAllMins, and calcAllAvgs functions.
- Use your print stats functions with the statistics from the earlier steps to print out each set of statistic.
