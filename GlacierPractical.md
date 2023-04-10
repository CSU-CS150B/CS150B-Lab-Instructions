# Practical Project > World Glacier Data

The World Glacier Inventory (WGI) contains information for over 130,000 glaciers. The WGI is based primarily on aerial photographs and maps with most glaciers having one data entry only. Hence, the data set can be viewed as a snapshot of the glacier distribution in the second half of the 20th century. It is based on the original WGI (WGMS 1989) from the World Glacier Monitoring Service (WGMS).” - National Snow and Ice Data Center

The provided comma-separated-value file has been modified and contains only select rows and columns to provide a file that is easier to parse. Visit this link and click on the User Guide tab to find more information about the data in the file.

For quick reference, the file is laid out as follows:

* wgi_glacier_id
* political_unit
* continent_code
* glacier_name
* latitude
* longitude
* mean_elev (m)
* form
* source_nourish
* total_area (km²)

With each category being a column in the file. So wgi_glacier_id is the first column (ask yourself if that is the 0 position in the list or first position).

## Required Functions To Implement (graded)
We will grade the following functions. Please note, that while there may be different ways to implement them, and you are free to write additional functions to help make the solution easier (divide conquer glue!). We just need the following function names to match, as those are the ones we are grading.

## Variables
You will create five variables as file wide variables (often called global). The first is file, which will store the file name to work with. That is ‘wgi_glacier_data.csv’ or ‘wgi_glacier_data_test_file.csv’ (note, you only need to store one in it, but this gives you the option to change the files you test with). The other variables are the index value of the columns in the wgi_glacier_data.csv file. The column that contains the name, the column that contains the glacier form, the column that contains the latitude, and the column that contains the area. See above, or better yet download the CSV file and load it into excel or google sheets to see more! Hint: loading the csv file into google sheets or excel will help you later if you want to generate graphs.
```python
file = 'wgi_glacier_data.csv'
name_index = ??
form_index = ??
latitude_index = ??
area_index = ??
```
**Note:** Remember that you will be dealing with a list in future methods. Be sure to brush up on how to access certain values of a list.

## Step 1: csv_reader(file)
Reads a file using csv.reader and returns a list of lists with each item being a row, and rows being the values in the csv row. Look back at the CSV lab on reading csv files into a list. The function will be mostly the same with one exception. Since the file has a header row, you may want to skip the first row, or remove it after you are done.

You should test this now. Maybe print out the length of the list returned from the method. For example, a test could be
```python
print("TESTING", len(csv_reader(file))) #where file is set above to either wgi_glacier_data.csv or the tests file
```

## Step 2: longest_glacier_name(glacier_list)
This function will take in the list created from csv_reader and will parse through each list to find the various names of all the glaciers. It will find the longest name and return that name at the end of the method. Make sure to test it!

Here is an example test (notice, we are just creating our own list))
```python
test_list = [['one','AT','4','short','0','0','0','0','0','0'], ['two','US','2','longest name','0','0','0','2','0','0']]
print("TESTING", longest_glacier_name(test_list))
print("TESTING", longest_glacier_name(csv_reader(file)))
```
## Step 3: most_common_glacier_form(glacier_list)
This function will take in the list that was created in the csv reader and will parse through each list to find the form of the glacier. You will want to keep track of each glacier and the number of times that form shows up. There are many ways to keep track of each glacier, you can create ten variables tracking values, use a list assuming index matches form, or use a dictionary (form:times). While the form names look like numbers they are strings. You are fine with returning the string value of the glacial form back, and you can assume no matter the file form ‘0’ is included (for ease), and that there are ‘0’ through ‘9’ forms though all may not show up in every file except for 0. In case of ties, the name that shows up first wins.
```python
test_list = [['one','AT','4','short','0','0','0','0','0','0'], 
             ['two','US','2','longest name','0','0','0','2','0','0']
             ['three','US','2','median','0','0','0','0','0','0']]
print("TESTING", most_common_glacier_form(test_list))
print("TESTING", most_common_glacier_form(csv_reader(file)))
```
## Step 4: highest_latitude(glacial_list)
This function will take in a list created from the csv reader and will parse through the list to find the name of the glacier at the highest latitude. Tests are similar to above, but you will want to add values for latitudes. You can assume latitudes are all decimal values, and not ordinal directions.

## Step 5: average_area()
This function will take in the list that was created from the csv reader and parse through it to find the area of each glacier and find the average area of all the glaciers in the dataset. You can create tests similar to above, but add values for the areas. Any area that shows up as empty, you can assume 0. For all other areas, make sure to use the float(), so you can add the numbers properly!

## Step 6: main()
This is the function that you will write to call all the functions that you have already written. You will need to print out each function return to match the formatting in order.
```
Average Area: 2.03
Highest Latitude Name: VOSTOK2
Most Common Glacier Form: 5
Longest Glacier Name: Shinchula Glacier
```
## Step 7: Turning it in
In this step you will turn in your assignment. If you do not receive full credit, go back and fix your work! You have a max of 15 submit for grading attempts. However, you can work in develop mode all you want, so setting up tests is essential. Start early, and work often!

## References
WGMS, and National Snow and Ice Data Center (comps.). 1999, updated 2012. World Glacier Inventory, Version 1. Boulder, Colorado USA. NSIDC: National Snow and Ice Data Center. doi: [https://doi.org/10.7265/N5/NSIDC-WGI-2012-02](https://nsidc.org/data/g01130/versions/1). Fall 2018.
