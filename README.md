### AstroNvim
```
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
```
### Docker
```
curl -fsSL https://get.docker.com | sh
```
```
sudo docker run -it --rm -v "$PWD":/usr/src/app -w /usr/src/app gcc:latest bash
sudo docker run -it --rm -v "$PWD":/usr/src/app -w /usr/src/app golang:1.21 bash
sudo docker run -it --rm -v "$PWD":/usr/src/app -w /usr/src/app python:3.9 bash
```
```
sudo docker run -it -p 9000:8000 -v "$PWD":/usr/src/app -w /usr/src/app python:3.9 bash
sudo docker start "container-name-or-id"
sudo docker exec -it "container-name-or-id" bash
```
```
sudo docker build --tag cardcredenciamento:latest --file Dockerfile --force-rm --rm .
sudo docker build -t devapp .
sudo docker run -it -p 9000:8000 -v "$PWD":/usr/src/app -w /usr/src/app devapp bash
```
```
https://codenotary.com/blog/extremely-useful-docker-commands
```
```
sudo docker rm -v -f $(sudo docker ps -qa);
sudo docker volume rm $(sudo docker volume ls -q --filter dangling=true);
sudo docker system prune --all --force;
```
### Postman
```
https://www.postman.com/downloads/
```
### DBeaver
```
https://dbeaver.io/download/
```
### WSL
```
wsl --install

wsl --list --online
wsl --install -d Ubuntu-20.04

wsl -l -v

wsl --list
wsl --unregister Ubuntu

How do I get back unused disk space from Ubuntu on WSL2?
https://superuser.com/questions/1606213/how-do-i-get-back-unused-disk-space-from-ubuntu-on-wsl2
When the command let optimize-vhd is not available in your system do the following:
- Shutdown the wsl before managing its disk
wsl --shutdown
- Save the following script as compact-disk.txt
select vdisk file="C:\Users\%username%\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu20.04onWindows_79rhkp1fndgsc\LocalState\ext4.vhdx"
attach vdisk readonly
compact vdisk
detach vdisk
- Open prompt as Administrator and run the saved script above
diskpart /s <SAVED_SCRIPT_FOLDER_PATH>\compact-disk.txt
```
### NerdHack Font
```
https://www.nerdfonts.com/font-downloads
https://github.com/ryanoasis/nerd-fonts/releases/download/v3.0.2/Hack.zip
```

### Portainer, Docker bind, venv
scripts para instalar o docker e portainer
```
-instalar o docker:
curl -fsSL https://get.docker.com | sh

-bind da pasta do docker para o disco de storage:
sudo systemctl stop docker
sudo rm -rf /var/lib/docker
sudo mkdir /var/lib/docker
sudo mkdir /sistemas/apps/docker
sudo mount --rbind /sistemas/apps/docker /var/lib/docker
sudo systemctl start docker

-instalar o portainer:
sudo docker run -d \
  -p 9001:9001 \
  --name portainer_agent \
  --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /var/lib/docker/volumes:/var/lib/docker/volumes \
  portainer/agent:2.18.4
```
scripts para configurar o bind
```
-mount bind permanente
sudo nano /etc/fstab
/sistemas/apps/docker /var/lib/docker none defaults,bind 0 0
```
scripts para o portainer manager
```
-criar volume para salvar as configs
sudo docker volume create portainer_data

-instalar o dashboard
sudo docker run -d -p 9000:9000 -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```
adicionar variaveis de ambiente
```
- Adicionar as variáveis no ambiente da maquina
      sudo nano /etc/environment
- Aplicar as novas variáveis
      source /etc/environment
- Listar as variaveis de ambiente pela palavra chave
      sudo env | grep -E "USER|PASSWORD"

Observação: deve-se utilizar o "sudo" para que as variáveis sejam acessadas pelos sistemas
```

#### Cisco WSL
```
Get-NetAdapter | Where-Object {$_.InterfaceDescription -Match "Cisco AnyConnect"} | Set-NetIPInterface -InterfaceMetric 6000 ; Restart-Service LxssManager
```
