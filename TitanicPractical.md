# Practical Project > Titanic

The titanic sunk in 1912, but the general public doesn't know much about its passengers. This dataset contains the details of passengers of the "unsinkable titanic".

## Introduction
In this practical you will be extracting data from a csv file about Titanic passengers, you will be trying to gather information about them as a whole.

__Make sure to open the CSV file and look at it to understand how the file works__

For quick reference, the file is laid out as follows.
* PassengerId (ID number of the given passenger)
* __Survived__ (Did the passenger survive? 1 if yes 0 if no)
* Pclass (What class of ticket did the passenger buy,values range from 1-3)
* __Name__ (What is the name of the passenger)
* __Sex__ (What is the sex of the passenger)
* Age (How old was the passenger at the time of the disaster)
* SibSp (How many siblings and spouses did the passenger have aboard the ship)
* Parch (How many parents and children did the passenger have aboard the ship)
* Ticket (What ticket did the passenger have, ticket number)
* __Fare__ (How much did the ticket cost)
* Cabin (What cabin was the passenger in)
* Embarked (Port of Embarkation C = Cherbourg; Q = Queenstown; S = Southampton)

__The names in bold are the columns that you will be using in your program.__

## Variables (Step 0)
you will create four variables as file wide variables (often called global). Each variable is the index value of the column in the titanic.csv file.
```python
name_index = ??
surv_index = ??
sex_index = ??
fare_index = ??
```

**Note:** Remember that you will be dealing with a list in future methods. Be sure to brush up on how to access certain values of a list.

## Step 1: csv_reader(file)
Reads a file using csv.reader and returns a list of lists with each item being a row, and rows being the values in the csv row. Look back at the CSV lab on reading csv files into a list. The function will be mostly the same with one exception. 

**Since the file has a header row, you will need to either skip the first row, or remove it after you are done.**
**NOTE:*** Recall that next(reader) can be used to skip a row.


You should test this now. Maybe print out the length of the list returned from the method. For example, a test could be
```python
print("TESTING", len(csv_reader(file))) #where file is set above to either titanic.csv or the tests file
```

## Step 2: longest_passenger_name(passenger_list)
This function will take in the list created from csv_reader and will parse through each list to find the various names of all the passengers.

It will then try to find the longest name, and return that name at the end of the method.

Make sure to test this method!

Here is an example test (notice, we are just creating our own list)
```python
test_list = [[1,0,3,"Longest Name"],[2,0,2,"Short"]]
print("TESTING", longest_passenger_name(test_list))
print("TESTING", longest_passenger_name(csv_reader(filename)))
```

## Step 3: total_survival_percentage(passenger_list)
This function will take in the list created from csv_reader and will parse through the list to find what percentage of passengers survived the sinking of the titanic.

**NOTE:** In the survived column, those who survived will have a 1, while those who died will have a 0.

The total number of survived should be divided by the total number of people to find the percentage.
```python
test_list = [[1,0],[2,1],[3,1],[4,1]]
print("TESTING",total_survival_percentage(test_list))
print("TESTING", total_survival_percentage(csv_reader(filename)))
```
your answer from the file should be a long decimal value and that is okay, we will format it in a later step!

## Step 4: survival_rate_gender(passenger_list)
This function will do something very similar to step 3, but instead of keeping an overall survival percentage, it keeps a seperate survival percentage for male and female.

This means you will need to count their number of survives and total number for each gender seperately.

At the end you will return a tuple in the form of (male_surivival_rate, female_survival_rate)
Remember in order to return a tuple you use the form return (item, item)

```python
test_list = [[1,1,3,"alice","female"],[2,0,2,"John","male"],[3,0,1,"Jane", "female"]]
print("TESTING",survival_rate_gender(test_list))
print("TESTING", survival_rate_gender(csv_reader(filename)))
```

## Step 5: average_ticket_fare(passenger_list)
This function will take in a list created from the csv reader and will parse through it to find the average ticket price, as denoted by the fare column of the file.

## Step 6: main()
This is the function that you will write to call all the functions that you have already written. You will need to print out each function return to match the formatting in order.

**NOTE:** Tuples can be accessed similar to a list. tuple[0] accesses the first element with tuple[1] being the second and so on.

**All decimal numbers should be formatted to two decimal places**
```
Longest Name: Penasco y Castellana, Mrs. Victor de Satode (Maria Josefa Perez de Soto y Vallejo)
Total Survival Percentage: 0.38
Male Survival Percentage: 0.19
Female Survival Percentage: 0.74
Average Ticket Cost: 32.20
```
