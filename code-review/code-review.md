## Introduction

This document captrures some essential (at least for me) pointers for conducting a code review for a Python code.

### Module docstring

### Function docstring
Beside the usual benefits it also eliminates the need of annotating the function arguments, i.e., stating their data types.


### DO NOT have comments in the code
Comments in the code do not serve any purpose. A comment explaining what a certain line or block of lines in a code does is a direct indication that that part of the code needs to be substituted by a function. Give that function a meaningful name inspired by the comments and add what the function does in the docstring. 

### Use variables to store constants
Use variables with upper case and underscores to store constants in the code. Declare these variables at the top of the module.

### Do not use import *
Explicitly state what you wish to import from a specific module

### Classify imports in standard library, third party and local application imports
Improves redability 

### use a die function if there isn't anything meaningful to execute in the 'else'
Make a user defiend function dead() and print something and exit(0) if needed

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
