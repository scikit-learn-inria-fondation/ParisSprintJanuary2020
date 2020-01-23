# January 28th : Beginner Workshop

(from 9.30AM to 6PM)

**Welcome!**

If you have not already downloaded them, please start now to download
[VS buildtools for Windows](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools).
Do not install it, we will do it together later.

## installing a Python dev environment

### git and github

- [git installation](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
(git bash for [Windows](https://git-scm.com/download/win)): git is a versioning system.
- [github](https://github.com) is where the sources are.

- git clone numpy
```
git clone https://github.com/numpy/numpy.git
```
- fork scikit-learn on github then git clone your fork
```
git clone https://github.com/<myuser>/scikit-learn
```
- git remote configuration
```
git remote -v
...
git remote add upstream https://github.com/scikit-learn/scikit-learn.git
```

### conda

#### Install miniconda

- [miniconda](https://docs.conda.io/en/latest/miniconda.html)
[installation](https://conda.io/projects/conda/en/latest/user-guide/install/index.html) (latest Python3 version)
- initialize the conda command in git bash (Windows only): open "Git Bash" and type

  ```
  ./Miniconda3/Scripts/conda init bash
  ```

  then close the "Git Bash" window and start a new one to type:
  
  ```
  conda info
  ```
  or
  
  ```
  which conda
  ```
  to check that the conda command is in your PATH and useable from the "Git Bash"
  terminal.

#### conda environments

- create an environment (`sklworkshop`)
- version listing and package listing
- activate and deactivate environments

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

## pytest
```
conda install pytest
```

Each sklearn subpackage comes with a `tests` folder that gathers the test files related to it.
Use VSCode to open the source code for the RandomForestClassifier class
Question: what is the path of this file?
Can you find the folder that holds the test for RandomForestClassifier in the VSCode file explorer?
Can you find the test folder in the command line?
Can you locate the file `test_forest.py` in that folder using the `ls` command.

```
pytest --verbose test_forest.py
```

Edit the source code of RandomForestClassifier to change the predict method always return 0.
Rerun the test: what do you observe? 

```
pytest -vlx test_forest.py
```

## github collaborative workflow (pull requests and code reviews)

https://learngitbranching.js.org/
https://learngitbranching.js.org/?NODEMO

- branching locally from your master
- push as a new branch to your fork
blabla

## what is continuous integration and how to read the CI reports and what are the main CI configuration files


    building the documentation with sphinx and sphinx gallery
    optional: quick intro to Cython
