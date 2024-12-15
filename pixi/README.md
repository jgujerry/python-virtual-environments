# pixi


`pixi`: package management made easy.

`pixi` is a cross-platform, multi-language package manager and workflow tool built on the foundation of the `conda` ecosystem. It's entirely written in Rust, and supports, and can spins up development environments quickly on Linux, Windows, and MacOS for multi-languages, such as Python, R, C/C++, Rust, Ruby, and so on.

`pixi` provides a more modern experience for developers managing Python environments. It provides a clean and simple command-line interface, centralizes the dependency management by using TOML file, and supports locking dependencies for reproducible builds.

Moreover, `pixi` is ready for production!


## How to install it?

#### Linux & MacOS
For Linux and MacOS users, you can install `pixi` by running the following command in your terminal:

```bash
$ curl -fsSL https://pixi.sh/install.sh | bash
```

This command automatically download, extract, and move the `pixi` package to `~/.pixi/bin`. Depending on your OS system and shell environment, it would update your `~/.bash`, `~/.zsh`, or `~/.bash_profile` to include `~/.pixi/bin` in your `PATH`, making `pixi` command invokable from anywhere.

You may need to restart or source your shell, for example,
```bash
$ source ~/.zsh`
```

To enable autocompletion for your shell,

For Bash users, you can add the following to your `~/.bashrc`:

```bash
eval "$(pixi completion --shell bash)"
```

For Zsh users, you can add the following to your `~/.zshrc`:

```bash
eval "$(pixi completion --shell zsh)"
```

#### Windows

For Windows `PowerShell` users,

```bash
$ iwr -useb https://pixi.sh/install.ps1 | iex
```

For Windowns `winget` users,

```bash
$ winget install prefix-dev.pixi
```

The installation location of `pixi` on Windows is `LocalAppData/pixi/bin`.

To enable autocompletion for your shell environment,

for `PowerShell`,

```bash
$ (& pixi completion --shell powershell) | Out-String | Invoke-Expression
```

for `Fish`, you can add the following into `~/.config/fish/config.fish`:

```bash
pixi completion --shell fish | source
```

Beside for the instructions above, `pixi` could be installed and configured in various other methods as well. For example, you can use `Homebrew` for MacOS user, use `msi` Windows installer for Windows user, and can install from the source. For more detailed information about installation and autocompletion, see the official documentation - [https://pixi.sh/latest/#installation](https://pixi.sh/latest/#installation).


After the installation, you can check by executing the following command:

```bash
$ pixi --version
```


## How to use it?

#### 1. Create a virtual environment

`pixi` supports two manifest formats: `pyproject.toml` and `pixi.toml`. We use `pyproject.toml` here, as it is the most common format for Python projects.

Creating a new project,

```bash
$ pixi init <project-name> --format pyproject
```

What's inside?

```bash
$ tree pixi-demo-project
pixi-demo-project
├── pyproject.toml
└── src
    └── pixi_demo_project
        └── __init__.py

2 directories, 2 files
```

Enter the project directory, then you can create the `default` environment by running the following command:

```bash
$ pixi install
```

A `.pixi` directory would be created under your project, which contains a `envs` diretory with the `default` environment.

```bash
$ tree .pixi -L 3
.pixi
└── envs
    └── default
        ├── bin
        ├── conda-meta
        ├── include
        ├── lib
        ├── man
        ├── share
        ├── shared
        ├── ssl
        ├── x86_64-conda_cos6-linux-gnu
        └── x86_64-conda-linux-gnu

12 directories, 0 files

```

If you like to create another environment, e.g. test environment, for your project. You can run the following command:

```bash
$ pixi project environment add --feature test test
✔ Added environment test
```

Your `pyproject.toml` would be updated automatically with the following content:

```toml
[tool.pixi.environments]
test = ["test"]
```


#### 2. Activate the virtual environment

There are multiple options to activate the virtual environment,

**Use `pixi shell`**

Open a shell with the environment activated,

```bash
$ pixi shell
```

To activate the test environment,

```bash
$ pixi shell -e test
```

**Use `pixi shell-hook**

This command would print the command to activate  the environment in your current shell.
```bash
$ eval "$(pixi shell-hook)"
```

**Use `pixi run`**

This helps run a command in the environment. For example,

```bash
$ pixi run python
```


#### 3. Manage Python packages

Add a single package to the project,

```bash
$ pixi add <package-name>
```

For example,
```bash
$ pixi add requests
```

If you need `pytest` for test environments, then you can run

```bash
$ pixi add --feature test pytest
```

To remove a dependency from the project,

```bash
$ pixi remove <package-name>
```

If you need to install all Python packages in `pyproject.toml` into the default environment, then

```bash
$ pixi install
```

If to install into the test environment, then

```bash
$ pixi install -e test
```

#### 4. Deactivate the virtual environment

To exit the activated shell environment,

```bash
$ exit
```

#### 5. Remove the virtual environment

There is not a direct `delete` or `remove` command to manage the environment, you can do this:

```bash
$ rm -rf .pixi/envs/<environment-name>
```


## Different Python versions?


By default, when you run:

```bash
$ pixi install
```

The latest Python version fron `conda-forge` would be applied. As the time of writting, the latest Python version is `python 3.13`,

```bash
$ pixi run python

Python 3.13.1 | packaged by conda-forge | (main, Dec  5 2024, 21:23:54) [GCC 13.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

To install different Python versions, you can do this, for example:


For Python 3.12,

```bash
$ python add python==3.12
```

Then you can validate by running:

```bash
$ pixi run python
Python 3.12.0 | packaged by conda-forge | (main, Oct  3 2023, 08:43:22) [GCC 12.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

If you need multiple versions of Python in your project for testing, then you can manage multiple version through `pixi` features.


To avoid conflicts, you need to allow multiple versions by adding:

```bash
$ pixi add python
```

Then, can run the following:
```bash
$ pixi add --feature py311 python==3.11
```

```bash
$ pixi project add environment --feature py311 py311
```

```bash
$ pixi shell -e py311
```

After the shell is activated,

```bash
$ python
Python 3.11.0 | packaged by conda-forge | (main, Jan 14 2023, 12:27:40) [GCC 11.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

For more information about `pixi`, please refer to the official documentation [https://pixi.sh/latest/](https://pixi.sh/latest/).

Happy coding!
