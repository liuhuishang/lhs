# 1.虚拟机的下载和安装
---
[参考连接](https://blog.csdn.net/qq_42417071/article/details/136327674)

根据以上教程进行虚拟机的安装以及ubuntu的安装，以便可以在电脑进行linux的相关学习。

# 2.docker的下载和使用

# 3.linux的基础命令

## 1.Linux yum 命令

---

首先进行yum的安装使用指令：apt-get install yum
![](C:\Users\13304\Desktop\学习图像\1.png)

---
   1.列出所有可更新的软件清单命令：yum check-update

   2. 更新所有软件命令：yum update

   3. 仅安装指定的软件命令：yum install <package_name>

   4. 仅更新指定的软件命令：yum update <package_name>

   5. 列出所有可安裝的软件清单命令：yum list

   6. 删除软件包命令：yum remove <package_name>

   7. 查找软件包命令：yum search <keyword>

   8. 清除缓存命令:

        yum clean packages： 清除缓存目录下的软件包
        yum clean headers： 清除缓存目录下的 headers
        yum clean oldheaders： 清除缓存目录下旧的 headers
        yum clean， yum clean all （= yum clean packages; yum clean oldheaders） ：清除缓存目录下的软件包及旧的 headers