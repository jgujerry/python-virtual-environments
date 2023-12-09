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

**1 Download the Miniconda Installer**

Download from [Miniconda](https://docs.conda.io/projects/miniconda/en/latest/) page, and got this

```bash
$ ls ~/Downloads
Miniconda3-latest-Linux-x86_64.sh
```

**2 Verify the Installer Hashes**

```bash
$ sha256sum ~/Downloads/Miniconda3-latest-Linux-x86_64.sh
d0643508fa49105552c94a523529f4474f91730d3e0d1f168f1700c43ae67595  Miniconda3-latest-Linux-x86_64.sh
```
The hash value is same as what's shown on the installer download page.

**3 Run the Installer Script**

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

After the installation, then add the miniconda installation path into `PATH`,

```bash
$  export PATH="$PATH:/opt/miniconda3/bin"
```

Now the installation and setup is done, then to verify it,

```bash
$ conda --version
```

For information on using our graphical installers for Windows or macOS, see the instructions for [installing Anaconda](https://docs.continuum.io/free/anaconda/install/).

## How to use it?

#### 1. Create a virtual environment

#### 2. Activate the virtual environment

#### 3. Manage Python packages

#### 4. Deactivate the virtual environment

#### 5. Remove the virtual environment


## Different Python versions?
