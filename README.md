# Dedicated server Fresh start
basic security & conf: see server & client side section

## connection
```
ssh root@YourServer -p YourPort
```

## server side
```
passwd root
```
```
apt update
apt upgrade
```
```
apt install zsh git vim
```
```
git clone --recursive https://github.com/agadiffe/dot_vim $HOME/.vim
ln -s $HOME/.vim/vimrc $HOME/.vimrc
ln -s $HOME/.vim/zshrc $HOME/.zshrc
vim +PluginInstall
```
```
chsh -s /bin/zsh # change default shell
```
```
vim /etc/ssh/sshd_config

Port 22 # change default port  
AddressFamily inet # listen only on IPv4  
```
```
reboot
```
```
adduser CustomUserName
usermod -aG sudo CustomUserName
```
```
vim /etc/ssh/sshd_config

LoginGraceTime 1m  
PermitRootLogin no  
StrictModes yes  
AllowUsers validuser1  
Protocol 2  
```
```
/etc/init.d/ssh restart
```
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
```
chmod 700 ~/.ssh
chmod 644 ~/.ssh/authorized_keys
chmod 644 ~/.ssh/known_hosts
chmod 644 ~/.ssh/config
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub
```
```
cat sshkey.pub | authorized_keys
```
```
vim /etc/ssh/sshd_config

PubkeyAuthentication yes  
AuthorizedKeysFile .ssh/authorized_keys  
PasswordAuthentication no  
```
```
alias sudo='sudo ' >> .zshrc # make alias work with sudo
```

## client side
```
~/.ssh/config
Host kimsufi
	User CustomUserName
	HostName YourServer
	Port YourPort
	IdentityFile ~/.ssh/YourPrivateSshKey
```

## Setting Up a Basic Firewall
ufw

## new user
use ```/etc/skel/```. Anything you shove in there will be copied out to a new user profile when you create them.

In its simplest form when used without any option, useradd will create a new user account with the default settings specified in the ```/etc/default/useradd``` file. # change default shell by example
