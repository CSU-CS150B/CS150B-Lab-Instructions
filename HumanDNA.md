# Lab 09 - Human DNA Length

## Introduction
Did you know that you share roughly 50% of the same DNA as a banana? That is bonanzas!

Of course, such jokes are a slippery slope, so let’s split and move onto what you need to do for this lab. In this lab, you will focus on topics you have worked on before, but you will be moving onto handling more of the information. Unlike most labs, we will be grading the output, so the main function will matter! You can still have your tests in the file however, as long as the last thing printed is the expected program output!

## Step 1 - dna_stats(lst)

We are actually going to work backwards for this program, as the dna_stats function can be built independently of other functions.

While the program will think of this as the lengths of DNA strands, the truth is that it is really just a list of int values (whole numbers).

This function is just building a nice looking __formatted string__ based on the stats of those numbers.

First, you will need to create the function declaration (look at the others for examples!) Don’t overthink it, and remember to indent the code block of the function like it talked about in the reading.

Now recall in Chapter 9, we covered some useful list functions. Most notably min, max, sum, and len. The min gives you the smallest value in the list, for example

```python
lst = [10, 3, -2, 3, -1]
small = min(lst)
print(small) # prints -2

large = max(lst)
print(large) # prints 10

total = sum(lst)
print(total) # prints 13

length = len(lst)
print(length) # prints 5
```
Using these four functions, you should be able to find the shortest (smallest) number, the longest (largest) number, and the average value! You will then return a __formatted string__ of the following format. You can have any number of numbers on the left-hand side, but only two decimal places on the average.

For example:

Shortest DNA Length: ###

Longest DNA Length: ###

Average DNA Length: ###.##

### Testing
To test this function, you can simply call it with arbitrary integer lists. For example:

```python
print("TESTING dna_stats", dna_stats([1, 1, 10, 11]))
print("TESTING dna_stats", dna_stats([-1, 11, 1110, 2111, 42]))
```

## Step 2 - file_int_list(file)

For this function, you will read in a file and then return a list of int values.

You should look back at the Files and CSV lab to recall how to read in all lines of a file.

This is not a csv file as they are only a list of value one value each line of the file (you can view the files by clicking the download button in zybooks). 

The problem? When you use .readlines(), every element of the list is a String, and the functions we used above (sum in particular) doesn’t work on strings.
 
As such, we want to convert every item in the list to be an int using the int(val) function.
  
This will involve first reading in the file, loading all the lines, and then looping through all lines building a second list of ints (use lst). You should return the list of ints.

### Testing
To test this function, feel free to use some of the files provided, and then print out the
list that is returned. For example:

```python
print("TESTING  file_int_list",  file_int_list("HumanGeneLengths1.txt"))
print("TESTING  file_int_list",  file_int_list("HumanGeneLengths2.txt"))
```
You may want to download the files just to make sure it is doing what you think!

## Step 3 - Finishing main()
The main function is only partially done. Now is your turn to change it into a working program. You go ahead and loop through every file in the file list provided. For each file,
 - call file_int_list with the file name, storing the value
 - print the file name
 - print the dna_stats for the stored int list
## Turning it in
By now, you should have completed all the functions and should have a working program by this point. When you are comfortable with how your program works, submit it through zybooks!

Unlike your other labs, you will need this last main working for full points, so this is a full points or not lab!

After you have turned it in, take a moment to reflect, and maybe even talk with a TA. How far have you come in the past 8 weeks? This lab combined all the skills you have been learning!

  
