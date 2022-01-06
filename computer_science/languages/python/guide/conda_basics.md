---
alias: [Conda Basics]
tags: [python, conda, anaconda, HOW-TO, guide]
status: ongoing
edited: 2022-01-06
---

# Conda Basics
[Official Guide](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)

After installation, make sure to run `conda init` so that conda can work properly in the shells.

## Create environment
`conda create -n {environment name} {python version}`

e.g.
`conda create -n my_env python=3.8`

## Activate environment
`conda activate {environment name}`

e.g.
`conda activate my_env`

## Deactivate environment
`conda deactivate`

## View list of environments
`conda env list`

## Set environment variables
Activate environment first, then `conda env config vars set {variable=value}`

e.g.
`conda env config vars set FLASK_APP=main.py`

## Check list of environment variables
Activate environment first, then `conda env config vars list`

## Remove environment
`conda env remove -n {environment name}`

e.g.
`conda env remove -n my_env`

## Working with Jupyter Notebook
Once an environment is created and activated, run `conda install ipykernel jupyter` to install Jupyter Notebook.

Once installed, run `python -m ipykernel install --user --name {environment name}` to create a kernel that the Jupyter Notebook can use.

e.g.
`python -m ipykernel install --user --name my_env`

In a normal Python Virtual Environment, there is no need to set ipykernel. However, for conda environment, this is necessary.