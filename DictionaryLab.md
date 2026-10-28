# Lab 16 - Dictionary Lab

## About Dictionaries
In Python, a dictionary is a collection of key pair values. Where in a collection like a list you would use a numbered index to retrieve a specific value at a specific location, a dictionary
allows you to access a value by using its key.

An example dictionary would look like:
```
fruits = {"Apples": 4, "Pears": 7, "Mangos": 5}
```
Where specific values can be accessed like:
```
print(fruits["Apples"])
# Prints 4
```
Adding a new key value pair to an existing dictionary is as easy as:
```
fruits["Grapes"] = 2
```
And you can update existing values the same way:
```
fruits["Apples"] = 3
```



In this lab, we'll be running a book store using Python dictionaries. To complete this lab you will need to:

- Display a book's information using dictionary keys
- Change the value of a key value pair
- Create a new dictionary
- Sort through a list of dictionaries

# Step 1
We want to easily display our books in a readable format for our customers, as raw dictionaries by themselves can be a little hard to 
understand. To accomplish this, we have the displayBook function that will put the details from the dictionary into an easy to read
description. 

Most of displayBook has been done for you, you just need to finish the last two steps. You'll need to index the Pages and Price values
using their keys in the same format as shown above. 

You'll want to print pages as "X Pages" and price as "$X". However, if the book
is out of stock you will want to print "Out Of Stock" instead of the price. 

This step does not require you to return any value, just print information to the console. 


# Step 2
We just received a new shipment of the book Katabasis and now we need to add it to our inventory. 

In our book dictionaries we have a field called "In Stock". Once we receive a new shipment of a sold out book, we need to update that book and our current inventory to reflect the new stock.

For the stock function, we want to update the value of "In Stock" to True, and then add it to our inventory list. Then, return inventory. 

If you aren't sure how to update a key value pair, look at the example at the top of the instructions. 

# Step 3
We need to be able to add new books that aren't in our system yet.

Our function addBook takes in all the information we need from parameters, we just need to use them to construct a dictionary. 
You'll want to create the book in the correct format so that it works with our system:
```
{"Title": X, "Author": X, "Release Year": X, "Pages": X, "Price": X, "In Stock": X}
# (X is a placeholder value that you'll have to replace with your actual values)
```
Once you have this dictionary with the proper values, return it

# Step 4
Some frugal customers want to buy our cheapest books, and we want to make that simple for them.

To find the cheapest book, we'll need to go through our entire inventory and compare the prices one by one.

We want a starting value so we have a "cheapest" book to begin with, you can use the first element of inventory.

Then loop through inventory and compare the price of the current book to the price of the cheapest book. 

If it is cheaper, set the cheapest book to the current book.

Return the cheapest book

