# tox

`tox` is a generic virtual environment management and test command line tool, 
it aims to automate and standardize testing in Python. 
`tox` is part of a larger vision of easing the packaging,
testing and release process of Python software 
(alongside [`pytest`](https://docs.pytest.org/en/latest/) and [`devpi`](https://www.devpi.net/)).

`tox` has influenced several other projects in the Python test automation space, such as 
[`Invoke`](https://www.pyinvoke.org/), [`nox`](https://nox.thea.codes/en/stable/).

## How to install it?

#### 1. via pipx

It's recommended to use `pipx` to install `tox` into an isolated environment, run this command:
```bash
$ pipx install tox
```

#### 2. via pip

Alternatively, you can install it within the global Python interpreter itself, run this command:
```bash
$ pip install --user tox
```

There are also other methods for `tox` installation, such as `wheel`, `sdist`. However, installation 
via `setup.py` is not recommended.

After the installation, validate it by running:
```bash
$ tox --help
```

## How to use it?

?

For more information about `tox`, please refer to the [official documentation](https://tox.wiki/).

Happy Coding!
