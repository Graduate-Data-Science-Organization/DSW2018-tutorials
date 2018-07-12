# How to Use this Tutorial

## Method 1: Binder

[binder](http://mybinder.org) is a free service that creates temporary cloud-deployed computational environments from GitHub repos.
Click the badge below (and wait up to a few minutes) to create one for this repository.
You'll be dropped into a new tab in your browser.
Open the `JupyterNotebookForGreatGood` folder and then `00 - basics of Jupyter.ipynb` to get started.

[![Binder](https://mybinder.org/badge.svg)](https://mybinder.org/v2/gh/charlesfrye/DSW2018-tutorials/master)

## Method 2: Local Installation

If you have the [Anaconda distribution](https://conda.io/miniconda.html)
of Python installed, download/clone this repository and then
navigate into the folder and run the command
```
conda env create -f environment.yml
```
in the Terminal/Command Prompt.

If you'd like to use `pip`+`virtualenv`, check the `environment.yml` file for dependencies.
The dependency on `rise` can be safely omitted if you're not trying to run `presentation.ipynb` as a presentation.

Once installation is complete, activate the environment
(Anaconda will provide instructions in the Terminal/Prompt)
and then run
```
jupyter notebook
```
in the Terminal/Prompt.
