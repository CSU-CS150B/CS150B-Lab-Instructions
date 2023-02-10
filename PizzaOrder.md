# Lab 05: Pizza Order Lab

## Introduction

In this lab you will get more practice with branching by extracting the code from a pizza order.


The pizza order is in the following format as a string:
topping_one, topping_two, price


## Get Topping One (Step 1)

Find the get_topping_one function in zyBooks. This has already been completed for you.

Please read through it, it will give you a hint for what to do for the next functions!


To understand this function, we must first introduce slices. This is when we take a range of indices from a string (or list).


For example:
```python
example = 'ABCDEF'
print(example[0]) # prints 'A'
print(example[0:2]) # prints 'AB'
print(example[3:6]) # prints 'DEF'
```

Topping one can only be 6 letters long, in order for our string slicing to work properly. Since topping one is the beginning of our pizza order we need to extract the topping starting at the first index of the string, which is where we get the 0 in pizza_order[0:7]. The index after the colon is where we want to stop the string. This character at that index will NOT be included in the string slice.

### Testing

Uncomment the two tests given to you for get_topping_one(). The first test should print out cheese and the second one olives.

## Get Topping Two (Step 2)
This function is very similar to the one you wrote above however it is extracting topping two from the string. 

You will need to figure out the indexes to extract a 9-letter topping. 

You won’t start at index 0 this time because you don’t want topping 1. 

What index will you need to start at? 

You need the index where the letter ‘p’ is at. 

Then you will have to count and stop at where the comma is at (remember that index is exclusive - meaning it won’t be included in the string).

Create your own test for this function using this string: “cheese, pepperoni, 3000”

If you did it correctly, pepperoni should be the only thing returned.

## Get price (Step 3)
Oh no! The pizza price got turned into cents while being sent to the kitchen! You need to convert the price back to dollars. 

For the get_price() function, use casting to convert a string value to an int, divide it by 100 and return it.

Hint: Here is the general formula for converting from cents to dollars 
```
cents/100 = Dollars
```
Note: Don’t forget you will need to use string slicing to extract the price from the string! (The price will always be 4 string characters long)

Create your own test for this function using this string: “cheese, pepperoni, 3000”

The value you should see should be 30.

## Too Much Cheese! (Step 4)
This function returns True or False depending on if there is cheese in the order.

Remember cheese can only be topping one because it is 5 letters.

You will have to call the get_topping_one function and if that value is equal to cheese, return True. Otherwise, return False.

In case you forgot how to call functions inside of functions, here is an example:

```
def appleCount(numApples): # helper function
    total += numApples
    return total
def findTotalApples():
    totalApples = appleCount(numApples) # creating a variable and assigning it to total from the helper function
```


Hint: Pass the pizza_order parameter into get_topping_one when calling the function

## Full Order (Step 5)

Now we are putting all the steps together. You will need to write a series of if/elif/else statements to meet the following criteria:

1. if too_much_cheese returns True, return “That’s a lot of cheese!”

2. if too_much_cheese returns False AND get_price returns 45 return “Wow that’s an expensive pizza!”

3. if get_topping_two returns pineapple return “Pineapple DOES belong on pizza.”

4. elif get_topping_two returns artichoke return “That’s an interesting combo.”

5. if get_price is less than 12 OR greater than or equal to 50 return “Are we sure they’re charging us right?”

6. else return “Now that’s a smokin’ deal! Give me more!”

Hint: You will need to call the other functions you completed in prior steps

Hint: Pay close attention to the wording given to determine if you need if, elif, or else

## Turning In (Step 6)

If you feel confident about your answers in develop mode, now you can run in submit mode to make sure you get full points.

Make sure you click through the Canvas link to the assignment if you haven’t already. 

This triggers the linking process, so Canvas can get an updated score.


