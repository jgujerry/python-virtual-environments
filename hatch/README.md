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

Actually, you never need to manually create the environment, as spawning a shell or running commands within a project will automatically
trigger the environment creation.

Where the virtual environments would be created? Well, it depends on the operation systems you are using. For my case, I am using Ubuntu,
the directory that contains the virtual environments are:
```bash
~/.local/share/hatch/env/virtual
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

At the time of writing, Hatch does not support dependency lock files, this feature is on roadmap, but until then you will need to
use `pip`, `pip-tools`, or other package management tools alongside Hatch.

Here, we use `pip` to manage Python packages,

```bash
$ pip install <package-name>
```


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

