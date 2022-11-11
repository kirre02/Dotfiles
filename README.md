# Dotfiles

This project is meant to provide a fully automated dev environment that is easy to setup and maintain. 

## Goals

The goal was to provide a fully automated `manjaro with i3` dev environment that is easy to use and maintain.

### Why Ansible

I happend to stumble upon ansible when looking for a solution to automate my dev environment that was easy to understand and so I chose Ansible.

### why Manjaro with i3

Manjaro provides an simple wizard for installing Manjaro with i3.

## requirements

### Operating system

This Ansible playbook only supports `Manjaro with i3`. Reason for this is to provide a consistent experience across hosts

- Download [Manjaro with i3](https://manjaro.org/downloads/community/i3/)
- Install OS

### System upgrade 

Verify your `Manjaro with i3` installation has all the packages that are needed before you are running the playbook

```
sudo pacman -Syu
```

## setup

### values.yaml

create the `values.yaml` at `~/.config/dotfiles/values.yaml` file to allow you to personalize your setup for your needs.

```bash
cd $HOME && mkdir -p .config/dotfiles && vim .config/dotfiles/values.yaml
```

Below is a list of all available values. Not all are required but incorrect values will break the playbook if not properly set.

| Name                  | Type                                | Required |
| --------------------- | ----------------------------------- | -------- |
| git_user_email        | string                              | yes      |
| git_user_name         | string                              | yes      |
|neovim_version         | string `(branch, tag or SHA)`       | yes      |


## Usage

### Install

This playbook includes a custom shell script located at `bin/dotfiles`. This script is added to your $PATH after installation and can be run multiple times while making sure any Ansible dependencies are installed and updated.

This shell script is also used to initialize your environment after installing `Manjaro with i3`, performing a full system upgrade and creating your `~/.config/dotfiles/values.yaml` configuration file as mentioned above.

> NOTE: You must follow required steps before running this command or things may become unusable until fixed.

```bash
$ bash -c "$(curl -fsSL https://raw.githubusercontent.com/kirre02/Dotfiles/main/bin/dotfiles)"
```

### Update

To update your environment run the `dotfiles` command in your shell:

```bash
$ dotfiles
```
