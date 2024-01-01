# nox

Nox is a command-line tool that automates testing in multiple Python environments, s
imilar to [tox](https://tox.wiki/). Unlike tox, Nox uses a standard Python file for configuration.


## How to install it?

Install nox via pip:

```bash
$ pip install --user nox
```

## How to use it?

Nox is configured via a `noxfile.py` file in your project’s directory. For example,

```python
import nox

@nox.session
def tests(session):
    session.install('pytest')
    session.run('pytest')

@nox.session
def lint(session):
    session.install('flake8')
    session.run('flake8', '--import-order-style', 'google')
```

#### 1. Create the virtual environment

By default, `nox` uses `virtualenv` as default backend to create the virtual environment.
You are not limited to `virtualenv` though, there is a selection of backends you can choose from as `venv`, `conda`, `mamba`:
```python
@nox.session(venv_backend="venv")
def tests(session):
    pass
```

By default, when calling `nox` command (see 2. Activate the environment),
nox will create a new virtual environment for each session using the same interpreter that Nox uses.


#### 2. Activate the virtual environment

Same as tox, you do not need to activate the virtual environment manually. 
to run both of these sessions mentioned above, use the following command:

```bash
$ nox
```

By default, under the project directory, nox will create a cache directory `.nox` which contains the
virtual environments defined with nox sessions.

#### 3. Manage Python packages

You can specify the Python packages that are required for running the tests in the virtual environment, like this:

```python
session.install("package1", "package2", ...)
```

If you have a list of packages in `requirements.txt`, you can use

```python
session.install("-r", "requirements.txt")
```

If your project is a Python package and you want to to install it:

```python
session.install("-e", ".")
```

#### 4. Deactivate the virtual environment

No need to deactivate the virtual environment manually, nox will take care of it automatically.


#### 5. Remove the virtual environment

To remove the cached virtual environments, you can run the following command:

```bash
$ rm -rf .nox
```

## Different Python versions?

You can tell Nox to use a different Python interpreter/version by specifying the `python` argument (or its alias `py`) to `@nox.session`:

```python
@nox.session(python="3.12")
def tests(session):
    pass
```

You can also tell Nox to run your session against multiple Python interpreters.
Nox will create a separate virtualenv and run the session for each interpreter you specify.

```python
@nox.session(python=["3.11", "3.12", "pypy-6.0"])
def tests(session):
    pass
```

For more information about nox, please look into the [official documentation](https://nox.thea.codes/en/stable/index.html)

Happy Coding!
