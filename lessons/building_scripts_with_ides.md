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
Create a script that prompts the user with the following questions, and stores the answers in dictionary key/value pairs. 

* Name of the user
* School attended
* Grade
* Favorite food
* Favorite place to visit 