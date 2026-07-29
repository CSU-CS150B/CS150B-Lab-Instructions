# Lab 2 - Intro to Python Instructions

**Welcome to your second lab!**\
This lab will help you get comfortable with Python basics.

You'll practice:
* printing
* variables
* user input
* type casting

These are the building blocks for all future labs so read carefully, experiment in the terminal, and run your program often!

**In this lab you will learn**
- How to print to the terminal
- How to define variables
- How to ask for user input
- How to change (cast) variable types


# Step 0 - Running Your Program

Click **run** to execute your code.

`"Hello, World!"` should print to the terminal. (This is because of the print statement already written)

Tip: Don't wait until your entire program is finished. Run your code frequently as you work through the steps to check your progress and catch any bugs you may have!


# Step 1 - Print Statements

A **print statement** displays output to the terminal.
- Text (strings) must go inside quotes:
    * ✅ `print("Hello")` -> outputs `Hello`
    * ❌ `print(Hello)` -> error (Python thinks `Hello` is a variable)
- Numbers can be printed directly:
    * `print(42)` -> outputs `42`

 --
 👉**Your task:**
 - Add a second line of output below `"Hello, World!"` that says:

   `This is my first print statement!`

When this step is complete, the terminal should look like this after hitting the run button:

```
Hello, World!
This is my first print statement!
```

Good work! You just coded your first print statement using Python!


# Step 2 -- Variables

A **variable** stores information. 

In Python you don't declare the type -- you just assign a value:

```
city = "Fort Collins"  # string is a data type for text
population = 169000    # integer is a data type for whole numbers
elevation = 5003.2     # float is a data type for decimal numbers
```

It is good practice to name your variables with meaning (i.e. age = 15 is better than x = 15). This helps your code be more readable.

 -- 👉 **Your task:**
 - Create a variable named 'animal' with the value 'elephant'
 - Create a variable named 'color' with the value 'gray' (**Note:** 'grey' will not pass the autograder, you must spell this with an 'a')
 - Use those variables in a print statement so the output is:
    * `The elephant is gray.`

Here is an example of using variables in print statements in case you're having trouble:

```
age = 34
print("I am", age, "years old.")
```

This will give the output:

`I am 34 years old.`

You can also use '+' signs instead of commas. Commas add an extra space, '+' signs do not.

```
age = 34
print("I am " + str(age) + " years old.")
```

This will give the same output:

`I am 34 years old.`

**Note:** the variable 'age' had to be converted to a string in the second method because the '+' sign "adds" (concatenates) the strings together to make one whole string. Since 'age' is an int, you can't add an int to a string. You will learn more about this in step 4.

When this step is complete, your total output to the terminal when you hit run should be:

```
Hello, World!
This is my first print statement!
The elephant is gray.
```

Run your code to test!


# Step 3 - User Input

The `input()` function pauses your program and waits for the user to type something.

This is when the program is asking for input from the user. Asking for input can be as simple as this:

`name = input()`

Though it is good practice to put a prompt in the parentheses to let your user know what input you are looking for. Adding a prompt would look like this:

`name = input("Please enter your name => ")`

`input()` will default to the string type. If you need to get a number from the user, you will need to use variable casting. Here is an example:

`age = int(input("Please enter your age => "))`

**Note:** When you run your code and have an `input()` function in it, the program is going to wait until you type something in the terminal!

-- 👉 **Your task:**
For this step we will be combining everything we have learned so far.

- Make a variable called 'username'
- Ask for input from the user, store this in the username variable
- The prompt should say "Please enter your username => " (**Note:** there is a space after the arrow)
- Print "user: " and the username you got from the input function

When this step is successfully completed, your total output to the terminal should be:

```
Hello, World!
This is my first print statement!
The elephant is gray.
Please enter your username => user: user543   # or whatever name you typed into the terminal
```

**Note:** 'user: user543' may print on a different line than 'Please enter your username => '. This is okay.


# Step 4 - Casting (Changing Types)

Sometimes you need to change a variable's type. This is called **casting**.

Examples:

```
x = "42"
y = int(x)     # string --> integer

z = 3
w = str(z)     # integer --> string
```

**Why do we have different data types in Python?**

Different types of data need different operations.

You wouldn't try to divide your name by 2, but you might divide a price by 2.

Python uses data types to know what operations make sense for each piece of data.
* **Strings** (text): joining, splitting, capitalizing
* **Integers** (whole numbers): adding, subtracting, multiplying
* **Floats** (decimals): calculations with precision

Data types help Python understand your intent and catch mistakes before they cause problems.

-- 👉 **Your task:**

You are given:

```
string1 = "14.2"
num1 = 3
```

* Cast 'string1' to a float
* Cast 'num1' to a string
* Print each value on its own line

Here is an example of casting a string to an int:

```
example_string = "54"
num = int(example_string)   # string --> int
```

If this step has been successfully completed, your terminal should show this when you hit run:

```
Hello, World!
This is my first print statement!
The elephant is gray.
Please enter your username => user: user543
14.2
3
```


# Step 5 - Submitting

When your program runs without crashing and your output matches the expected output:
* **Double-check your results** against the provided examples
* **Submit your work** by clicking the orange "Submit for grading" button
* **Review feedback if needed** - Don't worry if you don't recieve full credit on your first attempt! You have multiple submission opportunities and Zybooks will provide feedback to help you identify any issues if your code didn't pass. (**Note:** text highlited in green is something you added that was not expected, text highlighted in red is something expected that you didn't add)

⚠️ Important: Test your code thoroughly before submitting. Run it often!

---

✅ Congratulations! You've completed your second lab!
