#  Linux 下安装 Typora 
---

因为 Snap 里的 Typora 安装下来有一些问题，比如没有设置栏，经常崩溃，所以在网上搜索了教程来自定义安装 Typora 

######  Debian/Ubuntu

```
#or use
#sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -

#add Typora's repository
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update

# install typora
sudo apt-get install typora

# upgrade all packages include Typora 
sudo apt-get upgrade

```



# 参考

- [Install Typora on Linux](https://support.typora.io/Typora-on-Linux/)

