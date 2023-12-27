# pew

Pew represents for *Python Env Wrapper*, it is a set of commands to manage multiple Python virtual environments.
Pew can create, delete and copy your environments, using a single command to switch to them wherever you are, 
while keeping them in a single (configurable) location.

Pew builds abstractions on top of virtualenv package.

## How to install it?

Install Pew by using `pip`,
```bash
$ pip install --user pew
```

Check Pew installation by running the following command:
```bash
$ pew version
```

Instead, you can use Nix to install Pew on Nixos as well as other Linux distributions or Macos. For your knowledge,
nix is a purely functional package manager on *nix systems, such as Linux, MacOS. If you don't have that 
on your system, please run this command to install,

Install `nix` on Linux and MacOS with multi-user mode,
```bash
$ bash <(curl -L https://nixos.org/nix/install) --daemon
```

Then validate the nix installation by running the following command:
```bash
$ nix --version
```

Next, you can use nix to install Pew.
```bash
$ nix-env -iA nixpkgs.pew
```

## How to use it?

Pew is completely shell-agnostic and thus works on bash, zsh, fish, powershell, etc.

#### 1. Create a virtual environment

To create a virtual environment, use `new` command like below:
```bash
$ pew new <envname>
```

The virtual environments would be created under the direction of virtualenv `WORKON_HOME`. For my case, I am on Ubuntu,
the diretory is `~/.virtualenvs`.

There are more options with the `new` command,
```bash
$ pew new --help
usage: pew [-h] [-p PYTHON] [-i PACKAGES] [-r REQUIREMENTS] [-d] [-a PROJECT] envname
```

For example, if you like to install Python packages when initializing the virtual environment,

```bash
$ pew new -i <package1> -i <package2> <envname>
```

Or, if you have a list of Python packages in `requirements.txt`, then do this:

```bash
$ pew new -r requirements.txt <envname>
```


#### 2. Activate the virtual environment

List or change working virtual environments.

```bash
$ pew workon <envname>
```

If no `envname` is given, then the list of available virtual environments would be printed to stdout.

#### 3. Manage Python packages

Once inside the virtual environment, you can use `pip` to install additional Python packages like this:

```bash
$ pip install <package-name>
```

To uninstall the Python package,

```bash
$ pip uninstall <package-name>
```


#### 4. Deactivate the virtual environment

To deactivate current virtual environment by running this command:
```bash
$ exit
```

#### 4. Remove the virtual environment

To remove one or more environments from the `WORKON_HOME` directory,
```bash
$ pew rm <envname1> <envname2> ...
```


## Different Python versions?

By using different Python versions,
```bash
$ pew new --python <python-version> <envname>
```

For example,

```bash
$ pew new --python python3.10 testenv10
```

```bash
$ pew new --python python3.11 testenv11
```

```bash
$ pew new --python python3.12 testenv12
```

Besides, Since 0.1.16, Pew integrates Pythonz, which allows you to easily install a new python version (only on linux and macosx).
For more details, please refer to [Pythonz: a Python installation manager](https://github.com/saghul/pythonz).

Happy coding!
