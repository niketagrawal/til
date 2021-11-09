### Code coverage

use pytest-cov, install using pip: ```pip install pytest-cov```

#### Generate codecoverage report (without line numbers)

```
pytest --cov=package 
```
, where package is the root project directory with the source code. 

#### Generate html code coverage report

```
pytest --cov-report html:cov_html --cov=package tests/
```
Reference: https://pytest-cov.readthedocs.io/en/latest/reporting.html 
