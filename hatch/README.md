# hatch

Hatch is a modern, extensible Python project manager.


## How to install it?

Install using `pip`
```bash
$ pip install hatch
```

Or, install using `pipx`
```bash
$ pipx install hatch
```

Or, install using `conda`
```bash
$ conda install -c conda-forge hatch
```

For MacOS users, Hatch could be installed by using Homebrew,
```bash
$ brew install hatch
```

For more information about Hatch installtion, please see the [official documentation](https://hatch.pypa.io/latest/install/)


## How to use it?

If you like to use Hatch to manage your Python project, then firstly you need to create a new project or initialize an existing project using Hatch.

Create a new project,

```bash
$ hatch new <project-name>
```

For example,
```
hatch-example
├── LICENSE.txt
├── pyproject.toml
├── README.md
├── src
│   └── hatch_example
│       ├── __about__.
│       └── __init__.p
└── tests
    └── __init__.py

3 directories, 6 files
```

Initialize an existing project,

```bash
$ hatch new --init
```

wchich would create a `pyproject.toml` file in the existing project.

When we start the new `hatch-example` project, hatch creates a `default` virtual environment, any
dependencies added to the `dependencies` section of `pyproject.toml` will be installed into the `default` environment.

The main feature of Hatch is that it could create multiple environments for the same project. 
A common use case is to have a `test` environment
where testing dependencies are available, and/or a `docs` environment that contains dependencies to generate documentation.

#### 1. Create a virtual environment

Within the Hatch project, you can create virtual environments which are defined in `pyproject.toml` by using the following command,
```bash
$ hatch env create <envname>
```

Actually, you never need to manually create the environment, as spawning a shell (see 2 activate the virtual environment) or running commands within a project will automatically trigger the environment creation.

Where the virtual environments would be created? It's determined by the following heuristic order:
- The `patch` option
- configured `virtual` environment directory

In my case, the directory that contains the virtual environments are:
```bash
~/.local/share/hatch/env/virtual
```

e.g.

```bash
~/.local/share/hatch/env/virtual/hatch-example/
└── qrnKROyH
    └── hatch-example
        ├── bin
        │   ├── activate
        │   ├── activate.csh
        │   ├── activate.fish
        │   ├── activate.nu
        │   ├── activate.ps1
        │   ├── activate_this.py
        │   ├── coverage
        │   ├── coverage3
        │   ├── coverage-3.12
        │   ├── normalizer
        │   ├── pip
        │   ├── pip3
        │   ├── pip-3.12
        │   ├── pip3.12
        │   ├── py.test
        │   ├── pytest
        │   ├── python -> /home/jianli/.pyenv/versions/3.12.0/bin/python
        │   ├── python3 -> python
        │   └── python3.12 -> python
        ├── lib
        │   └── python3.12
        └── pyvenv.cfg

5 directories, 20 files
```

#### 2. Activate the virtual environment

Using the `env show` command to list all available virtual environments:
```bash
$ hatch env show --ascii
```

Spawn a shell to activate and use the environment,
```bash
$ hatch shell
```

#### 3. Manage Python packages

When you run `hatch shell`, Hatch will automatically spawn the environment and install the Python packages listed in `dependencies`.

In active state of the environment, at the time of writing, Hatch does not support dependency lock files, this feature is on roadmap, but until then you will need to
use `pip`, `pip-tools`, or other package management tools alongside Hatch.

And, for now you will need to hand-curate the dependencies in `pyproject.toml`.


#### 4. Deactivate the virtual environment

You can type `exit` to leave the environment,
```bash
$ exit
```

#### 5. Remove the virtual environment

You can remove a single virtual environment by using this command:
```bash
$ hatch env remove <envname>
```

If you try to remove all of a project's environments by using this command:
```bash
$ hatch env prune
```

## Different Python versions?

Virtual environments necessarily require a parent installtion of Python. The Python choice used to create the environment is determined by the version of Python found on your system, or you can set `HATCH_PYTHON` environment variable.

```bash
export HATCH_PYTHON=/usr/bin/python3.11
```

If no version has been chosen, the resolver will try to find a version that matches
the version of Python that Hatch is currently running on.
