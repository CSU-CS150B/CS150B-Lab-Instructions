# NBA Practical Project - CS150B
Analysts are constantly throwing around statistics in sports. Stats like points per game, shooting percentages, and player efficiency are used in almost every pre-game segment. It’s easy to forget that behind every statistic is a process of collecting, filtering, and calculating data just like what sports analysts do. In this practical project, you’ll analyze a dataset of NBA player statistics from the 2024–2025 season to calculate a number of stats. 

### Understanding the data:
Before you start coding, it is highly recommended that you **open** the dataset on zybooks and develop an understanding of the data we’ll be working with. Pay attention to which columns might be important for this project. Also, note that the dataset uses abbreviations for team names. Here is a list of the team abbreviations if you want to test your code on a specific team.

https://en.wikipedia.org/wiki/Wikipedia:WikiProject_National_Basketball_Association/National_Basketball_Association_team_abbreviations

The project also deals with player positions so here is a guide to the abreviations used.
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
0. Identify column indexes
   - Open the NBA 2024/2025 data and uncomment the provided variable names as you find their index value.

1. csv_reader(file)
   - Reads NBA player data from a CSV file
   - Returns data rows without the header

2. filter_team(data, team)
   - Filters player data to only include players of a specific team
   - Returns filtered dataset

3. find_stat_max(data, col)
   - Find the player with the max value for a specified stat.
   - Return the best performing player name and the stat value found. [player_name, max_value]

4. find_stat_max_by_position(data, col, pos)
   - Adds another layer to filtering your data. You will now also be filtering by position.
   - You must filter by position first then call find_stat_max to find the max value for the position-specific data.
   - Return the player name, max value, and position in a list. [player_name, max_value, position]

5. find_most_reliable(data)
   - You will compute a stat for every player you call this function with.
    (Make sure you only call this with team data)
   - The stat you are computing is a proportion of how many games a player started out of the games they played.
    games_started / games_played
  - If the proportion ≥ 0.95, add them to a list with the same format we've been using. [player_name, value]

6. main()
   - Here is where you piece it all together to give a summary of the 24/25 season.
   - Expected output format will be provided below

```

### Step 1 - Reading the CSV:
To begin the project you should start by writing the read_csv() function. The function takes in a string which contains a path to the CSV file location and returns a list of lists.
Remember the format of our output should look something like:

```
[[Name, Age, Favorite Food],
 [Juan, 25, Pizza],
 [Adrian, 21, Hamburger],
 [Angelica, 23, Pasta]]
```
Think of each list as a row on a spread sheet, with the commas defining the columns of the spreadsheet.
| Name | Age | Favorite Food |
|------|-----|--------------|
| Juan | 25 | Pizza |
| Adrian | 21 | Hamburger |
| Angelica | 23 | Pasta |

Since we will be working with numbers, we dont want the header in our data and getting passed through mathematical expressions. Make sure you remove the heder using `next()` or `.pop(0)`

### Step 2 - Filtering the data by team:
The next step is filtering the data to return a filtered dataset that contains only the values for players of a certain team.
This function has two parameters: *data* which contains the data you read in the last step and *team* which is the team you will be filtering for.
The rest of the project will be much easier if you don't have to keep going back to the dataset to remember which values are stored where. It is recomended to use the global variables on the top of the page. Once you have done that, you can complete this function by comparing the team row of each player to the team you are filtering by. If they match, add them to 
```
# THIS IS PSEUDOCODE IT WILL NOT RUN
def filter_data
  for row in data
    if row[team] is equal to *team argument* add it to the filtered dataset.
```
If you are struggling with this part please look back at your CSV Lab as much of what you learned in that lab applies to the first 2 steps of this project.

#### Testing tip (optional):
```python
league = csv_reader("NBA24-25season.csv")
nuggets = filter_team(league, "DEN")
print(len(nuggets))
#This test output should be 17, as that is how many players were on the Nuggets 2024/2025 roster.
```
### Step 3 - Finding Best Player for a Stat:

The `find_stat_max()` function identifies the player with the highest value for a specific statistic. This function requires two parameters:
- `data`: The dataset containing player data
- `col`: The column index of the statistic we want to find the max for. (You can test this with any global variable you defined in step 0)

The function implements a straightforward maximum-finding algorithm:

1. It initializes `max_player` to an empty string that will be updated with the best player's name eventually
2. Also initializes `max_value` to 0, which is where you'll store the best players numerical value.
3. It iterates through each player in the dataset
4. It compares the current player's statistic with the current maximum
5. If the current player's statistic is **greater than** the current maximum, this player and their value become the new maximums

#### **Tip: It is important that you make sure to cast the stat into a float!**

```python
#THIS IS PSEUDOCODE IT WILL NOT RUN
set max_player to ''
set max_valiue to 0
# Loop through each player in the filtered data
for each row in data:
    # Compare current player's stat with maximum player's stat
    # CRITICAL: Must use > comparison for correct results
    if float(row stat) > (max_value):
        # Update maximum player when better one is found
        max_player = player name
        max_value = player value
        
# Return the two values in a list
return [max_player, max_value]
```

### Step 4 - Finding the Best Player for a Stat by a Given Position:

The `find_stat_max_by_position()` function builds on the previous one but adds another layer by filtering by position as well. This function requires three parameters
- `data`: The dataset containing player data
- `col`: The column index of the statistic we want to find the max for. (You can test this with any global variable you defined in step 0)
- `pos`: The position you are filtering by. Choose from `"PG", "SG", "SF", "PF", "C"` when calling.

The function works by:

1. Filtering the data by a certain position **first**
2. Once you have the data filtered by position, you can call the `find_stat_max()` on that data to find the max value on the position specific data.
3. It should return a list like the one in the prior function, but with the position included now as well. `[max_player, max_value, pos]`

**Hint: The `find_stat_max()` function already returns `[max_player, max_value]`, now you just need to add the position to that list.**


### Step 5 - Find the most reliable player/s for a team:
The `find_most_reliable()` function will return a list of lists of reliable players and their starting proportion. `[player_name, starting_proportion]` This will only
need one parameter:
- `data`: This is the dataset for which you want to find the reliable players for.
  
**Important note**: This step uses team data that has already been filtered. Write this function assuming it is getting a list of filtered players from one team only.
You do not need to look through the whole league or check what team a player is on inside this function. Instead, when you call this function you should first call your filter_team() function, then use that result as the data argument.

For this project, player is considered *reliable* if they start 95% or more of the games they played. 

To compute this value, you must index two separate columns and divide the two. `games_started / games_played.`

```python
#THIS IS PSEUDOCODE IT WILL NOT RUN
set an empty list you will add reliable players to [], this is what you will return once you have found the reliable players.

for each row in data:
   proportion of games started = int(games_started)/ int(games_played)
   if the proportion of games started is greater than or equal to 0.95:
      append a list containing [name, percent of games started] to your empty list.
   
```
## !!!
**Notice: it says *percent* of games started, not proportion.**

To get the percent, round the proportion you compute to 2 decimals, then multiply the value by 100.

```
#Example
x = 0.78932
x_rounded = round(x, 2) - rounds a value to two decimal spots.
x_percent = x_rounded * 100

print(x_percent)
79.0
```

Here's what this function call should look like for the OKC Thunder:

```python
league = csv_reader("NBA24-25season.csv")
okc = filter_team(league , "OKC")
print(find_most_reliable(okc))
```

`[['Luguentz Dort', 100.0],
 ['Shai Gilgeous-Alexander', 100.0],
 ['Chet Holmgren', 100.0],
 ['Jalen Williams', 100.0]]`

 Some teams will have more reliable players than others, some may only have one. Feel free to use the test above to call the function on your favorite team and find your teams
 most reliable players for the 2024/2025 season.


### Step 6 - Tell a Summarizing Story Using the Functions:

The `main()` function will be where you call all the functions that you have already written, but display it in a neat way for all users to interpret.

 - You will need to find the league leaders for points, assists, and rebounds using the `find_stat_max()` function
 - Then find the highest scorer for the denver nuggets using the `find_stat_max()` again, **but** for the filtered Denver Nuggets data only which you can get using `filter_team()`
 - Next is the call for `find_stat_max_by_position()` which you will use to find the Denver Nuggets' leading passer (max assists) at the point guard position.
 - And, finally the last call is the function call for `find_most_reliable()`. **It is important you call this function with ONLY the Denver Nuggets data** or else you will have a long list of lists with reliable players throughout the entire league. (There are 116.)

Piecing it all together is the tricky part, it should remind you of your first few labs where you had to match output exactly how it is expected in Zybooks. Tedious, we know. But it is an imporant defining feature of Python to watch for every spelling, new line, and indentation required. We highly reccomend using f-strings for the formatting here, though any concatenation method we have learned will work.

The format to follow is listed below with the 2023/2024 NBA Season stats. *Make sure you include the empty lines in between each chunk of information* You can do this by adding an extra print() at the end of your chunk.

**Hint:** You can use a for loop for the final chunk `Most Reliable Players for the Nuggets:` to speed up the process.

```python

for player in nuggets_reliable:
   print(f"{player[0]} started {player[1]}% of the games he was available.")

```


## Expected Output of main() 
```
League Leaders:
Points: Joel Embiid with 34.7
Rebounds: Domantas Sabonis with 13.7
Assists: Tyrese Haliburton with 10.9

Best Scorer for the Nuggets: Nikola Jokić with 26.4 points
Best Passer at PG for the Nuggets: Jamal Murray with 6.5 assists

Most Reliable Players for the Nuggets:
Kentavious Caldwell-Pope started 100.0% of the games he was available.
Aaron Gordon started 100.0% of the games he was available.
Nikola Jokić started 100.0% of the games he was available.
Jamal Murray started 100.0% of the games he was available.
Michael Porter Jr. started 100.0% of the games he was available.
```

**The stats and players we have provided above are different as this output is for the 2023/2024 season**


    
