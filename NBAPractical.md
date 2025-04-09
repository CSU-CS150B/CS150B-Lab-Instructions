# NBA dataset Practical Project - CS150B
The goal this practical project is to build an application that will read through a dataset that contains the preformance of every NBA player for a single season and create the opitmal team based on a parameter given by the user. Given an input of 1 the output of your program should look like:

```
Select a team-building strategy:
1. Scoring (prioritize Points)
2. Rebounding (prioritize Rebounds)
3. Playmaking (prioritize Assists)
4. Custom (student defined)
Enter your choice (1-3): 1

=== MY DREAM TEAM ===
POSITION PLAYER                    PTS   REB   AST
--------------------------------------------------
C     Joel Embiid               30.6  2.1   4.2
PF    Giannis Antetokounmpo     29.9  2     5.8
SG    Devin Booker              26.8  0.7   4.8
PG    Luka Dončić               28.4  0.9   8.7
SF    LeBron James              30.3  1.1   6.2
--------------------------------------------------
TEAM RATING: 221.3
```
### Understanding the data:
Before you start coding, it is highly recommended that you download the dataset and develop an understanding of the data we’ll be working with. Pay attention to which columns might be important for this project. Also, note that the dataset uses abbreviations for team names. Here is a list of the team abbreviations if you want to test your code on a specific team.

https://en.wikipedia.org/wiki/Wikipedia:WikiProject_National_Basketball_Association/National_Basketball_Association_team_abbreviations

The project also deals heavily with player positions so here is a guide to the abreviations used.
| Position | Abbreviation |
|----------|--------------|
| Point Guard | PG |
| Shooting Guard | SG |
| Small Forward | SF |
| Power Forward | PF |
| Center | C |

### What is all this code?:
Lets walk through all the functions that you will have to implement to complete this project:
```

1. read_csv(filename)
   - Reads NBA player data from a CSV file
   - Returns data rows and header

2. filter_data(data, position)
   - Filters player data to only include players of a specific position
   - Returns filtered dataset

3. find_max(data, stat_index)
   - Finds the player with the highest value for a given statistic
   - Returns the best performing player's data

4. build_team(data, team_template)
   - Creates optimal team based on specified statistics for each position
   - Uses filter_data and find_max for each position
   - Returns complete team dictionary

5. calculate_team_rating(team)
   - Sums player ratings from the team
   - Returns total team rating

6. print_team(team)
   - Displays formatted team information and rating

7. get_user_strategy()
   - Gets user input for team-building strategy
   - Returns dictionary with position-statistic mappings

8. main()
   - Coordinates program execution
   - Calls other functions in sequence
    
```

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
This function has two parameters: *data* which contains the data you read in the last step and *postion* which is the position you will be filtering for.
The first thing to do is to find the index at which the player position is located and store this information somewhere. The rest of the project will be much easier if you don't have to keep going back to the dataset to remember which values are stored where. It is recomended to use global variables on the top of the page. If you are struggling to figure out the indices try printing out the header which is returned from the *read_csv* function with the data to see way data is stored in each column.
```
# index_position = ?
# index_pts = ?
# index_ast = ?
```
By storing the index of age in this variable you can simply type *index_team* whenever you are trying to access the team for a given player.
Once you've done this the general structure of the function should be:
```
# THIS IS PSEUDOCODE IT WILL NOT RUN
def filter_data
  for row in data
    if row[index_postion] is equal to *position argument* add it to the filtered dataset.
```
If you are struggling with this part please look back at your CSV Lab as much of what you learned in that lab applies to the first 2 steps of this project.

### Step 3 - Finding Best Player:

The `find_max()` function identifies the player with the highest value for a specific statistic. This function requires two parameters:
- `data`: The filtered dataset containing players of a specific position
- `stat_index`: The column index of the statistic we want to maximize

The function implements a straightforward maximum-finding algorithm:

1. It initializes `max_player` with the first player in the dataset
2. It iterates through each player in the dataset
3. It compares the current player's statistic with the current maximum
4. If the current player's statistic is **greater than** the current maximum, this player becomes the new maximum

```python
#THIS IS PSEUDOCODE IT WILL NOT RUN
max_player = data[0]
# Loop through each player in the filtered data
for each row in data:
    # Compare current player's stat with maximum player's stat
    # CRITICAL: Must use > comparison for correct results
    if (row stat) > (max_player stat):
        # Update maximum player when better one is found
        max_player = row
        
# Return the entire player record, not just the value
return max_player
```

### Step 4 - Building the Team:

The `build_team()` function assembles the optimal basketball team by finding the best player for each position based on specified statistics. This function takes two arguments:
- `data`: The complete dataset of all players
- `team_template`: A dictionary that maps positions to statistical indices for selection

The function works by:

1. Initializing an empty team dictionary with all five basketball positions (PG, SG, SF, PF, C) set to None
2. Iterating through each position-statistic pair in the team_template
3. For each position:
   - Filtering the dataset to only include players of that position using `filter_data()`
   - Finding the best player for that position based on the specified statistic using `find_max()`
   - Adding that player to the team dictionary under the appropriate position key

The team dictionary uses lowercase position abbreviations as keys ('pg', 'sg', 'sf', 'pf', 'c') with each value being the complete player record.

This approach creates a modular design where the `build_team()` function coordinates the overall team creation process by utilizing the specialized filtering and player selection functions from previous steps.

### Step 5 - Calculate team rating:
The `calculate_team_rating()` checks the overall performance of the team generated in the last step:
- `team`: A dictionary containing the team we made in step 4\
This function should initalize a variable *total* to 0. Then foreach position,player item in *team*:
    - Check if player exists with *if player:* (this is good practice but not strictly neccessary)
    - Add the players PRA score (contained in the last column of the dataset) to *total*

Finally return the *total* rounded to one decimal place with:
```
round(total, 1)
```
### Step 6 - Print Team Function:

The `print_team()` function displays your final basketball dream team in a neatly formatted table. This function takes one argument:
- `team`: The dictionary containing your selected players for each position

Here's how the function works:

1. First, it prints a header with "=== MY DREAM TEAM ===" to clearly mark the start of your team display

2. Next, it creates column headers for the table with:
  - "POSITION" - Which basketball position (PG, SG, etc.)
  - "PLAYER" - The player's name
  - "PTS" - Points per game
  - "REB" - Rebounds per game
  - "AST" - Assists per game

3. The `:<5` and `:<25` in the formatting tell Python to:
  - Left-align the text (that's what the `<` symbol does)
  - Reserve 5 spaces for most columns (or 25 spaces for the player name)
  - This ensures everything lines up nicely in columns

4. It draws a line of 50 dashes (`-`) to separate the headers from the data

5. For each position in the team dictionary:
  - It checks if there is a player assigned (`if player:`)
  - It prints the position, player name, and their key statistics
  - Note that `player[1]` accesses the player's name, while the negative indices (`-3`, `-11`, `-8`) access specific statistics from the end of the list

6. Finally, it:
  - Draws another line of dashes to close the table
  - Calls `calculate_team_rating(team)` to get the overall team rating
  - Displays "TEAM RATING" followed by the calculated value
```
Remember that the output should look like:

=== MY DREAM TEAM ===
POSITION PLAYER                    PTS   REB   AST
--------------------------------------------------
C     Nikola Jokić              27.1  2.8   7.9
PF    Draymond Green            7.5   1     7
SG    James Harden              21    0.6   10.5
PG    Chris Paul                14.7  0.3   10.8
SF    LeBron James              30.3  1.1   6.2
--------------------------------------------------
TEAM RATING: 183.8
```
### Step 7 - Pick user strategy:
Update the function *get_user_strategy* so that it takes in user input with the prompt "Enter your choice (1-4): " which shows that the user will be able to select one of the 4 options already printed above. The format of the rest of the function should be a structure of if statements that check to see if the user input is equal to a specific value and then returns the dictionary corresponding to that input value.
```
#All returned dictionaries should be of the format:
    {
        'c': index,
        'pf', index,
        'pg', index,
        'sf', index,
        'sg', index
    }
```
Try using the header returned from the first step along with the *.index()* builtin function to find the index of the columns that store points, assists and rebounds. The forth option may use any combination of values to create a unique team.
```
#Basic structure
choice = input("Enter your choice (1-4): ")
if(choice == '1'):
   return dictionary with points index
elif(choice == '2'):
   return dictionary with rebounds index
elif()choice == '3'):
 return dictionary with assists index
else:
   return dictionary with your own combination of team selection values
```


    
