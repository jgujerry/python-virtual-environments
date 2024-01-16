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

## Your Choice?

It's glad that the Python ecosystem offers numerous options for managing virtual environments and dependencies. Yet, for beginners, 
this abundance may lead to the common question: Which one should I choose? 
In this section, I aim to share my experience and opinions to guide beginners to make right choices.

#### 1. `venv` is easy and ready to use
None could be more easy than `venv`, as it is a Python (>=3.3) built-in module, nonthing needs to be installed, just running command `python -m venv` to use it.
If you simply want to create a virtual environment for your Python project, and don't want to install third party packages for this purpose, then go for with `venv`.
As a beginner, you could start with `venv` and `pip`, where use `venv` to create virtual environment, and use `pip` to manage environment dependencies.

#### 2. `virtualenv` is a very popular tool
`virtualenv` instead is an independent library to create isolated Python environments, and a subset of `virtualenv` has been integrated into the standard library under
the `venv` module. It's lightweight, fast, and very easy to use as well. If you try to use a third-party library to manage Pyton virtual environments, then I highly recommend learning and trying with it. 

Besides, several other popular tools like `virtualenvwrapper`, `pew`, `tox` and `nox` are depending on `virtualenv` and build abstractions on top of it.


[In progress...]

## Contact

If you have any question about this opinionated list, do not hesitate to contact me [@jgujerry](https://twitter.com/jgujerry) on X (Twitter) or open an issue on GitHub.


## License

This project is released under [MIT License](LICENSE)
