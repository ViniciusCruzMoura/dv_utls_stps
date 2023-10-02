# AstroNvim

sudo add-apt-repository ppa:neovim-ppa/unstable && sudo apt update

sudo apt install python3-pip python3-venv python3-dev python3-setuptools npm cargo build-essential nodejs make gcc ripgrep unzip neovim git

mv ~/.config/nvim ~/.config/nvim.bak
mv ~/.local/share/nvim ~/.local/share/nvim.bak
mv ~/.local/state/nvim ~/.local/state/nvim.bak
mv ~/.cache/nvim ~/.cache/nvim.bak

git clone --depth 1 https://github.com/AstroNvim/AstroNvim ~/.config/nvim

cargo install tree-sitter-cli

LAZYGIT_VERSION=$(curl -s "https://api.github.com/repos/jesseduffield/lazygit/releases/latest" | grep -Po '"tag_name": "v\K[^"]*')
curl -Lo lazygit.tar.gz "https://github.com/jesseduffield/lazygit/releases/latest/download/lazygit_${LAZYGIT_VERSION}_Linux_x86_64.tar.gz"
tar xf lazygit.tar.gz lazygit
sudo install lazygit /usr/local/bin

add-apt-repository ppa:daniel-milde/gdu
apt-get update
apt-get install gdu

curl -LO https://github.com/ClementTsang/bottom/releases/download/0.9.6/bottom_0.9.6_amd64.deb
sudo dpkg -i bottom_0.9.6_amd64.deb	

# Docker
curl -fsSL https://get.docker.com | sh

# Postman
https://www.postman.com/downloads/
# DBeaver
https://dbeaver.io/download/
# WSL
wsl --install

wsl --list --online
wsl --install -d Ubuntu-20.04

wsl -l -v

wsl --list
wsl --unregister Ubuntu

# NerdHack Font
https://www.nerdfonts.com/font-downloads
https://github.com/ryanoasis/nerd-fonts/releases/download/v3.0.2/Hack.zip
