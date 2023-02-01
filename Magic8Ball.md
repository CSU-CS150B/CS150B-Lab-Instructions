# Lab 03: Magic 8 Ball Lab

## Introduction
For this lab, you are going to build a simple magic eight-ball, so you no longer have to make any choices. On that note, if you haven’t, you should watch [Interstate 60](https://www.imdb.com/title/tt0165832/). All joking aside, you will build a 15 sided magic 8-ball, just for simplicity (an actual one has 20 sides for choices).

If you are curious about all the choices, you can read up more on them [here](https://en.wikipedia.org/wiki/Magic_8_Ball).

Also, if you need a refresher on if statements, go [here](https://www.tutorialspoint.com/python/comparison_operators_example.htm).

## Step 1 - Reading the code
First take a look at the provided code. You should change the comments to include your name at the top of the file. Furthermore, you will notice all the functions are ‘stubbed’ out for you. This means we have provided the function signature, and a dummy return value that you will replace completely.
We have also provided one function in its entirety, so you can use it as a sample/template to look at.
```python
def get_positive_answer(answer):
    ans = "You may rely on it." 
    if answer == 0:
        ans = "As I see it, yes."
    elif answer == 1:
        ans = "Signs point to yes."
    elif answer == 2:
        ans ="Outlook good."
    elif answer == 3:
        ans = "Without a doubt."
    return ans
```

There are also some lines under that method commented out. You should uncomment them and see what happens. In all languages it is good to test frequently, and often, and this is exactly what we are doing here. We have provided sample tests throughout the code that you should feel free to use, and add others.

This program requires input, so in the Enter program input (optional) box enter the word yes or no. For now, we suggest just putting no (or n) in the box, until you have completed the lab.

## Step 2 - get_negative_answer(answer)
get_negative_answer is just like get_positive_answer however the tone of the answer is negative instead of positive.
We completed get_positive_answer, but you need to complete get_negative_answer. Right now, it is stubbed out with
```python
def get_negative_answer(answer):
    ans = ""
    return ans
```

You will have five options that can be assigned to ans, using if/elif statements. You can follow the model above provided in get_positive_answer, or come up with your own. In either case, the following options need to be returned based on the ‘number’ of answer. Make sure to match spacing and punctuation exactly!
* 0 - Don’t count on it.
* 1 - My reply is no.
* 2 - My sources say no.
* 3 - Outlook not so good.
* 4 (or higher) - Very doubtful.

## Step 3 - get_no_answer(answer)
Similar to Step 2, build the if-statement for get_no_answer(answer) using the options below.
* 0 - Reply hazy, try again.
* 1 - Ask again later.
* 2 - Better not tell you now.
* 3 - Cannot predict now.
* 4 (or higher) - Concentrate and ask again.

## Step 4 - get_answer(category, answer)
You have worked on three functions (two really) that take in a single parameter to return an answer. Each of those functions are specific to a category. This function determines which of the three functions to call.

* If the category is less than 24, call and store the returned value of get_negative_answer(answer) passing in answer as the parameter.
* If the category is between 24 and 73 (including 73), call and store the returned value of get_no_answer(answer) passing in answer as the parameter.
* If the category is greater than or equal to 74, call and store the returned value of get_positive_answer(answer) passing in answer as the parameter.

You will then return the answer provided. (there may be different orders you can make the checks in)

For a quick refresher on how to call functions within if statements, here is some sample code (not related to this assignment).
```python
def a_func_with_if(val1, val2):
    ans = None
    if val1 < 0:
        ans = out_of_range(val2)
    elif val1 > 100:
        ans = out_of_range(val2)
    else
        ans = "In Range!" 
    return ans

def out_of_range(val2):
    return "Not really doing anything with {}".format(val2)
```

## Testing
This program requires input, so in the Enter program input (optional) box enter the word yes or no. You can enter yes as many times you want the program to run, but you need to end your input with no, so the program knows to end.

While you can run the program with random to test, you may find this difficult. Looking back at the other programs the past couple weeks, how can you incrementally test to make sure your method is working?

## Thinking Deeper
How would you change your code so negative numbers would still return an answer, or the 0 option is 0 or less, and the 4 option is 4 or higher?

## Turning in
Make sure to click through canvas before clicking submit for grading. Ideally, you should run it in develop mode as much as possible before clicking submit for grading.
