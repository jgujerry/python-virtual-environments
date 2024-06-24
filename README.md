# Python Virtual Environments

An ultimate guide on effectively managing Python virtual environments using different tools
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
* [14] [uv](uv/README.md)

## Your Choice?

It's glad that the Python ecosystem offers numerous options for managing virtual environments and dependencies. Yet, for beginners, 
this abundance may lead to the common question: Which one should I choose? 
In this section, I aim to share my experience and opinions to guide beginners to make right choices.

#### 1. Want to start an virtual environment in quick?
None could be more easy than `venv`, as it is a Python (>=3.3) built-in module, nonthing needs to be installed, just running command `python -m venv` to use it.
If you simply want to create a virtual environment for your Python project, and don't want to install third party packages for this purpose, then go for with `venv`.
As a beginner, you could start with `venv` and `pip`, where use `venv` to create virtual environment, and use `pip` to manage environment dependencies.

Please notice that `venv` does not support older versions of Python (<3.3 or 2.x), you will need to a third-party tool to help in this case.

#### 2. `virtualenv` + `pip` would be a popular option to start with.
`virtualenv` instead is an independent library to create isolated Python environments, and a subset of `virtualenv` has been integrated into the standard library under
the `venv` module. If you try to use a third-party library to manage Pyton virtual environments, then I highly recommend learning and trying with it.
Compared to `venv`, here are some advantages of `virtualenv`:
* it is faster
* it is extendable
* it can create environments for any python versions.
* it is upgrade-able via `pip`.
* it has rich programmatic API.

Besides, several other popular tools like `virtualenvwrapper`, `pew`, `tox` and `nox` are depending on `virtualenv` and build abstractions on top of it.


#### 3. Use wrappers to make virtualenv easier

`virtualenv` wrappers provide convenient commands to help create and delete virtual environments, otherwise managing the development workflow and making it easier 
to work on multiple projects without dependency conflicts.

`virtualenvwrapper` and `pew` are popular wrappers built on top of `virtualenv`, and both of the are great choices. The `workon` command is really convenient to help
switch environments when working on multiple Python projects with different dependencies.

For `virtualenvwrapper`:
* `virtualenvwrapper` automated tests run under these shells on OS X and Linux with bash and zsh. 
* Windows users need to usea separately distributed re-implementation with `virtualenvwrapper-win`.
* `virtualenvwrapper` is a set of shell functions defined in Bourne shell compatible syntax.

For `pew`:
* It would luanch a subshell when activating the environment.
* It is completely shell-agnostic and thus works on bash, zsh, fish, powershell, etc.
* It is invoked starting with `pew` in commands.

As a zsh user under both Ubuntu and MacOS, I personally like the command style and syntax of `virtualenvwrapper`, like `mkvirtualenv`, `rmvirtualenv`.
And I have been using it for years, there is no reason for me to switch from `virtualenvwrapper` to `pew` yet. 
But again, both of them are great, the choice depends on your work environment and personal flavor.

#### 4. Look for automated testing under multiple Python versions?

`tox` is a popular tool in the Python ecosystem used for testing and building projects across different environments. 
It is particularly useful for ensuring that your Python project works consistently across various Python versions and environments.
It uses a declarative configuration file, typically named `tox.ini`, where you specify the testing environments, dependencies, and commands. 

`nox` is another testing and automation tool for Python projects. Unlike `tox`, `nox` uses a code-based configuration approach, named `noxfile.py`

`tox` and `nox` serve similar purposes but differ in their configuration styles and approaches.
The choice between them depends on the preferences and requirements of the project and its developers.

#### 5. How do you manage multiple Python versions on your machine?

Typically, you lack significant control over the versions of your system Python, the Python version pre-installed with operating systems such as Linux and MacOS. 
These pre-installed Python versions often lag behind the latest releases. 
Installing and effortlessly switching between multiple Python versions on your machine can be challenging.

`pyenv` is designed to manage multiple versions of Python on your machine. It's not specifically designed for creating virtual environments, 
but it allows you to switch between different versions of Python on same machine easily. `pyenv-virtualenv` is an extension for `pyenv` that 
adds support for managing virtual environments, allowing you to create and switch between virtual environments associated with specific Python versions.

#### 6. Do you want dependency management with the tool?

With `venv` and `virtualenv`, you can create virtual environments, but need `pip` to help manage the dependencies.

`pipenv`, `poetry` `hatch`, `pdm`, these tools not only provides the support of Python environment creation, but also contains functionalities that help
manage Python dependencies.

* `hatch`, `poetry`, and `pdm` utilize the `pyproject.toml` file to manage dependencies, where `pyproject.toml` is is the specified file format of PEP 518 which contains the build system requirements of Python projects.
* `pipenv` use `Pipfile` and `Pipefile.lock` to manage the depdendencies. At the time of writing, there is an issue open for discussing `Pipfile` and `pyproject.toml` - https://github.com/pypa/pipenv/discussions/5673

#### 7. An operating system–agnostic environment & package manager

`conda` works consistently across various operating systems, including Linux, macOS, and Windows. 
This agnostic nature makes it a versatile tool for managing environments and packages in a way 
that is independent of the underlying operating system. 

`conda` is a popular choice for data science and various other fields. For example, 
GDAL (Geospatial Data Abstraction Library), which is crucial for tasks like spatial data processing and analysis. 
Installing and managing these dependencies directly on a machine can be a complex and challenging process, 
particularly when aiming to manage different versions for optimal functionality. 
This is where `conda` shines as an indispensable tool for geospatial data science.

However, `conda` environment is relatively heavy, and the size of the environment would be larger than environments created by using other tools.

#### 8. New Python packaging and tooling packages?

`rye` originated as a personal project by Armin, driven by his desire to establish a one-stop-shop solution for all Python-related requirements.
`rye` is an experimental endeavour to build a new type of packaging experience to Python inspired by `rustup` and `cargo` from Rust.
While I haven't personally incorporated it into my projects, rye has gained popularity on GitHub. If you're open to exploring innovative tools, 
consider giving it a try.

`uv` takes stewardship of `rye`, and will be expanded into a unified successor project, to fulfill the shared vision for Python packaging with `rye`. 
`uv` is an extremely fast Python package resolver and installer, written in Rust. `uv` is designed as a drop-in replacement for `pip` and `pip-tools`, 
and is ready for production use today in projects built around those workflows. I've applied `uv` in my projects, 
and it performs remarkably fast, living up to its advertised speed.


#### Summary
There isn't a one-size-fits-all solution for managing environments and dependencies in Python projects, as each has its own strengths and weaknesses. 
It's essential to try with various tools to discover the one that best suits your needs and aligns with your project's requirements.


## Contact

If you have any question about this opinionated list, do not hesitate to contact me [@jgujerry](https://twitter.com/jgujerry) on X (Twitter) or open an issue on GitHub.


## License

This project is released under [MIT License](LICENSE)
