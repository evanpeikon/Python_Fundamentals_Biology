# 🧬 Python Fundamentals For Biologists

I previously created a guide on [Bash Fundamentals for Bioinformatics](https://github.com/evanpeikon/bash_fundamentals). After publishing this I've gotten messages from a number of students and wet lab biologists who find themselves at a crossroads in the rapidly evolving field of bioinformatics, where big data is driving groundbreaking discoveries. While the allure of delving into the world of programming to unlock new insights is strong, the path forward can be daunting, especially for those with limited programming backgrounds.

This guide is for those who are interested in learning bioinformatics but are overwhelmed by the sheer volume of coding instructionals available. This guide aims to highlight key concepts without overwhelming beginners with minutiae or glossing over critical concepts.

Importantly, this guide assumes you are familiar with basic Python data types and syntax. With that foundation, you'll be ready to learn key programming concepts that will appear time and time again. From understanding the logic behind loops and conditionals, to deciphering the power of functions, and creating clean data visualizations, this guide is your short go-to resource, equipping you with the tools to decipher and compose code that unlocks the mysteries hidden in biological data.

## 🐍  Storing Data In Lists and Dictionaries 
Lists and dictionaries play pivotal roles in managing and manipulating biological data. In simple terms, a list is like an ordered checklist where each item has a discrete position, and a dictionary is like a set of labeled boxes where each item has a unique label. Lists are good for storing sequences of items, while dictionaries are great for associating information with specific labels or keys. Bioinformatics tasks, such as sequence analysis, rely heavily on these fundamental data structures to navigate and manipulate biological datasets efficiently.

###  Working With Lists

A list is a built-in data structure that allows you to store and organize a collection of objects, including integers, strings, and even other lists. In bioinformatics, DNA, RNA, and protein sequences are commonly stored as lists. Lists are defined with square brackets, ```[ ]```, and filled with objects separated by commas. Additionally, lists are ordered and mutable, meaning you can change their content by adding or removing elements.

Bioinformatics tasks frequently involve using loops to iterate over large datasets. Lists are well-suited for these loop operations because of their sequential structure, which enables efficient processing of large datasets. In the code sample below, I'll show you how to create a list:

```python
list_1 = [1,2,3,4,5] # a list of integers
print('List of Integers:', list_1)

list_2 = ['A', 'T', 'G', 'C'] # a list of strings
print('List of Strings:', list_2)

list_3 = [[1,2,3], ['A', 'T', 'G', 'C']] # a list of lists
print('List of Lists:', list_3)
```
Which produces the following output:

<img width="400" alt="Screenshot 2024-11-14 at 1 12 55 PM" src="https://github.com/user-attachments/assets/ba623b38-8a6d-4cf2-a691-027f1ce7f979">

The code above shows you how to create lists containing integers, strings, and other lists. Importantly, lists do not need to contain just one data type. You can have a single list that includes integers, strings, and more. Additionally, you can add two lists together to produce a single unified list. For example, if you were to write the code ```new_list = list_1 + list_2```, then ```print(new_list)```, the resultant output would be as follows: ```[1, 2, 3, 4, 5, 'A', 'T', 'G', 'C']```. Next, I'll demonstrate how to add and remove elements from a list:

```python
list = [1,2,3]
print('Here is a list:', list)
list.append(4)
print('Here is a list with a new item:', list)
ist.remove(2)
print('Here is a list with the second item removed:', list)
```
Which produced the following output:

<img width="400" alt="Screenshot 2024-11-14 at 1 17 04 PM" src="https://github.com/user-attachments/assets/a3c71a15-636e-4a13-a0e4-f3e43a72489b">

In the code above, I used the ```.append( )``` function to add a new object to my list and the ```.remove( )``` function to remove an item. To call the append function, you type your list's name followed by a period, the word append, and open and closed parentheses without spaces. You then type the object you wish to add to the list inside the parentheses. If you're adding an integer, you type the number as is, whereas if you add a string, it must be in quotation marks. The remove function works similarly, except you type the object as it appears in your list, within the parentheses, as demonstrated above. Next, i’ll show you how to call items from a list and slice lists:

```python
list = ['a', 'b', 'c', 'd', 'e']
print(list([3]) # retrieve the item in '3' position 
print(list[1:4] # retrieve items in positions 1-3
print(list[0:4:2] # retrieve items in positions 0-3, skipping every other item
print(list[:4] # retreive items 0-3
```
Which produces the following output:

<img width="157" alt="Screenshot 2024-11-14 at 1 20 59 PM" src="https://github.com/user-attachments/assets/df77b580-89fa-4c29-8fab-d803472c5f51">

In the code above, I show you how to call items from a list, which involves writing the list name followed by square brackets and the index number of the item you wish to retrieve from the list. You’ll notice that I write ```list[3]``` in my example, but the resultant output is the letter d, which is the fourth item in my list. The reason for this is that list indexing in Python follows zero-based indexing, where the first element in a list is at index 0, the second element is at index 1, and so on. 

Next, I show you how to slice lists, which is the process of extracting a portion of a given data sequence using the following notation: [start: stop: step]. This notation creates a new list with elements from the index start point up to, but not including, the stop point, with an optional step specifying the increment. For example, the code ```list[1:4]``` retrieves items in positions 1-3, whereas the code ```list[0:4:2]``` retrieves times 0-3 in increments of two, which in practice means items 0 and 2. In code line 5, in the example above, you’ll see that I failed to input a stop position for my list. This retrieves all items from my specified start index onward. Alternatively, in line 6, I failed to input a start position, which means starting at index 0 and retrieving all items unto, but not including my specified stop position. 

In the following block of code I’ll show you how to loop through lists:

```python
dna_sequences = ['ACTGGT', 'TGGCAG', 'CGTTAA']

for sequence in dna_sequences:
  print(sequence)
```
Which produces the folowing output:

<img width="60" alt="Screenshot 2024-11-14 at 1 23 13 PM" src="https://github.com/user-attachments/assets/d7d9d164-ba00-4924-9644-b02a6bea95b2">

Looping through lists enables the repeated execution of operations across numerous data points. In general, looping through a list takes the following form:

```python
for item in list:
    # code to execute for each item 
```

In essence, the code above works because the loop processes each item in the list and then performs the specified operations on that element. Later in this guide, I’ll provide a more comprehensive overview of for loops and while loops under the Control Flow section. Now, we’ll wrap this sub-section on lists up with the following demonstration on list comprehensions:

```python
dna_sequences = ['ACTGGT', 'TGGCAG', 'CGTTAA']
gc_content = [(seq.count('G') + seq.count('C')) / len(seq) for seq in dna_sequences]
print('The GC content of each sequence is:', gc_count)
```
Which produces the following output:

<img width="608" alt="Screenshot 2024-11-14 at 1 25 51 PM" src="https://github.com/user-attachments/assets/8fb18ea9-a347-420e-836c-1d65a8eafe76">

List comprehensions provide a concise and readable way to create lists and perform operations on existing ones. In bioinformatics, where data manipulation and analysis are frequent tasks, list comprehensions offer a compact syntax for tasks like filtering, transforming, or generating lists of data. For example, the list comprehension above calculates the GC content in various DNA sequences stored in a list by counting the occurrences of ‘G’ and ‘C’ and dividing that sum by the sequence length.

### Working With Dictionaries

## 🐍 Control Flow With Conditionals and Loops

### Control Flow With Conditionals

### Control Flor With Loops

## 🐍 Creating Modular Code With Functions

- add section with systems biologist functions

## 🐍 Data Manipulation With Pandas


# 🧬 Data Visualization Fundamentals For Biologists
This second section a compliment to the guide above on Python Fundamentals For Biologists. In this section, I'll provide an introduction to data visualization for bioinformatics without overwhelming beginners with minutiae or glossing over critical concepts. In bioinformatics, data visualization is crucial for interpreting complex biological datasets, making it easier for researchers to identify patterns, trends, and insights. Additionally, effective visualization enhances data-driven decision-making, aids in hypothesis generation, and facilitates communication of findings. Let's begin!

## 🐍 Introduction To Matplotlib and Seaborn


## 🐍 Identifying Patterns In Data With Scatter Plots

## 🐍 Visualizing Time Series Data With Line Charts

## 🐍 Comparing Categorical Data With Bar Charts

## 🐍 Understanding Data Distribution With Histograms

## 🐍 Boxplots for Outlier Detection


# 🧬 Additional Resources:
- Projects (easy to hard)
- Machine learning 
- F1L, Tommy books, etc
