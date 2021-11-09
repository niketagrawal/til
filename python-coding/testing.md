### Code coverage

```
pytest --cov=package 
```
where package is the root project directory with the source code. 

#### Generate html code coverage report

```
pytest --cov-report html:cov_html --cov=package tests/
```
