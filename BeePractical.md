# Insecticide Effect On Bees

For this assignment, you will be reading and filtering CSV data focused on the effects of insecticide on bees, sourced from usda.gov. This is field and lab data regarding the effects of 4 sublethal concentrations of a neonicotinoid insecticide (Imidacloprid) on honey bees and about a dozen native bee species.

As you work through this program, don't be intimidated by its size!<br>These instructions break the work you have to do into manageable chunks, so just work one step at a time, reading the instructions thoroughly and thinking through how you will go about coding each function.

* **The data for this project is stored in "BEETOX_updated.csv"**

#### The columns in the data are in order:

- 0 - Index in the file
- 1 - Level of Sociality : indicates whether a bee is social or solitary.
- 2 - bee genus/species
- 3 - Imidacloprid concentration (parts per billion)
- 4 - bee longevity in bioassay (days)
- 5 - days paralyzed


| Index | Level of Sociality | Bee Genus/Species | Imidacloprid Concentration (ppb) | Bee Longevity in Bioassay (days) | Days Paralyzed |
|-------|--------------------|-------------------|----------------------------------|----------------------------------|----------------|
| 0     | SOLITARY           | ANDRENA           | 20                               | 5                                | 0              |
| 1     | SOLITARY           | ANDRENA           | 100                              | 3                                | 3              |
| 2     | SOLITARY           | APIS              | 0                                | 1                                | 0              |
| 3     | SOLITARY           | APIS              | 0                                | 3                                | 0              |
| 4     | SOLITARY           | APIS              | 0                                | 4                                | 0              |
| 5     | SOLITARY           | APIS              | 0                                | 5                                | 1              |
| 6     | SOLITARY           | APIS              | 0                                | 8                                | 0              |
| 7     | SOLITARY           | APIS              | 0                                | 8                                | 0              |
| 8     | SOLITARY           | APIS              | 0                                | 10                               | 0              |
| 9     | SOLITARY           | APIS              | 0                                | 11                               | 0              |
| 10    | SOLITARY           | APIS              | 5                                | 5                                | 2              |
| 11    | SOLITARY           | APIS              | 5                                | 8                                | 3              |
| 12    | SOLITARY           | APIS              | 5                                | 10                               | 3              |
| 13    | SOCIAL             | APIS              | 5                                | 10                               | 4              |
| 14    | SOCIAL             | APIS              | 5                                | 11                               | 0              |




## main.py

All of your code will be written in main.py. The finished program will display the averages for the given input (Sociality or Genus/Species).

The final output will print out the average _imidacloprid concentration_, _longevity_, and _days paralyzed_ for the given input (Sociality or Genus/Species).

## Required Functions to Implement (Graded)

The goal of this project is to be able to analyze a large amount of data using python and clearly display the results. You will be graded on a function by function basis. The following functions are required:

## Step 0: run(data) (for tests)

This function will eventually take all of the functions you create and put them together.

## Step 1: read(csv_file)

This function takes the name of a csv file and will return a list of lists where each row is a list. 

No filtering is done at this step. 

Import and use the csv library or the pandas library.

## Step 2: filter_data(user_input, data)

This function takes a user_input that can be the sociality, species or genus that the user provid and a data (list of lists) returned from the read() function (from **Step 1**) as parameters.

You must look through each row of the data (list of lists) and compare the specicies and sociality levels against the user_input variable.

If the row is equal to the user_input variable, then add the row to a new list and return it.

__Make sure that you use the .upper() method before doing the comparison to make sure that capitalization doesn't matter__

__DO NOT USE IN WHEN COMPARING WITH THE FILTER!__

Example:
```
GIVEN: user_input = APIS
       data = [['SOLITARY', 'Apis', 1, 2, 3],
               ['Social', 'Agopostemon', 1, 2, 3],
               ['SOLITARY', 'Apis', 1, 2, 3]]
RETURN: [['SOLITARY', 'Apis', 1, 2, 3],
         ['SOLITARY', 'Apis', 1, 2, 3]]
```
## Step 3: calc_averages(filtered_data)

Given the filtered_data from **Step 2**, you are going to calculate and return the average for each one of the 3 following columns in the table :

- the Imidacloprid concentration (parts per billion).

- bee longevity in bioassay (days).

- and days paralyzed.

Return these three values in a tuple with the form (average concentration, average longevity, average days).

__We recommend you complete this using the helper function calc_average(data, column_index) described below as it will make your life easier, however it can be completed without it.__

calc_average(data, column_index) : The function takes two parameters, the data you want to look through and the index of the column that you want the average of, then finds the average value in that column.

## Step 4: calc_minimums(filtered_data)

Given the filtered_data from **Step 2**, yoou are going to calculate and return the minimum for each one of the 3 following columns in the table :

- the Imidacloprid concentration (parts per billion).

- bee longevity in bioassay (days). 

- and days paralyzed.

Return these three values in a tuple with the form (minimum concentration, minimum longevity, minimum days).

__We recommend you complete this using the helper function calc_minimum(data, column_index) described below as it will make your life easier, however it can be completed without it.__

calc_minimum(data, column_index) : The function takes two parameters, the data you want to look through and the index of the column that you want the minimum of, then finds the minimum value in that column.

## Step 5: calc_maximums(filtered_data)

Given the filtered_data from **Step 2**, yoou are going to calculate and return the maximum for each one of the 3 following columns in the table :

- the Imidacloprid concentration (parts per billion).

- bee longevity in bioassay (days).

- and days paralyzed.

Return these three values in a tuple with the form (maximum concentration, maximum longevity, maximum days).

__We recommend you complete this using the helper function calc_maximum(data, column_index) described below as it will make your life easier, however it can be completed without it.__

calc_maximum(data, column_index) : The function takes two parameters, the data you want to look through and the index of the column that you want the maximum of, then finds the maximum value in that column.

## Step 6: print_stats(user_input, stat_type, stats)

This function takes the user’s input, the type of statistic you are printing, and the statistics that will be printed. The statistics should show 2 decimal places.

Example output for print_stats('Solitary', 'Average', (29.5802, 4.9714, 1.2649))
```
Averages for Solitary bees:
Average Imidacloprid Concentration: 29.58
Average Longevity: 4.97
Average Days Paralyzed: 1.26
```

## Step 7: finish run(data)

The first thing the run function needs to do *only once* is to ask for the name of the file that the data will be read from. This should not be repeated with the rest of the loop you will create.

Your loop should start by asking for input. This user input will be the name of the species or genus or the level of sociality that the data will be filtered by. Then, filter the data and perform a check to make sure the input was valid (make sure you have data to work with). Next, calculate and print the averages, minimums, and maximums. Finally, ask the user if would like to see more data. If the user inputs 'Y' the loop should continue to execute and if the input is 'N' the loop should stop executing.
 
When asking for input, prompt the user with this sentence: “Enter the species/genus or the sociality of bee you would like information about: “

When asking if the user would like to see more data, prompt the user by asking: “Would you like to see more data? (Y/N) “

## Example outputs
### Example given genus (Apis):
```
Averages for APIS bees:
Average Imidacloprid Concentration: 32.07
Average Longevity: 9.73
Average Days Paralyzed: 2.12

Minimums for APIS bees:
Minimum Imidacloprid Concentration: 0.00
Minimum Longevity: 1.00
Minimum Days Paralyzed: 0.00

Maximums for APIS bees:
Maximum Imidacloprid Concentration: 100.00
Maximum Longevity: 20.00
Maximum Days Paralyzed: 13.00
```
### Example given Sociality (Solitary):
```
Averages for Solitary bees:
Average Imidacloprid Concentration: 29.51
Average Longevity: 5.27
Average Days Paralyzed: 1.34

Minimums for Solitary bees:
Minimum Imidacloprid Concentration: 0.00
Minimum Longevity: 1.00
Minimum Days Paralyzed: 0.00

Maximums for Solitary bees:
Maximum Imidacloprid Concentration: 100.00
Maximum Longevity: 24.00
Maximum Days Paralyzed: 14.00
```
Example given invalid input:

Test not found. Please enter valid Sociality or Species/Genus
## Conclusion

This reaches the end of what is required of your coding practical, however, after submitting, if you'd like to use python to investigate your data further, you are highly encouraged to do so!
If you would like to expand upon your data analysis you can load in the expanded data set instead by simply entering "BEETOX.csv", there are many different things you could look for. Examples are:

- Floral host differences across averages
- Sex differences across averages
- Overall statistics of the bees

These are just examples, feel free to come up with your own ideas of sorting/processing the data.
Reference

Sampson, Blair J.. (2019). Raw data for imidacloprid effects on native bees. Ag Data Commons. https://doi.org/10.15482/USDA.ADC/1503843. Accessed 2020-11-7.
