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
$ git clone https://github.com/numpy/numpy.git
```
- fork scikit-learn on github then git clone your fork
```
$ git clone https://github.com/<myuser>/scikit-learn
```
- git remote configuration
```
$ git remote -v
...
$ git remote add upstream https://github.com/scikit-learn/scikit-learn.git
```

### conda

#### Install miniconda

- [miniconda](https://docs.conda.io/en/latest/miniconda.html)
[installation](https://conda.io/projects/conda/en/latest/user-guide/install/index.html) (latest Python3 version)
- initialize the conda command in git bash
  - Windows: open "Git Bash" and type
  ```
  $ ./Miniconda3/Scripts/conda init bash
  ```
  - Linux:
  ```
  $ conda init bash
  ```
- then close your shell and start a new one to type:
  
  ```
  $ conda info
  ```
  or
  
  ```
  $ which conda
  ```
  to check that the conda command is in your PATH and useable from your shell.

#### conda environments

- create an environment (`sklworkshop`)
```
$ conda create --name sklworkshop
```
- activate and deactivate environments
```
$ conda activate sklworkshop
(sklworkshop)$ conda deactivate
```
- version listing and package listing
```
$ conda --version
$ conda list
```

### VS Code

Install VSCode following your
[system instructions](https://code.visualstudio.com/docs/setup/setup-overview#_cross-platform).

Launch VSCode and configure [Telemetry settings](https://code.visualstudio.com/docs/getstarted/telemetry).

Install the Python extension
- `Ctrl+Shift+X` open the extension manager
- search for the python extension: install

In order to work with VSCode in your Python environment
- `Ctrl+Shift+P` then "select python interpreter" and choose "sklworkshop"

Open project folders (numpy, scikit-learn): `Ctrl-k Ctrl-o` 

Switch between projects: `Ctrl-r`

Browse the code:
- by files `Ctrl-p`
- by symbols `Ctrl-t`

At some point VSCode will complain about not finding a linter: scikit-learn uses `flake8`
- Install `flake8` in your conda environment
```
$ conda activate sklworkshop
(sklworkshop)$ conda install flake8
```
- Select `flake8` as a linter in VSCode: `Ctrl-Shift-P` "select linter"

### Practical code navigation

Find example files that mention the word "importance" in different ways:
- VSCode: `Ctrl-p` "example importance" and open `plot_permutation_importance.py`
- Github: go to https://github.com/scikit-learn/scikit-learn in your browser, press `t` and type "example/importance"

Navigate to the RandomForestClassifier or Regressor from the `plot_permutation_importance.py` example:
- VSCode: ctrl-clicking on the class name
- github: clicking on the class name

Find the class KMeans in scikit-learn in two different ways:
- from the command line: using `git grep "class KMeans"` (-i case insensitive, note that without "class" you will find
all occurrences) 
- VSCode: `Ctrl-t` KMeans (disable the jedi extension if it doesn't work)

### Installing C/C++ compilers to be able to build native extensions

See instructions for your OS in the [installation guide](https://scikit-learn.org/stable/developers/advanced_installation.html#building-from-source).
- [Windows](https://scikit-learn.org/stable/developers/advanced_installation.html#windows)
- [macOS](https://scikit-learn.org/stable/developers/advanced_installation.html#macos)
- [Linux](https://scikit-learn.org/stable/developers/advanced_installation.html#linux)


## Building the master branch of numpy and scikit-learn

```
$ cd numpy
$ pip install -e .
$ cd ..
$ pip show numpy
$ conda install ipython
$ ipython
>>> import numpy as np
>>> print(np.__version__)
1.19.0.dev0+xxxxx
CTRL-D
```

```
$ cd scikit-learn
$ pip install -e .
$ cd ..
$ pip show scikit-learn
$ ipython
>>> import sklearn
>>> print(sklearn.__version__)
0.23.dev0
CTRL-D
```

## Run a scikit-learn example
`plot_permutation_importance.py`

### from the command line
```
$ cd scikit-learn
$ ls examples
$ ls examples/inspection
$ python examples/inspection/plot_permutation_importance.py
```

### from VScode
`ctrl-p` "plot permutation importance" then
`Ctrl-Shift-P` "Run Current File in Python Interactive Window"

## Run tests with pytest
```
$ conda install pytest
```

Each sklearn subpackage comes with a `tests` folder that gathers the test files related to it.

Use VSCode to open the source code for the RandomForestClassifier class.

- What is the path of this file?
- Can you find the folder that holds the tests for RandomForestClassifier in the VSCode file explorer?
- Can you find the test folder and list its content using the `ls` command?
- Locate the file `test_forest.py` in that folder.

To run the test
```
$ pytest --verbose ./<path_to_test_folder>/test_forest.py
```

Edit the source code of RandomForestClassifier to change the predict method always return 0.
Rerun the test: what do you observe? 

alternatively you can use the `vlx` flags as follows:
```
$ pytest -vlx ./<path_to_test_folder>/test_forest.py
```
Find out about the meaning of those flags with
```
$ pytest --help
```

## Write a new test of your own


## Collaborative workflow via github (pull requests and code reviews)

What does branching mean?

https://learngitbranching.js.org/

https://learngitbranching.js.org/?NODEMO

- Create a new branch locally from your master
```
$ cd scikit-learn
$ git status
$ git branch my-awesome-branch
$ git status
$ git checkout my-awesome-branch
```
- Make your modifications and commit
- Push the new branch to your fork
```
$ git push origin my-awesome-branch
```
- From the github interface open a Pull Request (PR) to your master

## Continuous Integration

- From the github interface open a PR to 
  - https://github.com/cmarmo/scikit-learn or
  - https://github.com/ogrisel/scikit-learn

**Please, do not submit the PR to scikit-learn/scikit-learn!!**



## Building the documentation with sphinx and sphinx gallery

Check the documentation [here](https://scikit-learn.org/stable/developers/contributing.html#documentation)
