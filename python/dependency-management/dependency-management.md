### Goal

Render reproducility and visibility to the software by managing dependencies in a manner that allows easy distribution of the software package by the developer and the replication of the development environment by potential contributors and users.

### Choosing Conda as development environment for better software reproducibility
Using conda environment for development provides the possibility for managing the depdnencies in a way that allows the software be distributed and be used by the users who use conda and also those who don't , i.e., using just pip (+ virtual env if desired)

Conda allows to create isolated virtual environments, as a best practice one environment should be cerated for each project. See conda/conda.md for more information

### Use a combination of conda + pip for dependency management. 

Use conda package manager to install packages inside conda environment. Using pip inside conda is discouraged as per the official documentation 
([ref1](https://www.anaconda.com/blog/using-pip-in-a-conda-environment),
[ref2](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#using-pip-in-an-environment))


### Dependency management targeting conda users - Export entire conda environment
Export entire conda environment into a yml file called an environment.yml file. environment.yml is the standard naming convention, generate this file for each project in respective project specific folder. Naming it environment.yml also enables it to be picked by other tools like binder [ref](https://researchsoftwarehour.github.io/sessions/rsh-011/)


#### Workflow
Install packages required for development using `conda install`. At the end, use the following command to export the environment into a yml file
```
cond env export > environment.yml
```
Other users can replicate the conda virtual environment using this file by using the command
```
conda env create -n myenv -f environment.yml
```

### Generate requirements.txt

Here we plan to generate a requirements.txt file so that non-conda users can use `pip install -r requirements.txt` to install the dependencies the usual way.

#### Make sure to generate requirements.txt in pip compatible format!

conda also allows to create a requirements.txt file uisng the command `conda export --list > requirements.txt`, but this has a different format than the requirements.txt that is used by pip for dependency management. 

To generate requirements.txt for pip, generally the command `pip freeze > requirements.txt` is used. However, since we install the packages using `conda install` instead of `pip install` as per the recommended best practice, generating requirements.txt using `pip freeze > requirements.txt` will result in a file that contains symbolic links which still can't be used with pip. For details, see this [Stack Overflow issue](https://stackoverflow.com/questions/64500342/creating-requirements-txt-in-pip-compatible-format-in-a-conda-virtual-environmen).

#### Tip to stick to using conda install and still being able to generate pip compatible requirements.txt 

The solution provided in the above linked stack overflow issue allows to stick to the best practice of using `conda install` for installing packages in conda environment while also be able to generate a pip compatible requirements.txt file that non conda users can use. 

To generate requirements.txt file that is compatible with pip, use the following command
`pip list --format=freeze > requirements.txt`

#### Tailor the requirements.txt before distributing it

Note that this pip compatible requirements.txt file generated above may still result in errors when used in the command `pip install -r requirements.txt` by non conda users as it may contain some extra packages that were installed as part of conda install.

Therefore, it is recommended to manually tailor this requirements.txt file to keep only those packages which are actually being imported in the code.

### Project directory structure

[This](https://stackoverflow.com/questions/48787250/set-up-virtualenv-using-a-requirements-txt-generated-by-conda) shows a typical structure for a python project repository. The project directory contains both environment.yml (for Conda users) and requirements.txt (for pip).