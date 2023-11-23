# pipenv

`pipenv` is a Python virtualenv management tool that supports cross-platform and nicely bridges the gaps between Python (using system Python, `pyenv` or asdf), `pip` and `virtualenv`.

A key feature to highlight is that `pipenv` uses `Pipfile` and `Pipfile.lock` to manage package dependencies.

## How to install it?

Before installing `pipenv`, please make sure you have Python and `pip` available on your system.

The recommended way to install `pipenv` on most platforms is using `pip`.

```bash
$ pip install --user pipenv
```

For MacOS users, homebrew would be another choice of installing `pipenv`.

```bash
$ brew install pipenv
```

More detailed installation instructions can be found [here](https://pipenv.pypa.io/en/latest/installation.html).

## How to use it?

Use `--help` option to check the `pipenv` command usage,

```bash
$ pipenv --help
```

#### 1. Create a virtual environment

`pipenv` abstracts away many of the complexities of virtual environment management, under the hood, it relies on `virtualenv` 
to handle the actual creation and management of isolated environments.

The directory path is significant to `pipenv`, as it uses the current working directory to determine the context for the virtual environment and the project's dependencies.

Before we create the virtual environment, it needs to enter the project directory. For example, suppose we have a project under `~/projects/myapp`,

```bash
$ cd ~/projects/myapp
```

After entering the project directory, then run the following command to create the virtual environment,

```bash
$ pipenv --python 3.12
```

On my side, the outputs include:
* The virtual environment is created under `.virtualenvs` directory which is my `virtualenv`'s default installation location.
* The virtual environment name is `myapp-SH-hhpBV`, which is the directory name of my project `myapp` plus the hash of full path to the project's root.
* `Pipfile` is created under the project directory.

Please notice that the outputs of your system maybe different, but the idea here is same.

You can control the behavior of virtual environment creation by configuring related environment variables.For more configuration details, please see the documentation - [Configuration With Environment Variables](https://docs.pipenv.org/advanced/#configuration-with-environment-variables)

Another method of virtual environment creation is to run the `shell` command, like this:

```bash
$ python shell
```

This will create a virtual environment if one does not exist before entering the shell environment. And, the Python version is the default version on your system.


#### 2. Activate the virtual environment
Run the `shell` command to activate the virtual environment,

```bash
$ pipenv shell
```

It would spawn a shell in existing virtual environment to isolate the development of the application.


#### 3. Manage Python packages

To install packages for your project, use the following command:

```bash
$ pipenv install <python-package>
```

This will install specified package and automatically add it to your `Pipfile` and `Pipfile.lock`.

For example, you need `requests` for your project, and need `pytest` for testing in development.

```bash
$ pipenv install requests

$ pipenv install --dev pytest
```

What's inside the `Pipfile`?

```bash
[[source]]
url = "https://pypi.org/simple"
verify_ssl = true
name = "pypi"

[packages]
requests = "*"

[dev-packages]
pytest = "*"

[requires]
python_version = "3.12"
python_full_version = "3.12.0"
```

After the installation, `pipenv` would automatically lock the dependencies and update `Pipfile.lock` for your project.

To remove the package, and update the `Pipfile` and `Pipfile.lock`, use:

```bash
$ pipenv uninstall <python-package>
```

#### 4. Deactivate the virtual environment

To deactivate the virtualenv environment you are using, run command

```bash
$ exit
```

It'll exit the shell spawned by `pipenv`.

#### 5. Remove the virtual environment

To remove the virtual environment, run this command under your `~/projects/myapp` directory,

```bash
$ pipenv --rm
```

Please note that, after removing the virtual environment, the `Pipfile` and `Pipfile.lock` files would not 
be removed from your project directory, and you need manually delete these files if need.

## Different Python versions?

One best practice with virtual environment creation is always specify the Python version.

The option `--python` could be used with `pipenv` to specify the Python version, for examples,

```bash
$ pipenv --python 3.10
```

```bash
$ pipenv --python 3.11
```

```bash
$ pipenv --python 3.12
```

For more information about `pipenv`, please refer to the [official documentation](https://pipenv.pypa.io/en/latest/).

Happy coding!
