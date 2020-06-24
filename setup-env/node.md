# Node and JavaScript

## Update Environment

### Update `nvm` the Node Version Manager

Documentation is at [nvm-sh](https://github.com/nvm-sh/nvm#manual-upgrade).

```bash
nvm --version
cd $NVM_DIR
git fetch --tags origin
git checkout <version>
```

Replace `<version>` with the most recent version tag, e.g. `git checkout v0.35.3`.

### Download Latest Node Version

Check current status of node.

```bash
node --version
nvm ls
```

```bash
nvm ls-remote | tail -n20
# most recent stable release
nvm install node --reinstall-packages-from=default
# most recent long term stable release
nvm install lts/* --reinstall-packages-from=default
nvm alias stable NODE_VER
```

Where `NODE_VER` is the stable version which was downloaded.

### Update Global `npm` Packages

Check the current status of npm and global packages.

```
npm --version
npm ls
npm ls -g --depth=0
```

Lookup information about each package at [npm](https://www.npmjs.com/).
For each package use the following command replacing `<package-name>` with the name of the package.

```bash
npm install -g <package-name>@latest
```

For example,

```bash
npm install -g npm@latest
npm install -g typescript@latest
npm install -g @angular/cli@latest
```

## Setup Environment

We first install nvm which allows for switching between and installing multiple versions of node. 

### Install `nvm` the Node Version Manager

Documentation is at [nvm-sh](https://github.com/nvm-sh/nvm#git-install).

- First clone the repository and checkout the latest version tag.

    ```bash
    cd ~
    git clone https://github.com/nvm-sh/nvm.git .nvm
    cd ~/.nvm
    git checkout <version>
    ```

  Replace `<version>` with the most recent version tag, e.g. `git checkout v0.35.3`.

- Next activate by sourcing the shell script `~/.nvm/nvm.sh` to automatically source add the following lines to `~/.bashrc`.

    ```bash
    export NVM_DIR="$HOME/.nvm"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
    [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
    ```

### Download Latest Node

List versions of node available for install.
The first command will list the 20 most recent versions.
The second command will list the long term stable release versions.

```bash
nvm ls-remote | tail -n20
nvm ls-remote --lts
```

The first command will install the most recent version of node.
The second command will install the most recent long term stable version.

```bash
nvm install node
nvm install lts/*
```

### Install Global `npm` Packages

Note that `npm` is installed with node, but may need to be updated with the command:

```
npm install -g npm@latest
```

Lookup information about each package at [npm](https://www.npmjs.com).

```
npm install -g typescript
npm install -g @angular/cli
```
