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

### Using Git bash terminal in VS code with Anaconda python interpreter

In windows, vscode uses git bash as the default termnal. Activating anaconda environments and using the anaconda python interpreter from here may not be possible. To fix this problem, some changes in the .bashrc and .bash_profile are required as described in [this Stack Overflow issue](https://stackoverflow.com/questions/57560017/stuck-when-setting-up-to-use-anaconda-with-vs-code-and-integrated-git-terminal)


### Specifying conda-forge as one of the channels
 Instead of specifying conda-forge as a channel every time when using the conda instll command, add it to the list of channels using the below commad which will be queried for package installation when using the command conda install <package>
```
conda config --add channels conda-forge
```


