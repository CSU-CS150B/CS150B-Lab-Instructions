# Practical Project > Weather

Weather in Fort Collins is great. Except for when it’s not. This dataset contains the temperature and wind speed for every hour between 2008 and 2015, and is [provided](https://climate.colostate.edu/~autowx/fclwx_access.php) by the Fort Collins Weather Station and Colorado State University.

## Introduction
In this practical you will be extracting data from a csv file with data about temperatures and wind speeds at certain dates and times.

The Temperatures.csv dataset is split into the following four columns:

* Date - The date when the data was recorded. Formatted day-month-year (ex. “10-Jun-2010”)

* Time - The time when the data was recorded. Formatted in 24-hour time (ex. “16:21”)

* Temperature - The temperature in fahrenheit (ex. “69.9”) (Note: Some temperatures are missing and are recorded simply as ***)

* Wind Speed - The wind speed in mph (ex. “1.7”)

## Required Functions to Implement (graded)
We will grade the following functions. There are many be different ways to implement them, and you are free to write helper functions. For the ones we grade, the names need to match the specification, but the others we ignore.

## Step 0 - Variables
Keeping track of which index is which column in a CSV can be a challenge. You will create two variables that match the column indices in the CSV file.
```
date_index - what index in weather has the date
temp_index - what index in weather has the temperature
```
You will use these index below when pulling specific data out from each day in the lists you generate

## Step 1 - csv_reader(file)
Using the file name provided, load the row data of the CSV file into a list, and return that list. As the files contain a header column, you will want to skip that header or remove it before returning the list of row values. Look back at the CSV labs for examples, as the code is pretty similar.

## Step 2 - client_input()
This functions simply prompts the client for input, so that the values in the file can be filtered when calculating average, maximum, and minimum. The prompt is as follows
```
Please enter a filter: 
```
The values entered can be anything, but you do not have to worry about invalid values. Example values are:
```
 2015 - will be used to only look at Temperatures in 2015
 Jan - will be used to only look at Temperatures in January across all years
 01-Jan - will be used to only look at Temperatures on the first of January across years
etc
```
While the value returned from this function will be used to filter values, this function does not worry about that. Instead it simply prompts the client for input and returns the answer (yes, this is a one line function).

## Step 3 - average_temperature(weather, filter)
Given a specific filter, return the average temperature for everything that matches that filter (all days in 2015 for example). When working with the filter, this is a case for the in operator. You can say if filter in row[date_index](if you already pulled row from your weather list), and that will only return true if the filter shows up in that date. That is valid to use, as are other methods.

A question turns into how do you test this? Here is an example of a test that used
```python
weather = csv_reader('Temperatures.csv')
input_one = "2015"
input_two = "Dec"
answer_one = "{:.2f}".format(average_temperature(weather, input_one))
answer_two = "{:.2f}".format(average_temperature(weather, input_two))
print("TESTING", answer_one)
print("TESTING", answer_two)
```
## Step 4 - maximum_temperature(weather, filter)
Given a specific filter, find the maximum temperature.

## Step 5 - minimum_temperature(weather, filter)
Given a specific filter, find the minimum temperature.

## Step 6 - run()
Now is the time to build this into a working program! In the run function, you will load the data from Temperatures.csv into a variable, and also get the value from client_input(). Using both values, you will call average_temperature(), maximum_temperature(), and minimum_temperature(). The output will be formatted as follows (here are a few examples):
```
Please enter a filter: Dec
Average Temperature for Dec: 28.10
Maximum Temperature for Dec: 66.30
Minimum Temperature for Dec: -14.90
Please enter a filter: 2015
Average Temperature for 2015: 50.89
Maximum Temperature for 2015: 94.30
Minimum Temperature for 2015: -1.40
```
## Reference
Fort Collins Weather Station, Fort Collins Weather Station Data Access, Colorado State University, Fort Collins Colorado. [http://ccc.atmos.colostate.edu/~autowx/fclwx_access.php. Accessed 2016](https://climate.colostate.edu/~autowx/fclwx_access.php).
