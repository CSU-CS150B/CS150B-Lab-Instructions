# Lab 12 - Loops Part 2

In todays lab, you will be working with for loops to parse over sequences to achieve a desired result. 
Remember that .lower() will allow you to compare two characters without case sensitivity

## Step 1: Find the total number of a specific character in a string
In this step, you will have a string and a search character to be found within the string.  

To accomplish this task, create a counter variable that starts at 0, as well as a for loop to iterate over the string.  

Within the loop, compare the current character with the one you are looking for (search variable). If they are the same, add 1 to the counter. If they aren't, the
loop keeps moving.  

This pattern should continue until you've gone through the whole string. The function should return the total number of the search character within the string. 

```
def findAll(string, search):
    counter equal to 0
    for each character of string:
      if character is equal to search:
        counter + 1
    return counter
```

## Step 2: Find the last index of a specific character in a string
In this step, you have a string and a search character again, but this time you are looking for the index of the very 
last instance of the search character in the string.  

To complete this step, you will want to create an index variable set to -1 (in case the character is not in the string), and a for loop that iterates over the range of the length of 
the string, so that the current index is retrievable.  

For each iteration of the loop, compare the current character with the search variable. If they are the same, set the index variable to be the current index.  

Repeat this until you've iterated over the entire string, and then return the final index value of the search character.

```
def findLast(string, search):
    index equals -1
    for each value in the range of the length of string:
        if character at value is equal to search:
            index equals value
    return index
```

## Step 3: Find the first index of a specific character in a string
In this step, the logic is almost identical to Step 2.  

However, the main difference is that you will need to find the very first index of the search character within the string, and stop there.  

There are two main approches you can take to this. Within the loop, once you've found the first index of the search character, you can either return the index 
immediately, or you can use the break keyword after setting index. 

## Step 4: Find the total, first, and last index of a character over a list of strings
In this final step, you are given a list of strings and a search character.  

All you have to do for this step is create a for loop that iterates over the list, and calls the previous three functions on the current string with the search variable in the 
order of findAll, findFirst, and findLast. Your code should also print the results of each function call to the console.  

To make the output easier to understand, each iteration should start by printing the string to be checked and end with an empty line to make a break between loops

```
def getListStats(lst, search):
    for each string in lst:
        print string
        print "The number of {search}'s in the string is: " and then a call to findAll with string and search
        print "The first index of {search} in the string is: " and then a call to findFirst with string and search
        print "The last index of {search} in the string is: " and then a call to findLast with string and search
        print empty line
```
    
