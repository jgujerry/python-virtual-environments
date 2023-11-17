# virtualenv

[virtualenv](https://virtualenv.pypa.io/en/latest/) is a tool to create isolated Python environments. 

Since Python 3.3, a subset of virtualenv has been integrated into the standard library under the [venv](https://docs.python.org/3/library/venv.html) module. However, virtualenv contains more features that enables virtualenv management to be more faster, extendable, and flexible. 

## How to install?

Here is using `pip` to install the `virtualenv` package,

```bash
$ pip install --user virtualenv
```

There are several more methods to install virtualenv, like using pipx, wheel, sdist, etc., please refer to the [official documentation]((https://virtualenv.pypa.io/en/latest/installation.html)) for more information.There are also details about the compatibility of `virtualenv` with differnet Python interpreters and OS environments.


## How to use it?

Use the `--help` command,

```bash
$ virtualenv --help
```

you can find out these rich [flag options](https://virtualenv.pypa.io/en/latest/cli_interface.html#cli-flags) of `virtualenv`.


#### 1. Create a virtual environment

Run this command to create a virtual environment,

```bash
$ virtualenv testenv
```

What's inside after the creation?

```bash
testenv
├── bin
│   ├── activate
│   ├── activate.csh
│   ├── activate.fish
│   ├── activate.nu
│   ├── activate.ps1
│   ├── activate_this.py
│   ├── deactivate.nu
│   ├── pip
│   ├── pip3
│   ├── pip-3.12
│   ├── pip3.12
│   ├── python -> /usr/bin/python3.12
│   ├── python3 -> python
│   ├── python3.12 -> python
│   ├── wheel
│   ├── wheel3
│   ├── wheel-3.12
│   └── wheel3.12
├── lib
│   └── python3.12
└── pyvenv.cfg

3 directories, 19 files
```

#### 2. Activate the virtual environment

Source to activate the virtual environment,

```bash
$ source testenv/bin/activate
```

You may need to run different activation file based on your system.

#### 3. Manage Python packages

To install or uninstall a single package, run

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

Run the following command to deactivate the virtual environment,

```bash
$ deactivate
```

#### 5. Remove the virtual environment

Removing the virtual environment is simple, just to remove the virtual environment directory.

```bash
$ rm -r testenv
```

## Different Python versions?

If you have multiple Python versions installed, then you can use `--python/-p` option to specify the Python version when creating the virtual environment. For example,

```bash
$ virtualenv -p python3.10 testenv10
```

```bash
$ virtualenv -p python3.11 testenv11
```

```bash
$ virtualenv -p python3.12 testenv12
```

Happy coding!
