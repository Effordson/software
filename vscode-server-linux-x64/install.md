---
date: 2022-10-30 15:54
tags:
- Linux
- vscode
aliases: 
---


# 1 需求场景
需求场景：VS code推出了可以在本地连接远程服务器开发，开发环境在远程服务器，但是使用扩展插件Remote SSH，可以连接远程，就像在本地开发一样。原理就是在远程有VS code服务端，本地连接到远程，开发环境就像在本地一样

# 2 注意事项
1、本地和远程服务器需要是相同的版本，也就是有相同的commit，可以通过 菜单=》帮助=》关于，查看commit id，所以建议关闭自动升级，否则服务端不匹配版本会报错。关闭升级(用户级别设置)：设置=》搜索：更新=》Update:mode=none,修改写入配置文件：~\AppData\Roaming\Code\User\settings.json 【"update.mode": "none"】
2、扩展插件安装：下载离线安装包，

# 3 远程服务器安装
1、下载安装包： https://update.code.visualstudio.com/commit:<commit-id>/server-linux-x64/stable，要选择stable表示稳定版本的意思。这个里面的commit-id表示要下载的vscode版本id
当前版本下载：https://update.code.visualstudio.com/commit:d045a5eda657f4d7b676dedbfa7aab8207f8a075/server-linux-x64/stable

2、创建目录：mkdir -p ~/.vscode-server/bin

3、上传到Linux服务器目录~/.vscode-server/bin中并解压

4、重命名：mv vscode-server-linux-x64 d045a5eda657f4d7b676dedbfa7aab8207f8a075

5、安装扩展插件：Remote - SSH、Remote - SSH: Editing Configuration Files

6、连接到远程服务端，自动识别到已经下载vscode-server-linux-x64.tar.gz 进入自动初始化环节，安装完毕后就可以正常打开服务器上的文件进行开发了

安装扩展插件：
1、在本地下载python扩展插件的vsix文件，并上传到远程服务器
2、在vscode中，ctrl+shift+p打开命令行，输入Extensions: install from VSIX，选中上一步上传好的 vsix 文件
3、重启VS code

