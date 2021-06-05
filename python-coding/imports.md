
When using relative imports in python 3, run the scripts as module using the `python -m <module>` format, where `module` is code.py

When using absolute import, first add the root package to Pythonpath and then run the modules as scripts as usual using `python module.py`
Installing the package in development mode places the package in Python path.

Absolute imports render a better readability than relative imports.

The root package gets added to the python path when the package is installed in the system. <br/>
References: <br/>
https://stackoverflow.com/questions/16981921/relative-imports-in-python-3 - absolute vs relative import<br/>
https://docs.pytest.org/en/6.2.x/goodpractices.html for basic setup.py content that is need to install the package in development mode.

The above behavior is slightly different when using pytest. If there are only functions by the name tests_<something> in the test modules, then it is Okay to use absolute imports and not locally install the root package (i.e., add root package to Python path via installing package in dev mode). The tests can still be run when the command `pytest` is run from anywhere in the package. However, if there is any executable piece of code in the modules that contains test functions then the same behavior as mentioned in the previous paragraph is observed.
