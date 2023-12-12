# hatch

Hatch is a modern, extensible Python project manager.


## How to install it?

Install using `pip`
```bash
$ pip install hatch
```

Or, install using `pipx`
```bash
$ pipx install hatch
```

Or, install using `conda`
```bash
$ conda install -c conda-forge hatch
```

For MacOS users, Hatch could be installed by using Homebrew,
```bash
$ brew install hatch
```

For more information about Hatch installtion, please see the [official documentation](https://hatch.pypa.io/latest/install/)


## How to use it?

#### 1. Create a virtual environment

You can create virtual environments by using the following command,
```bash
$ hatch env create
```

Actually, you never need to manually create the environment, as spawning a shell or running commands within a project will automatically
trigger the environment creation.

Where the virtual environments would be created? Well, it depends on the operation systems you are using. For my case, I am using Ubuntu,
the directory that contains the virtual environments are:
```bash
~/.local/share/hatch/env/virtual
```

#### 2. Activate the virtual environment

Using the `env show` command to list all available virtual environments:
```bash
$ hatch env show --ascii
```

Spawn a shell to activate and use the environment,
```bash
$ hatch shell
```

#### 3. Manage Python packages

#### 4. Deactivate the virtual environment

You can type `exit` to leave the environment,
```bash
$ exit
```

#### 5. Remove the virtual environment

You can remove a single virtual environment by using this command:
```bash
$ hatch env remove
```

If you try to remove all of a project's environments by using this command:
```bash
$ hatch env prune
```

## Different Python versions?

