# January 28th : Beginner Workshop

(from 9.30AM to 6PM)

## installing a Python dev environment with

### conda

- miniconda installation
- create an environment
- version listing and package listing
- activate and deactivate environments

### github

- where the sources are (numpy, skl, pandas)
- skl fork

### git

- install
- git clone numpy
- git clone fork sklearn
- git remote configuration
https://learngitbranching.js.org/
https://learngitbranching.js.org/?NODEMO

### VS Code
Install main et plugins
activate environment before launching
Open project folders (skl numpy) CTRL-K CTRL-O 
Switch projects (CTRL-R) 
Code browsing (`CTRL-P`, files , `CTRL-T`, symbol navigation)
`CTRL-SHIFT-P` "select linter"

### Practical code navigation

Find the class RandomForestRegressor in skl in two different ways
- from the commande line using `git grep "class RandomForestRegressor"` (-i case insensitive, without class all occurrences) 
- CTRL-T RandomForestRegressor (disable jedi if it doesn't work) in VScode

Find example files that mention the word Forest in different ways:
- CTRL P "example forest" in Vscode
- go to https://github.com/scikit-learn/scikit-learn in a browser then press `t` then type "example/forest"

Navigate back to the RandomForesClassifier or Regressor from the plot_forest_iris.py example clicking on the class name in 
github or by ctrl-clicking on the class name in VScode


###  installing C/C++ compilers to be able to build native extensions





    cloning and building the master branch of scikit-learn, pandas, numpy...
    tutorial on how to use pytest to run the tests of a specific module
    presentation of the github collaborative workflow (pull requests and code reviews)
    what is continuous integration and how to read the CI reports and what are the main CI configuration files
    building the documentation with sphinx and sphinx gallery
    optional: quick intro to Cython
