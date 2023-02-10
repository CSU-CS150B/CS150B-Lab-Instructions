# Lab 05: Pizza Order 

## Introduction
In this lab you will get more practice with branching by extracting the code from a pizza order.


The pizza order is in the following format as a string:
topping_one, topping_two, price


## Get Topping One (Step 1)
Find the get_topping_one function in zyBooks. This has already been completed for you.

Please read through it, it will give you a hint for what to do for the next functions!


To understand this function, we must first introduce slices. This is when we take a range of indices from a string (or list).


For example:
example = 'ABCDEF'
print(example[0]) # prints 'A'
print(example[0:2]) # prints 'AB'
print(example[3:6]) # prints 'DEF'


Topping one can only be 6 letters long, in order for our string slicing to work properly. Since topping one is the beginning of our pizza order we need to extract the topping starting at the first index of the string, which is where we get the 0 in pizza_order[0:7]. The index after the colon is where we want to stop the string. This character at that index will NOT be included in the string slice.
