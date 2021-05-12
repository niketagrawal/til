## Introduction

This document presents a collection of some minor and major suggestions compiled into a checklist for use when conducting a code review. While some of the points only applys to Python but other points are applicable to other programming languages too. This checklist is a work under progress and will be updated in due course with other things to be cosidered while reviewing a Python code.

### Module docstring
A docstring at the top of the module providing an overview of what a module does, what other modules it is used by and any other useful details besides just author name and date. 

### Function docstring
Beside the usual benefits it also eliminates the need of annotating the function arguments, i.e., stating their data types.


### Get rid of comments in the code
It is quite common to have comments in the initial versions of the code but you can eventually evolve your code to have no comments.
In most cases comments actually do not serve any purpose. For example, a comment explaining what a certain line or block of lines in a code does is a direct indication that that part of the code needs to be substituted by a function or should ideally be in the function docstring, or could be eliminated by using better function and variable names . 

### Use variables to store constants
Use variables with upper case and underscores to store constants in the code. Declare these variables at the top of the module.

### Use explicit impots 
Explicitly state what you wish to import from a specific module instead of using import *. A wildcrad is often not needed for relatively small size modules.

### Classify imports in standard library, third party and local application imports
Improves redability 

### Meaningful variable names

### Modularize the main()
make a single call to main() after the if "__name__" == __main__ line in the code. This main() must run everything yoou wish to run. Modularize it further if the function body is big.

### Have zero or 1 argument in the functions
Try to have less functions with two input arguments, 3 input argument is rare. In that case break the function further. Less input arguments make writing tests easier as the need for testing against several permutations and combinations of inputs is significantly reduced or completely eliminated.

### Use for loop instead of while loop in most cases
All loops that do not need to be run infinitely (mostly the case) can be implemented using for loop. The error margins are less with for loop.

### Do not use hardcoded file input paths
Let the user enter the file input path via command line argument if they are passing self constructed input to the program 

### Do not store input files next to code in the same repository

### Make the functions as atomic as possible.

### References
1. Clean Code: A handbook of Agile software craftsmanship