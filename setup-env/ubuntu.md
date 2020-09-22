# Setting Up Ubuntu

## Change Permissions for Shared Partition

If the shared partition is mounted at `/work` then the owner is probably set to 'root' and the user only has read access.
One solution is to change the owner:

```bash
sudo chown USER_NAME /work
```

## Install Software

Using `Ubuntu Software` app consider installing any of the following programs:

- Firefox Web Browser
- Chromium
- Spotify
- LibreOffice (Writer, Calc, Impress, Base, Draw)
- Transmission

- Visual Studio Code
- IDEA Community
- PyCharm CE

- Synaptic Package Manager
- Disk Usage Analyzer
- GParted

- GNU Image Manipulation Program
- Inkscape
- TeXstudio

Using command line follow the pattern:

```bash
sudo apt update
sudo apt install curl
```
