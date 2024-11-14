# NBA dataset Practical Project - CS150B
The goal this practical project is to build an application that will read through a dataset that contains the preformance of every NBA player for a single season and display information about a given team depending on input given by the user. Given team name "DEN" and stat type "Free Throw" the output of your program should look like:

```
Stats for the NBA team: DEN
The average age of the players is 26.
Vlatko Čančar has the highest 3 point accuracy at 0.583
He is 24 which is younger than average.
Carlik Jones has the lowest 3 point accuracy at 0.0
He is 24 which is younger than average.
```
### Understanding the data:
Before you start coding, it is highly recommended that you download the dataset and develop an understanding of the data we’ll be working with. Pay attention to which columns might be important for this project. Also, note that the dataset uses abbreviations for team names. Here is a list of the team abbreviations if you want to test your code on a specific team.

https://en.wikipedia.org/wiki/Wikipedia:WikiProject_National_Basketball_Association/National_Basketball_Association_team_abbreviations

### What is all this code?:
Lets walk through all the code that we have provided to start you out on this project starting with the main function:
```
def main():
    # Get user input
    user_team = input("Enter your favorite team: ")
    print("Stat types: [Free Throw | Field Goal | 3 Point | 2 Point]")
    stat_type = input("Chose stat: ")
    
    # This code handles changing the index based on the users input
    global index_stat
    index_stat = input_handler.get(stat_type.lower())
    if index_stat is None or index_stat < 0:
        print("Invalid stat type.")
        return -1
    
    # Your work starts here
```
This function is the starting point for the entire project and the code provided just gets you started. Most of it should be familar to you but a couple lines may seem kind of strange. Lets work through them to understand.
* user_team = input("Enter your favorite team: ") : this line is getting the name of the team that the user whats to view data for.
* print("Stat types: [Free Throw | Field Goal | 3 Point | 2 Point]") : this line prints the options of the different statistics the user can select.
* stat_type = input("Chose stat: ") : this line gets the statistic from the user.
  
The *main()* function is started for you but not completed for you.

```
input_handler = {
    "field goal": 10,
    "3 point": 13,
    "2 point": 16,
    "free throw": 20
}
```
What is input_handler at the top of the program?
  * input_handler is a dictionary that conatins the indices at which all the different statistics that we will be exploring through this project are stored. You shouldn't worry about this to much, just treat the index you get from it as you would any other index. It just allows you code to handle the different output possiblities.

### Step 1 - Reading the CSV:
To begin the project you should start by writing the read_csv() function. The function takes in a string which contains a path to the CSV file location and returns a list of lists.
Remember the format of our output should look something like:

```
[[Name, Age, Weight, Favorite Food],
 [Nels, 22, 173, Pizza],
 [Frank, 47, 200, Hamburger],
 [Lisa, 20, 140, Ice Cream]]
```
This is situation each list inside the larger list is acting like a row in a spreadsheet where the nth element in the row corresponds to the nth column indentified in the first row. 
So the elements in the 0th postition of every list form the column:
```
[Name]
[Nels]
[Frank]
[Lisa]
```
### Step 2 - Filtering the data:
The next step is filtering the data to return a filtered dataset that contains only the values for players of a certain team.
This function has two parameters: *Team_Name* which contains the name of the teams that you will be filtering by and *data* which contains the data you read in the last step.
The first thing to do is to find the index at which the team is located and store this information somewhere. The rest of the project will be much easier if you don't have to keep going back to the dataset to remember which values are stored where. It is recomended to use global variables that have been left commented out on the top of the page. 
```
# index_name = ?
# index_age = ?
# index_team = ?
```
By storing the index of age in this variable you can simply type *index_team* whenever you are trying to access the team for a given player.
Once you've done this the general structure of the function should be:
```
# THIS IS PSEUDOCODE IT WILL NOT RUN
def filter_data
  for row in data
    if row[index_team] is equal to *Team_Name* add it to the filtered dataset.
```
If you are struggling with this part please look back at your CSV Lab as much of what you learned in that lab applies to the first 2 steps of this project.

### Step 3 - Finding Best & Worst Players:
The next step finding the players on the team who preform the best and the worst in the given area by writing the functions *find_best_player()* and *find_worst_player()*. Both functions take in two arguments, *data* which is the dataset filtered by team and index which is the index of the statistic in which we are interested. 

This is the first section in which we will be using the *index_stat* variable that we discussed at the start of the instructions. Remeber that *index_stat* is just a variable that stores a number that represents the index of the stat that you selected at the start of the lab. You should use it whenever you need to access the statitistic because if you do not your output will not change when the users inputs different values.

The general algorithm for finding the best player is:
```
def best_player
  highest = 0
  player = []
  for row in filtered data
    if float(row[index_stat]) >= highest 
      then highest should be set equal to float(row[index_stat])
      player = row
  return player
```
Remeber to include *>=* or *<=* or your answers will not be correct.
You may be suprised that we are returning a list instead of a single value from the is function but this is because we can use this list to represent a single player which has multiple atributes so that we can find other information about the player such as age later on.

To find the worst player you should use a similar approach but you should set the value you are comparing to to something impossibly large such as 1,000,000 and then replace it if the value from the dataset is smaller than it.

### Step 4 - Average age:
For this step we will be calculating the average age of all the players on the team. This function takes in one input *data* which is the filtered dataset and returns and interger. 
The first thing to to as always is to find the index of the players age in the dataset and then store it somewhere.
Average age should be calculated as: 
```
average_age = sum_of_team_ages // number_of_players
```
We use using integer(or floor) divsion *//* so that we get back a whole number for age.

### Step 5 - Printing stats:
  For this step you are printing out the info about a given team base on the parameters provided by the user.
  ```
"Stats for the NBA team: {team_name}"
"The average age of the players is {average_age}"
"{highest_player[index_name]} has the highest {stat_type} accuracy at {highest_player[index_stat]}"
"He is {highest_player[index_age]} which is {younger/equal/older than average}."
"{lowest_player[index_name]} has the lowest {stat_type} accuracy at {lowest_player[index_stat]}"
"He is {highest_player[index_age]} which is {younger/equal/older than average}."
```
There are two helper functions in the templete for this step which are not strictly neccessary but highly recommended to make your code much more readable and therefore debuggable. The first is *compare_age()* which takes in  the teams average age and the players age and returns a string based on how old the player is in comparision to the average. 
```
if greater than average
  return "is older than average"
elif equal to average
  return "is the average age"
else
  return "is younger than average"
```
This function will save you from having to write the same condidtionals over and over again and is highly recomeded. 

The next helper function is *print_info()* which prints out the info for a given player so that you do not have to rewrite the same code twice for the higest and lowest players.

Finally *print_stats()* is a vital function from which all your other functions are called. It takes in the filtered dataset along with the team name and the stat type. To check your output carefully against the provided examples as the ZyBooks is harsh on grading whitespace.

