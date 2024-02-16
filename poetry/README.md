# poetry

`poetry` is a tool for environment management and packaging in Python. 
It allows you to declare the packages your project depends on and it will install/update them for you. 
`poetry` offers a lockfile to ensure repeatable installs, and can build your project for distribution.


## How to install it?

`poetry` requires Python 3.8+.

#### Official installer
For Linux, macOS, and Windows, run this command:

```bash
$ curl -sSL https://install.python-poetry.org | python3 -
```

By default, Poetry is installed into a platform and user-specific directory:

* MacOS: `~/Library/Application Support/pypoetry`
* Linux/Unix: `~/.local/share/pypoetry`
* Windows: `%APPDATA%\pypoetry`

Then add `poetry` to your PATH if the following directory is not present in your `$PATH`.

* Linux/Unix: `$HOME/.local/bin`
* Windows: `%APPDATA%\Python\Scripts`

#### Check installation
You can test that everything is set up by executing:

```bash
$ poetry --version
```

If you are a `pipx` user, then you can also install it by using `pipx`. For more information about `poetry` installation, please refer to the [official documentation](https://python-poetry.org/docs/#installation).

#### Enable tab completion for Bash, Zsh, or Fish

Bash

```bash
$ poetry completions bash >> ~/.bash_completion
```

Zsh
```bash
$ poetry completions zsh > ~/.zfunc/_poetry

# Then add the following lines into ~/.zshrc
fpath+=~/.zfunc
autoload -Uz compinit && compinit
```

Oh My Zsh
```bash
mkdir $ZSH_CUSTOM/plugins/poetry
poetry completions zsh > $ZSH_CUSTOM/plugins/poetry/_poetry

# Then add peotry to the plugins array in ~/.zshrc
plugins(
	poetry
	...
	)
```

Fish
```bash
$ poetry completions fish > ~/.config/fish/completions/poetry.fish
```

## How to use it?

#### 1. Create a virtual environment
Create a new poetry project with `pyproject.toml`, the creation of Python virtual environment by using `poetry` depends on it.

```bash
$ poetry new myapp

Created package myapp in myapp
```

Instead, if you want to use `poetry` with existing project, then run

```bash
$ poetry init
```

which would guide you to create only `pyproject.toml` file in existing project.

What are inside?

```bash
myapp
├── myapp
│   └── __init__.py
├── pyproject.toml
├── README.md
└── tests
    └── __init__.py
```

Then run the `env use` command (I am on Ubuntu) to create the virtual environment,
```bash
$ poetry env use python3

Creating virtualenv myapp-Op_t6Wui-py3.12 in ~/.cache/pypoetry/virtualenvs
Using virtualenv: ~/.cache/pypoetry/virtualenvs/myapp-Op_t6Wui-py3.12
```

`poetry` has its own distinct way of handling virtual environments. Instead of placing virtual environments inside the project directory, `poetry` puts them in a centralized cache directory that varies according to the operating system.

* Linux/Unix: `~/.cache/pypoetry/virtualenvs`
* MaxOS: `~/Library/Caches/pypoetry/virtualenvs`
* Windows: `C:\Users\<username>\AppData\Local\pypoetry\Cache\virtualenvs`, or `%LOCALAPPDATA%\pypoetry\Cache\virtualenvs`

If you'd like to have the virtual environment `.venv` created inside your project, then run the following command:

```bash
$ poetry config virtualenvs.in-project true
```


#### 2. Activate the virtual environment

To activate the current virtual environment used by `poetry` project, run this command:

```bash
$ poetry shell
```

#### 3. Manage Python packages

Add a single dependency to the project,

```bash
$ poetry add <package-name>
```

The package would be installed in the virtual environment, and added into `pyproject.toml` file.

You can use `--group` option to group the dependencies, for example,

```bash
$ poetry add --group dev pytest
```

Once dependencies are resolved and installed, `poetry` creates a `poetry.lock` file in the project root directory. This file is a manifest of all of the downloaded dependencies, and should be saved along with the rest of your project. Then anyone who pulls a copy of the project from source control will get the same versions of all required Python packages.

Add all existing dependencies to project's virtual environment,

```bash
$ poetry install
```

The `install` command reads the `poetry.lock` file from the current directory, processes it, and downloads and installs all the libraries and dependencies outlined in that file. If the file does not exist it will look for `pyproject.toml` and do the same.


To remove a dependency from the project,

```bash
$ poetry remove <python-package>
```

If you want to export the dependencies into `requirements.txt`, then run the following command:

```bash
$ poetry export --without-hashes --format=requirements.txt > requirements.txt
```


#### 4. Deactivate the virtual environment

```bash
$ exit
```

#### 5. Remove the virtual environment

```bash
$ poetry env remove python3
```

## Different Python versions?

If you have multiple Python versions installed on your system, then you can specify the Python version when creating the virtual environment by using `poetry`.

```bash
$ poetry env use python3.10
```

```bash
$ poetry env use python3.11
```

```bash
$ poetry env use python3.12
```

For more information about poetry, please see the [official documentation](https://python-poetry.org/docs/).

Happy coding!
