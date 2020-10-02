#  修改 Windows 控制台的默认代码页

---

注意：不同版本或计算机都有可能导致修改方式不同，本文仅供参考。

---

####  1. 为什么要修改这玩意

一般在程序开发中你使用的编码是统一的 UTF-8，在 Windows 下有时会遇到乱码问题，比如下面这个程序：

```C
#include<stdio.h>
int main()
{
    char a=176,b=219;
    printf("%c%c%c%c%c\n",b,a,a,a,b);
    printf("%c%c%c%c%c\n",a,b,a,b,a);
    printf("%c%c%c%c%c\n",a,a,b,a,a);
    printf("%c%c%c%c%c\n",a,b,a,b,a);
    printf("%c%c%c%c%c\n",b,a,a,a,b);
    return 0;
}
```

运行时会出现中文乱码。

这是因为 Window cmd 的默认编码是 GBK。与程序采用的 UTF-8 不一致造成的中文及特殊字符乱码。

####  查看系统编码

打开运行 —— 命令提示符窗口输入 `chcp`，回车。

或者，打开 cmd 后，点击 cmd 窗口左上角图标，选"属性"菜单。



####  修改方法

#####  第一种：临时修改编码

使用 `chcp` 命令，例如 `chcp 65001`，这会将当前代码页变为 utf-8 编码，不过这种方式在关闭 cmd 之后会自动失效。

|十进制码值|对应编码名称 |
| ------ | --------- |
|   950  | 繁体中文    |
|  65001 | UTF-8 代码页|
|  936   | 简体中文默认的 GBK|
|  437   |  MS-DOS 美国英语 |

#####  第二种：永久性修改

永久修改及修改注册表

打开注册表编辑器：运行 —— 输入 `regedit`。

定位到：HKEY_CURRENT_USER\Console\%SystemRoot%_system32_cmd.exe

将 CodePage 值修改为 十进制 65001 。

或

转到  [HKEY_LOCAL_MACHINE\Software\Microsoft\Command Processor\Autorun]

将值修改为 @chcp 65001>nul

或

转到 [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage\OEMCP]

将值修改为65001

如果改完仍无法正常显示 UTF-8 字符，则需改变字体属性：在命令行标题栏上点击右键，选择"属性" -> "字体"，将字体修改为 True Type 字体 "Lucida Console" ，然后点击确定将属性应用到当前窗口。

####  不得不提的事

不懂 Windows 操作系统的内部运作

一开始进入注册表编辑器时在 HKEY_CURRENT_USER\Console\

下没有 %SystemRoot%_system32_cmd.exe

只有关于 PowerShell 的设置，过了一段时间，

正找其它教程时，再次打开注册表编辑器，

发现多出了两个目录，一个关于 cmd ，一个关于 CodeBlocks。

然后，只是修改 cmd 并不能完全解决开头的代码输出问题，最后修改 CodeBlocks 的 CodePage 值为 437 才得到理想的输出。

---

#  参考资料

---
-  [修改 Windows 的系统编码](https://www.cnblogs.com/xy-ouyang/p/10688575.html)
-  [修改 cmd 控制台默认代码页编码的几种方法【GPK、UTF-8】](https://blog.csdn.net/gulang03/article/details/81771343)
- [修改 cmd 控制台默认代码页编码的几种方法](https://www.pianshen.com/article/7569611838/)
- [更改 cmd 代码页，修正中文显示](https://my.oschina.net/aiguozhe/blog/108542)

