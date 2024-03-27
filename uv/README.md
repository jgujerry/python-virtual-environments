# uv

`uv` is an extremely fast Python package installer and resolver, written in Rust, and designed as a drop-in replacement for `pip` and `pip-tools` workflows.


## How to install?

There are multiple ways to install `uv` on your system, including

```bash
# On macOS and Linux.
curl -LsSf https://astral.sh/uv/install.sh | sh

# On Windows.
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"

# With pip.
pip install uv

# With pipx.
pipx install uv

# With Homebrew.
brew install uv

# With Pacman.
pacman -S uv
```


## How to use it?

#### 1. How to create the virtual environment?

Run the following command to create a virtual environment

```bash

$ uv venv
```

It will create a virtual environment named `.venv` under the current working directory.


```bash
$ tree .venv -L 2
.venv
├── bin
│   ├── activate
│   ├── activate.bat
│   ├── activate.csh
│   ├── activate.fish
│   ├── activate.nu
│   ├── activate.ps1
│   ├── activate_this.py
│   ├── deactivate.bat
│   ├── pydoc.bat
│   ├── python -> /usr/bin/python3.10
│   ├── python3 -> python
│   └── python3.10 -> python
├── CACHEDIR.TAG
├── lib
│   └── python3.10
└── pyvenv.cfg

3 directories, 14 files
```

#### 2. Activate the virtual environment

To activate the virtual environment, run the following command on Linux,

```bash
$ source .venv/bin/activate
```

If you are on Windows, run the following command,

```bash
$ .venv\Scripts\activate
```

#### 3. Manage python packages

To install python packages,

```bash
$ uv pip install <package-name>
```

The syntax of `uv pip` would be same as `pip`, for examples,

```bash
uv pip install flask                # Install Flask.
uv pip install -r requirements.txt  # Install from a requirements.txt file.
uv pip install -e .                 # Install the current project in editable mode.
uv pip install "package @ ."        # Install the current project from disk.
uv pip install "flask[dotenv]"      # Install Flask with "dotenv" extra.
```

To lock the current dependencies into `requirements.txt`,

```bash
$ uv pip freeze | uv pip compile - -o requirements.txt
```

#### 4. Deactivate the virtual environment

Simply run:

```bash
$ deactivate
```


#### 5. Remove the virtual environment

Deactivate the virtual environment and remove the `.venv` directory,

```bash
$ rm -r .venv
```


## Different Python versions?

When I created the virtual environment by running `uv venv`, it created an environment of Python 3.10.

As I have multiple Python versions installed on my machine, what's about if I want to create a virtual
environment with different Python versions?

The answer is to use `--python` option,

```bash
$ uv venv --python python3.12
```

```bash
$ uv venv --python python3.11
```

For more information about `uv`, please see the github repository - https://github.com/astral-sh/uv.

Happy coding!
