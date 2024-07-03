# Unattended Install Script for ERPNext
Unattended script for ERPNext installation (Supports Versions 13, 14 and 15).

This is a no-interactive script for installing ERPNext Versions 13, 14 and 15. You can set up either development or production with very minimal interaction.

# How To:
To use this script, follow these steps:

# Before Installation

Make sure you install the latest package versions by updating system packages if you are running this script on a fresh Ubuntu machine.
The first command will remove the new kernel version update/upgrade
```
sudo apt full-upgrade -y --auto-remove
sudo apt update && sudo apt -y upgrade
```
and then reboot your machine 

# Important!
Do not run this script as root as it will fail when setting up the site. If your VPS default user is root, create a non-root user by following these steps:

1. Create a new user and add it to sudoers
```
sudo useradd -m erpnext -s /bin/bash
sudo usermod -aG sudo erpnext
sudo passwd erpnext
sudo su - erpnext
sudo apt update
```
2. Ensure you're on created user's home directory:
```
cd /home/erpnext
```
3. Continue with the next steps below.

# Installation:

1. Clone the Repo:
```
###git clone https://github.com/flexcomng/erpnext_quick_install.git
git clone https://github.com/zyztek/erpnext-script/blob/main/erpnext_install.sh
```
2. navigate to the folder:
```
cd erpnext_quick_install
```
3. Make the script executable
```
chmod +x erpnext_install.sh
```
4. Run the script:
```
source erpnext_install.sh
```
# Compatibility

Ubuntu 24.04 LTS,
Ubuntu 23.04 LTS,
Ubuntu 22.04 LTS,
Ubuntu 20.04 LTS

Debian 10 (Buster),
Debian 11 (Bulls Eye)
Debian 12 (Bookworm)

# NOTE:

Version 15 Compatibility is set to Ubuntu 22.04 LTS and above and Debian 12 only. Lower versions are not supported for version 15 installation due to dependency issues.
Visit https://github.com/gavindsouza/awesome-frappe to learn about other apps you can install.

If you encounter spawn error on socketio when running bench restart, run the following commands:

```
bench setup socketio
bench setup supervisor
bench setup redis
sudo supervisorctl reload
```
This will fix the spawn error and all services will restart successfully.

to run bench use:
```
cd frappe-bench
bench start
```
if bench not running execute this command
```
bench serve --port 8001
```
