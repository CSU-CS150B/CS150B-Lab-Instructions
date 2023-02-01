# Lab 04: Modulo Lab

## Introduction
In this lab you will learn how to write a while loop and get practice using the modulo operator. A while loop can be used to calculate a set of statements as long as the while condition is true. The **modulo operator** (%) evaluates the remainder of the division of two integer operands.

In this lab you will learn:

* Using functions to divide a problem into smaller parts.
* While loops
* Modulo

## Provided Code
You will notice we provided two functions for you. **main** and **run**. You should not modify anything in the **run** function, but we encourage you to read through it. The **run** function is the ‘glue’ in the Divide-Conquer-Glue strategy.

## What’s in a Name (Step 0)
```
## @author YOUR_NAME
##         YOUR_EMAIL
```
Add your name and email!

**REMINDER**: You should be running your code as you work - just to see what is happening.

## Factorial Calculation (Step 1)
Find the **factorial** function. Given a number, find the factorial of it. For example 4! = 4 x 3 x 2 x 1 = 24

You should be using a while loop to do this. Since this is your first lab using a while loop, it has already been done for you. All you need to do is add one line of code in the while loop.

Before writing any code, run the program to see what it does. Make sure to have input in the **Predefine program input (optional)** box or else you will get an error.

Did you get an error? That was supposed to happen!

The error says:

“We couldn’t run your program to completion. Could be a temporary system issue – please try again. Could be your program never finished, due to an infinite loop, infinite recursion, waiting for input, or other possibilities.”

This error was caused by an infinite loop. This is because the number passed in from input never decreases, so it’s stuck in the while loop because it never reaches 0.

Your goal is to add a statement to decrease that number by 1 each time it goes through the while loop.

Once you add your code, run it again! You should get the factorial this time.

## Modulo Practice (Step 2)
Given a random number, calculate the remainder if that number is divided by 9. Make sure to use the modulo operator.

For example:

If 81 is passed in, the result returned should be 0.
```
>>> 81 % 9
0
```
If 4 is passed in, the result returned should be 4. This is because you cannot divide 4 by 9, so the remainder will be 4 because 4/9 = 0 with a remainder of 4.
```
>>> 4 % 9
4
```
If 64 is passed in, the result returned should be 1.
```
>>> 64 % 9
1
```
Remember to run and test it.

If you don’t understand how modulo works, go back through reading 6 in zyBooks.

## Find if Number is Even (Step 3)
Find the **evenNum** function. Given a number passed in as a parameter, you should use the modulo operator to see if that number is even. If the number is even, return True. If it is not even, return False.

**Note:** Return True and False as Booleans and not as Strings.

**Hint:** if a number is even, the remainder should equal 0. You need to figure out which number to divide by to get 0.
```
Note: the hashtag (#) represents any number in this example. i.e. 4

if num1 % # == 0:
    return True
else:
    return False
```

## Find if Number is Odd (Step 4)
Find the **oddNum** function. You should use the modulo operator to see if the number passed in is odd. Return True if the number is odd and return False if it is not.

**Hint:** This should be very similar to the **evenNum** function. If a number is odd, it will not divide evenly, therefore the remainder will **not** equal 0.

## Check if Number is Even or Odd (Step 5)
Using the previous functions, check to see if a number is even or odd. If the number is even, return “even”. If the number is odd, return “odd”.

## Turning In (Step 6)
Make sure you click through the canvas link to the assignment if you haven’t already. This triggers the linking process, so canvas can get an updated score. As with the previous assignment, you only have five changes to ‘submit for grading’, so it is important to run the program testing it for various cases before you click submit for grading.
