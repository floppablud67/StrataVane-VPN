Installing StrataVane VPN

StrataVane requires admin/root privileges to run (OpenVPN needs to modify network interfaces and routing tables). Pick your OS below.

Arch-based (CachyOS, Arch, Manjaro, EndeavourOS)
bash
sudo pacman -Syu
sudo pacman -S python python-pip python-pyqt5 python-requests python-beautifulsoup4 openvpn
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
sudo python3 stratavaneVPN.py
Debian-based (Ubuntu, Debian, Linux Mint, Pop!_OS)
bash
sudo apt update
sudo apt install python3 python3-pip python3-pyqt5 python3-requests python3-bs4 openvpn
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
sudo python3 stratavaneVPN.py
BSD-based (FreeBSD)

Package names can shift slightly between FreeBSD releases — if a name below doesn't resolve, run pkg search pyqt5 / pkg search beautifulsoup to find the current one for your version.

sh
sudo pkg update
sudo pkg install python3 py39-pip py39-pyqt5 py39-requests py39-beautifulsoup4 openvpn
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
sudo python3 stratavaneVPN.py

(OpenBSD/NetBSD: package managers and names differ — pkg_add on OpenBSD, pkgin on NetBSD — the general shape is the same: install Python 3, PyQt5, requests, beautifulsoup4, and openvpn, then run as root.)

Windows
Install Python 3 from python.org — check "Add python.exe to PATH" during setup.
Install OpenVPN Community Edition from openvpn.net/community-downloads (this installs the TAP driver StrataVane needs).
Open Command Prompt as Administrator (right-click → "Run as administrator").
cmd
pip install PyQt5 requests beautifulsoup4
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
python stratavaneVPN.py
   Must stay in the elevated (Administrator) terminal — StrataVane checks for
   admin rights on launch and exits if it isn't running elevated.

**Verify the connection (PowerShell):**
```powershell
ipconfig
# look for a "TAP-Windows Adapter" with an IP assigned
curl.exe ifconfig.me
```

---

## macOS

```bash
# Install Homebrew first if you don't have it: https://brew.sh
brew install python openvpn
pip3 install PyQt5 requests beautifulsoup4
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
sudo python3 stratavaneVPN.py
```

**Verify the connection:**
```bash
ifconfig utun0      # macOS names the tunnel interface utun0/utun1, not tun0
curl ifconfig.me
```

---

## Verifying it's actually working (Linux)

```bash
ip a show tun0          # tunnel interface should exist with an IP
ip route                # default route should go via tun0
curl ifconfig.me        # your public IP should change vs. before connecting
ping -c 4 8.8.8.8        # basic connectivity sanity check
```

---

## Notes

- StrataVane fetches free configs and credentials directly from
  [vpnbook.com](https://www.vpnbook.com) at runtime — nothing is bundled or
  pre-baked, so you're always getting current servers/passwords.
- Requires admin/root because OpenVPN needs to create a `tun`/`utun`/TAP
  interface and rewrite your default route — there's no way around this on
  any OS.
