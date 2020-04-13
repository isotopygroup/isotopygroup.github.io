# Node and JavaScript

## Update Environment

### Update ``nvm`` the Node Version Manager

Documentation is at [nvm-sh](https://github.com/nvm-sh/nvm#manual-upgrade).

```bash
nvm --version
cd $NVM_DIR
git fetch --tags origin
git checkout <version>
```

Replace ``<version>`` with the most recent version tag, e.g. ``git checkout v0.35.3``.

### Download Latest Node

Check current status of node (and npm which is linked to node).

```bash
cd ~
node --version
nvm ls
npm --version
npm ls
npm ls -g --depth=0
```

```bash
nvm ls-remote | tail -n20
nvm install lts/* --reinstall-packages-from=default
nvm alias default stable
```

### Update Global ``npm`` Packages

Lookup information about each pack at [npm](https://www.npmjs.com/).
For each pack use the following command replacing ``<package-name>`` with the name of the package.

```bash
npm install -g <package-name>@latest
```

For example,

```bash
npm install -g npm@latest
npm install -g typescript@latest
npm install -g @angular/cli@latest
```