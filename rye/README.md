# rye

Rye is built by [Armin Ronacher](https://github.com/mitsuhiko/rye), 
it is a personal one-stop-shop for all Python needs, but still an **experimental** package management solution.


## How to install it?

#### 1. Installing Rye
For Linux/MacOS users,

```bash
$ curl -sSf https://rye-up.com/get | bash
```

Where `rye` got installed?

```bash
This installer will install rye to ~/.rye
This path can be changed by exporting the `RYE_HOME` environment variable.
```

For Windows users, you can install the `.exe` file,
* [rye-x86_64-windows.exe](https://github.com/mitsuhiko/rye/releases/latest/download/rye-x86_64-windows.exe) for 64bit Intel Windows
* [rye-x86-windows.exe](https://github.com/mitsuhiko/rye/releases/latest/download/rye-x86-windows.exe) for 32bit Intel Windows

#### 2. Add Shims to Path

Bash
```bash
echo 'source "$HOME/.rye/env"' >> ~/.bashrc
```

Zsh
```bash
echo 'source "$HOME/.rye/env"' >> ~/.zshrc
```

Fish
```bash
set -Ua fish_user_paths "$HOME/.rye/shims"
```

Unix Shells
```bash
echo '. "$HOME/.rye/env"' >> ~/.profile
```

Windows
* Press `Win+R`, enter sysdm.cpl and hit *Enter*.
* In the "System Properties" dialog, click the "Advanced" tab.
* Click on "Environment Variables".
* In the top list, double click on the Path variable.
* In the "Edit environment variable" dialog click on "New".
* Enter `%USERPROFILE%\.rye\shims` and hit *Enter*.
* Click repeatedly on "Move Up" until the newly added item is at the top.
* Click on "OK" and close the dialog.

#### 3. Validate Rye Installation

Run the following command to validate the installation:

```bash
$ rye --version
```

For more information about `rye` installation, please see the [documentation](https://rye-up.com/guide/installation/)

## How to use it?

To use Rye you need to have a `pyproject.toml` based Python project. If not, then you need to run:

```bash
$ rye init
```

It'll initialize the project with the following:
```bash
$ .
├── pyproject.toml
├── .python-version
└── src
    └── rye
        └── __init__.py

2 directories, 3 files
```

#### 1. Create the virtual environment

When initializing the project, rye would use its shimed Python version,

```bash
$ which python
~/.rye/shims/python
```

On my system, the Python version is:
```bash
$ python --version
Python 3.12.0
```

Therefore, in `.python-version`,
```txt
cpython-x86_64-linux@3.12.0
```

Next, run this command to create the virtual environment:
```bash
$ rye sync
```

The virtual environment that Rye manages is placed in `.venv` next to the `pyproject.toml`.

```bash
.venv
├── bin
│   ├── activate
│   ├── activate.csh
│   ├── activate.fish
│   ├── activate.nu
│   ├── activate.ps1
│   ├── activate_this.py
│   ├── hello
│   ├── python -> ~/.rye/py/cpython@3.12.0/install/bin/python3
│   ├── python3 -> python
│   └── python3.12 -> python
├── lib
│   └── python3.12
├── pyvenv.cfg
└── rye-venv.json

3 directories, 12 files
```

#### 2. Activate the virtual environment


You can spawn a shell with the Python environment activation
```bash
$ rye shell
```

However, there is one notable exception: the Python installation in it does not contain `pip`.

#### 3. Manage Pyton packages

Use the add command to add dependencies to your project.

```bash
$ rye add <package1> <package2> ...
```

If you like to add dependencies for development only, then

```bash
$ rye add --dev <package1> <package2> ...
```

To remove the dependencies,

```bash
$ rye remove <package1> <package2> ...
```

Rye currently uses [`pip-tools`](https://github.com/jazzband/pip-tools) to download and install dependencies, 
and it creates two "lockfiles" (called `requirements.lock` and `requirements-dev.lock`).

Whenever `rye sync` is called, it will update lockfiles as well as the virtual environment. 
If you only want to update the lockfiles, then `rye lock` can be used.

#### 4. Deactivate the virtual environment

Run `exit` to deactivate the current virtual environment,

```bash
$ exit
```

#### 5. Remove the virtual environment

Remove the virtual environment,

```bash
$ rm -rf .venv
```

## Different Python versions?

To use a different Python version, you can use the following command to setup,

For example
```bash
$ rye pin 3.11
```

which would update the `.python-version` file,
```bash
3.11.6
```

Then, run sync to apply the change,
```bash
$ rye sync
```

It will create the new virtual environment based on Python version `3.11.6`.

For more usage information of rye, please see the [official documentation](https://rye-up.com/).

Happy Coding!
