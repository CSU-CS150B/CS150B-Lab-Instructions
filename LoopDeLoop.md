# Lab 08 - Loop de Loop

In this lab, you will practice creating lists and using loops. You will write four functions (Steps 2-5) and review one provided function (Step 1). Each function builds on the loop concepts from your readings and lectures.

**Learning Objectives:** By the end of this lab you will be able to create and return lists using for loops and while loops, use `range()` to control loop behavior including counting downward, write nested for loops, and use f-strings to format output.

## Step 1 - Make a List (provided for you)

Look at the function `makelist()` in your starter code. This function is already complete — you do not need to write anything for this step. Read through it carefully because you will use similar patterns in the steps that follow.

`makelist()` takes one parameter, an integer. It creates an empty list, then uses a for loop with `range()` to add each number from 0 up to (but not including) the parameter to the list. Finally, it returns the list.

**Examples:**
```python
makelist(10) # returns [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
makelist(3)  # returns [0, 1, 2]
```

Take a moment to trace through the loop by hand. What does `range(10)` produce? Why does the list end at 9 and not 10?

## Step 2 - Lift Off!

Write a function called `rocketcountdown()` that takes one parameter, an integer. This function should return a list that counts down from that number to 1, then ends with the string `"We have lift off!"`

**Here is your approach:** Create an empty list. Use a for loop that counts down from the parameter to 1. One way to do this is to loop through `range()` normally and subtract each value from the starting number, similar to how `makelist()` adds each value. After the loop finishes, append the string `"We have lift off!"` to the list. Return the list.

**Examples:**
```python
rocketcountdown(10) # returns [10, 9, 8, 7, 6, 5, 4, 3, 2, 1, "We have lift off!"]
rocketcountdown(2)  # returns [2, 1, "We have lift off!"]
```

## Step 3 - Double Loop

Write a function called `doubleloop()` that takes two parameters, both integers. This function should return a list of strings showing every pairing of numbers between 0 and the first parameter and 0 and the second parameter, separated by a colon.

You will need a nested loop — one for loop inside another. The outer loop controls the first number and the inner loop controls the second number. For each combination, use an f-string to format the two numbers with a colon between them, like `f"{i}:{j}"`.

Here is an example of how nested loops work:
```python
for i in range(num1):
    for j in range(num2):
        mylist.append(f"{i}:{j}")
```

**Examples:**
```python
doubleloop(2, 2) # returns ["0:0", "0:1", "1:0", "1:1"]
doubleloop(3, 4) # returns ["0:0", "0:1", "0:2", "0:3", "1:0",
                 #          "1:1", "1:2", "1:3", "2:0", "2:1",
                 #          "2:2", "2:3"]
```

## Step 4 - How Many Combinations?

Write a function called `howmanycombos()` that takes three parameters, all integers. This function returns a list of all possible combinations for a lock, where each combination is a string of three numbers separated by colons.

This is very similar to Step 3, but with three nested loops instead of two. The first loop goes from 0 to the first parameter, the second from 0 to the second, and the third from 0 to the third. Format each combination as an f-string like `f"{i}:{j}:{k}"`.

**Example:**
```python
howmanycombos(2, 2, 2) # returns ["0:0:0", "0:0:1", "0:1:0", "0:1:1",
                       #          "1:0:0", "1:0:1", "1:1:0", "1:1:1"]
```

## Step 5 - Cans of Pop on the Wall

Write a function called `cansofpop()` that takes two parameters, both integers. The first is the total number of cans of pop on the wall. The second is how many cans to take down each round.

This function uses a **while loop** instead of a for loop. Each time through the loop, create a string using this exact format:
```python
f"{current} cans of pop on the wall {current} cans of pop, take {takedown} down and pass them around, {remaining} cans of pop on the wall"
```

where `current` is how many cans are on the wall right now, `takedown` is how many you remove, and `remaining` is what is left after removing them.

**Here is your approach:** Create an empty list. Write a while loop that runs as long as there are cans remaining. Inside the loop, before building the string, check whether `takedown` is greater than the number of cans left. If it is, set `takedown` equal to the number of cans left so you don't end up with a negative number. Append the formatted string to your list, then subtract `takedown` from the current number of cans. After the loop ends, append the string `"All cans of pop are gone!"` to the list. Return the list.

**Example:**
```python
cansofpop(3, 1)
# returns:
# ["3 cans of pop on the wall 3 cans of pop, take 1 down and pass them around, 2 cans of pop on the wall",
#  "2 cans of pop on the wall 2 cans of pop, take 1 down and pass them around, 1 cans of pop on the wall",
#  "1 cans of pop on the wall 1 cans of pop, take 1 down and pass them around, 0 cans of pop on the wall",
#  "All cans of pop are gone!"]
```

## Testing Your Code

Before submitting, test each function in `main()`. Here are some suggested test calls:
```python
print(makelist(10))        # should give you [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
print(makelist(0))         # should give you []
print(rocketcountdown(5))  # should give you [5, 4, 3, 2, 1, "We have lift off!"]
print(rocketcountdown(1))  # should give you [1, "We have lift off!"]
print(doubleloop(2, 3))    # should give you ["0:0", "0:1", "0:2", "1:0", "1:1", "1:2"]
print(howmanycombos(2, 2, 2))  # should give you 8 items
print(cansofpop(10, 3))    # check that it ends at 0 and not a negative number
print(cansofpop(5, 5))     # what happens when takedown equals the total?
```

Think about edge cases: what should happen when you pass 0 or 1 to these functions?

## Step 6 - Turning It In

Once you have finished Steps 1-5 and tested your code, submit to Zybooks!
