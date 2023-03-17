# Lab 08 GPS Distance Calculator Lab
## Introduction
For this lab, you are going to use GPS coordinates read in from a file to calculate the distance between cities. In doing so, you will learn how to read in files, search through data, parse strings, and convert strings to numerical values.

## Step 0 - Read the code

Before you attempt to write any of the required functions, take some time to read through the code that has been provided. 
The main and distance_between() functions have been provided. 
These functions provide a framework so that you can see what results are expected from each of the functions you will be writing.

## Step 1 - Write read_file()

The goal of this function to return a list of lists, where each line/city in the file gets its own list. The file you will be working with looks like this:

``` 
Fort Collins,40°35'6.9288"N,105°5'3.9084"W
Denver,39°44'31.3548"N,104°59'29.5116"W
Boulder,40°0'53.9424"N,105°16'13.9656"W
New York,40°42'46.7346"N,74°0'25.9374"W
Los Angeles,34°3'12.042"N,118°14'32.4564"W
Sydney,33°52'21.9324"S,151°12'22.23"E
Rio de Janeiro,22°54'40.1538"S,43°12'15.9156"W
London,51°30'0.5466"N,0°7'34.449"E
Tokyo,35°41'22.2216"N,139°41'30.1194"E
```

Sample output:

``` python
[['Fort Collins','40°35'6.9288"N','105°5'3.9084"W'], 
 ['Denver','39°44'31.3548"N','104°59'29.5116"W'],
  ...
]
```
You can and should use the CSV library as you used in the previous lab! This would involve looping through every line to append it to the List as you read in the file.

## Step 2 - Write get_city_info()

Now that we have all of our data stored in way that we can access easier, lets work on getting data for just one city at a time.

This function will take two parameters: the data that returned from read_file() and the name of the city we want data for.

Check each city to see if the name (what index will the name be in?) matches the city name parameter that was passed in.
If they match, return the list of data for that city.

For example, if the city was ‘Fort Collins’, you would return ['Fort Collins','40°35'6.9288"N','105°5'3.9084"W'].

If the city that you were looking for was not found, return the data for Fort Collins by default.

Hint: Convert the city names to lower case to make your comparisons more forgiving. (Use: .lower())

## Step 3 - Write get_city_latitude()

This is a very simple function that takes the list of data for a single city and returns the value of the latitude from that list (hint: what index is the latitude at?).

## Step 4 - Write get_city_longitude()

This function is almost identical to the previous one except the index for the longitude is different from the index for latitude.

## Step 5 - Write convert_degrees_to_decimal()

This function will be the most challenging of the functions in this lab. Given a string value version of either latitude or longitude, you must return its decimal value.
```python
Given: 40°35’6.9288”N # 40 degrees, 35 minutes, 6.9288 seconds, direction north

Return: 40.585258 # decimal value of the given string.
```
In order to do this, you will need to isolate the numbers from the string, convert them to a float, and then manipulate them accordingly.

There are multiple ways to do this, but every way involves exploiting the pattern of the string.

We know, no matter the values, the values before ° are the degree values, the values before ‘ but after ° are the minutes, and between ‘ and “ are the seconds.

The last character is always a single digit, and tells you the direction.

Remember that string .find helps you find a location of an character in a string, so:
```python
degree_char = str_value.find('°') # return 2 in the string 40°35'6.9288"N
```
would return 2. However, we can then use string slice to get the first bit from there
```python
degree = float(str_value[0: degree_char])
```

for the minutes, we may need to use a different start location for the start of the slice, in place of 0. What value could that be that you already have? Remember that the beginning index in a string slice is inclusive so maybe add 1 to it, so you don’t end up with an Off By 1 error?

SUGGESTION: Just see if you can break the string up first, printing out between every line as you write this function! Else it will be extremely easy to get lost. It is also very good to write out in english what this function is doing! This is harder to think about, than it is to write!

The decimal value is calculated using this equation:
```python
decimal_value = degree_value + (minute_value / 60) + (second_value / 3600) * direction
```
__The degree value comes before °, the minute values is right before the ‘, the second value is right before the “, and the direction is dependant on the letter at the end. If the letter is N or E, direction is 1. If the letter is S or W, direction is -1.__

### Windows only (outside zybooks)
If you are running this script on windows and getting the float cannot be converted error, you need to modify your code to include the following:
```python
float(str_value[0:degree_pos].strip("Â"))
```
(see the strip). This is because windows hides an invisible character in the file, that doesn’t happen on non-windows based systems. There are other ways to fix this, but this is the simplest way for this project.

## Testing
Each time you complete one of these functions, you should test them individually in the __run_tests()__ function. Give an input that you know the output for and make sure that is what you are actually getting. Waiting until you completed every to test will make finding where you went wrong very difficult.

## Turning in
Make sure you test using the develop mode before submitting for grading!
