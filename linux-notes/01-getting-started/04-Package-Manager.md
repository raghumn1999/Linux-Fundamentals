# Package Managers in Linux

## 📌 What is a Package Manager?
* Package manager is a tool,that automates the process of installing,updating,configuring 
  and removing softwares in linux system.


## How Does Package manager work?

1) Download package: Package manager fetch software packages from official repositories
  (online storage of packages)

  Ex: Ubuntu fetch sofware packages from archive.ubuntu.com
  If packages are not availabl in archive.ubuntu.com,that software company hosts private 
  repository,we can add that repository in apt.source.list.d folder,apt package manager 
  able to read software package from apt.source.list.d folder, download, configuare and 
  install software

2) Install software: it resolve dependencies, install, configure software
3) update software: two commands update all installed softwares into latest version
   $ apt update --> update package list from repositories
   $ apt upgrade  --> download and install latest version of soffware from updated package list
4) remove software: packages manager also support removal of software from system without 
   leaving unnecessary files

## 📦 Popular Package Managers in Linux
| Linux Distro   | Package Manager | Command Example |
|---------------|----------------|----------------|
| Ubuntu, Debian | `apt` (Advanced Package Tool) | `sudo apt install nginx` |
| Fedora, RHEL, CentOS | `dnf` (or `yum` for older versions) | `sudo dnf install nginx` |
| Arch Linux | `pacman` | `sudo pacman -S nginx` |
| OpenSUSE | `zypper` | `sudo zypper install nginx` |

## 🌍 How Package Managers Fetch Software from Repositories
A **repository** is a server that stores software packages. When a package manager installs software:

1. It **checks the repository list** (e.g., `/etc/apt/sources.list` in Ubuntu).
2. It **downloads the package** and its dependencies.
3. It **installs and configures the software** automatically.

## 🔄 Why Should You Run `apt update` After Installing Ubuntu?
When you install Ubuntu, the packages included in the ISO image might be outdated. Running:
```bash
apt install sudo
sudo apt update
```
✅ Updates the package list from repositories.

Then, to install the latest versions of packages, run:
```bash
sudo apt upgrade -y
```

## 🛠 Essential Package Manager Commands
### **APT (Debian, Ubuntu)**
```bash
sudo apt update         # Update package lists
sudo apt upgrade -y     # Upgrade installed packages
sudo apt install nginx  # Install a package
sudo apt remove nginx   # Remove a package
sudo apt autoremove     # Remove unused dependencies
sudo apt search nginx   # Search for a package
```

### **DNF (Fedora, RHEL, CentOS)**
```bash
sudo dnf check-update   # Check for updates
sudo dnf update         # Update all packages
sudo dnf install nginx  # Install a package
sudo dnf remove nginx   # Remove a package

## 🚀 Best Practices for Using Package Managers
- ✅ **Always update your package list before installing software:**
  ```bash
  sudo apt update && sudo apt upgrade -y
  ```
- ✅ **Use `autoremove` to clean up unused dependencies:**
  ```bash
  sudo apt autoremove
  ```
- ✅ **Enable automatic security updates (Ubuntu):**
  ```bash
  sudo apt install unattended-upgrades
  sudo dpkg-reconfigure unattended-upgrades
  ```