# Lab 01: All About Functions Lab
## Defining a function guide (Step 0.5)
Before we start grading lets quickly go over how to define a function in Python. A function is a reusable block of code which you can *call* to run the code contained within it.
The first line of a function defintion will always include the keyword *def* then the name of the function a set of parethesis *()* and a colon at the end of the line. Inside the paranthesis you can also include optional parameters which are variables that can be passed into the function.
```
def *name of function*(*parameters*):
```
Next is the body of the function which will contain the code we want to execute whenever the function is called. This code must be indented to be considered part of the function. The function body can end with a return statement which will return a value back to whereever the function was called from.
```
def example_function(var1, var2):
    answer = var1 + var2
    return answer
```
Lastly there is the function call which is the code that activates the function we have just written. This code calls the example function above with the numbers 3 and 5 passed as parameters.
```
print(example_function(3, 5))
```

## Creating your own print statement (Step 1)

We will continue with the printStatement function. Under the print(“Welcome to your second lab”), print “This is my first print statement!”. 
Make sure it is indented underneath the function at the same indentation level as the other print statement. 

Make Sure to remove the __#__ to uncomment the print(printStatement()) located in run() before you run the function!

_If you don't remember what comments are, refer to section 2.2 in your reading._

Run your program and make sure you have the correct output! It should look like this:
```
Welcome to your second lab!
This is my first print statement!
```

## Returning Values (Step 2)

Find the returnValues function. It’s very similar to the printStatement function except we are returning “Welcome to your second lab!” instead of printing.

Go down to the run function and uncomment out returnValues(), then run your program. Notice how nothing changes from your last run? This is because the value WAS returned, but it was not printed. In order to show that returned value, you need to print out the call to the function. 

Add a print statement to encapsulate returnValues(), it should look like this:
```python
print(returnValues())
```

Now rerun your code and now the output should be:
```
    Welcome to your second lab!
    This is my first print statement!
    Welcome to your second lab!
 ```

## Returning Values Part 2 (Step 3)
Let’s try returning our own value now. Unlike print statements, we can only have one return statement per function (in most cases). Let’s change that return line to say ‘This is my first return statement!’

Output should now look like this:
```
   Welcome to your second lab!   
   This is my first print statement! 
   This is my first return statement!
```

## Parameters (Step 4)
Find the parameters function. It looks like this:
```python
   def parameters(num1,num2):
        multiplication = num1 * num2
        return multiplication
```

Notice how this function is defined a little differently. There are variables in the parentheses. These are called parameters and are essentially placeholders. Parameters are used so that you can call the function multiple times using different values each time.

Go down to run() and uncomment print(parameters(1,4))

Your output should now look like this:
```
   Welcome to your second lab!   
   This is my first print statement! 
   This is my first return statement!
   4
```

Below print(parameters(1,4)), create another call to the parameters function using the numbers 5 and 7.

Output should look like this:
```
   Welcome to your second lab!   
   This is my first print statement! 
   This is my first return statement!
   4
   35
```

*Hint: If you are having trouble with this, copy the example given to you, and replace 1 and 4 with 5 and 7.*

## Putting it all together (Step 5)
In this step we will be combining everything we’ve learned so far.

1. First you will need to define a function called iceCreamOrder with no parameters. Go to step 0.5 to learn about defining a function if you don’t remember how to.
2. Within that function, create an int variable called cost and assign it to equal 6.
3. Then ask the user for input asking “What flavor would you like? => “ and store their answer in a variable called flavor. Hint: If you don’t remember user input, look back at lab 00.
4. Next return a statement stating “The **flavor** will cost **cost** dollars.” replacing flavor and cost with your two variables you created.
*Hint: Follow the same format as how you coded your print statement in lab 00.*

*Hint: Use casting to cast cost from an int to a string or else it won’t return properly. (An error will occur)*

5. __In the run() function, make sure to write a function call to your iceCreamOrder() function so that you will get output.__

In the zyBooks input box, put ‘vanilla’ to test your code.

Don’t forget to call the function to see the output. Make sure to put it above the return in run().

If you do this successfully, the output should look like:
```
    Welcome to your second lab!
    This is my first print statement!
    This is my first return statement!
    4
    35
    What flavor would you like? => The vanilla will cost 6 dollars.
```
Nice work, you just finished the lab! Now you can run in ‘Submit Mode’ to make sure you get full points.

Make sure to check the next step below to make sure your grade is sent to Canvas.

## Turning In (Step 6)
Make sure you click through the canvas link to the assignment if you haven’t already. This triggers the linking process, so canvas can get an updated score. As with the previous assignment, you only have five changes to ‘submit for grading’, so it is important to run the program testing it for various cases before you click submit for grading.
