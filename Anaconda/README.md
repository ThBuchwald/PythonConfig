# Anaconda Environments

Anaconda is the package management system for data science-related development and research tasks. It's the stepping stone to a fully functional Python environment\* inside JupyterLab\**.

\* It offers much more functionality in several other programming languages, of course.

\** Anaconda doesn't restrict you to the use of Jupyter; please see this doc in the context of the main ReadMe.

## Some Basic Commands

These require you to have a functioning, i.e. initialized and activated, Conda (see main ReadMe). They are all taken from the [Anaconda doc](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-with-commands).

`conda --version`: gives you the version number of the current installation

`conda update --all`: updates all installed packages

`conda create --name myenv`: create an environment

`conda create -n Python2 python 2.7`: create an environment with Python 2

`conda install -n myenv scipy`: install SciPy (or any package) for a given environment

`conda env list` / `conda info --envs`: list all environments

`conda create --name myclone --clone myenv`: create a clone of an environment

`conda activate myenv`: activated the desired environment; the current environment is shown in your Bash window in brackets above each prompt.

`conda env export > environment.yml`: export the active environment to a new file

`conda env create -f environment.yml`: create an environment from a .yml-file

`conda remove --name myenv --all`: deletes an environment with all its packages

## Some Rules and Hints

taken from the [doc](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-with-commands) as well as some [good](https://towardsdatascience.com/get-your-computer-ready-for-machine-learning-how-what-and-why-you-should-use-anaconda-miniconda-d213444f36d6) [reference](https://medium.com/data-science-bootcamp/anaconda-miniconda-cheatsheet-for-data-scientists-2c1be12f56db) [articles](https://towardsdatascience.com/a-guide-to-conda-environments-bc6180fc533).

* Conda makes sure that all interdependencies of packages are satisfied/installed. `conda install pandas` will install *numpy* as well.
* It is best to install all packages at once, so that all of the dependencies are installed at the same time.
* It is recommended to install packages not from within an environment (which totally works), but from the default shell. In order for this to work, you have to specify the name of the environment that you want to install to: `conda install --name myenv scipy`. This way you don't clutter your base environment with unnecessary packages.
* **DO NOT** clutter the base environment with packages! Create new environments for specific tasks.
* Searching for a specific package name and "Anaconda" on your favourite search page will almost always turn up a site where it will tell you how to install the package. Many packages are included with the Anaconda install, others you get from Conda-Forge or some other repo.
* Do not install via `pip`. This is seldom if never necessary.

## Ideas for Environments

This will be filled over time as the list of environments grows.

### Python 2 for Legacy

An environment with a working Python 2.7 is recommended for cases where you find old code on the internet.

`conda create -n Python2 python=2.7 pandas`

### Data Science Base

`conda create -n Python3 pandas scipy sympy matplotlib jupyterlab` 

### Machine Learning Base

`conda create -n MachineLearning pandas scipy matplotlib jupyterlab scikit-learn`

### Excel IO

`conda create -n ExcelIO pandas scipy jupyterlab openpyxl xlsxwriter`