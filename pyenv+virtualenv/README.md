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
$ sudo apt-get install -y make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev \
libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python3-openssl
```

For Fedora/CentOS/RHEL,
```bash
$ sudo yum install gcc zlib-devel bzip2 bzip2-devel readline-devel \
sqlite sqlite-devel openssl-devel xz xz-devel libffi-devel
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

## How to use?

#### 1. Create a virtual environment



#### 2. Activate the virtual environment

#### 3. Manage Python packages

#### 4. Deactivate the virtual environment

#### 5. Delete the virtual environment

## Different Python versions?

