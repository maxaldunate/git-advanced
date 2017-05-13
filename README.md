# git-advanced
Advanced Git Tips and Trciks
by Enrico Campidoglio
Pluralsight

## Add-ons
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
$ wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh --quiet --show-progress -O ~/install.sh

## Git Alias
```bash
$ git config alias.st status
$ git config --list
$ cat .git/config | grep -A 1 "\[alias\]"
```

## Git Configs
--> Config per: Repo()current, User(--global) or System(--system)
https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration
--system  /etc/gitconfig
--global  ~/.gitconfig (or ~/.config/git/config)
--no_one .git/config or current repo

$ git config --system --unset

* Short status
$ git config --global alias.st "status --short --branch"
* Quick merge
$ git checkout -b new_branch_name
$ git config --global alias.qm "!git checkout $1; git merge @{-1}"
$ git config --global alias.qm

to push a branch
$ git push origin +testinggit

alias.st=status --short --branch
* Commit All
alias.cma=commit --all -m
alias.qm=git st checkout ; git merge @{-1}

$ git qm master

### Git Log
$ git log
$ git log --pretty=oneline
$ git log --pretty=%h | %d %s (%cr) [%an]





END