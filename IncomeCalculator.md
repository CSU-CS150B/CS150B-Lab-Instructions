# Lab 02: Income Calculator Lab

## Income Calculator Lab
In this lab, you will be writing functions, returning different values, using String formatting, and calling functions within functions. If you are unfamiliar with any of these ideas, please go back through the readings, lectures, and other assignments to help you understand the concepts before starting this lab.

## Step 1: calculate_income(rate, period)
In this step, you will write a function called calculate_income() that requires 2 parameters, the first is the rate of how much one would earn in a paycheck. The second parameter will determine if one gets paid annually or quarterly.

**rate** is an integer variable which can hold any value corresponding to the amount someone is paid per pay period.

**period** is an integer variable and will either hold the value 1 for annual or 4 for quarterly this is the pay period that someone is paid on. 
Note: the function calling will always pass the value 1 or 4, you as a programmer do not need to hard code it into the function.

For example:
If someone is paid in a lump sum of $100,000 every quarter, their total income for the year would be $400,000

Calculate what the total income would be for someone per year using the variables rate and period, and return that value. Note: do **NOT** print it.

## Step 2: format_name(firstname, lastname)

This step you will write a function called format_name(). This, like the previous function, will take 2 parameters. The first parameter will be the first name of an employee and the second parameter will be their last name.

Once you have included the parameters, you will create a new String that takes the first and last name and formats them to be in the order “lastname, firstname”. The goal is to use String formatting and pass in the values of the first and last name into a new String.

**Note: Make sure there is no newline character in return string of the format_name function, otherwise the final test will fail, even though the output will look exactly the same**

For example:

```python
format_name("Spencer", "Baloga Loufek") # returns -  "Baloga Loufek, Spencer"
```

You need to return a value, but remember to test what is returned (hint: use print(format_name("first", "last")) to test!)

## Step 3: employee_info(firstname, lastname, department, email, rate, period)
This function, called employee_info(), will take in 6 parameters, first name, last name, department, email, rate, and period. You will be calling 2 other functions within this. You will need to call format_name() and calculate_income() to help you with this function.

You will create a new String that formats the given parameters, each parameter will be followed by a new line in the firmatted String (hint: \n\). The format is as follows:
```
Last, First
$income
department
email
```
To help you format Last,First and income, you should call the functions you wrote in Step 1 and Step 2 and use the Strings those functions return. Make sure to end every line with a new line!
```
Baloga Loufek, Spencer
$400000
CSU Computer Science
spencebl@colostate.edu
```
Remember: you are returning this String! Don’t use print() unless you are calling employee_info() as a test.

## Step 4: Turning it in!!
Congratulations on finishing this lab! If you have done everything correctly, you should receive a perfect score, if not, go back to the functions that return a failing test and rubber duck your way through your code to find what is causing the errors! You got this!!
