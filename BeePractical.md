

Effects of insecticide on bees (usda.gov). Field and Lab data regarding the effects of 4 sublethal concentrations of a neonicotinoid insecticide (Imidacloprid) on honey bees and about a dozen native bee species.
Details

#### The columns in the data are in order:

- 0 - Level of Sociality
- 1 - Degree of floral specialization
- 2 - Habitat floral host
- 3 - bee species
- 4 - bee genus/species
- 5 - Date bee captured and installed in bioassay unit (Julian day)
- 6 - bee sex
- 7 - Imidacloprid concentration (parts per billion)
- 8 - bee longevity in bioassay (days)
- 9 - days paralyzed
- 10 - days active
- 11 - % of days bee is paralyzed

#### The parts you will need for the methods you are tested on are:

__Level of Sociality:__

this indicates whether a bee is social or solitary

__bee genus/species:__

This states the genus or species of the bee

__Imidacloprid concentration (parts per billion):__

States the concentration of insecticide used

__bee longevity in bioassay (days):__

This states the days the bee survived

__days paralyzed:__

This states the amount of days the bee was paralyzed

## main.py

This file is the main driver file of your program. It will display the averages for the given input (Sociality or Genus/Species).

The final output will print out the average imidacloprid concentration, longevity, and days paralyzed for the given input (Sociality or Genus/Species). Use the following examples as a template for the output

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

Required Functions

The goal of this practical is to be able to analyze a large amount of data using python and clearly display the results. The example output above should be used as a guideline for the finished product however, you will be graded on a function by function basis. The following functions are required:
## read(csv_file)

This function takes the name of a csv file and will return a list of lists where each row is a list. 

No filtering is done at this step. 

Import and use the csv library or the pandas library.
## filter_data(user_input, data)

This function takes the sociality/species/genus that the user provided and the data returned from the read() function as parameters.

Search through each row of the data and compare the specicies and sociality levels to the user_input variable.

The rows that are equal to the user_input variable are then added to a new list and returned.

__Make sure that you use the .upper() method before doing the comparison to make sure that capitalization doesn't matter__

Example:
```
GIVEN: user_input = APIS
       data = [['SOLITARY', 'Apis', 1, 2, 3],
               ['Social', 'Agopostemon', 1, 2, 3],
               ['SOLITARY', 'Apis', 1, 2, 3]]
RETURN: [['SOLITARY', 'Apis', 1, 2, 3],
         ['SOLITARY', 'Apis', 1, 2, 3]]
```
## calc_averages(filtered_data)

Given the filtered data from the earlier step, calculate and return the average for the Imidacloprid concentration (parts per billion), bee longevity in bioassay (days), and days paralyzed columns.
## calc_minimums(filtered_data)

Given the filtered data, calculate and return the minimum for the Imidacloprid concentration (parts per billion), bee longevity in bioassay (days), and days paralyzed columns.
## calc_maximums(filtered_data)

Given the filtered data, calculate and return the maximum for the Imidacloprid concentration (parts per billion), bee longevity in bioassay (days), and days paralyzed columns.
print_stats(user_input, stat_type, stats)

This function takes the user’s input, the type of statistic you are printing, and the statistics that will be printed. The statistics should show 2 decimal places.

Example output for print_stats('Solitary', 'Average', [29.5802, 4.9714, 1.2649])
```
Averages for Solitary bees:
Average Imidacloprid Concentration: 29.58
Average Longevity: 4.97
Average Days Paralyzed: 1.26
```
## run(data)

This function takes all of the functions you have created this far and puts them together. It should start by asking for input. Then, filter the data and perform a check to make sure the input was valid (make sure you have data to work with). Next, calculate and print the averages, minimums, and maximums. Finally, ask the user if would like to see more data. This method should return True if it needs to be run again (there are two cases where this needs to occur) and return False if it does not need to run again.

When asking for input, prompt the user with this sentence: “Enter the species/genus or the sociality of bee you would like information about: “

When asking if the user would like to see more data, prompt the user by asking: “Would you like to see more data? (Y/N) “
## main()

This function will be provided for you in order to keep the structure consistent for everyone.
```python3
def main():
    if len(sys.argv) != 2:
        print('Invalid arguments given')
        return
    data = read(sys.argv[1])
    while run(data):
        continue
```
Suggestions / Insights

Before you start coding it is always good to plan your code out. Look at what each method is asking for and think about how you can accomplish it. (Think about how an average is calculated, and how to compare strings.)

If you would like to expand upon the data there are many different things you could look for. Examples are:

- Floral host differences across averages
- Sex differences across averages
- Overall statistics of the bees

These are just examples, feel free to come up with your own ideas of sorting/processing the data.
Reference

Sampson, Blair J.. (2019). Raw data for imidacloprid effects on native bees. Ag Data Commons. https://doi.org/10.15482/USDA.ADC/1503843. Accessed 2020-11-7.
