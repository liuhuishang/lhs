# 1.虚拟机的下载和安装
---
[参考连接](https://blog.csdn.net/qq_42417071/article/details/136327674)

根据以上教程进行虚拟机的安装以及ubuntu的安装，由于我之前安装过并且拥有一个centos，所以我现在有两个linux的系统以便可以在电脑进行linux的相关学习。


# 2.linux的基础命令

## 1.vi/vim命令

使用vi建立一个txt文件

![vi的使用](/image/9.png)

## 2.Linux yum 命令

---

使用centos此处先进行更换yum源配置[参考链接](https://blog.csdn.net/2402_84664620/article/details/141193078)

![yum的更新配置](/image/1.png)

---
   1.列出所有可更新的软件清单命令：yum check-update
   
 ![yum的使用](/image/2.png)
       
   2. 更新所有软件命令：yum update
      
![yum的使用](/image/3.png)

   3. 仅安装指定的软件命令：yum install <package_name>
   
 ![yum的使用](/image/4.png)


   4. 仅更新指定的软件命令：yum update <package_name>
   
![yum的使用](/image/3.png)

   5. 列出所有可安裝的软件清单命令：yum list

 ![yum的使用](/image/5.png)
 
   6. 删除软件包命令：yum remove <package_name>

 ![yum的使用](/image/6.png)
 
   7. 查找软件包命令：yum search <keyword>

![yum的使用](/image/7.png)

   8. 清除缓存命令:

        yum clean packages： 清除缓存目录下的软件包
      
        yum clean headers： 清除缓存目录下的 headers
      
        yum clean oldheaders： 清除缓存目录下旧的 headers
      
        yum clean， yum clean all （= yum clean packages; yum clean oldheaders） ：清除缓存目录下的软件包及旧的 headers
![yum的使用](/image/8.png)

## 2.Linux apt 命令

---
关于虚拟机和主机之间的复制粘贴问题：可以在主机上进行ctrl+c进行复制，然后在虚拟机中使用shitft+ctrl+v进行粘贴

[在centos中安装apt](https://www.mryunwei.com/258600.html)

由于我同时安装了Ubuntu和centos此处便使用ubuntu便于使用apt命令

---

1.列出所有可更新的软件清单命令：sudo apt update

![apt的使用](/image/10.png)

2.升级软件包：sudo apt upgrade

![apt的使用](/image/11.png)

3.列出可更新的软件包及版本信息：apt list --upgradable

![apt的使用](/image/12.png)

4.升级软件包，升级前先删除需要更新软件包：sudo apt full-upgrade

![apt的使用](/image/13.png)

5.安装指定的软件命令：sudo apt install <package_name>

![apt的使用](/image/14.png)

6.安装多个软件包：sudo apt install <package_1> <package_2> <package_3>

![apt的使用](/image/14.png)

7.更新指定的软件命令：sudo apt update <package_name>

8.显示软件包具体信息,例如：版本号，安装大小，依赖关系等等：sudo apt show <package_name>

![apt的使用](/image/15.png)

9..删除软件包命令：sudo apt remove <package_name>

![apt的使用](/image/16.png)

10.清理不再使用的依赖和库文件: sudo apt autoremove

![apt的使用](/image/17.png)

11.移除软件包及配置文件: sudo apt purge <package_name>

![apt的使用](/image/18.png)

12.查找软件包命令： sudo apt search <keyword>

![apt的使用](/image/19.png)

13.列出所有已安装的包：apt list --installed

![apt的使用](/image/20.png)
14.列出所有已安装的包的版本信息：apt list --all-versions
![apt的使用](/image/21.png)