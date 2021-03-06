# General trunc of my config

## Why a general trunc ?
Some people at school are using my config and don't agree with all the
modifications I want to do so I've got 2 options :
- I don't do what I want to not bother them
- I do it because I really want it, sorry guys

The thing is, when I find something fun which can help with school's Mac, they
might need to update and take the (not wanted) modifications anyway.

## Solution
I split my config in 2
- global stuff for everyone
- personal stuff
This repo is the global one

## What did it provide ?
- Some usefull alias
- Basic configuration for zsh
- Install script that help at school with zfs change

## How to use
### Clone it
First, you need to clone it in "$HOME/.config_common"
```bash
cd
git clone https://github.com/Jaahd/config_common.git .config_common
```
### Run it
Then run it
```bash
.config_common/install.sh <options>
```
### Options
- -u : Update the symbolic link
- -f|--force : Doesn't ask question, do it
- -p|--personal <url_to_personal_git_repo> : you need to pass the url to your
  personal config repo and it will clone it
- -b : update brew, tap repo if any and install applications if any
- -h|--help : display help

### Personal config
Well, it's just a repo with your files inside.
#### Specific files
- brew_apps : contain application you would like to install with brew, one
  application per line
- brew_tap : contain list of depot to tap with brew, one depot per line
- install.sh : If you provied a install.sh in your personal repo, the global
  install.sh will run it
- ln : the global install.sh will make symbolic link, cf "ln file" below
- prompt : it should only contain the prompt you would like to use, if not
  provied, the general one will be use
- zshrc : the global zshrc will source it at the end of it's own execution

#### ln file
In this file, you can write the symlink you want to create. Those symlink will
be updated by the global install.sh if you've got a zfs change. The syntax is
as follow :
```text
<file_to_symlink>:<name_of_symlink>
```
If those name begin with '/', they will be used as given, if not, those names
will be prefixed. In the second case, the command that will be run is the
following :
```bash
cd
ln -s .config_personal/<file_to_symlink> <name_of_symlink>
```
Note that every time you start the install script with the -u flag, the symblink
will be updated

#### Usage example
##### Installation with personal configuration
```bash
cd
git clone https://github.com/Jaahd/config_common.git .config_common
cd .config_common
./install.sh -u -b -f -p https://github.com/Jaahd/config_personal.git
```
##### Update symbolic link
```bash
cd ~/.config_common
./install.sh -u -f
```
## Changelog
- 12/12/2015 :
  - correct few bug in install.sh
  - correct typo (personnal instead of personal)
