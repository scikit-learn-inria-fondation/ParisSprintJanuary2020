# January 28th : Beginner Workshop

(from 9.30AM to 6PM)

Please start now the [VS buildtools for Windows](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools) if you have not already. Do not install it.


## installing a Python dev environment with

### conda

- miniconda installation
- create an environment (`sklworkshop`)
- version listing and package listing
- activate and deactivate environments

### github

- where the sources are (numpy, skl, pandas)
- skl fork

### git

- install (git bash for [Windows](https://git-scm.com/download/win))
- git clone numpy
- git clone fork sklearn
- git remote configuration
https://learngitbranching.js.org/
https://learngitbranching.js.org/?NODEMO

### VS Code

Install VSCode and its Python extension

activate `sklworkshop` environment before launching
or shift ctrl p "select python interprerter" and choose "sklworkshop"

Open project folders (skl numpy) CTRL-K CTRL-O 

Switch projects (CTRL-R) 

Code browsing (`CTRL-P`, files , `CTRL-T`, symbol navigation)
`CTRL-SHIFT-P` "select linter"

### Practical code navigation

Find example files that mention the word "importance" in different ways:
- CTRL P "example importance" in Vscode and open `plot_permutation_importance.py`
- go to https://github.com/scikit-learn/scikit-learn in a browser then press `t` then type "example/importance"

Navigate to the RandomForestClassifier or Regressor from the `plot_permutation_importance.py` example clicking on the class name in
github or by ctrl-clicking on the class name in VScode

Find the class KMeans in skl in two different ways
- from the commande line using `git grep "class KMeans"` (-i case insensitive, without class all occurrences) 
- CTRL-T KMeans (disable jedi if it doesn't work) in VScode

### installing C/C++ compilers to be able to build native extensions

See instructions for your OS in the [installation guide](https://scikit-learn.org/stable/developers/advanced_installation.html#building-from-source).
- [Windows](https://scikit-learn.org/stable/developers/advanced_installation.html#windows)
- [macOS](https://scikit-learn.org/stable/developers/advanced_installation.html#macos)
- [Linux](https://scikit-learn.org/stable/developers/advanced_installation.html#linux)


## building the master branch of numpy and scikit-learn

```
cd numpy
pip install -e .
cd ..
pip show numpy
conda install ipython
ipython
>>> import numpy as np
>>> print(np.__version__)
1.19.0.dev0+xxxxx
CTRL-D
```

```
cd scikit-learn
pip install -e .
cd ..
pip show scikit-learn
ipython
>>> import sklearn
>>> print(sklearn.__version__)
0.23.dev0
CTRL-D
```

## Run a scikit-learn example
`plot_permutation_importance.py`
### from the command line
```
cd scikit-learn
ls examples
ls examples/inspection
python examples/inspection/plot_permutation_importance.py
```

### from VScode
ctrl P "plot permutation importance"
shift ctrl P "Run Current File in Python Interactive Window"


    tutorial on how to use pytest to run the tests of a specific module
    presentation of the github collaborative workflow (pull requests and code reviews)
    what is continuous integration and how to read the CI reports and what are the main CI configuration files
    building the documentation with sphinx and sphinx gallery
    optional: quick intro to Cython
