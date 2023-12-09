# conda

Conda is an open-source package and environment management software that can run on multiple operation systems.

- As a package manager, Conda can help find and install Python packages and their dependencies.
- As environment manager, Conda can create and manage virtual environments on the computer.

Conda environments allow users to manage project dependencies effectively, and it offers a command-line interface for package and environment operations.

## How to install it?

Before the installation, make sure you are not confused with Conda, Miniconda, and Anaconda.

- Conda is the core tool for managing virtual environments and installing packages.
- Miniconda combines Conda, Python, and some base core packages.
- Anaconda includes Miniconda as well as a large of the most widely used Python packages.

The fastest way to obtain Conda is to install Miniconda. Please refer to the following documentation for installation:

- [Linux](https://conda.io/projects/conda/en/latest/user-guide/install/linux.html) 
- [MacOS](https://conda.io/projects/conda/en/latest/user-guide/install/macos.html)
- [Windows](https://conda.io/projects/conda/en/latest/user-guide/install/windows.html)

Here, I'll only show the Conda installation on the system I am using, that is, Ubuntu 22.04.

**1. Download the Miniconda Installer**

Download from [Miniconda](https://docs.conda.io/projects/miniconda/en/latest/) page, and got this

```bash
$ ls ~/Downloads
Miniconda3-latest-Linux-x86_64.sh
```

**2. Verify the Installer Hashes**

```bash
$ sha256sum ~/Downloads/Miniconda3-latest-Linux-x86_64.sh
d0643508fa49105552c94a523529f4474f91730d3e0d1f168f1700c43ae67595  Miniconda3-latest-Linux-x86_64.sh
```
The hash value is same as what's shown on the installer download page.

**3. Run the Installer Script**

Check `-h` and get the installtion options,
```bash
$ bash Miniconda3-latest-Linux-x86_64.sh -h

usage: Miniconda3-latest-Linux-x86_64.sh [options]

Installs Miniconda3 py311_23.10.0-1

-b           run install in batch mode (without manual intervention),
             it is expected the license terms (if any) are agreed upon
-f           no error if install prefix already exists
-h           print this help message and exit
-p PREFIX    install prefix, defaults to ~/miniconda3, must not contain spaces.
-s           skip running pre/post-link/install scripts
-u           update an existing installation
-t           run package tests after installation (may install conda-build)
```

By default, it would install `~/miniconda3`, you could specify another `-p` prefix to install Miniconda int other location based on your preference. For example,

```bash
$ sudo bash Miniconda3-latest-Linux-x86_64.sh -p /opt/miniconda3
```

**4. Conda & Shell Configuration**

After the installation, we will need to initialize the shell. `zsh` is what I am using, so I run:

```bash
$ conda init zsh
```

What's changed in `.zshrc`?

```bash
# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/opt/miniconda3/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/opt/miniconda3/etc/profile.d/conda.sh" ]; then
        . "/opt/miniconda3/etc/profile.d/conda.sh"
    else
        export PATH="/opt/miniconda3/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<
```

By default Conda is configured to activate the `base` environment when I open a fresh terminal session.

To disable that, run this command:

```bash
$ conda config --set auto_activate_base false
```

which would create `~/.condarc` file with content below:
```
auto_activate_base: false
```

**5. Conda Validation**

Now the setup is done, then to verify it,

```bash
$ conda --version
```

For information on using our graphical installers for Windows or macOS, see the instructions for [installing Anaconda](https://docs.continuum.io/free/anaconda/install/).

## How to use it?

#### 1. Create a virtual environment

There are several different ways to create a virtual environment,

Create a new virtual environment,

```bash
$ conda create --name envname python=3.12
```

Or, create virtual environment from `environment.yml` or `requirements.txt` file,
```bash
$ conda env create

$ conda env create -n envname

$ conda env create folder/envname

$ conda env create -f /path/to/environment.yml

$ conda env create -f /path/to/requirements.txt -n envname

$ conda env create -f /path/to/requirements.txt -p /home/user/envname

```

#### 2. Activate the virtual environment

List the virtual environments on your machine,
```bash
$ conda env list
```

The choose your virtual environment to activate by this command,

```bash
$ conda activate envname
```

#### 3. Manage Python packages

Then you can install Python packages in the activated environment,

To install a signle Python package,

```bash
$ conda install <package-name>
```

To install all Python packages from `requirements.txt` file,

```bash
$ conda install --file requirements.txt
```

To update specified environment according to `environment.yml` file,

```bash
$ conda env update --file environment.yml --prune
```

To update other environment, you could specify environment name,

```bash
$ conda env update --name envname --file environment.yml --prune
```


To export all Python packages in the environment, run this command:

```bash
$ conda env export -f environment.yml
```

If you'd like to export them into `requirements.txt` file, run this command:

```bash
$ conda list -e > requirements.txt
```


#### 4. Deactivate the virtual environment

To deactivate the current environment, run this command:
```bash
$ conda deactivate
```

#### 5. Remove the virtual environment

To remove the specified environment, run this command:
```bash
$ conda env remove --name envname
```


## Different Python versions?

It is recommended to create the virtual environment with Python version specified,

```bash
$ conda create --name envname python=3.12
```

```bash
$ conda create --name envname python=3.11
```

```bash
$ conda create --name envname python=3.10
```

Happy Coding!
