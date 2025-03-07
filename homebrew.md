[mobilege](/README.md) 
/ [Homebrew](/homebrew.md)
    <sub>&nbsp;&nbsp;Documentation</sub> 
    <sub>&nbsp;&nbsp;[tldr](https://tldr.inbrowser.app/pages/common/brew)</sub>

# Homebrew
- **https://brew.sh**
- [Cheatsheet](https://devhints.io/homebrew)
- https://youtu.be/SELYgZvAZbU


##
```shell
brew update       # updates the local Homebrew installation, does not update installed packages
brew upgrade      # updates installed packages to their newest versions
brew install git  # installs the latest version of Git
```

## Paths


**`Cellar` stores multiple versions, `opt` symlinks to one of the versions in `Cellar`.**


##
_Prompt: List all the directories, files and symbolic links created when homebrew is installed via the install script. Provide a brief description of each. Present the info neatly in a markdown table like code so I can copy._

| Path                                     | Description                                           |
|------------------------------------------|-------------------------------------------------------|
| `/usr/local/bin/brew`                    | Symbolic link to the Homebrew executable              |
| `/usr/local/Homebrew/bin/brew`           | (Actual) Homebrew executable                          |

| Path                                     | Description                                           |
|------------------------------------------|-------------------------------------------------------|
| `/usr/local/Homebrew`                    | Homebrew installation directory.                      |
| `/usr/local/Caskroom`                    | Directory for macOS applications installed via Cask.  |
| `/usr/local/Cellar`                      | Directory where formulae (packages) are installed.    |
| `/usr/local/Frameworks`                  | Directory for Homebrew-managed macOS frameworks.      |


_Prompt: List all the directories, files and symbolic links created when a package eg tldr is installed via homebrew._

| Item                                      | Description                                           |
|-------------------------------------------|-------------------------------------------------------|
| `/usr/local/bin/tldr`                     | Symbolic link to the `tldr` executable.             |
| `/usr/local/Cellar/tldr`                  | The directory for the `tldr` package.               |
| `/usr/local/Cellar/tldr/{version}/bin`    | Executable binaries for `tldr`.                     |