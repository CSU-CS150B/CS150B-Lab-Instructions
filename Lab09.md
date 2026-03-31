# Lab 09 - Files and CSV

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

Below is some code that will help you print the contents of the CSV file to the screen as a number of lists. `file_list` is a **list** where each element itself is its own **list** (each element being one song and its info).

```python
with open(filename, 'r') as myfile:
    file_list = csv.reader(myfile)  # remember: import csv at the top of the file
    for row in file_list:
        # then add each row to the list
```

> **Notice:** The first row will be the header. For our implementation we want to omit the header so when/if you do analysis on the data it won't have unexpected behaviors. You can do this in two ways:

1. Use `next(file_list)` — this reads the first element in your data, hence skipping it.

**OR**

2. Once you fully populate your list of data, remove the first element using `lst.pop(0)`. This will remove the element at index 0 (the header).

Once you are printing the lines of the CSV file, you can then work on the modifications you need for the `csv_data` function.

This function will:

* Create an empty list
* Loop through the dataset using the variable that called `csv.reader()`
* Append each row (loop variable) to the empty list
* Return the populated list

**Example implementation:**

```python
import csv

def csv_data(filename):
    """
    Reads a CSV file and returns its content as a list of lists, skipping the header.
    """
    data = []
    with open(filename, 'r') as myfile:
        file_list = csv.reader(myfile)
        next(file_list)  # Skip the header row
        for row in file_list:
            data.append(row)
    return data
```

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

**Example implementation:**

```python
def get_filtered_CSV(filename, filter_by):
    """
    Filters CSV data by a specified genre (case-insensitive) and returns a list of matching rows.
    """
    filtered_list = []
    all_data = csv_data(filename)
    for row in all_data:
        if len(row) > 3 and row[3].lower() == filter_by.lower():
            filtered_list.append(row)
    return filtered_list
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
    find_songs = []
    song_genre = get_filtered_CSV(filename, genre)

    earliest_year = int(earliest)
    latest_year = int(latest)

    for row in song_genre:
        if len(row) > 2:
            try:
                year = int(row[2])
                if earliest_year <= year <= latest_year:
                    find_songs.append(row)
            except ValueError:
                print(f"Skipping row with invalid year data: {row}")

    return find_songs
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
