# 🧬 Python Fundamentals For Biologists

I previously created a guide called [Bash Fundamentals for Bioinformatics](https://github.com/evanpeikon/bash_fundamentals), which provided a crash course on essential Bash commands, including how to navigate a file system and move, copy, edit files, and more. After publishing this guide I received a number of messages from students and wet lab biologists who want to break into bioinformatics, but are daunted because they lack a programming background. 

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
A Python dictionary is a built-in data type that stores and organizes data in key-value pairs. In other words, it's a collection of items, each identified by a unique key, and each key is associated with a corresponding value. Keys must be strings, numbers, or tuples, and values can be of any data type, including numbers, strings, lists, or even other dictionaries. In the code block below I'll show you how to create a dictionary:

```python
patient_info = {'Patient 1':{'Height':170, 'Weight':60}, 'Patient 2':{'Height':160, 'Weight':50}}
print(patient_info) # prints contents of dictionary

dna_to_rna = {'A':'A', 'T':'U', 'C':'C', 'G':'G'}
print(dna_to_rna['T']) # retrieve value associated with the key 'T'
```
Which produces the following output:

<img width="647" alt="Screenshot 2024-11-14 at 3 34 53 PM" src="https://github.com/user-attachments/assets/2ba98644-7e3c-40b5-82d7-81ee7751efa3">

As previously stated, dictionaries excel at storing data in key-value pairs. In bioinformatics, this mirrors the relationship between biological entities and their associated attributes. For example, a dictionary can contain patient data, such as in the example above. In this case, the key is the patient's ID, and the value is another dictionary containing information about the patient. In the second example above, we have a dictionary called ```dna_to_rna```, where each key is a DNA nucleotide, and the value is the associated RNA nucleotide. After defining a dictionary, you can retrieve information based on a specific identifier (i.e., key). 

Dictionaries are mutable, meaning you can modify their content by adding, removing, or updating key-value pairs. In the code below, I'll demonstrate how to add and remove key-value pairs from a dictionary:

```python
dna_to_rna = {'A':'A', 'T':'U', 'C':'C', 'G':'G'}
print(dna_to_rna)

dna_to_rna.pop('T') # remove value by key
print(dna_to_rna)

dna_to_rna['T'] = 'U' # add key-value pair to dictionary
print(dna_to_rna)
```
Which produces the following output:

<img width="323" alt="Screenshot 2024-11-14 at 3 43 18 PM" src="https://github.com/user-attachments/assets/5a9a28a0-2340-4395-a068-2e7920e4b781">

In the code above, I use the ```.pop( )``` function to remove a key-value pair from my dictionary. To call the pop function, you type your dictionary name followed by a period, the word pop, and open and closed parentheses without spaces. You then type the key for the key-value pair you wish to remove within the parenthesis. To add a new key-value pair to your dictionary, you write the name of your dictionary followed by close brackets and an equal sign. You then type the key for your new key-value pair within the closed brackets and the new value after the equal sign, as demonstrated in the code above. 

In the final demonstration in this section i’ll show you how to convert a tuple into a dictionary:

```python
dictionary = dict([('GeneA','protein_coding'), ('GeneB','non_coding),('GeneC','protein_coding')])
print(dictionary)
```
Which produces the following output:

<img width="600" alt="Screenshot 2024-11-14 at 3 45 00 PM" src="https://github.com/user-attachments/assets/be4803a3-d315-4f5c-841e-a659c062dd8b">

The sample code above is a simple example of converting a list of tuples into a dictionary. However, in bioinformatics, you might encounter more complex scenarios where converting tuples to a dictionary is beneficial for better data representation, organization, and analysis, as demonstrated in the code below:

```python
gene_annotations = [
    ('GeneA',1000,2000,'protein_coding'),
    ('GeneB',3000,4000,'non_coding'),
    ('GeneC',5000,6000,'protein_coding')]

gene_dictionary = [{'gene_name':name, 'start_position':start, 'end_position':end, 'gene_type',gene_type} for name, start, end, gene_type in gene_annotations]
```

In the code above we have gene annotations provided as a list of tuples, where each tuple represents information about a gene, such as gene name, start position, end position, and gene type. We then use a list comprehension to convert the list of tuples store in ```gene_annotation``` into a dictionary called ```gene_dictionary```.

## 🐍 Control Flow With Conditionals and Loops

Control flow is crucial in bioinformatics for navigating and processing diverse biological data by controlling the order in which statements are executed in a code block. Additionally, control flow provides the flexibility to handle different conditions, iterate over data, implement algorithms, and automate tasks, contributing to the efficiency and effectiveness of bioinformatics analyses and computational biology research.

In this section, I’ll cover the two most common types of control flow you’ll encounter: conditionals and loops. Conditionals help you make decisions in your code by executing specific blocks based on whether a condition is true or false. Loops, on the other hand, enable you to repeat a set of instructions multiple times, making it easier to process data or perform repetitive tasks.

### Control Flow With Conditionals

Conditionals in Python are structures that allow you to execute certain code blocks based on whether a specified condition is true or false. In the sample code below I’ll demonstrate the simplest type of conditional, called conditional execution:

```python
x=15
if x>10:
  print('x is greater than 10')
```

In the code above, we have a simple example of conditional execution. If the logical statement ```x > 10``` is true, then the code in the indented statement below it is executed (thus, in the code block above the print statement would be executed). If the logical statement is not true, then the indented statement is skipped, and nothing happens. Next, I’ll demonstrate another type of conditional called alternative execution:

```python
x=5
if x>10:
  print('x is greater than 10')
else:
  print('x is less than or equal to 10') # in this example this second print statement is executed
```

The fundamental logic behind alternative execution is similar to conditional execution, with the slight difference that code is executed whether or not the logic statement is true. For example, we have a logical statement ```if >10``` in the code block above. If the logical statement is true, the indented code on line 4 is executed. Alternatively, the indented code on line 6 is executed if the logic statement is false. Once you understand alternative execution, the next type of conditional, called a nested conditional, is easy to comprehend:

```python
x=5
y=6
if x==y:
  print('x and y are equal')
else:
  if x<y:
    print('x is less than y') # in this case, this second print statement is executed.
  else:
    print('x is greater than y')
```

A nested conditional refers to a situation where one or more conditional statements are nested inside another conditional statement. In other words, there is a conditional statement within the block of code controlled by another conditional statement. This nesting can occur at any level, creating a hierarchy of conditions. The example above shows an outer if statement that checks if x and y are equal. If that statement is true, the code prints ‘x and y are equal.’ If the outer statement is false, the else block containing another if/else alternative conditional is executed. 

Now, before we review loops there is one more type of conditional to review, called a chained conditional:

```python
x=6
y=6

if x>y:
  print('x is greater than y')
elif x<y:
  print('x is less than y')
else:
  print('x and y are equal') # in this case this third print statement is executed.
```
Whereas a nested conditional refers to one or more conditional statements nested inside another conditional statement, a chained conditional is a conditional statement that contains a series of alternative branches using ```if```, ```elif```, and ```else``` statements that are all indented at the same depth, as demonstrated in the code block above. 

### Control Flow With Loops

In Python, loops enable you to repeat a block of code multiple times, making it easier to process data or perform repetitive tasks. There are two types of loops you should be familiar with: for loops and while loops. A for loop iterates over a sequence (such as a list, tuple, string, or range) and executes a code block for each element in that sequence. The syntax of a for loop is as follows:

```python
for variable in sequence:
  # code to execute for each element in the sequence
```

In bioinformatics, a common scenario involves iterating over a collection of biological sequences, such as DNA, RNA, or protein sequences. In the example below, I’ll show you how to use a for loop for this task:

```python
dna_sequences = ['ACTGGT', 'TGGCAG', 'CGTTAA']

for sequence in dna_sequences: 
  length = len(sequence)
  print(f'The length of the DNA sequence '{sequence}' is: '{length} bases')
```
Which produces the folowing output:

<img width="432" alt="Screenshot 2024-11-14 at 3 57 27 PM" src="https://github.com/user-attachments/assets/49e6960b-98a0-4700-b5b0-169af2668b2e">

In the example above, the code ```for sequence in dna_sequences:``` initiates the for loop. For each item (sequence) in our list, the code then calculates the length and prints the length of each DNA sequence and the sequence itself.

> Note: There is nothing special about the word 'sequence' in the code above. It could just as easily say ```for peanut_butter in dna_sequences:```, and in the subsequent lines of code you'd need to replace every other instance of the word ```sequence``` with ```peanut_butter```.

Whereas for loops iterates over a sequence and executes a code block for each element in that sequence, while loops repeatedly execute a block of code as long as a specified condition is true. The syntax of a while loop is as follows:

```python
while condition:
  # code to execute as long as the condition is True
```

As previously mentioned, for loops are commonly used in bioinformatics for iterating over sequences or datasets. While loops, on the other hand, are useful in scenarios where the number of iterations is not known beforehand or when iterating until a specific condition is met.

In bioinformatics, a while loop might be used to simulate a scenario where a biological process continues until a certain condition is met. Let's consider a simplified example where we simulate a mutation in a DNA sequence until a specific mutation pattern is achieved:

```python
import random
dna_seq = 'TGGATCCATGCA'
target_mutation = 'TGGATCCATGCT'
mutations = 0

while dna_seq != target_mutation:
  position = random.randint(0, len(dna_seq)-1)
  mutated_base = random.choice('ATCG'.replace(dna_seq[position],''))
  dna_seq = dna_seq[:position]+mutated_base+dna_seq[position+1:]
  mutations +=1

print(f'Target mutation achieved after {mutations} mutations.')
print('Final DNA sequence:', dna_seq)
```
Which produces the following result:

<img width="428" alt="Screenshot 2024-11-14 at 4 02 45 PM" src="https://github.com/user-attachments/assets/42a90724-955c-42e7-86bd-8b54ec2d1afa">

In the code block above, the while loop is active as long as ```dna_seq``` and ```target_mutation``` are not equal. In each iteration through the while loop, a random position in ```dna_seq``` is chosen and the base at that position is mutated. The while loop tracks the number of mutations performed until ```dna_seq =target_mutation```.

## 🐍 Creating Modular Code With Functions

A function is a reusable block of code that performs a specific set of tasks. For example, in bioinformatics, functions are often used for tasks such as sequence manipulation, statistical analysis, or data preprocessing. Functions enhance the readability of code, allowing for the reuse of code snippets and facilitating the development of robust and modular bioinformatics workflows. The code block below provides you with the basic Python function syntax:

```python
def function_name(parameter_1, parameter_2, ...etc.):
    # code to perform a task
    # optionally, return a result
```

There are a few key components in the code example above. First, the word ```def``` is the keyword used to define a function in Python. Next, ```function_name``` is the function's name, which you'll use to call the function later on. Ideally, the name should be descriptive. After that, we have a set of parentheses followed by a colon. You can declare one or more parameters or inputs the function accepts within the parentheses. Then, the indented code blocks contain the statements that define what the function does. Often, functions will end with a command to return a specific value using the return statement. Below is a simple example of a function that takes a ```dna_sequence``` as its single input and then returns the corresponding ```rna_sequence```:

```python
dna_seq = 'ACGTGTCAGTGGGAC

def dna_to_rna(any_dna_sequence):
  rna_sequence = dna_sequence.repace('T':'U')
  return rna_sequence

rna_seq = dna_to_rna(dna_seq)
print(rna_seq) # the code will return the rna sequence ACGUGUCAGUGGGAC
```

In the example code above, the name of my function is ```dna_to_rna```, and the function takes a DNA sequence as input. Inside the function, my code creates a new object named ```rna_sequence```, which is defined by the code ```dna_sequence.replace('T', 'U')```. My function then returns the ```rna_sequence``` using the ```return``` statement. 

I then call my function with the code ```rna_seq = dna_to_rna(dna_seq)```. Importantly, when you call a function, you must write the function's name, in this case, ```dna_to_rna( )```, and then put the input parameter within the parenthesis. You'll note that the parameter I inputted when I called the function is different than when I defined the function. This is okay as long as the input parameter I choose is formatted correctly for the operations my function performs. 

I provided an example of a simple function in the code above. However, in bioinformatics, functions often call other functions to create modular and reusable code. In the code below, i'll provide an example where one function calculates the GC content of a DNA sequence, and another function uses this information to determine whether the GC content is low, moderate, or high:

```python
def get_gc_content(any_dna_sequence):
  gc_count = dna_seq.count('G')+dna_seq.count('C')
  nucleotide_count = len(dna_seq)
  gc_content = (gc_count/nucleotide_count)*100
  return gc_content

def analyze_gc_content(any_dna_seq):
  gc_content = get_gc_content(any_dna_seq)
  if gc_content > 65:
    return f'DNA sequence has high GC content: {gc_content}%'
  elif gc_content < 40:
    return f'DNA sequence has low GC content: {gc_content}%'
  else:
    return f'DNA sequence has moderate GC content: {gc_content}%'

dna_seq = 'ATGCCGTTCAATAGACGTA'
result = analyze_gc_content(dna_seq)
print(result)
```
Which produces the following output:

<img width="496" alt="Screenshot 2024-11-14 at 4 16 31 PM" src="https://github.com/user-attachments/assets/913db787-5b1b-454e-85b7-d722bb6b0d73">

In the code above, the first function, ```get_gc_content( )```, computes the GC content of a given DNA sequence, then the second function, ```analyze_gc_content( )```, calls the first function to get the GC content of a DNA sequence and then analyzes the result. 

If you're interested in learning more about functions, you can checkout my [systems_biology GitHub repository](https://github.com/evanpeikon/systems_biology), which contains assorted functions and programs for using numerical methods, quantitative modeling, and solving common problems in systems biology. 

## 🐍 Data Manipulation With Pandas

Pandas is a powerful open-source data manipulation and analysis library for Python. It provides data structures, such as series and data frames, designed to efficiently handle and analyze structured data. Pandas is widely used in various fields, including bioinformatics, for data cleaning, exploration, and analysis tasks. In the code below I’ll show you how to import the Pandas library, how to load a CSV file as a Panda’s data frame, and how to display the data frame as a table:

<img width="1090" alt="Screenshot 2024-11-14 at 4 20 11 PM" src="https://github.com/user-attachments/assets/a8c63424-c6e9-4076-be9f-b8c2de882302">

I import the Pandas library in the code block above by typing ```import pandas as pd```. I then load a CSV file with information about different viruses using Panda’s ```pd.read_csv( )``` function, which allows me to store the CSV file as a data frame in the df variable. I then use IPython’s ```display( )``` function to display my datagrams, resulting in the above table. You can also choose to display a specified number of the first or last set of rows using ```[name of data frame].head( )``` and ```[name of data frame].tail( )```, respectively. For example, if you only want to view the first ten rows of data, you can type ```[name of data frame].head(10)```. Now, let’s say that when viewing your data, you notice missing values. In that case, you can use the ```[name of data frame].dropna( )``` command, which removes all null values from your data. 

After viewing your data frame, you can perform more complex exploratory data analysis. For example, in the code below, i’ll show you how to generate summary statistics for the data in your data frame using the ```.describe( )``` command:

<img width="584" alt="Screenshot 2024-11-14 at 4 21 39 PM" src="https://github.com/user-attachments/assets/a75a85ce-3620-4599-847c-59c1af10a901">

After using Pandas to load a data frame, you can also use additional libraries such as ```matplotlib.pyplot)``` for performing exploratory data analysis with various visualization tools. For example, in the code below I'll demonstrate how to generate a scatter plot to better understand the relationship between viruses inner and outer radius:

<img width="423" alt="Screenshot 2024-11-14 at 4 22 32 PM" src="https://github.com/user-attachments/assets/252715d2-3d66-4837-b411-5b2128a48b26">

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
