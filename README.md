Markdown# Installing StrataVane VPN

StrataVane requires admin/root privileges to run (OpenVPN needs to modify network interfaces and routing tables). Pick your OS below.

## Arch-based (CachyOS, Arch, Manjaro, EndeavourOS)

Update system repositories:
```bash
sudo pacman -Syu
Install required packages:Bashsudo pacman -S python python-pip python-pyqt5 python-requests python-beautifulsoup4 openvpn
Clone the repository:Bashgit clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
Enter the project directory:Bashcd YOUR_REPO
Run StrataVane with root privileges:Bashsudo python3 stratavaneVPN.py
Debian-based (Ubuntu, Debian, Linux Mint, Pop!_OS)Update package lists:Bashsudo apt update
Install required packages:Bashsudo apt install python3 python3-pip python3-pyqt5 python3-requests python3-bs4 openvpn
Clone the repository:Bashgit clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
Enter the project directory:Bashcd YOUR_REPO
Run StrataVane with root privileges:Bashsudo python3 stratavaneVPN.py
BSD-based (FreeBSD)Package names can shift slightly between FreeBSD releases — if a name below doesn't resolve, run pkg search pyqt5 or pkg search beautifulsoup to find the current one for your version.Update package repository:Bashsudo pkg update
Install required packages:Bashsudo pkg install python3 py39-pip py39-pyqt5 py39-requests py39-beautifulsoup4 openvpn
Clone the repository:Bashgit clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
Enter the project directory:Bashcd YOUR_REPO
Run StrataVane as root:Bashsudo python3 stratavaneVPN.py
(OpenBSD/NetBSD: package managers and names differ — pkg_add on OpenBSD, pkgin on NetBSD — the general shape is the same: install Python 3, PyQt5, requests, beautifulsoup4, and openvpn, then run as root.)WindowsInstall Python 3 from python.org — check "Add python.exe to PATH" during setup.Install OpenVPN Community Edition from openvpn.net/community-downloads (this installs the TAP driver StrataVane needs).Open Command Prompt as Administrator (right-click → "Run as administrator").Install required Python packages:DOSpip install PyQt5 requests beautifulsoup4
Clone the repository:DOSgit clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
Enter the project directory:DOScd YOUR_REPO
Launch the app (must stay in the elevated Administrator terminal):   DOSpython stratavaneVPN.py
Verify connection adapter (PowerShell):PowerShellipconfig
Check public IP address (PowerShell):PowerShellcurl.exe ifconfig.me
macOSInstall Homebrew first if you don't have it: https://brew.shInstall OpenVPN and Python:Bashbrew install python openvpn
Install Python libraries:Bashpip3 install PyQt5 requests beautifulsoup4
Clone the repository:Bashgit clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
Enter the project directory:Bashcd YOUR_REPO
Run StrataVane with root privileges:Bashsudo python3 stratavaneVPN.py
Verify tunnel interface (macOS uses utun0 or utun1):Bashifconfig utun0
Check public IP address:Bashcurl ifconfig.me
Verifying Connection (Linux)Check that the tunnel interface exists with an assigned IP:Baship a show tun0
Verify the default route routes traffic through tun0:Baship route
Confirm your public IP address has changed:Bashcurl ifconfig.me
Network sanity check:Bashping -c 4 8.8.8.8
NotesStrataVane fetches free configs and credentials directly from vpnbook.com at runtime — nothing is bundled or pre-baked, so you're always getting current servers/passwords.   Requires admin/root because OpenVPN needs to create a tun/utun/TAP interface and rewrite your default route — there's no way around this on any OS[cite: 1].
