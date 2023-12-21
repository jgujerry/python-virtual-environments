# pew

Pew represents for *Python Env Wrapper*, it is a set of commands to manage multiple Python virtual environments.
Pew can create, delete and copy your environments, using a single command to switch to them wherever you are, 
while keeping them in a single (configurable) location.

Pew is completely shell-agnostic and thus works on bash, zsh, fish, powershell, etc.

## How to install it?

You can use Nix to install Pew on Nixos as well as other Linux distributions or Macos. For your knowledge,
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

Check Pew installation by running the following command:
```bash
$ pew version
```


## How to use it?



## Different Python versions?

