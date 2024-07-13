# mamba

Mamba is a reimplementation and drop-in replacement for Conda package manager in `C++`.

1. Parallel downloading of repository data and packages using multi-threading.
2. Utilizes libsolv for faster dependency solving, a library also used by RPM package managers like Red Hat, Fedora, and OpenSUSE.
3. Core components are implemented in C++ for maximum efficiency.

Mamba maintains compatibility with Conda by using the same command line parser, package installation and removal code, and transaction verification routines.


## How to install it?

Similar to Conda, there are two versions of Mamba,
* `mamba`
* `msicromamba`

`micromamba` is a tiny version of the mamba package manager. It is a statically linked `C++` executable with a separate command line interface. Please refer to the official documentation for installation - https://mamba.readthedocs.io/en/latest/installation/mamba-installation.html

To start with lightweight package manager, I installed `micromamba` on my Ubuntu 22.04.

Run the following command to install `micromamba`,

```bash
"${SHELL}" <(curl -L micro.mamba.pm/install.sh)
```

The installation is an interactive process and asking you to provide preferred options. And, it updated my `.zshrc` (I am using `.zshrc`) with the following configuration.

```bash
# >>> mamba initialize >>>
# !! Contents within this block are managed by 'mamba init' !!
export MAMBA_EXE='~/.local/bin/micromamba';
export MAMBA_ROOT_PREFIX='~/.micromamba';
__mamba_setup="$("$MAMBA_EXE" shell hook --shell zsh --root-prefix "$MAMBA_ROOT_PREFIX" 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__mamba_setup"
else
    alias micromamba="$MAMBA_EXE"  # Fallback on help from mamba activate
fi
unset __mamba_setup
# <<< mamba initialize <<<

```

Verify the installation,

```bash
$ micromamba --version
```

Create an alias to short the command,

```bash
$ alias mamba=micromamba
```


## How to use it?


### 1. Create a virtual environment
It's nearly same as the usage of `conda`.

```bash
$ mamba create --name envname python=3.12
```

Or, create virtual environment from `environment.yml` or `requirements.txt` file,
```bash
$ mamba env create -n envname

$ mamba env create -f /path/to/environment.yml

$ mamba env create -f /path/to/requirements.txt -n envname

$ mamba env create -f /path/to/requirements.txt -p /home/user/envname

```

### 2. Activate the virtual environment

List the virtual environments on your machine,

```bash
$ mamba env list
```

Then choose your virtual environment to activate by this command,

```bash
$ mamba activate envname
```

### 3. Manage Python packages


Then you can install Python packages in the activated environment,

To install a signle Python package,

```bash
$ mamba install <package-name>
```

To install all Python packages from `requirements.txt` file,

```bash
$ mamba install --file requirements.txt
```

To update specified environment according to `environment.yml` file,

```bash
$ mamba env update --file environment.yml --prune
```

To update other environment, you could specify environment name,

```bash
$ mamba env update --name envname --file environment.yml --prune
```


To export all Python packages in the environment, run this command:

```bash
$ mamba env export -f environment.yml
```

However, Mamba does not have a `--export` option with `mamba list` as Conda for `requirements.txt` export.


#### 4. Deactivate the virtual environment

To deactivate the current environment, run this command:
```bash
$ mamba deactivate
```

#### 5. Remove the virtual environment

To remove the specified environment, run this command:
```bash
$ mamba env remove --name envname
```



## Different Python versions?


It is recommended to create the virtual environment with Python version specified,

```bash
$ mamba create --name envname python=3.12
```

```bash
$ mamba create --name envname python=3.11
```

```bash
$ mamba create --name envname python=3.10
```

Happy Coding!
