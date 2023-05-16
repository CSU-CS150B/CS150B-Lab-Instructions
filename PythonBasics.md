# Lab 00 - Basics
## Introduction
First things first, there is a lot of information in this lab. Please read carefully and entirely as all of this information will be useful for future labs and will give you the basis of how to code in Python!

Welcome to your first lab! This lab is to help you become familiar with Python basics.

The skills you learn in this lab will be applied to the rest of the labs. It’s a great tool to look back on if you’re struggling with future labs, so make sure to complete this fully!!

In this lab you will learn:

print statements
defining variables
user input
casting
## Run Your Program (Step 0)
To run your program, make sure you are in the ‘Develop Mode’ and click run. The output should look like this:

```python3
Hello World!
```
One should never write an entire program and then run it. 

__They should instead run frequently and without reservation making sure the lines you type are indeed correct.__

## Print statement (Step 1)
Take a look at the provided code:

```python3
print("Hello World!")
```

This is called a print statement. When you want to show output from your code you can use a print statement.

Here are some facts about print statements:

When you want to print out text, aka a string, you wrap that text in quotes. 

For example print(“Hello”) will output Hello vs. print(Hello) will say that Hello is not defined, because it’s looking for a variable named Hello. 

You can test that out if you’d like.

You can also print out other variable types. print(3) prints out 3 as an integer. print(“3”) also prints out 3, except as a string.

You can print out almost anything you’d like, as long as it is defined.

Under the print(“Hello World!”), print “This is my first print statement!”. 

Run your program and make sure you have the correct output. It should look like this:
```
Hello World!
This is my first print statement!
```
Good work! You just coded your first print statement using Python!

## Working with Variables (Step 2)
Variables were mentioned in the beginning but were never explained. That’s why this step exists 😄

Some examples of variables include:

strings
ints
longs (large ints)
floats (decimal nums)
One cool thing about Python is that you don’t have to declare what type of variable you’re creating, you just have to assign a value.

for example:
```python3
    x = 15
    y = "15"
```
x is an int and y is a string.

It is good practice is to name your variables with meaning, so age = 15 would be better than x = 15.

Here are some more examples of assigning variables:
```python3
    firstName = "John" #string
    lastName = 'Doe' #string
    age = 33 #int
    height = 70.5 #float 
```
Notice how first and last name are wrapped in different quotes. Both are acceptable and represent strings.

For this step you need to create a string called animal and assign it to equal ‘elephant’. Then create another string called color and assign it to equal ‘gray’.

Then print out this sentence using those variables:

    The elephant is gray.
Here is an example using variables in print statements, in case you are having trouble.
```python3
    age = 34
    print("I am",age,"years old.")
 ```
gives the output:

    I am 34 years old.
You could also do it using + signs instead of commas. Commas add an extra space, + signs do not.
```python3
    age = 34
    print("I am " + str(age) + " years old.")
```
gives the same output:

    I am 34 years old.
Note: I had to convert age to a string in the second method because the + sign ‘adds’ (concatenates) the strings together to make one whole string. Since age is an int, you can’t add an int to string. You will learn more about this in step 4.

Your total output should now be:

Hello World!
This is my first print statement!
The elephant is gray.

## User Input (Step 3)
This next step is about user input.

This is when the program is asking for input from the user. Asking for input can be as simple as this:
```python3
    name = input()
```
but it is good practice to put a string in the parentheses to let the user know what input they are looking for, so it would look like this:
```python3
    name = input("Please enter your name => ")
```
input() default variable is a string, so to change that we use variable casting. Take a look at how we casted age from a string to an int using int(input()).
```python3
    age = int(input("Please enter your age => "))
```
For this step we will be combining everything we’ve learned so far. Make a variable called username and ask for input from the user. You should say something like “Please enter your username => “.

Then print “user: “ with the username following. For example user: user864

Before you run, you need to give the program input. Find the box in zyBooks that says “Enter program input (optional)” and put in the following input:
```
user543
```
If you do this successfully, the output should look like:
```
Hello World!
This is my first print statement!
The elephant is gray.
Please enter your username => user: user543
```
## Casting (Step 4)
You’re almost done!! Casting is the last step. 

Casting is used to change the variable type, for example an int variable may already exist but it needs to be a string for concatenation/printing purposes, like in the example in step 2.

Notice how you were given a couple variables.
'''python3
   string1 = "14.2"
   num1 = 3
'''
Right now string1 is a string and num1 is an int. You need to cast string1 to a float and num1 to a string. Then print both out, each in separate print statements.

Here is an example of casting a string to an int:
```python3
   string1 = "54"  
   num1 = int(string1)
   ```
You just have to specify the new variable type and wrap the old variable in parentheses.

Yours will be slightly different since you need a float and a string, so use float and str to cast.

Your final output should look like this:

``` Hello World!
    This is my first print statement!
    The elephant is gray.
    Please enter your username => user: user543
    14.2
    3
```
Congratulations!! You’ve completed your first lab! Now you can run in ‘Submit Mode’ to make sure you get full points.

Make sure to check the next step below to make sure your grade is sent to Canvas.

## Turning In (Step 5)
Make sure you click through the canvas link to the assignment if you haven’t already. 

This triggers the linking process, so canvas can get an updated score.

As with the previous assignment, you only have five changes to ‘submit for grading’, so it is important to run the program testing it for various cases before you click submit for grading.


