# Advanced Git Tips and Tricks
Git-advanced   
by Enrico Campidoglio  
at Pluralsight

## Introduction

*Add-ons*

for win
### posh-git
for unix
### git-completion.bash
```bash
$ wget https://github.com/git/git/blob/master/contrib/completion/git-completion.bash --quiet --show-progress -O ~/git-completion.bash
$ echo -e "\nsource ~/git-completion.bash" >> ~/bash_profile
```

### Better for zsh (z shell)
first isntall zsh
https://gist.github.com/derhuerst/12a1558a4b408b3b2b6e

### oh-my-zsh
```bash
$ wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh --quiet --show-progress -O ~/install.sh
```

## The Command Line

### Git Alias
```bash
$ git config alias.st status
$ git config --list
$ cat .git/config | grep -A 1 "\[alias\]"
```

### Git Configs

--> Config per: 
https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration

* Repo()current `--no_one` .git/config or current repo
* User(--global) ~/.gitconfig (or ~/.config/git/config)
* System (--system) /etc/gitconfig

`$ git config --system --unset`

**Short status**
`$ git config --global alias.st "status --short --branch"`

**Quick merge**
```bash
$ git checkout -b new_branch_name
$ git config --global alias.qm "!git checkout $1; git merge @{-1}"
$ git config --global alias.qm
```

* To push a branch
`$ git push origin +testinggit`

* Status
`alias.st=status --short --branch`

* Commit All
```bash
alias.cma=commit --all -m
alias.qm=git st checkout ; git merge @{-1}
$ git qm master
```

### Git Log
```bash
$ git log
$ git log --pretty=oneline
$ git log --pretty='%h | %d %s (%cr) [%an]'
$ git log --pretty='%Cred%h%Creset | $C(yellow)%d%Creset %s %Cgreen(%cr)%Creset %C(cyan)[%an]%Creset'
$ git log --pretty='%Cred%h%Creset | $C(yellow)%d%Creset %s %Cgreen(%cr)%Creset %C(cyan)[%an]%Creset' --graph

$ git config --global alias.lg "log --pretty='%Cred%h%Creset | $C(yellow)%d%Creset %s %Cgreen(%cr)%Creset %C(cyan)[%an]%Creset' --graph"

```

### Diffs
Diferencias en los ficheros

```bash
$ git config --global core.pager 'less -RFX'
$ git diff --word-diff
$ git diff --word-diff --unified=10         //Maybe for text
$ git diff --patience         //Maybe for source code
$ git diff --histogram         //Maybe for source code
$ git config --global diff.algorithm histogram 
```

### Diffs in Commits

```bash
$ git show HEAD
$ git show HEAD~2
```

* so = show-object 

`$ git config --global alias.so "show HEAD --pretty='parent %Credp%Creset commit %Cred%h%Creset%C(yellow)%d%Creset%n%n%w(72,2,2)%s%n%n%w(72,0,0)%C(cyan)%an%Creset %Cgreen%ar%Creset'"`

```bash
$ git so
$ git so HEAD~2
```

* Just commit metadata

`$ git so HEAD --no-patch`

* Just summary changes

`$ git so HEAD --stat`

**The Snapshot contains**
* Tree
* Blob

Git records **entire files** in the working directory for each commit

### Plumbing

```bash
$ git cat-file -p HEAD  //same info than show command but with no patch

tree 14028e3ed8166e2e0c131ac08096c1f766d3530a
parent 8b242f4d1584131f37bfa8a6dbc00c143be006e0
author Max Aldunate <maxaldunate@gmail.com> 1494672184 +0200
committer Max Aldunate <maxaldunate@gmail.com> 1494672184 +0200

make an alias

$ git cat-file -p 14028e //The tree object

100644 blob d825de51610aed981e6dd0dc1f6bd489b6fb956e	README.md

$ git cat-file -p d825d //The blob object containing the entire file (not a diff)

...`the content of the file`...

```

*IMPORTANT*

There is a **tree object** for every **sub directory** and
a **blob object** for every **file**.

### Delta changes

* Diferenies between commits to save disk space
```bash
$ git diff HEAD~4..HEAD
$ git diff HEAD~4..HEAD --stat
$ git diff HEAD..HEAD~4 --stat  //Reverse comparision
```

* Comparing 2 files from differents commits
```bash
$ git diff HEAD~3:README.md..HEAD:README.md
```

## Crafting Commits













Max Aldunate