#  Linux 下使用 SSR

---

使用系统：Ubuntu 18.04.

####  1、使用 electron-ssr

因为原作者已经将项目删除，不再维护

只能找到备份：

https://github.com/qingshuisiyuan/electron-ssr-backup/releases

https://github.com/x-Armin/Resource/blob/master/electron-ssr-0.2.6.deb



##### 安装配置
```Linux
sudo dpkg -i electron-ssr-0.2.6.deb
```

#####  软件依赖问题   

```Linux
libcanberra-gtk-module
gconf2
gcon-service
```

执行

```
sudo apt-get -f install
```

再次输入

```
sudo dpkg -i electron-ssr-0.2.6.deb
```

如果在运行时出现弹窗提示：进程 XXX 可能无法关闭
可尝试安装
```
sudo apt-get install libsodium-dev
sudo apt-get install libssl-dev
sudo apt-get install libssl-doc

```
因为 Ubuntu 默认安装了 python，所以我不需要进一步安装
但如有需要，可以使用以下命令
```
sudo apt install python
```
#####  修改系统设置

|       代理       |            地址               |   端口  |
| -------------- |  --------------------- | -------  |
| HTTP 代理  |http://127.0.0.1  | 12333 |
| HTTPS 代理 |https://127.0.0.1 | 12333 |
| Socks 主机 | 127.0.0.1         | 1080  |
| 忽略主机   | localhost, 127.0.0.0/8,::1|

配置和 Windows 上的客户端差不多，拷贝 ssr 订阅链接，更新，选择喜欢的节点即可。

#####  卸载
```
sudo dpkg -r electron-ssr
```
#####  小问题：

- 更换系统为 Kubuntu 20.04.2 后，需要使用下面这个才能连通全局代理
```bash
$ export https_proxy="http://127.0.0.1:12333"
```

#  参考
---
-  [Debian 系列 —— Ubuntu18.04 为例](https://github.com/qingshuisiyuan/electron-ssr-backup/blob/master/Ubuntu.md)
-  [在 Ubuntu18.04 上使用 SSR](http://x-armin.com/%E5%9C%A8Ubuntu%E4%B8%8A%E4%BD%BF%E7%94%A8SSR/)
-  [运行 electron-ssr 后报错且无法访问外网](https://github.com/qingshuisiyuan/electron-ssr-backup/issues/26)
-  [Linux 上安装和使用 Electron SSR 代理服务器](https://note.jianrry.com/tool/linux/software-management/how-to-install-and-use-electron-ssr-on-linux)


