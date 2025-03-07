[mobilege](/README.md) 
/ [Git](/git.md)
    <sub>&nbsp;&nbsp;Documentation</sub>
    <sub>&nbsp;&nbsp;[tldr](https://tldr.inbrowser.app/pages/common/git)</sub>

# Git
- https://docs.gitlab.com/ee/topics/git/
- https://www.atlassian.com/git/tutorials
- https://github.com/git-guides
- `/usr/bin/git` is the path to the system-provided Git executable.
  - Apple actually maintain and ship their own fork of Git. [_source_](https://www.atlassian.com/git/tutorials/install-git)
- `/usr/local/bin/git` symbolic link to the Git executable when installed via Homebrew
  - points to `/usr/local/Cellar/git/2.34.1/bin/git`   

###### Git Branching

```shell
$ git branch testing   # Create a new local branch
$ git checkout testing # Switch to an existing local branch

$ git checkout -b iss53 # Create a new local branch & switch to it (in one step)
```
<sup>https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging</sup>


###### Pushing

```shell
$ git push <remote> <local branch>:<remote branch>
$ git push origin serverfix  # if the local & remote branches have the same name
$ git push  # pushes current branch, if tracking set up
$ git push --all   # pushes all branches
```
<sup>https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches</sup>

###### Tracking Branches
```shell
$ git checkout -b <branch> <remote>/<branch>
$ git checkout --track origin/serverfix
$ git checkout serverfix
# Branch serverfix set up to track remote branch serverfix from origin.
# Switched to a new branch 'serverfix'
```
<sup>https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches > 'Tracking Branches'</sup>

###### [`git remote prune origin`](https://www.atlassian.com/git/tutorials/git-prune) 
- _deletes refs to branches that don't exist on the remote_

## Miscellaneous

#### Multiple GitHub accounts
- [Using Multiple SSH keys - Beginner Friendly.md](https://gist.github.com/aprilmintacpineda/f101bf5fd34f1e6664497cf4b9b9345f)

```shell
$ git remote set-url origin git@<host>:rabin-joshi-cognizant/cognizant-enablement.git
# <host> should match the host alias defined in ~/.ssh/config
```

```shell
$ git config user.name "rabin-joshi-cognizant" # updates local 
$ git config user.email "rabin.joshi@cognizant.com" # updates local 
$ git config -l # shows all: system, global and local
```

###### SSH Config

```shell
$ code ~/.ssh/config # opens the file in VS Code
```

<img width="629" alt="using-the-ssh-config-file" src="https://user-images.githubusercontent.com/6307250/209201683-72c67ac9-83e0-4059-90b1-467e4ca129e2.png">
<sup>https://linuxize.com/post/using-the-ssh-config-file/</sup>

