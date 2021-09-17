### Software documentation
Three key aspects to keep in mind when creating the documentation for your project:

+ The target audience
+ The content of the documentation
+ The structure of the documentation

#### The Audience

Documentation is generally developed for two sets of target audience, i.e., end-users and developers. Having this clarity will help you to identfy the content and structure your documentation well.
 
**End-Users**: This audience is concerned with only using the software. Information about the software design, code and internal details is not relevant. 
**Developers**: This audience is concerned with contributing to the software by adding new functionality/features, tests, documentation, fixing bugs, etc. Information about the software design, code and internal details is therefore important. 

#### The Content

**User documentation**
It should contain at least the following:

+ Provide a brief overview of the software answering the below questions:
    + What does the software do?
    + Who is it for?
+ Installation instructions
+ Examples and tutorials to get started

**Developer documentation**
+ Source code documentation - docstrings and comments
+ Provide a contributing guide with the following information:
    + What to contribute? - features, bug reports, bug fixes, tests, documentation
    + How to contribute?
    + How to set up a local development environment?
    + Information on the branching model 
    + Merge request guidelines
+ Technical reference - software design details, description of modules and components
+ API documentation (if applicable)

 #### How to structure the documentation? 

+ As a bare minimum, user documentation should be present. A Readme file can be provided with the software that includes the following.
    + Brief description of the software 
    + Installation instructions
    + Getting started information/How to use?(examples, tutorials)
+ Add the examples, tutorials, developer documentation in separate markdown files in the software repository and link them in the Reamde, thereby keeping the Readme file short.
+ For small projects with basic documentation, use the above approach of a Readme file + additional markdown files.
+ For projects with more extensive documentation, consider using a documentation hosting service such as [Read the Docs] (https://docs.readthedocs.io/en/stable/#) that offers features such as continuous documentation, notebook style documentation (embedding code in documentation), etc.

#### References
+ [A beginner’s guide to writing documentation](https://www.writethedocs.org/guide/writing/beginners-guide-to-docs/#id1)