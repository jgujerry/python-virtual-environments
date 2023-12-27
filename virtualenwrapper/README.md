# virtualenvwrapper

`virtualenvwrapper` is a set of shell scripts that enhance the functionality of `virtualenv`, a tool for creating isolated Python environments. The extensions include wrappers for creating and deleting virtual environments and otherwise managing your development workflow, making it easier to work on more than one project at a time without introducing conflicts in their dependencies.


## How to install?

Install `virtualenv` and `virtualenvwrapper` using `pip`

```bash
$ pip install --user virtualenv virtualenvwrapper
```

Setup your shell by adding the following lines into your shell profile (e.g. `.bashrc`, or `.zshrc`)

```bash
$ export WORKON_HOME=$HOME/.virtualenvs
$ export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
$ export VIRTUALENVWRAPPER_VIRTUALENV=~/.local/bin/virtualenv
$ export VIRTUALENVWRAPPER_SCRIPT=~/.local/bin/virtualenvwrapper.sh
$ source ~/.local/bin/virtualenvwrapper.sh
```

Please check your installation path and configure `Python` version, `virtualenv`, `virtualenvwrapper.sh` properly.


## How to use it?


#### 1. Create a virtual environment

Please check the `--help` document,
```bash
$ mkvirtualenv --help
```

Here we only provide the basic usage command, supposing we are creating a virtual environment named `testenv`.

```bash
$ mkdirvirtualenv testenv
```

To duplicate an existing virtual environment,
```bash
$ cpvirtualenv <env-name> testenv
```

What's inside the virtual environment?

```bash
$ cdvirtualenv

$ lssitepackages

$ cdsitepackages
```

You can easily tell what the command is trying to do from the command name.

#### 2. Activate the virtual environment

If run `workon` command without any arguments, it will list all virtual environments.

```bash
$ workon
```

Another command to list the virtual environments is

```bash
$ lsvirtualenv
```

To activate the virtual environment, run the following command
```bash
$ workon testenv
```


#### 3. Manage Python packages

To install or uninstall a single package, run

```bash
$ pip install <package-name>
```

To install a list of Python packages in `requirements.txt`, run

```bash
$ pip install -r requirements.txt
```

To uninstall the Python package,

```bash
$ pip uninstall <package-name>
```

If you try to remove all of the installed third-party packages in current virtual environment, run this command

```bash
$ wipeenv
```


#### 4. Deactivate the virtual environment

Run the following command to deactivate the virtual environment,

```bash
$ deactivate
```


#### 5. Remove the virtual environment

Run the following command to remove the virtual environment,

```bash
$ rmvirtualenv testenv
```

## Different Python versions

If there are multiple Python versions installed on your system, then you could specify a version with `-p/--python` when creating the virtual environment.

```bash
$ mkvirtualenv -p python3.10 testenv10
```

```bash
$ mkvirtualenv -p python3.11 testenv11
```

```bash
$ mkvirtualenv -p python3.12 testenv12
```

For more details about virtialenvwrapper, please refer to the [official documentation](https://virtualenvwrapper.readthedocs.io/en/latest/).

Happy coding!
