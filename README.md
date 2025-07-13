# nmapCommands
nmap is a great tool for scanning hosts, domains, networks, and everything in-between. It is useful for conducting reconnaissance on target systems, network monitoring, troubleshooting, and vulnerability testing. When I was first getting into Linux and nmap, I was more inclined to use Zenmap on Windows because I didn’t fully understand the CLI and all of its switches/structure - so the GUI seemed like a more intuitive version of the software. As a beginner, that is fine. I will attempt to explain the structure and possible inputs of nmap commands to make it less daunting from a beginner standpoint - and I will also include some uncommon and complex commands with explanations attached to each. My end goal is to create a directory of commands that anyone can download and use directly into a terminal - with a description attached to each one.


# All Platforms Download / Installation

This page has all of the different installation directions and packages: https://nmap.org/download.html

*Note*-The focus is on Linux platforms because this is where most people are really using nmap. It is generally better suited for security and can easily be installed on a Virtual Machine using a hypervisor like VirtualBox.

# Windows Installation

1. Go to https://nmap.org/book/inst-windows.html and follow the directions.

# Linux Installlation

If you’re on one of the following Linux Distros, you’re in luck because you already have Linux pre-installed:

## Linux Distributions that typically include nmap:

**Security-focused distros:**

- **Kali Linux**
- **Parrot Security OS**
- **BackBox**
- **Pentoo**
- **BlackArch**

**Some server-oriented distros:**

- **CentOS/RHEL (in some configurations)**
- **Some Ubuntu Server variants**

If you’re on a different distro, here’s how to install nmap:

1. Open a terminal.
2. Verify the installation first: `nmap --version` or `nmap -V` .
3. If you do not have nmap installed, on Debian-based Linux distributions like Ubuntu, you can use `sudo apt-get install nmap`
4. If you do have an old version installed, to update the package lists: `sudo apt-get update`

## Easy installation on most distros:

**Debian/Ubuntu-based:**`sudo apt update && sudo apt install nmap`

**Red Hat/CentOS/Fedora:**`sudo dnf install nmap
*# or older systems:*
sudo yum install nmap`

**Arch Linux:**`sudo pacman -S nmap`

**Alpine Linux:**`sudo apk add nmap`

**OpenSUSE:**`sudo zypper install nmap`


# Options Menu

In your terminal, type:

```bash
nmap
```
Or:

```bash
nmap -h
```

This will display some of the most commonly used nmap commands and a description of the function and general overview of how they function

*Note* - The commands with a “-” before them are called “switches”. Ex. -sL or -A

*Note* - In regards to the options menu “It helps people remember the most common options, but is no substitute for the in-depth documentation in the rest of this manual. Some obscure options aren't even included here.” (https://nmap.org/book/man-briefoptions.html)
