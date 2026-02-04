---
tags: 
  - Linux
  - Utils
  - nvim
alias: []
created: 2025-09-09
updated: 2025-09-09
source: neovim.io
---

# Install neovim
1. Visit  [neovim website](neovim.io) to install neovim.
2. Clone config and redirection to `~/.config/nvim`.
3. Visit [nvm github](https://github.com/nvm-sh/nvm) to install nvm.
	- After installed nvm, need isntall latest nodejs.
	- `nvm install node`, node mean latest version.
4. Visit [nerdfonts websit](https://www.nerdfonts.com/) and download any fonts look lovely.
	- Recommand use MONO type fonts.
	- insatll nerd font.
5. Setup terminal fonts.
	- open `preference`, setup `Unname` or add profiles.
	- checked  "Custom font" and select to which font install before.
6. Install essential tools
	- rg: `sudo apt install ripgrep`
	- fd: `sudo apt install fd`
	- luarocks: `sudo apt install luarocks`
	- rust:
		- `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`
		- `source "$HOME/.cargo/env"`
	- tree-sitter-cli: `cargo install --locked tree-sitter-cli`
7. open nvim in terminal.