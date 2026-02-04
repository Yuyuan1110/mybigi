---
tags:
  - development
  - env
  - starup
alias: []
created: 2026-02-03
updated:
source:
---

## Set up Development environment
### After installed OS, please execute update first.
	1.`sudo apt update`
	2.sudo apt upgrade`
	3.`sudo yum update`
	4.sudo yum upgrade`
### Install essential tools
	1. curl: `sudo apt install curl`
	2. tmux: `sudo apt install tmux`
	3. vim: `sudo apt install vim`
	4. nvim: Refer to [[neovim]]
	5. git: `sudo apt install git`
	6. python utils: `sudo apt install python3-pip python-venv`
	7. node.js utils: 
		- `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash`
		- `source ~/.bashrc`
		- check: `nvm --version`
		- latest node: `nvm install node`
		- specify version: `nvm install 18.17.0`
		- list: `nvm ls`
	8. build essential: `sudo apt install build-essential`
	9. htop: `sudo apt install htop`
### Other tools
	1. flameshot: `sudo apt install flameshot`
		- flameshot need to cooperate with `flameshot gui --raw | wl-copy --type image/png` and `flameshot gui` and could setup shortcut.

### Other Settings
	1. Disable the usb media automount
		- `gsettings set org.gnome.desktop.media-handling automount false`
		- `gsettings set org.gnome.desktop.media-handling automount-open false`
	2. Disable some power settings
		- `sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target`
		- screen saver: 
			- `gsettings set org.gnome.desktop.screensaver lock-enabled false`
			- `gsettings set org.gnome.desktop.lockdown disable-lock-screen true`