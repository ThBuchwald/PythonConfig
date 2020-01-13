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

### Upgrading the Base Environment

There are some very handy features that should be installed in the base environment in order to work globally. For this, *open the Bash shell as admin*.

First of, `rise` enables you to create a slide show directly from (and also within) your notebook. See [here](https://www.blog.pythonlibrary.org/2018/09/25/creating-presentations-with-jupyter-notebook/) for an example.

`conda install -c conda-forge rise`

`jupyter-nbextension install rise --py --sys-prefix`

`jupyter-nbextension enable rise --py --sys-prefix`

Secondly, the [`nbextensions`](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/index.html) package gives you some useful tools in working with the Jupyter Notebook*. These have to be installed globally as well; otherwise the extensions tab won't open in your notebook's home tab. There are some [good](https://www.endtoend.ai/blog/jupyter-notebook-extensions-to-enhance-your-efficiency/) [resources](https://medium.com/@maxtingle/10-jupyter-notebook-extensions-making-my-lyfe-easier-f40139a334ce) on the web with regards to the best extensions.

*A list of all maintained packages can be found [here](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions.html).

`conda install -c conda-forge jupyter_contrib_nbextensions`

`jupyter contrib nbextension install --system`

`jupyter nbextensions_configurator enable --system`

These steps have to be repeated in each environment where `rise` or `nbextensions` are wanted/needed. There is the possibility that it only needs to be done once — I don't know, and either way, it won't hurt executing the command twice. The flags `--sys-prefix` and `--system` should be replaced by `--user`.

### Python 2 for Legacy

An environment with a working Python 2.7 is recommended for cases where you find old code on the internet.

`conda create -n Python2 python=2.7 pandas jupyterlab`

Note that `pandas` requires `numpy`, so `numpy` does not need to be installed explicitly. Of course you can check for this package when Conda prompts for verification of the package list to be installed.

### Data Science Base

This includes:

* `pandas` for DataFrame-based computing
* `scipy` for all sorts of fitting options
* `sympy` for analytical math expressions
* `matplotlib` for plotting the results

`conda create -n Python3 pandas scipy sympy matplotlib jupyterlab` 

### Machine Learning Base

The only difference compared to the **Data Science Base** really is the missing `sympy` package, as symbolic maths is seldom needed in machine learning. Instead, the most popular ML module `scikit-learn` is installed here.

`conda create -n MachineLearning pandas scipy matplotlib jupyterlab scikit-learn`

### Excel IO

This is more or less a test environment providing Excel functionality. Will in most cases be combined with other packages, depending on the application.

`conda create -n ExcelIO pandas scipy jupyterlab openpyxl xlsxwriter`

### Productivity Environment

This environment contains all the packages you can use to be a hell of a lot more productive with lots of good extensions, and building on top of the **Data Science Base** above. There are some very useful pointers regarding productivity given in [this article](https://towardsdatascience.com/10-simple-hacks-to-speed-up-your-data-analysis-in-python-ec18c6396e6b).

1. Basic packages:

   `conda create -n Productivity pandas scipy sympy matplotlib jupyterlab`

2. `rise` and `nbextensions`:

   `conda install -n Productivity -c conda-forge rise`

   `jupyter-nbextension install rise --py --user`

   `jupyter-nbextension enable rise --py --user`

   `conda install -n Productivity -c conda-forge jupyter_contrib_nbextensions`

   `jupyter contrib nbextension install --user`

   `jupyter nbextensions_configurator enable --user`

3. Useful `nbextensions`: [spellchecker](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/spellchecker/README.html), [ExecuteTime](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/execute_time/readme.html), [Notify](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/notify/readme.html), [Skip-Traceback](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/skip-traceback/readme.html), [Scratchpad](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/scratchpad/README.html), [Snippets Menu](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/snippets_menu/readme.html), [Initialization Cells](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/init_cell/README.html), [Collapsible Headings](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/collapsible_headings/readme.html), [Table of Contents (2)](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/toc2/README.html), [Hinterland](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/hinterland/README.html), [Variable Inspector](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/varInspector/README.html)

   There are many more, just browse through the collection.

   ![nbextensions](M:\Git_Projects\Install_Instructions\Anaconda\nbextensions.PNG)

4. plotting tools:

   [This article](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions.html) convinced me of the increased productivity of [`seaborn`](https://seaborn.pydata.org/tutorial.html) over `matplotlib`.

   `conda install -n Productivity -c anaconda seaborn`

   For interactive plots, there is the choice between several packages, popular are for example (see again the article linked above) `bokeh` and `plotly`. The article above also links to [a very useful website](https://www.data-to-viz.com/) that tells you how to do certain graphs/diagrams.

   `conda install -n Productivity -c plotly plotly  `

5. [Widgets](https://github.com/jupyter-widgets/ipywidgets):

   `conda install -n Productivity -c anaconda ipywidgets`

   There are lots of features you get with the inclusion of interactive widgets. Some are described [here](https://towardsdatascience.com/bringing-the-best-out-of-jupyter-notebooks-for-data-science-f0871519ca29). This article also describes the usefulness of themes, for example if you want a different background in your slide show. Let's do that:

6. Notebook Themes:

   `conda install -n Productivity -c conda-forge jupyterthemes  `

### Others

When you found a working tool for an application, build a new environment from the packages that you found suitable.