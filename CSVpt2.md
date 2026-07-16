# Welcome to Lab 14

Today we will be going over writing to files using "with open".

As a reminder, to create and write to a file you do:

    with open("file.txt", "w") as f:
        f.write("hello")

The key factor here is using the "w" keyword to open the file in write mode. Using "w" will either create a new file or
overwrite a file that already exists. 

As you'll be creating new files in this lab, you'll want to be able to view them. To do this in Zybooks, look for the file
icon in the top left corner of the coding window. Click that and it will open a list of all files currently loaded into
this Zybooks lab. 

## Step 1: Writing to a text file
This step only requires you to write one line of code, as the file you need to write to has already been opened for you.
To write to a file, use .write() on the open file and pass the text you want to write as the argument. For example:

    with open("file.txt", "w") as file:
        file.write("This text will go into the file")

To complete this step, write "Hello World!" to file.txt

## Step 2: Adding all sums to a text file
We want to create a file called "sums.txt" and have it contain the sum of the number n plus every number less than and
equal to it, starting from 0. You will have to cast the sum to a string to write it to the file.
If n = 3, sums.txt should look like:

    3
    4
    5
    6

With every sum having a newline after it. Take note that writing to a file several times in one "with open" will not overwrite but append
to the open file. 

## Step 3: Append to a text file
Now that we create a file containing all the sums, we want to append the statement, "Sums of {n} complete!" to the end of "sums.txt".

To append rather than overwrite, use "a" when opening the file instead of "w". For example:

```
with open("append.txt", "a") as f:
```

Doing this will simply add to the file instead of erasing everything when writing. 

## Step 4: Writing to CSVs
Now that we're comfortable with text files, we'll move on to the more data focused CSV file. Just like reading CSVs, the CSV module
includes the ability to write to CSVs. You still need to use "with opens" to create/open the file, and to create a CSV writer, just like a 
reader, do:

    writer = csv.writer(f)

Then to write to the file:

    writer.writerows(ENTER DATA HERE)

Take note that .writerows() specifically takes in a list of lists. writerows() will write every row to the file in one go, without 
the need for a loop. There is one provided for you to test with called students.

## Step 5: Append to a CSV
We want to be able to add new students to "students.csv" without completely erasing everything we've already added. This step will look almost 
identical to the last, but instead we want to open the file in append rather than write, and write to the file using:

    writer.writerow(ENTER DATA HERE)

instead of .writerows(). writerow(), singular, will write one row to the file using one single list. 




