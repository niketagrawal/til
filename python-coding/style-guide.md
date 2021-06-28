Available linters for static code analysis:

- flake8: Covers PEP8 
- Pylint: Identify more specific programming errors and offers suggestions in addition to covering PEP8.
- Black: Not a linter, but a code auto-formatter. Follows PEP8.

### How should the coding style be incorporated in the development process? - manually or automated (via CI)?

Integrating the above solutions in CI is desirable so that a consistency is maintained in the code that is on the repository. 

Flake8 can be put in CI. This means that the CI will fail if there are even minor indentation errors. This can be a bit inconvenient but the developers can run black before committing the code which will take care of most of the errors that they might see in the CI. It does not seem like a good idea to create a client side pre-commit hook that runs black because then after every commit the source files will be modified again by Black which will result in an extra commit each time.

Pylint can be run by the developers on their local system to identify code smells or look into suggestions for improving code quality and make it clean. Pylint highlights missing function and module docstrings but the downside is that it also expects the same in tests. Test functions are self explanatory, they don’t need docstrings. This can't be ignored in CI.

Putting only flake8 in CI will help maintain at least a bare minimum code standard.
