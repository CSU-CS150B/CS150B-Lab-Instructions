# Lab 5: Error Tracing

This lab is focused on an essential part of programming; debugging. The instructions for today are very simple, debug this code until it properly runs without error.
The majority of the problems that break the code and will be visible, which you can see in the black terminal box below your code when you run it. The structure of the error will
make it easy to trace back to the source. For example, based on your previous lab:

```
1. File "/usercode/main.py", line 30
2.    return f"The {flavor} will cost {cost} dollars.
3.           ^
4. SyntaxError: unterminated string literal (detected at line 30)
```

Line 1 tells you the file the error occurs in (not important for this course) and the line it is occuring on (very important). With this example, we know that whatever problem we're having 
is happening on line 30 in our code. 
Line 2 writes out the line that is causing the error. The error should be visible in this line. If the error message is very long, start at the bottom and work up.
In this example, some part of this return statement is preventing the code from continuing. 
- Line 3 tries to point out where in the line the error is happening. In this example, we can see that the problem is coming from this f string, although does not point out the 
exact issue.
- Line 4 gives us the error type and its reasoning. In this example, we can see that we are getting a SyntaxError because of an unterminated string literal. This means that the 
string was started, but never ended. We have the opening quoatation mark but the string is missing its closing quotation mark. Once we fix this, we will be error free.

**Error Examples:**
```
x = "Hello World (Syntax Error: Missing closing quotation mark)
print Hello World (Syntax Error: Missing parentheses and quotation marks)
print(y) (Name Error: variable y doesn't exist)
x = int("Hello World") (Type Error: Cannot cast string to int)
```

**Logic Error Example:**
```
bill = "7.89"
tip = "1.22"
total = int(bill) + int(tip)
print("Your total bill is $" + total) #prints "8"
(Correct output would keep our cents in decimal place, but casting to int instead of float makes it a whole number)
```

## Your Lab:

To complete this lab, you will have to find the errors of each of these types and fix them. Your terminal will help in locating and identifying the problem, but it will be up
to you to get the code running properly. These instructions will not go over the code you will be using for todays lab, because the terminal should tell you everything you need.
However, a very important note is that the terminal might mention the run() function when describing an error, but it is not the issue. Do NOT remove the run() function in any
lab.

Your final output should look like:
```
    my favorite number is 7
    my 2nd favorite number is 4
    49
    11
```

Hit run to check that your code works, and trace the error from the terminal if not.
Hit submit to check your current progress against the desired output.
