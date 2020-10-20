### Creating and using a separate virtual python environment for each project

Post anaconda installation, a root python environment called `base` is created. Conda also allows to create virtual python environments.

When working on multiple projects simultaneously, a good practice is to use a dedicated virtual environment for it to install the required dependcies and libraries, instead of installing everything from each project into the root (base) environment.

(Below commands are as per Git Bash)

This can be done by the following command. 
```
conda create --name <env_name> python=3.X
```

The current list of environments can be fecthed by 
```
conda env list
```
By default, the root (base) environment is activated marked by a *. Another env from the list can be activated using

```
conda activate <env-name>
```

### Activation of virtual env has terminal scope.
Activation of virtual env on conda prompt/Git bash does not reflect it system wide on other active terminals. For e.g., activation of a virtual env on gitbash will not activate it on VScode's terminal. The same operation has to be repeated there too.


