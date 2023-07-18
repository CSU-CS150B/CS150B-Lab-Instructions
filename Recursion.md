# Lab 11 - Introduction to Recursion
## Introduction
Recursion is another way to loop, using method calls. Arguably, if you practicing divide-conquer-glue actually means recursion is a more natural way to loop. However, many people trip themselves up over recursion, as it can be difficult to picture what is going on, and they try to picture the entire process at once. Once you understand recursion, you will find your ability to represent code and handle complex situations becomes exponentially better! Why? Because there are many problems out there that are naturally recursive, and arguably very difficult to do with loops. However, these problems are also ones you will deal with in a later class. In this class, we will send the next week working on this recursion lab, and we encourage you to seek a deeper understanding of every example problem.

## Step 1 - countdown(n)
Looking at the code, you are provided with an incomplete recursive function. The code provided is as follows:
```python
    if n == 0:
        return
    countdown(n-1)
```
What you need to do is add a print(n) statement in the code, that will cause the function to print the following to the screen if countdown(4) is called:
```
4
3
2
1
0
```
Now think about this code, how does this “recursive loop” work? Try writing out the function calls on a piece of paper, so you can visualize what is going on.

### Testing
You will notice we provided some tests in the main function. You should feel free to comment those out, and add your own. These tests will not affect your final grading for the lab, as we will be testing each function individually.

## Step 2 - countup(n)
Now let’s go ahead and switch the direction of the print, instead of printing the number from n to 0 counting down, you should print number for 1 to n, counting up. This function is intentionally blank as you should write it from scratch. You will find most all the code is the same as countdown, though where you place the print(n) changes!

How can just changing the print location change the order the numbers are printed on the screen? Write out the function calls on a piece of paper, and see what is going on. If you don’t understand, please reach out to a TA either in lab or online help desk to go over how this works!

### Testing
Make sure to uncomment the code in the main function, and add your own tests. You could actually modify the function to take negative values without it affecting the zybooks tests, so that could be an interesting challenge problem.

## Step 3 - factorial(n)
Factorials is a classic example of recursion. If you need to brush up on what a factorial is go here [https://en.wikipedia.org/wiki/Factorial]. In quick review, a a factorial takes a number, and multiples all numbers that lead up to that number together. For example, 5! = 5 * 4 * 3 * 2 * 1 = 120.

You should implement a recursive function that does just that - make it recursive, don’t use a loop! This method (called factorial()) will take in one parameter, an int, and you will calculate the factorial value.

Before writing the recursive call, make sure you implement the base case! When do you stop counting down, and if you hit that point, what do you return?

Once you have the base case in place, then work on the recursive call. While the countdown and countup you were printing, for factorial, you will need to return a value and multiple the results. If you are stuck, you should look back at your readings in zybooks. There may be a similar example, but try doing it first before looking back!

### Testing
For testing recursive methods, your tests often happen at multiple parts. We personally would test after we write the base case, passing in the condition for the base case as the parameter in my test. This may seem tedious at first, but you are basically ‘solving’ the simplest case first - making sure it works, and then working on the n+1 case for the recursive call. We would then start testing as we work on the recursive call - you may not always get the results you expect - and that is fine.

## Step 4 - string_reverse(string)
We are going to work with strings now. This function called string_reverse() will take in a string parameter should return the string reversed. Algorithm wise, this function will take out the last character in the string and recursively calls the function with the string minus the last character (hint: use the string splice operator :)

We have provided the base case. Why is this the base case? When do you hit that base case?

Example output:
```
string_reverse('Cam the Ram') => maR eht maC
string_reverse('race car') => rac ecar
```
Make sure to draw this out! It makes a ton of more sense if you can picture the function calls, and then see how it all assembles back together.

### Testing
First try figuring out this function with a string of two items (“hi”!). Can you get it working for that? Then test it with a string of three items, and so on. Lastly, make sure you uncomment the functions in main. We have a message for you there to read!

## Step 5 - build_reverse_list(n)
Recursion and lists go hand-in-hand as you will see in the next two functions. These two functions can be challenging, but once the solution is built you will find the lines are fairly limited. Your goal for this function is to build a list of numbers, from n to 0. For example:
```
build_reverse_list(4) # returns [4, 3, 2, 1, 0]
build_reverse_list(3) # returns [3, 2, 1, 0]
```
We have provided the base case. When you hit 0, you return a list with the 0 item. However, that list with 0 as an item, needs to be concatenated into the list with [1] in it and so on! Note that lst = [n] is intentionally there as a variable you can use. For example return lst + (something here!) may be part of your code. Draw it out, and also run it frequently. When we first started building it, we got weird results of [3, [2, [1, [0]]]] which meant we had lists in lists, and too many brackets in our code!

### Testing
We have provided an example, but you may want to write your own. Also, make sure you test frequently, and expect it to be slightly off the first time. You may also get type issues, so that is another challenge to think about and solve through solid testing as you work on building the function.

## Step 6 - even_odd_list(values)
This is the function where you put all the different concepts together. You will build a function from scratch that will take in a list of number values. You will recursively build another list that has “even” or “odd” matching each number in the original list! Really think about how it can be done recursively.
```python3
even_odd_list([1,2,3,4,5]) #returns ['odd','even','odd','even','odd']
```
This type of function is called ‘map-to’ or ‘map’, where you map a set of values across a different set of values - and is very common in recursion and later when you study data structures! If you recall the Human DNA Lab, you had to convert a series of strings to ints. If you knew recursion at that time, you could have done that relatively quickly using a built in function called map.

### Testing
Test often. First, make sure you figure out your base case, and test just that! You don’t want to create a recursive loop that never stops!

## Turning it in!
This is the final step! Make sure that your code is running correctly and do not forget to submit it to zybooks!
