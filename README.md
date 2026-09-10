# StrataVane-VPN
a openvpn based vpn without the terminal struggle,right out of the box
.📋 Prerequisites & Requirements

    Python 3.8+

    OpenVPN installed and present in your system PATH

    Administrative/Root privileges (required by OpenVPN to manage virtual network adapters and routing tables)

🪟 1. Windows Installation & Setup
Step 1: Install Dependencies

    Install OpenVPN:

        Download the OpenVPN installer from the official OpenVPN downloads page.

        Run the installer. Ensure OpenVPN Service and TAP/TUN drivers are selected.

    Install Python 3:

        Download Python from python.org.

        During installation, check the box: "Add python.exe to PATH".

    Install Required Python Modules:
    Open Command Prompt or PowerShell as Administrator and run:
    DOS

    pip install PyQt5 requests beautifulsoup4

Step 2: Run StrataVane VPN

Open Command Prompt or PowerShell as Administrator (right-click -> Run as administrator) and navigate to your repository folder:
DOS

python stratavaneVPn.py

Verification: The dark-themed StrataVane VPN window will open, load available .ovpn profiles, and automatically populate the connection credentials.
🐧 2. Linux & Unix Installations
🅰️ Arch-based Distributions (Arch Linux, CachyOS, Manjaro)

Open terminal and run:
Bash

# Install system packages & Python dependencies
sudo pacman -S openvpn python-pyqt5 python-requests python-beautifulsoup4

# Run the script with root privileges
sudo python3 stratavaneVPn.py

🅱️ Debian-based Distributions (Ubuntu, Debian, Pop!_OS, Mint)

Open terminal and run:
Bash

# Update package list and install dependencies
sudo apt update
sudo apt install -y openvpn python3-pyqt5 python3-requests python3-bs4

# Run the script with root privileges
sudo python3 stratavaneVPn.py

❄️ NixOS
Option A: Direct Execution using nix-shell

Run an ephemeral shell environment containing all dependencies:
Bash

nix-shell -p openvpn python3 python3Packages.pyqt5 python3Packages.requests python3Packages.beautifulsoup4 --run "sudo python3 stratavaneVPn.py"

Option B: System-wide Configuration (configuration.nix)

Add OpenVPN and Python packages to your environment.systemPackages in /etc/nixos/configuration.nix:
Nix

environment.systemPackages = with pkgs; [
  openvpn
  (python3.withPackages (ps: with ps; [
    pyqt5
    requests
    beautifulsoup4
  ]))
];

Rebuild your configuration and run:
Bash

sudo nixos-rebuild switch
sudo python3 stratavaneVPn.py

🍎 3. macOS Installation & Setup
Step 1: Install Dependencies via Homebrew

Open Terminal and run:
Bash

# Install Homebrew if not already present
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install OpenVPN and Python packages
brew install openvpn python
pip3 install PyQt5 requests beautifulsoup4

Step 2: Run StrataVane VPN

Because OpenVPN on macOS requires root privileges to manage TUN/TAP interfaces, run:
Bash

sudo python3 stratavaneVPn.py

🚀 Quick Usage Guide

    Launch the application with admin/root rights as described above for your OS.

    The app will sync available .ovpn profiles and automatically scrape dynamic credentials from VPNBook.

    Select a profile from the Select OpenVPN Profile list (or click Browse Custom .ovpn File...).

    Click CONNECT. Monitor the live log window at the bottom until Connected! OpenVPN tunnel is active. appears.

    Click DISCONNECT to terminate the connection and restore your standard network interface.
