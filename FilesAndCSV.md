# Lab 07 - Files and CSV

## Introduction
Working with files is essential to all programs, as files are how we hold information for the programs. As such, learning to read files is essential to programming.

In this lab you will learn how to open files, read the files, and perform different calculations with the data in the file.

The most common way to open a file in python is with the “with” statement. This allows the file to close automatically when you are finished working with it.
```python
with open("myfile.txt",'r') as mytextfile:
```
We will be reading the files directly, and working with CSV files that will convert file information to lists for our use.

In this lab you will learn:

* Opening files
* Reading files
* Working with loops and lists on files

## Provided Code
You will notice we provided two functions for you. main and run. You can add tests in the run function.

Note: Each function that requires a parameter will use different ones in submit mode.

REMINDER: You should be running your code as you work! Running tests, and even trying stuff out before you finalize your functions.

## file_addition(filename) (Step 1)
Find the file_addition function. In this function, you will need to open a file with the file name being passed in as a parameter. The format of the file being passed in will look like this:
```
3
4
```
There will be two numbers each on separate lines. You will read in the those two lines, convert the numbers to integers, and return the sum of adding the two together. Remember when you read in a file it reads it in as a string, which is why you need to convert the numbers to integers. int(val) will help you!

If you are stuck on where to start, take a look at Figure 9.4.1 in your zybook. Do not ‘write’ like the example in zybook does. Instead, just return the result of adding the two numbers together.

## line_counter(filename) (Step 2)
For this function, you should use the with statement to open a file. You will then want to count the number of lines in the file, and simply return the total lines. There are two ways you can look at doing this. You could loop through every line incrementing a counter. OR you can use the .readlines() to load every line into a list, and take the len() of that list.

## csv_data(filename) (Step 3)
First, in order to work with CSV files, you need to import the CSV module. In order to do that, uncomment the
```python
import csv
```
That is at the top of the file. This will give you a number of CSV tools, but at this point, we just care about reading the lines into lists for us to process those lines!

Below is some code that will help you just print the contents of the CSV file to the screen as a number if lists (one list for each line in the file using commas to separate the elements)
```python
with open(filename, 'r') as myfile:
    csv_reader = csv.reader(myfile) #remember import csv at the top of the file
    for row in csv_reader:
        print(row)
```
Once you are printing the lines of the CSV file, you can then work on the modifications you need for the csv_data function. You will see the function returns a tuple of count and max_row_length. You will need to count the total number of lines in the CSV file (in the loop increment counter!), and also check each line to see if the row length changes (len(row) gives you the row length!).

This function will give you practice counting the total lines in a CSV file using a loop, and also having an if-statement within the loop as you look at each line individually.

## get_filtered_CSV(filename, filter_by) (Step 4)
Let’s build more on CSV files. First off, for this function, make sure you can open and print out the contents of a CSV file. This will help you make sure you are down the right path (see Step 3). Now that you have the file printing we can work on the actual goal of the function. For this function, you will return a list of lists (rows), but only ones that match the filter_by value in the first location of the row.

For example, if row[0] equals “United” (the value I passed into filter_by), the entire row will be added to lst using .append, but if the row[0] does not equal the filter_by value, I simply ignore the move and move on.

In the end, I should have a list of lists filtered by the first value in the row.

## find_flight(filename, airlines, city, earliest, latest) (Step 5)
This function is a review of list manipulation more than file reading. For the first step, you will want to call get_filtered_CSV(filename, airlines), so get all the flights from that airline. Since get_filtered_CSV filters the CSV for you, you will end up with a list of lists. Maybe print that out now just to make sure it worked?

As you loop through the list, you will then look at positions 1 and 2 in the list. If the item in position 1 matches the city, AND the item in position 2 is greater than or equal to earliest and less than latest, return that flight / list. You can safely assume position 1 in the list is always the city, and position 2 is always the departure time for the flight. You can also assume the first flight found is all that is needed (no need to look for other options).

Here’s an example for this part: the item in position 2 is greater than or equal to earliest and less than latest

You can do this two different ways:
```python
if highest > item >= lowest:
```
or
```python
if item >= lowest and item < highest:
```
Reminder: This is only the second part of the if statement, don’t forget to add the first part (If the item in position 1 matches the city)

For example:
```python
find_flight("files/Airport.csv", "United", "Portland", "0000", "2400") - should return ['United', 'Portland', '1335', 'B36']
find_flight("files/Airport.csv", "Southwest", "Denver", "0800", "1700") - should return ['Southwest', 'Denver', '1455', 'B56']
```
This function is combining the knowledge of the past few labs, so can be challenging to think through. However, the actual code is fairly limited. Try to not ‘over do it’. Instead, KEEP IT SIMPLE, and take it in steps. Can you loop through the results returned by get_filtered_CSV. Can you simply return the first flight to the selected city? ok, now that you can check for the city, use your boolean and to check for the departure time range.

If you try to do much more than that (open the file again for example), you are probably doing too much!

## Turning In (Step 6)
Make sure you click through the canvas link to the assignment if you haven’t already (or haven’t in the last 20 minutes). This triggers the linking process, so canvas can get an updated score.
