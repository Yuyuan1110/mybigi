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
1. After installed OS, please execute update first.
	- `sudo apt update`
	- `sudo apt upgrade`
	- `sudo yum update`
	- `sudo yum upgrade`
2. Install essential tools
	-  curl: `sudo apt install curl`
	-  tmux: `sudo apt install tmux`
	-  vim: `sudo apt install vim`
	-  nvim: Refer to [[neovim]]
	-  git: `sudo apt install git`
	-  python utils: `sudo apt install python3-pip python-venv`
	-  node.js utils: 
		- `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash`
		- `source ~/.bashrc`
		- check: `nvm --version`
		- latest node: `nvm install node`
		- specify version: `nvm install 18.17.0`
		- list: `nvm ls`
	-  build essential: `sudo apt install build-essential`
	- htop: `sudo apt install htop`
3. Other tools
	- flameshot: `sudo apt install flameshot`
		- flameshot need to cooperate with `flameshot gui --raw | wl-copy --type image/png` and `flameshot gui` and could setup shortcut.