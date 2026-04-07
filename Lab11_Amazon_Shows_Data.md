# Amazon Prime Lab: Getting Comfortable with `pandas`

Welcome!  
In this lab, you'll explore real-world data from Amazon Prime titles using `pandas`. You'll learn how to:

- Read in a CSV file
- Explore rows and columns in a table of data
- Use loops and conditionals
- Write simple functions to analyze real data


---

## Load the Data

We'll start by loading the dataset using `pandas`.

The dataset is hosted online so you don't need to download or upload anything it will load directly into your notebook.

```python
import pandas as pd

url = 'https://raw.githubusercontent.com/CSU-CS150B/amazon-prime-data/refs/heads/main/amazon_prime_titles.csv'
df = pd.read_csv(url)
df.head(10)
```

```python
df.groupby('type').count()
```

---

## What is a DataFrame?

A **DataFrame** is a table where:

- Each **row** is a single item (in our case, a TV show or movie)
- Each **column** is a piece of information about that item (like title, rating, or release year)

You can think of it like a spreadsheet or a SQL table.

**DataFrames are useful because they let us:**

- Quickly search, filter, and count values
- Clean up messy data
- Apply logic across multiple rows

### Let's try exploring the DataFrame:

Use the code below to answer the following questions:
- How many rows (titles) are in the dataset?
- What are the column names?
- What are the first 5 titles?

```python
print("Total rows:", len(df))
print("Column names:", df.columns.tolist())
print("First five titles:", df['title'][0:5])
```

---

## Looping Through DataFrames

We can use a `for` loop and an index to go through rows of the DataFrame.
This helps when writing simple logic like counting or filtering.

```python
for i in range(5):
    print("Row", i, "Title:", df['title'][i])
```

---

## Writing Simple Functions

Let's write a function that counts something in the data.

For example: How many titles are classified as Movies?

```python
count = 0
for i in range(len(df)):  # notice the in keyword! (Notes below)
    if df['type'][i] == "Movie":
        count += 1
print("Total movies:", count)
```

### Example format for your function:

```python
def count_movies(df):
    count = 0
    for i in range(len(df)):
        if df['type'][i] == "Movie":
            count += 1
    return count
```

Test each function using print statements:

```python
print(count_movies(df))
```

---

### Understanding the `in` Keyword in Python

The `in` keyword is used to check if something **exists inside** something else.

You can use it to:
- Check if a **word is in a sentence**
- Check if an **item is in a list**
- Check if a **letter is in a word**

### Example: Check if a word is in a string

```python
title = "Secrets of Deception"
if "Secret" in title:
    print("This title contains the word 'Secret'")
```

You can use `in` when looping through your dataset to check if a keyword appears in a title:

```python
count = 0
for i in range(len(df)):
    if "Secret" in df['title'][i]:
        count += 1
print("There are", count, "titles with the word 'Secret'")
```

---

# Your Turn – Lab 11 Instructions (Guided)

You'll be writing and testing **three functions** that each analyze the `amazon_prime_titles.csv` dataset using **for loops**, **if statements**, and column indexing like `df['column'][i]`.

> Tip: `len(df)` gives you the number of rows, and you can loop through rows using `for i in range(len(df))`.

---

### Function 1: `count_tv_shows(df)`

Write a function that returns **how many rows in the dataset are TV Shows** (i.e., where `type == "TV Show"`).

#### What to Think About:
- Loop through each row in the DataFrame.
- Look at the value in the `"type"` column.
- If the type is `"TV Show"`, increase your count.

#### Pseudocode:
*(Pseudocode just means writing out code logic in English — it won't actually run!)*

```
Set a counter to 0
For each index i from 0 to len(df):
  If df['type'][i] == 'TV Show':
    Add 1 to the counter
Return the counter
```

---

### Function 2: `count_titles_with_word(df, word)`

Write a function that returns **how many titles** include the given word (e.g., `"Secret"`).

#### What to Think About:
- You'll need to look at the `"title"` column.
- Use `.lower()` to ignore capitalization.
- Use the `in` keyword to check if the word appears in the title.

#### Pseudocode:

```
Set a counter to 0
For each index i from 0 to len(df):
  Get the title from df['title'][i]
  If the given word is in the title (case-insensitive):
    Add 1 to the counter
Return the counter
```

---

### Function 3: `count_most_seasons(df)`

Write a function that returns **the title of the TV Show with the most seasons** and how many seasons it has.

#### Goal:
From the dataset, find the TV show with the highest number of seasons listed in the `"duration"` column.

The `"duration"` column has values like:
- `"3 Seasons"`
- `"1 Season"`

These are strings! How do we compare strings... we cast them to ints. (This is called *data cleaning* and it is the most important part of extracting cool insights that no one else can find.)

We want to:
- Extract the number (e.g., 3, 1)
- Convert it to an integer
- Keep track of the highest number we've seen so far

#### Step-by-Step Breakdown:

1. **Initialize two variables**:
   - `max_seasons` to store the highest number of seasons seen so far. Should store numbers.
   - `max_title` to store the corresponding show title. Should store words.

2. **Loop through every row** in the DataFrame:
   - Only do the next steps if the `type` is `"TV Show"`

3. **Extract the number of seasons**:
   - Get the value in the `"duration"` column (e.g., `'3 Seasons'`)
   - Use `.split()` to split the string by spaces (e.g., `'3 Seasons'` becomes `['3', 'Seasons']`)
   - Take the first part and convert it to an integer using `int(...)`

4. **Compare with the current maximum**:
   - If the number is greater than `max_seasons`, update both `max_seasons` and `max_title`

5. **Return the result** as a **tuple** containing the title and number of seasons

---

#### Quick Reminder: What is a Tuple?

You've seen tuples before! A **tuple** is like a list, but it uses **parentheses** instead of square brackets, and its values **cannot be changed** after it's created.

```python
# A tuple looks like this:
result = ("Some Show", 10)

# You can access elements just like a list:
print(result[0])  # prints: Some Show
print(result[1])  # prints: 10
```

Tuples are useful when you want to **return multiple values** from a function — like both a title *and* a number — bundled together.

---

#### Pseudocode:

```
Set max_seasons to 0
Set max_title to an empty string

For each index i from 0 to len(df):
  If df['type'][i] == 'TV Show':
    Get the value of df['duration'][i]
    Split the string and take the first part
    Convert it to an integer and store as num_seasons
    If num_seasons > max_seasons:
      Set max_seasons to num_seasons
      Set max_title to df['title'][i]

# Return a TUPLE - two values bundled together in parentheses
# Reminder: tuples look like (value1, value2) and let you return multiple things at once!
Return (max_title, max_seasons)

# When you call the function, you can print it like this:
# print(count_most_seasons(df))
# Output will look like: ('Show Name', 12)
```

---

### Bonus Thought

What would your function return if **two shows** had the same (max) number of seasons?

> Would it return the first one? The last one? Could you modify your function to return all shows with the most seasons?

---

## Extra Credit Challenge (Optional)

Write your own question and solve it with a function!

If you add this extra function and solve it — show it to a UTA in your lab so that they can sign off on your weekly worksheet page one. They need to write **"Extra Credit approved by- [UTA NAME]"**.

Here are some ideas:
- How many titles are longer than 100 minutes?
- How many shows were added in 2021?

Keep experimenting with real data and enjoy discovering patterns!
