Installing StrataVane VPN

StrataVane requires admin/root privileges to run (OpenVPN needs to modify network interfaces and routing tables). Pick your OS below.   
PY
Arch-based (CachyOS, Arch, Manjaro, EndeavourOS)
Bash

sudo pacman -Syu

Bash

sudo pacman -S python python-pip python-pyqt5 python-requests python-beautifulsoup4 openvpn

Bash

git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git

Bash

cd YOUR_REPO

Bash

sudo python3 stratavaneVPN.py

Debian-based (Ubuntu, Debian, Linux Mint, Pop!_OS)
Bash

sudo apt update

Bash

sudo apt install python3 python3-pip python3-pyqt5 python3-requests python3-bs4 openvpn

Bash

git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git

Bash

cd YOUR_REPO

Bash

sudo python3 stratavaneVPN.py

BSD-based (FreeBSD)

Package names can shift slightly between FreeBSD releases — if a name below doesn't resolve, run pkg search pyqt5 / pkg search beautifulsoup to find the current one for your version.
Bash

sudo pkg update

Bash

sudo pkg install python3 py39-pip py39-pyqt5 py39-requests py39-beautifulsoup4 openvpn

Bash

git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git

Bash

cd YOUR_REPO

Bash

sudo python3 stratavaneVPN.py

(OpenBSD/NetBSD: package managers and names differ — pkg_add on OpenBSD, pkgin on NetBSD — the general shape is the same: install Python 3, PyQt5, requests, beautifulsoup4, and openvpn, then run as root.)
Windows

    Install Python 3 from python.org — check "Add python.exe to PATH" during setup.

    Install OpenVPN Community Edition from openvpn.net/community-downloads (this installs the TAP driver StrataVane needs).

    Open Command Prompt as Administrator (right-click → "Run as administrator").

DOS

pip install PyQt5 requests beautifulsoup4

DOS

git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git

DOS

cd YOUR_REPO

DOS

python stratavaneVPN.py

Must stay in the elevated (Administrator) terminal — StrataVane checks for admin rights on launch and exits if it isn't running elevated.   
PY

Verify the connection (PowerShell):
PowerShell

ipconfig

PowerShell

curl.exe ifconfig.me

macOS

Install Homebrew first if you don't have it: https://brew.sh
Bash

brew install python openvpn

Bash

pip3 install PyQt5 requests beautifulsoup4

Bash

git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git

Bash

cd YOUR_REPO

Bash

sudo python3 stratavaneVPN.py

Verify the connection:
Bash

ifconfig utun0

Bash

curl ifconfig.me

Verifying it's actually working (Linux)

Check tunnel interface with assigned IP:
Bash

ip a show tun0

Verify default route goes via tun0:
Bash

ip route

Confirm public IP has changed:
Bash

curl ifconfig.me

Basic connectivity sanity check:
Bash

ping -c 4 8.8.8.8

Notes

    StrataVane fetches free configs and credentials directly from vpnbook.com at runtime — nothing is bundled or pre-baked, so you're always getting current servers/passwords.   
    PY

    Requires admin/root because OpenVPN needs to create a tun/utun/TAP interface and rewrite your default route — there's no way around this on any OS.   
    PY
