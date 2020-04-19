# Dedicated server Fresh start
basic security & conf

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


## client side
```
~/.ssh/config
Host kimsufi
	User CustomUserName
	HostName YourServer
	Port YourPort
	IdentityFile ~/.ssh/YourPrivateSshKey
```
