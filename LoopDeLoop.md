# Lab 06 - Loop de Loop
## Loop de loop
In this lab you will be making lists, and using loops to execute your functions! If you have any questions about what lists are, or how to make a loop, go back to your readings or lectures to remind yourselves.

## Step 1 - Make a List
This first step is about looking over the function called makelist() 
  
This function takes in one parameter, an integer. Within the function, it creates a new empty list. 
  
Then, there is a for loop that starts at 0 and ends at the parameter that was passed in. Every iteration of the for loop will be added to the empty list. 

Once the loop is done, it returns the list.

Examples:
``` python
makelist(10) # returns [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
makelist(3)  # returns [0, 1, 2] 
```

## Step 2 - Lift Off!
In this step, you will be writing function called rocketcountdown() and it will take in one parameter, an integer. 
  
In this function you will start by making an empty list, then you will make a for loop that counts DOWN form the parameter to 0 (But not including 0).
  
You will be adding each number as it is passed through the for loop to your list and when it hits 0, you will add the string ‘We have lift off!’

Examples:
``` python
rocketcountdown(10) # returns [10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 'We have lift off!']
rocketcountdown(2)  # returns [2, 1, 'We have lift off!']
```
## Step 3 - Double Loop
In this step, you will create a function named doubleloop() that will take in 2 parameters, both ints. 

This function will also return a list of numbers.

You will want to make a nested loop for the list to parse through all the possible numbers between 0 and parameter one and between 0 and parameter two. 
You will pair them together with the use of string formatting and then separate them by a colon.

Examples:
``` python
doubleloop(2, 2) # returns ['0:0' , '0:1' , '1:0' , '1:1']
doubleloop(3, 4) # returns ['0:0', '0:1', '0:2', '0:3', '1:0', 
                           '1:1', '1:2', '1:3', '2:0', '2:1', '2:2', '2:3']
```
Here’s an example of a nested loop:
``` python
    for i in range(num1):
        for j in range(num2):
            list.append(f'{i},{j}')
```
## Step 4 - How many combinations?
In this step, you will be creating a function called howmanycombos() and it will take in 3 parameters, all integers. 

Like in step 1, you will be creating an empty list. 
              
The goal of this function is to return a list of all possible combinations in a lock (like the old ones that you would have to spin left to the first number, right to the second number, and then left again to the third number).

You will be using nested for loops to make this function, each loop will go to the desired number that was passed into the parameter. 
  
So, the first loop will go from 0 to the first parameter, then the next loop will go from 0 to the second parameter, and the third one will go from 0 to the third parameter.

To add the number combination to the list, use string formating (or fstring) to show which numbers that you used! each number will be separated by a “:”

Once the list has all possible combinations, return the list to be printed.

Hint: This is very similar to step 3, except there will be three loops nested instead of 2.

Examples:
``` python
howmanycombos(1,1,1) # returns ['0:0:0', '0:0:1', '0:1:0', '0:1:1', '1:0:0', '1:0:1', '1:1:0', '1:1:1']
```
## Step 5 - Cans of pop on the wall
In this function, you will be writing a while loop. 
 
The function name is called cansofpop() and it will take in 2 parameters, both integers. 

The first integer will be the total number of cans of pop on the wall and the second integer will be the interval of how many cans of pop to take off the wall.

You will be using the format string:

'{0} cans of pop on the wall {0} cans of pop, take {1} down and pass them around, {2} cans of pop on the wall'
### 5.1
In the beginning of your function you will create a new empty list. Then, you will write a while loop that will run until there are no more cans of pop to grab
#### hint, you might need a conditional statement to check to make sure that you have 0 or < 0 cans of pop). Every time you go through the while loop, add the current string to the list you created. When the loop is done, add the following string to the end of your list:
#### 'All cans of pop are gone!'
### 5.2
Once you have make the list, created the while loop, and added the final string, return the list.

#### Hint: Once takedown is greater than the number left, you will need to set takedown to be equal to the number left. 
For example:
```
if we have 9 left and have to takedown 14, that would equal a negative number. 
9 - 14 = -5
```

You need to add something in your code so that cans of pop equals 0 at the end.
 

  Examples (ignore new lines - only there so you can see it on the webpage)
``` python
cansofpop(3, 1) # returns ['3 cans of pop on the wall 3 cans of pop, take 1 down and pass them around, 
#                           2 cans of pop on the wall', '2 cans of pop on the wall 2 cans of pop, 
#                           take 1 down and pass them around, 1 cans of pop on the wall', 
#                           '1 cans of pop on the wall 1 cans of pop, take 1 down and pass them around, 
#                           0 cans of pop on the wall', 'All cans of pop are gone!']
```
Step 6 - Turning it in!
Once you have finished steps 1-5 and you have tested them, submit them to zybooks!
