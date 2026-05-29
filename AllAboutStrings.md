# Lab 2 - All About Strings

## Introduction
This lab will be all about the "String" data type in Python and the many different ways you can use them. 
You should already have some experience with several of these concepts from the previous lab, but here
we will expand and reinforce them.
By the end of this lab, you should understand the different ways of making a string and the operations you
can perform on them. 
Strings will be an essential data type in just about every single lab in the class, so getting them down now
will help you succeed. 

## Step 0

Comments are an important concept for code readability. They allow you to have a line in your code with no
functionality, having a way to mark important sections or save code you are not ready to run. 
Comments are similar to Strings, in that they allow you to have lines of text in your code, 
but functionally they are very different.
On line 5 of your code, there is a line of text that is NOT a string. Running the code with it present
will cause an error, as Python doesn't recognize it as runnable code. To fix this, add a # to the start
of the line to make it a comment.

## Step 1

This step covers the three ways of creating a String in Python.

The comma (,) used in string1 allows us to have a break in our String to allow us to insert other data types.
```python
string1 = "String", 1, "uses commas"
```
The above example uses an integer, in this case the number 1, to create a string. The commas will automatically seperate each part with a space,
and no casting is required. 

The plus sign (+) used in string2, like the comma, allows us to have a break in out string to insert other data types. The
main differences between the plus and the comma is 
1. the plus does not add a space to the final string. Spaces will need to be added manually. This can be a benefit, as it
allows for more control in the string (when you don't want a space)
2. Using the plus sign in a string performs addition. As such, you cannot add a string and a number. However, You can add two 
strings together (expanded on later). When using the plus and adding a number to a string, you first need to cast that number
to a string.
```python
string2 = "String " + str(2) + " uses a plus sign (Notice the casting!)"
```
If you do not cast, you will get an error and the code will not run. Overall, using a plus is preferable to a comma. You will
find out why when we print these strings.

The formatted string (f"") used in string3 allows us the most control when creating our strings. Using the f string, we can insert 
other data types in our strings using curly brackets ({}). 
```python
string3 = f"String {3} uses a formatted string (or fstring)"
```
This combines the strengths of the plus and the comma, giving us greater control over our spacing and requiring no casting. In 
addition, it's also more readable than the other options. 

Now that we've gone over the three types, we will print them to the console.
For example:
    print(string1)
You will notice that the first print in the code is identical to string1. However, when we store string1 in a variable and print
that you'll notice that it doesn't look quite right. This is because when stored it becomes a tuple, which will be covered much 
later in this course. This is why using a plus or f string is preferable to the comma. 

## Step 2

Before you are three strings. To complete this step, you'll have to uncomment each print and fix the one simple mistake in each
that is preventing it from printing as intended. Each of these mistakes are very easy to make, hard to notice, and will likely
happen often, so it's good to get practice with them now.

## Step 3
Concatanation is a very useful tool that will be used quite often. In Python, Concatanation is as simple as addition, using the
plus sign between strings to combine them.
```python
half1 = "This is both stri"
half2 = "ngs put together"
string = half1 + half2
```
For this step, concatanate half1 and half2 like you can see above, and print the final result. 

## Step 4
As we saw in the last step, we are able to use addition on strings. We can actually use multiplication on them as well.
Using the * sign at the end of a string allows us to multiply that string by a number. Doing this will repeat that string
several times.
For example:
```python
string = "Hello" * 3
print(string) #prints HelloHelloHello
```
For this step, times the "over and over and " part of the print statement by 10. Hit run to see the result!

## Step 5
Hit the submit button when you're ready to turn in the lab.




