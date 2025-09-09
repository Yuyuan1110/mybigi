---
tags: Linux, Utils,boshiamy, input
alias: []
created: 2025-09-09
updated: 2025-00-09
source:
---

# Installation

1. Install `fcitx5` input method. (provide Chinese input method for Linux)
	- `$ sudo apt install fcitx5-table-extra`
2. Launch `fcitx5`, then open `fcitx5 configration`
3. Uncheck `Only show currently language` at right-down side, and search `boshiamy` at right-top text box.
4. Add `boshiamy` input method to left select box.
5. Install gnome-shell-extension-manager.
	- `$ sudo apt install gnome-shell-extension-manager`
6. open browser and visit this [website](https://extensions.gnome.org/extension/261/kimpanel/)
7. Install `gnome-shell-extension-kinpanel` on website.
8. Setup launch `fctix5` when system login
	- open system settings
	- Navigation to `system -> Region & Language -> Manage Installed Language`
	- Setup `Keyboard input method system` to `fcitx 5`
9. reboot.