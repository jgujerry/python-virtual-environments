# Python Virtual Environments

A beginner's guide on effectively managing Python virtual environments using different tools
in Python ecosystem.

Popular Python virtual environment management options:
* [1] [venv](venv/README.md)
* [2] [virtualenv](virtualenv/README.md)
* [3] [virtualenvwrapper](virtualenwrapper/README.md)
* [4] [pipenv](pipenv/README.md)
* [5] [poetry](poetry/README.md)
* [6] [pyenv-virtualenv](pyenv-virtualenv/README.md)
* [7] [conda](conda/README.md)
* [8] [hatch](hatch/README.md)
* [9] [pdm](pdm/README.md)
* [10] [pew](pew/README.md)
* [11] [tox](tox/README.md)
* [12] [nox](nox/README.md)
* [13] [rye](rye/README.md)

## Options

#### 1. venv
[`venv`](https://docs.python.org/3/library/venv.html) is a built-in module since Python 3.3 for creating lightweight, isolated Python environments. It provides basic functionality for creating and managing virtual environments.

#### 2. virtualenv
[`virtualenv`](https://virtualenv.pypa.io/en/latest/) is a popular third-party tool for creating isolated Python environments. Compared to `venv`, `virtualenv` offers more features, is extendable & upgrade-able via `pip`, runs faster, and can create virtual environments for any installed Python versions.

#### 3. virtualenvwrapper
[`virtualenvwrapper`](https://virtualenvwrapper.readthedocs.io/en/latest/) is a set of shell scripts that enhance the functionality of `virtualenv`. It simplifies the management of multiple virtual environments by providing commands for creating, deleting, and switching between them.

#### 4. pipenv
[`pipenv`](https://pipenv.pypa.io/en/latest/) is a packaging tool for Python that aims to bring the best of all packaging worlds (bundled, required, and development) to the Python world. It automatically creates and manages a virtual environment for your projects, along with the necessary dependencies.

#### 5. poetry
[`poetry`](https://python-poetry.org/) is a modern dependency management and packaging tool for Python. It not only handles virtual environments but also simplifies the process of declaring and installing project dependencies.

#### 6. pyenv-virtualenv
[`pyenv-virtualenv`](https://github.com/pyenv/pyenv-virtualenv) is a plugin for `pyenv` that provides support for managing virtual environments. It allows you to create and switch between virtual environments easily using `pyenv`.

#### 7. conda
[`conda`](https://docs.conda.io/en/latest/) is a cross-platform package manager and environment manager. It can install and manage packages and dependencies for any language, and it is not Python-specific. It is often used for scientific computing and data science.

#### 8. hatch
[`hatch`](https://github.com/pypa/hatch) is a tool that focuses on project initialization and management. While it can create virtual environments, its primary goal is to streamline the process of creating and distributing Python packages.

#### 9. pdm
[`pdm`](https://github.com/pdm-project/pdm) is a modern Python package manager that emphasizes performance and simplicity. It manages virtual environments, dependencies, and project metadata, aiming to provide a fast and reliable workflow.

#### 10. pew
[`pew`](https://github.com/pew-org/pew) is a lightweight virtual environment manager built on top of `virtualenv` that allows you to create and manage virtual environments easily. It simplifies switching between different environments and provides a clean interface for managing Python installations.

#### 11. tox
[`tox`](https://tox.wiki/) is a testing tool that automates the process of testing code against multiple Python environments. While it's not primarily a virtual environment manager, it often involves creating and managing isolated environments for testing purposes. The configuration file is `tox.ini`.

#### 12. nox
[`nox`](https://nox.thea.codes/en/stable/) is a testing automation tool that focuses on making testing in multiple environments easy. Like `tox`, it's not a dedicated virtual environment manager but often involves creating and managing isolated environments for testing. `nox` uses `noxfile.py` as configuration file.

#### 13. rye
[`rye`](https://github.com/mitsuhiko/rye) is built by [Armin Ronacher](https://github.com/mitsuhiko/rye), it is a personal one-stop-shop for all Python needs, but still an **experimental** package management solution.


## Contact

If you have any question about this opinionated list, do not hesitate to contact me [@jgujerry](https://twitter.com/jgujerry) on X (Twitter) or open an issue on GitHub.


## License

This project is released under [MIT License](LICENSE)
