# venv

Since version 3.3, Python has come with a built-in module [venv](https://docs.python.org/3/library/venv.html) for the creation of virtual environments.


## How to install?
`venv` is a built-in module of Python, normally you do not need to install. However, please note that in some Linux distributions, like Ubuntu, the `venv` module is not installed together with the Python installation. It needs to be installed separately.

```bash
$ sudo apt install python3.12-venv
```

## How to use it?

#### 1. Create a venv

```bash
$ python -m venv /path/to/testenv
```

Running this command to creates the target directory, a common name for the target directory is `.venv`.

If run with `-h`, the command will show the available options.

```bash
$ python -m venv -h
usage: venv [-h] [--system-site-packages] [--symlinks | --copies] [--clear] [--upgrade] [--without-pip] [--prompt PROMPT] [--upgrade-deps] ENV_DIR [ENV_DIR ...]

Creates virtual Python environments in one or more target directories.

positional arguments:
  ENV_DIR               A directory to create the environment in.

options:
  -h, --help            show this help message and exit
  --system-site-packages
                        Give the virtual environment access to the system site-packages dir.
  --symlinks            Try to use symlinks rather than copies, when symlinks are not the default for the platform.
  --copies              Try to use copies rather than symlinks, even when symlinks are the default for the platform.
  --clear               Delete the contents of the environment directory if it already exists, before environment creation.
  --upgrade             Upgrade the environment directory to use this version of Python, assuming Python has been upgraded in-place.
  --without-pip         Skips installing or upgrading pip in the virtual environment (pip is bootstrapped by default)
  --prompt PROMPT       Provides an alternative prompt prefix for this environment.
  --upgrade-deps        Upgrade core dependencies: pip setuptools to the latest version in PyPI

Once an environment has been created, you may wish to activate it, e.g. by sourcing an activate script in its bin directory.
```

The following shows what are created in the target directory.

```bash
testenv
├── bin
│   ├── activate
│   ├── activate.csh
│   ├── activate.fish
│   ├── Activate.ps1
│   ├── pip
│   ├── pip3
│   ├── pip3.10
│   ├── python -> python3
│   ├── python3 -> /usr/bin/python3
│   └── python3.10 -> python3
├── include
├── lib
│   └── python3.10
├── lib64 -> lib
└── pyvenv.cfg

5 directories, 11 files
```

The content of `pyvenv.cfg` file,
```
home = /usr/bin
include-system-site-packages = false
version = 3.10.6
```

The `home` key pointing to the Python installation from which the command was run.


#### 2. Activate the venv

Activate the virtualenv environment,

```bash
# Replace <vent> by the target directory containing the virtual environment.
$ source testenv/bin/activate
```

The inovation of the activation script is platform-specific.

On Unix or MacOS,
```bash
# bash/zsh
$ source testenv/bin/activate

# fish
$ source testenv/bin/activate.fish

# csh/tcsh
$ source testenv/bin/activate.csh

# PowerShell
$ testenv/bin/Activate.ps1
```

On Windows,
```
# cmd.exe
C:\> testenv\Scripts\activate.bat

# PowerShell
PS C:\> testenv\Scripts\Activate.ps1
```

#### 3. Manage Python packages

Make sure your `pip` module is up-to-date in this environment,
```bash
$ pip install --upgrade pip
```

Install a single package,
```bash
$ pip install <python-package>
```

If you have a `requirements.txt` file,
```bash
$ pip install -r requirements.txt
```

To install a package,

```bash
$ pip uninstall <python-package>
```


#### 4. Deactivate the venv
When not using the virtual environment, you can terminate the session where you are using it.

```bash
$ deactivate
```

Windows users on the Command Prompt need to run `deactivate.bat` from the `Scripts` subdirectory.


#### 5. Remove the venv

Python virtual environments are self-contained. When it's no longer needed, then you can deactivate it, then just delete the directory of virtual environment.

```bash
$ rm -r testenv/
```


## Different Python versions?

While `venv` is a built-in module and provides basic way to create virtual environments, it is tied to the Python version with which it is invoked.

Suppose you have multiple versions installed on the machine like me, you could manage the virtual environments in different Python versions this way.

```bash
$ python3.10 -m venv ./testenv10
```

```bash
$ python3.11 -m venv ./testenv11
```

```bash
$ python3.12 -m venv ./testenv12
```

Happy coding!
