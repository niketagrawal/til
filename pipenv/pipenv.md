### Using pipenv in a conda environment

Following error may be encountered when using pipenv inside a conda virtual environment.

```
$ pipenv shell
Creating a virtualenv for this project...
Pipfile: C:\Users\myPC\code\Pipfile
Using C:/Users/myPC/Anaconda3/python.exe (3.8.3) to create virtualenv...
[==  ] Creating virtual environment...FileNotFoundError: [Errno 2] No such file or directory: 'c:\\users\\myPC\\anaconda3\\Lib\\venv\\scripts\\nt\\python.exe'

Failed creating virtual environment

[pipenv.exceptions.VirtualenvCreationException]:
Failed to create virtual environment.
```

***To fix this error***, copy python.exe and pythonw.exe from C:\ProgramData\Anaconda3 and paste in C:\ProgramData\Anaconda3\Lib\venv\scripts\nt ([ref](https://github.com/ContinuumIO/anaconda-issues/issues/10822))

Do this for each virtual env inside which you wish to use pipenv

### COnfiguring pipenv to use the correct python interpreter 

Firstly, pipenv can be installed as usual by using
`pip install pipenv`

Then, you must specify the python interpreter corresponding to the virtual env that you are using to the pipenv

TO do this, first fetch the path of the python interpreter for the current conda environment

```
$ which python
/c/Users/niketagrawal/Anaconda3/envs/my-dev/python
```

Then use the general pipenv install command with the flag --python=<python-path> 

```
pipenv install --python=/c/Users/niketagrawal/Anaconda3/envs/my-dev/python.exe
```
The above operation of specifying the python interpreter version needs to be done only once. 

Now, the virtual environment can be activated and run using 
```
pipenv shell
```

***Interesting behavior observed!***
When the pipenv virtual env is activated by typing `pipenv shell`, the conda environment changes to base! When this env is exited, the env changes back to the new conda env that was active earlier. Is this normal?

[Pipenv documentation](https://pipenv.pypa.io/en/latest/advanced/#pipenv-and-other-python-distributions) says the following.
To use Pipenv with a third-party Python distribution (e.g. Anaconda), you simply provide the path to the Python binary:
```
$ pipenv install --python=/path/to/python
```
Does the path to python binary needs to be given each time we use pipenv command like activating the virtual env by launching a shell?


### Best practices for dependency management 


set-prereleases option's significance in Pipfile is not clear at this point

#### Scenario 1: When creating a new project which will be packaged and distributed in future

Ask the end user to first generate a lock file corresponding to their system and then use that to install dependencies

#### Scenario 2: When using an already existing software package with Pipfile and pipfile.lock

Pipfile.lock contains the specific version numbers of the dependencies and the sub dependencies required by a project. This is the preferred choice when insalling dependencies from an already exsting pipfile.lock. However, pipfile.lock contains system specific hashes and may not work across different systems.

***To be verified!***
`pipenv lock` should be run on your system first and then the new pipfile.lock should be used for installing dependencies using the command
```
pipenv install --ignore-pipfile
```

It needs to be checked whether generating a new lock file on our system modifies the version number information in the original lock file or not.






