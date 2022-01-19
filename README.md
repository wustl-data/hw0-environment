# Environment Setup
***
Follow these steps to get a working Python environment going that should prepare you for the programming assignments in this course. These are suggestions to get you started -- you may use your own environment setups if you are more familiar with them (i.e. Anaconda distribution, pure-Windows setups, etc.). If you are confident using your own environment, you may skip to [Clone This Repository](#clone-this-repository) to test out our workflow. 

If following this tutorial causes errors at any step of the process, please [open an issue](https://github.com/wustl-data/environment-setup/issues/new) -- it is likely other students are experiencing the same problem as well. Obviously, you may skip any steps for which you already have the software installed.

## Windows Users Only - WSL installation
I prefer using the Windows Subsystem for Linux (WSL), which allows us to use a fully-operational Ubuntu operating system within Windows. In addition to the added stability of using Ubuntu over Windows, we get to use a Unix-style command-line interface (`bash` by default) which matches those commonly found in various software tutorials and installations.

From PowerShell:
```shell
$ wsl --install
```
> Note: shell commands are usually denoted with a $ sign for clarity. Do not copy the $ if you copy and paste commands from any documentation.

Restart your machine if prompted. Ubuntu should now be available in your Windows Apps, if not, download it from the Microsoft Store. Open Ubuntu and enter some basic credentials (your password does not need to be secure without good reason).

From your (Ubuntu) bash shell, run the following to upgrade Ubuntu's installed packages:
```bash
$ sudo apt update && sudo apt upgrade
```

## All Users - Pyenv and Python 3.9.6 installation
1. Install the [Python build dependencies](https://github.com/pyenv/pyenv/wiki#suggested-build-environment) for your OS.
2. Try running the automatic Pyenv installer using the command:
```bash
$ curl https://pyenv.run | bash
```
If that fails, try the [manual installation process](https://github.com/pyenv/pyenv#installation) using the directions for your OS (WSL users, use the "GitHub Checkout" instructions for Ubuntu).

Install Python version 3.9.6 -- this is the latest version available on Pyenv as of the creation of this document and will be the Python version we use throughout this course.
```bash
$ pyenv install 3.9.6
```
You may set the global Python version as 3.9.6 or establish this version individually for each project/assignment. See `pyenv --help` for some hints on how to do this, if it hasn't been done for you already.

## Poetry
Now, install `poetry`:
```bash
$ curl -sSL https://install.python-poetry.org | python3 -
```
This will manage both your dependencies and your virtual environments. If you don't know what this means, please [open an issue](https://github.com/wustl-data/environment-setup/issues/new) for discussion.

> A note on virtualenv management: You may be familiar with a package/virtualenv manager called Pipenv. While using Pipenv is perfectly reasonable, many people in Python are moving to Poetry, especially for its use of a `pyproject.toml` configuration file, which is quickly becoming a [Python standard](https://www.python.org/dev/peps/pep-0621/). Pipenv (and pip in general) are a little more common, so most package installations will ask you to run `pip install <packagename>`. Poetry's corresponding command is `poetry add <packagename>` and will work as a substitute for `pip install` in 99% of instances.

## Configure your GitHub credentials.
Especially if you have not done this before from your command line, you will likely need to establish your git credentials to communicate with GitHub. Follow the instructions [here](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github#authenticating-with-the-command-line) to authenticate your command line. I won't go into further detail here to save time and space, but these steps are historically a little bit finicky, so please open an Issue if you have any roadblocks.


## Clone this Repository
> A quick note about `bash` syntax: your "home" folder is designated by a `~`: that is why you see a `~` on your shell, indicating your _current directory_ (`cd`). To list the files in your current directory, type `ls` or `ls -a` (the `-a` flag shows hidden files designated with a `.` at the beginning of their filename e.g. `.bashrc`/`.bash_profile, which executes the code within each time you open your shell).

From your home directory or a directory of your choosing (`~/code/` is a common choice), make a directory for this class:
`mkdir cse314 && cd cse314`
or
`mkdir dcds510 && cd dcds510`
or whatever you would like.

> The `&&` simply executes the next command after the first one successfully completes.

Now clone this repository, which will copy the files contained herein to a new folder on your machine. Go to the top of this page and copy the repository URL, which you can find by clicking the big green "Code" button. Be sure to use the correct URL (HTTP or SSH) depending on how you set up your credentials. Now perform the clone:

```bash
$ git clone <your-repo-url>
```
These URLS are generally found using the big green "code" button at the top of this page.

`cd` into your new folder:
```bash
$ cd hw0-environment
```

## VS Code IDE
VS Code is a state-of-the-art IDE that works cross-platform (including with WSL) and provides many nice features and extensions, including an integration with GitHub Classroom (we will have to find out how that works together). Feel free to use your IDE of choice, but this one is a good, stable choice. [Install it](https://code.visualstudio.com/) if you haven't already.

You may open VS Code from your bash shell by entering `code .` (the dot instructs VS Code to open in the _current directory_). You should now have a VS Code window opened to your assignment directory.

If there isn't one open already, open a terminal window within VS Code using the menu at the top or the shortcut Ctrl+Shift+` (that's a backtick).

## Install the project dependencies
The code in the git repository that you cloned includes some package dependencies, so we will install them:
```bash
$ poetry install
```
Now, we will let Poetry create a virtual environment for us (which isolates our package dependencies from the rest of our system) and activate it for our shell:
```bash
$ poetry shell
```
You should now see your activated virtualenv on your command line next to your shell prompt. You are now ready to Python!!!

## Create a Python script
Using your IDE (or a command line command if you're feeling endeavorous), create a file called `hw0.py`.

## Commit your changes
You made a successful change to your repository, so it's time to commit your changes. As we progress, you may skip some of these smaller steps between commits, but it's better to make too many commits now and get in the habit of performing them often.

1. Check on your git status:
  ```bash
  git status
  ```
  You will notice that `hw0.py` is not being tracked. Let's fix that.
2. Add your new file to "staging":
  ```bash
  $ git add hw0.py
  ```
3. Check your git status again to make sure that your file was added to staging. It should be a nice green color. In general, "staging" should be reserved for files that are ready to commit, but you want to wait until you finish coding up some other files before committing them all together. Since this is the only file we are changing, let's commit:
4.
  ```bash
  $ git commit -m "add hw0.py"
  ```
  The `-m` flag stands for "message" and is required on all git commits -- simply type a sentence that describes what the commit does.  Someone reviewing your code should easily be able to review all of the steps you took via your commit history through these messages.
  
 Great job, almost done!
 
 ## Write some Python
 The dependencies you installed with Poetry included a neat package that generates fake data called `Faker`. Let's use this code to make a `.csv` file full of fake information.
 
 1. Open `hw0.py`
 2. Skim the `Faker` documentation and write a script that generates 1000 unique first names. Seed the data with your student ID. 
 3. Commit your code.
 4. Now, add some code that creates a file named `fake_data.csv'. I suggest using Python's built-in `csv` module or installing Pandas and using the `.to_csv` function. The `csv` route might be quicker, easier and more "Pythonic." However, now is as good of a time as any to start getting acquainted with Pandas if you are not already familiar.  Commit your code again -- I expect at least two commits out of this step.

## Submit your code for grading
Your code is ready for grading!
Push to the repository you cloned this from:
```bash
$ git push
```
Behind the scenes, this runs `git push origin main` by default-- `origin` specifies which _remote_ repository you would like to push to, while `main` specifies which branch you would like to push.

GitHub will now autograde your assignment; check it out and correct any changes you need to make before re-pushing.

Congrats on finishing Homework 0!!! You've got the boring stuff out of the way!!!
