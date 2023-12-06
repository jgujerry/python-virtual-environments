# pyenv + virtualenv

[`pyenv`](https://github.com/pyenv/pyenv) let you manage multiple versions of Python easily. It's simple, unobtrusive, and follows
the UNIX tradition of single-purpose tools do one thing well.

[`pyenv-virtualenv`](https://github.com/pyenv/pyenv-virtualenv) is a [`pyenv`](https://github.com/pyenv/pyenv) plugin that 
provides features to manage Python virtual environments for Python on UNIX-like systems.



## How to install?

#### 1. Install build dependencies

As `pyenv` installs Python by building from source, which means it needs OS-specific dependencies. Before installing `pyenv`, you will need to install its build dependencies first.

For Ubuntu/Debian,

```bash
$ sudo apt-get install -y build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev \
liblzma-dev python3-openssl make
```

For Fedora/CentOS/RHEL,
```bash
$ sudo yum install gcc zlib-devel bzip2 bzip2-devel readline-devel \
sqlite sqlite-devel openssl-devel xz xz-devel libffi-devel
```

For openSUSE,
```bash
$ zypper in zlib-devel bzip2 libbz2-devel libffi-devel \
libopenssl-devel readline-devel sqlite3 sqlite3-devel xz xz-devel
```

For MacOS,

```bash
$ brew install openssl readline sqlite3 xz zlib
```

#### 2. Install `pyenv` package

For Linux/Unix, use `pyenv-installer` to install `pyenv`,

```bash
$ curl https://pyenv.run | bash
```

It would install `pyenv` application, as well as several other plugins, including `pyenv-virtualenv`.


For MacOS, you can run this command,
```bash
$ brew install pyenv pyenv-virtualenv
```


After the installation, then need to config `.bashrc`, `bash_profile`, or `.zshrc` file,
depending on what OS system and shell script you are using.

```bash
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"

eval "$(pyenv virtualenv-init -)"
```

Next to source the config file, or restart your shell environment to make the configuration taking effect.

To validate the installtion,

```bash
$ pyenv --version
```

```bash
$ pyenv virtualenv --version
```

More information about the installation? Please refer to the [documentation](https://github.com/pyenv/pyenv#installation)


## Different Python versions

Let's run the following command to create a virtual environment,

```bash
$ pyenv virtualenv 3.9.9 testenv
pyenv-virtualenv: `3.9.9' is not installed in pyenv.
Run `pyenv install 3.9.9' to install it
```

Apparently, it does not run successfully, because I don't have Python 3.9.0 available on my machine as base to create such a virtual environment.

What should we do? As shown above, we need to use `pyenv` to install according Python version first, then to create the virtualenv.


#### 1. Install specific Python versions

Use the following command to check available Python versions for installation:

```bash
$ pyenv install --list
```

Then install a specific version like this:
```bash
$ pyenv install 3.9.9
```

```bash
$ pyenv install 3.12.0
```

As `pyenv` builds Python from the source, it may take a couple of minutes to install.

Where the Python version is installed?

```bash
$ ls ~/.pyenv/versions/
3.12.0  3.9.9
```

#### 2. Uninstall specific Python versions

To uninstall a specific Python version, run this command:
```bash
$ pyenv uninstall 3.9.9
```

Therefore, `pyenv` could help you manage multiple Python versions on the machine easily. Based on the available Python versions, you can create desired Python virtual environment easily as well.

## How to use?

#### 1. Create a virtual environment

Use the following command to create a virtualenv,
```bash
$ pyenv virtualenv 3.12.0 testenv
```

Where this `testenv` virtual environment installed?

```bash
$ ls ~/.pyenv/versions 
3.12.0  testenv
```

What's inside of `testenv` directory?

```bash
testenv
├── bin
│   ├── activate
│   ├── activate.csh
│   ├── activate.fish
│   ├── Activate.ps1
│   ├── pip
│   ├── pip3
│   ├── pip3.12
│   ├── pydoc
│   ├── python -> python3.12
│   ├── python3 -> python3.12
│   ├── python3.12 -> ~/.pyenv/versions/3.12.0/bin/python3.12
│   ├── python3.12-config -> ~/.pyenv/versions/3.12.0/bin/python3.12-config
│   ├── python3-config -> ~/.pyenv/versions/3.12.0/bin/python3-config
│   └── python-config -> ~/.pyenv/versions/3.12.0/bin/python-config
├── include
│   └── python3.12
├── lib
│   └── python3.12
├── lib64 -> lib
└── pyvenv.cfg

6 directories, 15 files
```

#### 2. Activate the virtual environment

Use this command to list your available virtualenvs,
```bash
$ pyenv virtualenvs
```

To activate the virtual environment, use this command:

```bash
$ pyenv activate testenv
```

Or you can use the following command,

```bash
$ pyenv local testenv
```

#### 3. Manage Python packages


To install or uninstall a single package within virtual environment, run

```bash
$ pip install <package-name>
```

To install a list of Python packages in `requirements.txt`, run

```bash
$ pip install -r requirements.txt
```

To uninstall the Python package,

```bash
$ pip uninstall <package-name>
```


#### 4. Deactivate the virtual environment

To deactivate the virtual environment,

```bash
$ pyenv deactivate
```

If you use `pyenv local` activate your virtual environment, then

```bash
$ pyenv local --unset
```

#### 5. Delete the virtual environment

To remove the virtual environment,
```bash
$ pyenv virtualenv-delete testenv
```

More information about these packages
* `pyenv` - https://github.com/pyenv/pyenv
* `pyenv-virtualenv` - https://github.com/pyenv/pyenv-virtualenv

Happy Coding!
