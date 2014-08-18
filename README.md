# ansible-packer

An Ansible module for installing [AUR](https://aur.archlinux.org/) packages via the [packer][packer] AUR helper.

This assumes your target node already has packer and its dependecies installed.

## Dependencies (Managed Node)

* [Arch Linux](https://www.archlinux.org/) (Obviously)
* [jshon](https://www.archlinux.org/packages/community/x86_64/jshon/) for packer
* [packer][packer]

## Installation

1. Clone this repo
2. Copy or link the `packer` file into your global Ansible library (usually `/usr/share/ansible`) or into the `./library` folder alongside your top-level playbook

## Usage

Pretty much identical to the [pacman module][pacman-mod]. Note that package status, removal, the corresponding `pacman` commands are used (`-Q`, `-R`, respectively).

More detailed docs are on the way, but in general:

### Options

* `name` - required, name of the AUR package to install
* `recurse` - optional, yes/no, whether to recursively remove packages. See [pacman module docs][pacman-mod]
* `state` - optional, present/absent, whether the package needs to be installed or not

### Examples

```yaml
# Install package foo
- packer: name=foo state=present

# Remove packages foo and bar
- packer: name=foo,bar state=absent

# Recursively remove package baz
- packer: name=baz state=absent recurse=yes
```

## Todo

* Add inline, ansible-doc compatible documentation
* ???

Have other ideas? Better way of doing something? Open an issue or a pull request.

[packer]: https://github.com/keenerd/packer
[pacman-mod]: http://docs.ansible.com/pacman_module.html