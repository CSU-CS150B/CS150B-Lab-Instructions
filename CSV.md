# Lab 13 - Files and CSV

## Introduction
Working with files is essential to all programs, as files are how we hold information for the programs. As such, learning to read files is essential to programming.

In this lab you will learn how to open files, read the files, and perform different calculations with the data in the file.

The most common way to open a file in python is with the `with` statement. This allows the file to close automatically when you are finished working with it.

```python
with open("myfile.txt",'r') as mytextfile:
```

We will be reading the files directly, and working with CSV files that will convert file information to lists for our use.

**with open()** does the following:

* `with open("somefile.txt", 'r')` → this opens `somefile.txt` to read from.
* `as yourfilevariable` → takes the content of `somefile.txt` and puts it in `yourfilevariable`.
* Be sure to be indented under the `with open()` statement when accessing `yourfilevariable`.

## Provided Code
You will notice we provided the run function. You can add tests in the run function.

> **Note:** Each function that requires a parameter will use different ones in submit mode.

> **REMINDER:** You should be running your code as you work! Running tests, and even trying stuff out before you finalize your functions.

---

## Step 1 — `file_addition(filename)`

In this function, you will need to open a file with the file name being passed in as a parameter. The contents of the file being passed in will look like this:

```
3
4
```

There will be two numbers each on separate lines. You will read in those two lines, convert the numbers to integers, and return the sum of adding the two together.

> **Remember:** When you read in a file it reads it in as a string, which is why you need to convert the numbers to integers. `int(val)` will help you!

If you are stuck on where to start, take a look at Figure 9.4.1 in your zybook. Do not 'write' like the example in zybook does. Instead, just return the result of adding the two numbers together.

---

## Step 2 — `line_counter(filename)`

For this function, you should use the `with` statement to open a file. You will then want to count the number of lines in the file, and simply return the total lines. There are **two ways** you can look at doing this:

1. You could loop through every line incrementing a counter.

**OR**

2. You can use `.readlines()` to load every line into a list, and take the `len()` of that list.

```python
lines = myfile.readlines()
total_lines = len(lines)
```

---

## Step 3 — `csv_data(filename)`

> **This can be the last time you have to manually open the file using `with open`.**

First, in order to work with CSV files, you need to import the CSV module. Uncomment the following at the top of the code:

```python
import csv
```

This will give you a number of CSV tools, but at this point, we just care about reading the lines into lists for us to process!

> **Tip:** To the left of the **run** button there is a file symbol. Click on this and you can select a specific file to view the raw contents of the CSV.

Remember to open a csv you will need to use a "with open" statement and specifiy the mode you want to use ('r' for reading, 'w' for writing, 'a' for appending). Once you have opened the csv, you can read the file contents in one of four ways:
* .read() - this will read all file contents into a single string
* .readline() - this will read one line of the file at a time
* .readlines() - this will read the file into a list of strings, where each string in the list is a row of the csv file
* csv.reader({your_file_name}) - this will utilize the csv module to read the file contents into a reader object which you can iterate over in a loop to access the individual lines. You can think of this object as a list of lists, where each list element in the overall list is a row of the csv file ([[row1], [row2], [row3]]). It is important to note that once you read a line from the reader object, it will remove it from memory and you will not be able to access it again so if you want to be able to access the file contents multiple times you will want to add them to a data structure like a list. You will also need to have "import csv" at the top of your program to access this method.

These reading methods all return the contents so you will need to store that return value in a variable.
  
Below is some psuedocode of one way you could read the csv into your program using the csv.reader() method.

```python
Open the csv using with open in read mode:
    Create an empty list to hold the file contents
    Create a reader object by using csv.reader({your_filename})
    Iterate over the reader object using a loop:
        Add each element of the reader object to the empty list we made earlier
    Return the now populated list
```

> **Notice:** The first row will be the header. For our implementation we want to omit the header so when/if you do analysis on the data it won't have unexpected behaviors. You can do this in two ways:

1. Use `next(file_list)` — this reads the first element in your data, hence skipping it, and will need to be placed before your loop. This method will only work if you are using the csv.reader() method as next() is a function in the csv module.

**OR**

2. Once you fully populate your list of data, remove the first element using `lst.pop(0)`. This will remove the element at index 0 (the header).

Once you are printing the lines of the CSV file, you can then work on the modifications you need for the `csv_data` function.

This function will:

* Create an empty list
* Loop through the dataset using the variable that called `csv.reader()`
* Append each row (loop variable) to the empty list
* Return the populated list

---

## Step 4 — `get_filtered_CSV(filename, filter_by)`

Let's build more on CSV files. For this function, make use of the previous function in Step 3. Keep in mind the return value in Step 3 is the list of songs, which you can then loop through. For this function, you will return a list of lists (rows), but only ones that match the `filter_by` value — which is the **genre column** in the dataset.

For example, if `row[3]` of a specific song equals `"Pop"` (the value passed into `filter_by`), the entire row (artist, song name, release year, genre) will be added to the list using `.append`. If `row[3]` does not equal the `filter_by` value, ignore the row and move on.

> **NOTE:** Your program should recognize the genre regardless of character case (e.g., R&B should match `r&B`, `r&b`, or `R&b`). You can do this using `.upper()` or `.lower()`:

**.lower() Example**

```python
name = "CHRIStopher"
print(name.lower())
# Will print out "christopher"
```

**.upper() Example**

```python
name = "chrisTOPHER"
print(name.upper())
# Will print out "CHRISTOPHER"
```

In the end, you should have a list of lists that only includes songs of the specific genre (argument) that was passed in.

**Example psuedocode:**

```python
def get_filtered_CSV(filename, filter_by):
    """
    Filters CSV data by a specified genre (case-insensitive) and returns a list of matching rows.
    """
    Create a list to hold the filtered data
    Get the unfiltered data list by calling the csv_data() function you wrote in step three
    Use a loop to iterate over the elements in the unfiltered data list:
        If the length of the row is greater than 3 and contains the word we are looking for:
            Add to the filtered list
    Return the filtered list
```

---

## Step 5 — `find_era(filename, genre, earliest, latest)`

This function is a review of list manipulation more than file reading. Here's the approach:

* Call `get_filtered_CSV(filename, genre)` to get all the songs of that genre. This gives you a **list of lists** with songs of one specific genre that you can loop through. Maybe print that out first just to make sure it worked?

* As you loop through the list, look at **index 2** in each row (the release year).

* If the value at index 2 is greater than or equal to `earliest` **AND** less than or equal to `latest`, add that row to your result list.

You can write the condition two different ways:

```python
if highest >= item >= lowest:
```

or

```python
if item >= lowest and item <= highest:
```

> **IMPORTANT:** `earliest` and `latest` will be years. Please keep the range at a span of 10+ years (e.g., `find_era("songs.csv", "pop", "2000", "2010")`). If the span is too small you will likely get an empty list.

**Expected output examples:**

```python
find_era("songs.csv", "rock", "1970", "1980")
# Returns: [['The Beatles', 'Let it Be', '1970', 'Rock'], ['ACDC', 'Highway to Hell', '1979', 'rock']]

find_era("songs.csv", "pop", "2000", "2010")
# Returns: [['Britney Spears', 'Toxic', '2003', 'pop']]
```

This function is combining the knowledge of the past few labs, so it can be challenging to think through. However, the actual code is fairly limited. Try not to "over do it" — **KEEP IT SIMPLE**, and take it in steps.

**Example implementation:**

```python
def find_era(filename, genre, earliest, latest):
    """
    Finds songs of a specific genre within a given release year range.
    """
    Create an empty list to hold the songs we find matching our year
    Get the list of songs that match our genre parameter by calling the get_filtered_CSV() function you wrote in step 4

    Create a loop to iterate over the elements in the list of songs get_filteres_CSV() returned:
        If the row length is greater than 2:
            If the element in that row at the year index (index 2) is greater than earliest and less than lastest:
                Add song to the empty list we made at the top of the function

    Return the now populated list holding songs that match our specified genre and year
```

**Sample test output:**

```
Testing find_era function:

Rock Songs from the 70s:
['The Beatles', 'Let it Be', '1970', 'Rock']
['ACDC', 'Highway to Hell', '1979', 'Rock']

Pop Songs from the 2000s:
['Britney Spears', 'Toxic', '2003', 'Pop']

Hip-Hop Songs from the 90s:
No Hip-Hop songs found from 1990-1999 (expected for dummy data).
```

---

## Step 6 — Turning In

Make sure you click through the Canvas link to the assignment if you haven't already (or haven't in the last 20 minutes). This triggers the linking process so Canvas can get an updated score.
