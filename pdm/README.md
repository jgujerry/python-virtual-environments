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

You will need to answer a few questions to help `pdm` to initialize a project with `pyproject.toml` file. For example,

```
[project]
name = "pdm-example"
version = "0.1.0"
description = "Default template for PDM package"
authors = [
    {name = "jgujerry", email = "j*@gmail.com"},
]
dependencies = [
    "requests>=2.31.0",
]
requires-python = "==3.12.*"
readme = "README.md"
license = {text = "MIT"}


[tool.pdm]
package-type = "application"

```

#### 1. Create a virtual environment

```bash
$ pdm venv create --name <envname>
```

You can create multiple virtual environments for one project.

Where the virtual environments got created? 
* If no `--name` was specified, `pdm` will create the `.venv` under the project directory.
* Otherwise, if the `venv.location` configuration was defined, the virtualenvs would go there.
* If no `venv.location` configuration defined, they would be created under the shared directory of your system.

On my Ubuntu system, they are created under this location:
```bash
$ ~/.local/share/pdm/venvs/
```

#### 2. Activate the virtual environment

Go the project directory, run the following command to list all available virtual environments with the project,
```bash
$ pdm venv list
```

Now you can choose the virtual environment name and activate it using this command:
```bash
$ eval $(pdm venv activate <envname>)
```

Please note that `pdm venv activate` only print the activation command, use `eval` to run it.

#### 3. Manage Python packages

Add Python packages to project,
```bash
$ pdm add <package1> <package2> ...
```

To add all dependencies listed in `pyproject.toml`, run this:
```bash
$ pdm install
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

Run this command to deactivate the virtual environment,

```bash
$ deactivate
```

#### 5. Remove the virtual environment

To remove given virtual environment, using this command:
```bash
$ pdm venv remove <envname>
```

To purge all created virtual environments, run this command:
```bash
$ pdm venv purge
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
where you can select your Python version for project initialization.

#### 2. Specify `python` position argument in `pdm venv create` command

For example,
```bash
$ pdm venv create --name testenv python3.11
Virtualenv ~/.local/share/pdm/venvs/pdm-HaUr6rC4-testenv is created successfully
```

```bash
$ pdm venv create --name testenv2 python3.12
Virtualenv ~/.local/share/pdm/venvs/pdm-HaUr6rC4-testenv2 is created successfully
```

For more information about `pdm`, please see the [official documentation](https://pdm-project.org/latest/).

Happy coding!
