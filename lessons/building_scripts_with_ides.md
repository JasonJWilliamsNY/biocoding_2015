#Introducing IDEs

An IDE [Integrated Development Environment](https://en.wikipedia.org/wiki/Integrated_development_environment) is a nice way to starting using scripts and Python outside of the context of the iPython/Juypter notebook. A script is simply a collection of code (usually grouped into functions). We can save our script and call it back at the Linux shell. In the course, we will use the 'Spyder' IDE. 

####Starting Spyder

At the terminal, start Spyder with the following command:

```bash
$ spyder
```

You will get an editor (with numbered lines) that you can start using to build your Python script:

```python
# -*- coding: utf-8 -*-
"""
Created on Thu Aug 27 07:31:04 2015

@author: biocoder
"""
```

In the triple-quotemark comments section, you can leave notes that describe the nature of your script. You will also see an interactive Python shell console (looking something like this): 

```python
Python 2.7.6 |Anaconda 1.9.2 (x86_64)| (default, Jan 10 2014, 11:23:15) 
[GCC 4.0.1 (Apple Inc. build 5493)] on darwin
Type "help", "copyright", "credits" or "license" for more information.

Imported NumPy 1.8.0, SciPy 0.13.3, Matplotlib 1.3.1
Type "scientific" for more details.
>>> 
```
scripts run in the editor will be run in the interactive console.

### Scripts and inputs

Now that we have our script and the interactive Python shell, we should introduce the concept of accepting user input. To do this we can use the ``raw_input()`` function. Use this block of code:
>**Tip:** see some of the help features of the IDE that explains a functions parameters:

```python
def dna_to_rna(dna):
    rna = dna.replace('t','u')
    return rna

dna = raw_input('Please input some DNA\n')
print dna_to_rna(dna)
```

>**Tip:** Save the script as dna_to_rna.py

#### Challenge:
Create a script that prompts the user with the following questions, and stores the answers in dictionary key/value pairs. Let your partner provide answers to the questions (switch computers) and then view the results. 

* Name of the user
* School attended
* Grade
* Favorite food
* Favorite place to visit 

### Scripting

Write a script call ``dna_to_protein.py``

This script should do the following
* accept a DNA input that the user types in
* report to the user the size of the DNA sequence
* report the RNA sequence to the user
* report the protein sequence to the user

# Working with files

Up until now, we have been giving you sequences to work with, either by writing them into the iPython notebook, or just now by showing you how you can accept input from the user. Let's look at opening a file, reading its content, and then processing that information with python. 

## Open a file containing DNA sequence and then writing the results to a new file. 

```python
filepath = ''

#open a file for reading
with open(filepath,'r') as input_file:
    for line in input_file:
        if '>' in line:
            fasta_header = line.strip()
        else:
            sequence = line.strip()

#print back the header and sequence 
print fasta_header
print sequence

# translate sequence to DNA
dna = sequence.replace('u','t')
print dna

#write the dna to file
with open('dna_result.txt','a') as result_file:
    result_file.write(fasta_header + '\n')
    result_file.write(dna + '\n')
```

# Running your Python script at the shell

Lets add just one more feature to make your script work at the shell, and without an editor/IDE:

```python
from sys import argv
filepath = argv[1]

#open a file for reading
with open(filepath,'r') as input_file:
    for line in input_file:
        if '>' in line:
            fasta_header = line.strip()
        else:
            sequence = line.strip()

dna = sequence.replace('u','t')

#write the dna to file
with open('dna_result.txt','a') as result_file:
    result_file.write(fasta_header + '\n')
    result_file.write(dna + '\n')
```