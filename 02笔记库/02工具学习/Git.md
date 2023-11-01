# 安装

在git官网[download](https://git-scm.com/downloads)，然后默认配置安装。
# 创建版本库
## 创建库
```bash
 mkdir learngit      # 创建一个空目录
 cd learngit         # 跳转到新建目录
 pwd                 # 显示当前的目录
/Users/michael/learngit
```
再使用`git init`命令使当前目录变为git仓库
`git init`命令可以在**空目录**下使用，也可以在**有文件的目录**中使用，**但是要注意备份**

## 添加文件
使用`git add xxx.xx`将文件**添加**到**仓库**
使用`git commit`命令将文件**提交**到**仓库**
###### git commit -m
在提交文件时要使用`git commit -m"xxx"`其中`xxx`是提交的**说明**
在任何时候都要提交**具体的说明**，不能使用`xxx`代替，为了他人和自己的**阅读体验**
在**add**文件是可以**add**多个，但**commit**文件，只需要**commit**一次
如需要**add**多个文件,可以使用`git add .`或者`git add --all`命令

# 版本控制
## 版本回退
将文件修改并提交后，如果想要**回退**，使用`git log`获得版本修改历史后，使用`git reset --hard HEAD^`
`HEAD`指当前文件的最新版本,`^`指前一个版本
