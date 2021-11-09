
When using relative imports in python 3, run the scripts as module using the `python -m <module>` format, where `module` is code.py

When using absolute import, first add the root package to Pythonpath and then run the modules as scripts as usual using `python module.py`
Installing the package in development mode places the package in Python path.

Absolute imports render a better readability than relative imports.

The root package gets added to the python path when the package is installed in the system. <br/>
References: <br/>
https://stackoverflow.com/questions/16981921/relative-imports-in-python-3 - absolute vs relative import<br/>
https://docs.pytest.org/en/6.2.x/goodpractices.html - basic setup.py content that is need to install the package in development mode.

If there is __init__.py in the same directory as the source code then local installation of the project is not needed. For example, the project structure in [pytemplate](https://github.com/niketagrawal/pytemplate) has __init__.py in the same directory as the soure code, this facilitates running tests by executing 'pytest' from the root directory and not having to install the package in the developmen mode. Ref: https://blog.finxter.com/python-import-error-modulenotfounderror/

Install the project in editable mode only when you are testing your patch to a package through another project. Ref: https://newbedev.com/when-would-the-e-editable-option-be-useful-with-pip-install In other cases it is not needed and can be skipped to avoid complexities.





