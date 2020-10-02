#  Linux 安装 搜狗输入法

---

- Download Linux Sogou PinyinInput Installation package，[click here](https://pinyin.sogou.com/linux/)

- cd Downloads 
- Use Terminal commands like this:  
```Linux
$ sudo dpkg -i sogoupinyin_2.3.2.07_amd64-831.deb
```
- In my Kubuntu, there have some software dependency issues
```
fcitx-frontend-qt4 
libqtwebkit4
libopencc2
libopencc1
fcitx-libs
libfcitx-qt0
```
-  I use the following command to fix my problem:
```Linux
$ sudo apt-get -f install
$ sudo apt-get install libopencc2 fcitx-libs
```
-  Bye! No longer use...

#  Reference
---

- [Ubuntu安装搜狗输入法](https://zhuanlan.zhihu.com/p/34270907)

