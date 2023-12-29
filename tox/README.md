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


`tox` is an environment orchestrator, it needs `tox.ini` configuration file to define what tools required to
setup and execute on your project's test environment. 

#### 1. The default environment

Create `tox.ini` with the following configuration:
```ini
[tox]
skipsdist = true
```

Then run `tox` command:
```bash
$ tox
  py: OK (0.15 seconds)
  congratulations :) (0.20 seconds)
```

What's happened? Under the work directory, a `.tox` directory was created with the following contents:

```bash
.tox
└── py
    ├── bin
    │   ├── activate
    │   ├── activate.csh
    │   ├── activate.fish
    │   ├── activate.nu
    │   ├── activate.ps1
    │   ├── activate_this.py
    │   ├── pip
    │   ├── pip3
    │   ├── pip-3.10
    │   ├── pip3.10
    │   ├── python -> /usr/bin/python3
    │   ├── python3 -> python
    │   ├── python3.10 -> python
    │   ├── wheel
    │   ├── wheel3
    │   ├── wheel-3.10
    │   └── wheel3.10
    ├── lib
    │   └── python3.10
    ├── pyvenv.cfg
    └── tmp

5 directories, 18 files
```

You can see **py** is the default environment created by tox, and py version is what default in your machine.

#### 2. Customize the environment list

You can control the environment creation by specifying the `env_list` or `envlist` option

```ini
[tox]
skipsdist = true
env_list = py310,py311,py312
```

Then run command `$tox` again, you can see these Python environments created under `.tox` directory,

```bash
.tox
├── py310
│   ├── bin
│   ├── lib
│   ├── pyvenv.cfg
│   └── tmp
├── py311
│   ├── bin
│   ├── lib
│   ├── pyvenv.cfg
│   └── tmp
└── py312
    ├── bin
    ├── lib
    ├── pyvenv.cfg
    └── tmp

12 directories, 3 files
```

What's about if you specify a Python version that does not exist on your system? For example, if I specify `py39` in `env_list` and Python 3.9 
is not installed on my machine, then `tox` would skip it and show the following information:

```bash
py39: skipped because could not find python interpreter with spec(s): py39
py39: SKIP ⚠ in 0.02 seconds
```

#### 3. More on `tox` configuration

There are two types of configurations: core settings `[tox]`, and per-run environment settings `[testenv]` and `[testenv:<envname>]`.

Except for the `tox.ini` configuration, `tox` supports `pyproject.toml` and `setup.cfg` as well. `tox` supports three configuration locations
prioritized in the following order:

1. `tox.ini`
2. `pyproject.toml`
3. `setup.cfg`


For more information about `tox`, please refer to the [official documentation](https://tox.wiki/).

Happy Coding!
