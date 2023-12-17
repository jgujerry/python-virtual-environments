# pdm
A modern Python package and dependency manager supporting the latest PEP standards. It is meant to
be a next generation Python management tool.


## How to install it?

Install via script:

**Unix/Linux/Mac**
```bash
$ curl -sSL https://pdm-project.org/install-pdm.py | python3 -
```

**Windows**
```bash
$ (Invoke-WebRequest -Uri https://pdm-project.org/install-pdm.py -UseBasicParsing).Content | python -
```

The installer will install PDM into the user site and the location depends on the system:

* `$HOME/.local/bin` for Unix
* `%APPDATA%\Python\Scripts` on Windows

Other installation methods:

If you are on MacOS and using `homebrew`, install it by:

```bash
$ brew install pdm
```

If you are a `pip` user, run
```bash
$ pip install --user pdm
```

If you use `pipx`, then run
```bash
$ pipx install pdm
```


## How to use it?

Run `--help` to check available commands and options:
```bash
$ pdm --help
```

To start with, create a new `pdm` project,
```bash
$ pdm init
```

You will need to answer a few questions to help `pdm` to initialize a project with `pyproject.toml` file.

#### 1. Create a virtual environment

```bash
$ pdm venv create --name <envname>
```

#### 2. Activate the virtual environment

```bash
$ eval $(pdm venv activate <envname>)
```

#### 3. Manage Python packages

Add Python packages to project,
```bash
$ pdm add <package1> <package2> ...
```

Remove Python packages from project,
```bash
$ pdm remove <package1>
```

Update Python packages in project,

```bash
$ pdm update <package1> <package2>
```

#### 4. Deactivate the virtual environment


#### 5. Remove the virtual environment

```bash
$ pdm venv remove <envname>
```

## Different Python versions?

#### 1. Choose the Python version when initializing the project

Here are the interactive sections when running `pdm init` command:

```bash
$ pdm init
Please enter the Python interpreter to use
0. ~/.pyenv/shims/python3 (3.10)
1. ~/.pyenv/shims/python3.12 (3.12)
2. ~/.pyenv/versions/3.12.0/bin/python3.12 (3.12)
3. /usr/bin/python3.12 (3.12)
4. /usr/bin/python3.11 (3.11)
5. /usr/bin/python3.10 (3.10)
6. /usr/bin/python3 (3.10)
Please select (0): 1
Would you like to create a virtualenv with /usr/bin/python3.12? [y/n] (y): y
Virtualenv is created successfully at ~/Workspace/python-virtual-environments/pdm/.venv
Project name (pdm): pdm-example
...
```

#### 2. Specify `python` position argument in `pdm venv create` command

```bash
$ pdm venv create --name testenv python3.11
Virtualenv ~/.local/share/pdm/venvs/pdm-HaUr6rC4-testenv is created successfully
```
