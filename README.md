# PythonConfig
This is simply a README to guide through the installation of a proper Python environment for work in a scientific background **in Windows 10**. Please be careful not to wreck your system; this text has not been written by an experienced user...*

This guide aims at the first-time user that has not heard much about any of the programs found below. For example: if you know your way around Anaconda, this is not for you; if you instantly recognize Atom as a bad choice, definitely not for you.

*I actually wrote the first version after I had only used Git, Python, Anaconda, and such for two weeks.

## Installation Procedure
Please follow the installation procedure strictly in the [sequence](https://wiki.lesswrong.com/wiki/Sequences) shown below.

### 1) install Atom
Atom is a light-weight, free and open-source text editor that is easily configurable to your needs.
Download Atom (https://atom.io/) for 64-Bit Windows 7 or later. If in doubt, run the setup as admin.

There are some things you can do to make your life instantly easier in Atom. Once open, go to File ? Settings ? Install. There you can search for and consequently install some useful packages:
* _script_: This package runs Python and other code, depending on the file extension you give. Simply run a file with `Strg+Shift+b`. If you're only getting started, this may be the only package you need.
* _minimap_: Zoom out to get an idea of your location in a zillion lines of code.
* _linter-pylint_: This one analyzes your code and gives you feedback regarding style incongruities. It will ask you to install some dependencies.

### 2) install Git
Git is the version control software you have probably heard about (although it is not the same as GitHub, they're both deeply intertwined).

What is also installed is Git Bash. This is a command line interface (CLI) that is vastly superior to the Windows CMD. You need this to run Jupyter Notebooks, do version control via Git, setup Anaconda, etc.

Download the Git setup (https://git-scm.com/) for 64-Bit Windows. Make sure that run the file as admin. There are some important steps you must not skip during the installation:
* Check _Git Bash Here_ for context menu and to associate certain files with Git.
* _Use Atom as Git's default editor._ In some cases, this option will be greyed out. Just default to using Vim; we'll change the default editor later.
* _Git from command line and also from 3rd-party software_
* _Use the OpenSSL library._ Should be the default.
* _Checkout Windows style._
* _Use MinTTY._ Important, as this improves a lot on the standard Windows terminal.

### 3) set up Git (Bash)
After installing Git, open Git Bash. This may be a good moment to start using the keyboard instead of the mouse, as you'll be opening a terminal window. Press `Windows`, type the first few characters of `Git Bash`, until the program's shortcut appears and press `Enter`.

First, right-click on the Bash symbol in the upper left corner to open options. Ther you can change the appearance of the terminal. I usually lighten the background from black to a dark grey, as it goes easier on the eyes.

Once your done, type `cd` and press `Enter`. This command sends you to your home directory. Enter `pwd` to print your working (in this case, home) directory. If you enter `start .`, the current folder/directory is openend. This is supposed to be the user folder under which you normally sign into the computer. If this is not the case, most likely you ran the terminal as admin. If this is the case, close the terminal (enter `exit`) and open it up again.

As normal user, enter some commands. In each case, the dollar symbol `$` signifies a new terminal line.
* `$ cd`
* `$ touch .bash_profile` This creates a new file.
* `$ git config --global user.name "<your-full-name>"`
* `$ git config --global user.email "<your-email-address>"`
* `$ git config --global color.ui auto`
* `$ git config --global merge.conflictstyle diff3`
* `$ git config --global core.editor "atom --wait`
* `$ git config --list` This will give you an overview of the saved settings. All of the above should be found there.

**Pro-Tip**: Use the arrow keys to navigate through a history of commands you entered in the current terminal session. This will save you a lot of typing.

Don't manually exit the terminal, instead type `$ exit` and press `Enter`.  

### 4) install Anaconda

Instead of installing Python manually, Anaconda (https://www.anaconda.com/) brings all of the most important Python packages for data science. This will be your default Python installation.

Download the Python 3, 64-Bit version and start the setup .exe. 

Make sure that you _add to PATH_! This is not recommended by the set-up. However, in the case where your Windows user is not admin, not checking this option can introduce some headache during the setup of Git Bash later. If you want to set up your home system, this is most likely not be required as you can do it later in Git Bash.

### 5) set up Anaconda in Git Bash
First, get the path to the Anaconda folder. If installed for all users, this would be something like `/c/ProgramData/Anaconda3`.

Open Git Bash, **this time as admin**.  If the PATH was set correctly during installation, `$ conda --version` will print a version number, e.g. `conda 4.7.12`. If this is not the case, you need to set the path to the Anaconda install directory:

`$ cd`

`$ echo 'export PATH="$PATH:[YOUR_PATH]:[YOUR_PATH]/Scripts"' >> .bashrc`

`$ echo 'alias python="winpty python.exe"' >> .bashrc`

`$ source .bashrc`

After this, it should give you the version number. 

You can also check for working Python like this:

`$ python --version`

`$ python`

`$ exit()` + `Enter`

Now, to setup a base Anaconda environment with some important Python packages, simply type:

`$ conda update --all`

`$ conda install numpy pandas matplotlib jupyterlab`

Anaconda will ask you to confirm by entering `y`.

If you open the Bash terminal as a normal user, and `conda --version` and/or `python --version` gets you an error, you will have to include the PATH to Anaconda again as shown above -- this time it will be for the standard (non-admin) user.

If all went well:
Congratulations, you're done!

## Usage
You now have a working Python environment. The command `jupyter notebook` (in a Git Bash instance) will bring up a -- you guessed it -- Jupyter Notebook in your standard browser. Enter some Python code and execute it. There is the [Definite Guide to Jupyter Notebooks](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook) which is a good starting point.

Anaconda is great at managing different environments for different configurations of Python, R, and some other programming languages. For example, for older tutorial Notebooks, you can set up a Python 2.7 environment, which you could activate whenever you want to run older code. There is a great manual at [docs.conda.io](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html).

Finally, it's probably worth your while to check out Git. This README is part of a project that has been pushed to GitHub from a local Git repository created solely in a Git Bash instance. Don't be afraid, it's super simple.

## License
[CC0](https://creativecommons.org/publicdomain/zero/1.0/deed.de)