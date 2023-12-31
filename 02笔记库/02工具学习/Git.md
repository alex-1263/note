---
uid:
---
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
如果需要**add**多个文件,可以使用`git add .`或者`git add --all`命令

# 版本控制
## 工作区
**git**分为**工作区**<span style="background:#A0CCF6">**workspace**</span> ,**暂存区**<span style="background:#A0CCF6">**index/stage**</span>,**资源库**<span style="background:#A0CCF6">**Repository**</span>和**远端库**<span style="background:#A0CCF6">**Remote Directory**</span>,如下图所示
![[Pasted image 20231101084721.png]]
如果需要查看**工作区状态**需要使用`git status`命令
## 文件修改
在**git**中**暂存区**和**工作区**的文件是不同步的,如果先对文件进行了一次修改,然后使用`git add`命令后再对文件进行修改后并使用`git commit`会发现提交的文件与现在的文件不相同,这时候可以使用`git add`和`git commit`命令进行一次提交,<font color=#f20736>**git管理的不是文件,是修改**</font>,所以不管如何修改文件,只要没有提交到资源库,都可以从资源库恢复
## 撤销文件修改
在修改文件之后,如果没有添加到暂存区,想要撤销文件修改可以使用`git restore <file>`来恢复到最近一次`add`或者`commit`的版本
在修改文件之后,使用`git add`添加到暂存区,在没提交的时候,可以通过`git restore --staged <file>`来删除**暂存区**中的**修改**,
如果修改文件之后,使用了`add`并`commit`后,并没有推送给远程库,需要使用`git reset --hard HEAD^`来回退版本
如果修改文件之后,使用了`add`并`commit`后,且推送到了远程库,如何撤销文件修改?
## 删除文件
在git中**删除文件**也是一个修改操作,当我们文件资源管理器中删除文件或者使用`rm`命令删除文件后,使用`git status`后可以得知哪些文件被删除 
接下来可以选择使用`git rm <file>`和`commit`来删除并提交修改或者使用`git restore <file>`来恢复文件
<font color=#f20736>**如果一个文件没有被提交过,则不能恢复**</font>
## 版本回退
将文件修改并提交后，如果想要**回退**，使用`git log`获得版本修改历史后，使用`git reset --hard HEAD^`
`HEAD`指当前文件的最新版本,`^`指前一个版本,`HEAD^`指最新版本的上一个版本
## 撤销版本回退
在将文件**回退版本**后,如果想要撤销可以使用`git reflog`命令,获得**修改历史**,找到需要回退的版本的**commit id**,输入**commit id**,不需要完全输入,只要前几位相同,**git**会帮我们找到匹配的版本,使用`git reset --hard commitid`命令


# 远程库
## 创建一个SSH Key
使用`ssh-keygen -t rsa -C "youremail@example.com"`创建一个key,在用户目录中找到`id_rsa.pub`将其中keyt添加到GitHub中
## 添加远程库
使用**GitHub** crate a new Repository,填入你想创建的远程库的名字后,根据GitHub上的提示在**git Bash**上运行下面代码
```bash
git remote add origin git@github.com:michaelliao/learngit.git
git branch
git push -u origin master
```
推送成功后,即可在GitHub上看到自己的代码
## 从远程库克隆
使用**GitHub** crate a new Repository,填入你想创建的远程库的名字,并勾选`Initialize this repository with a README`,或者从已经有的库中进行克隆
运行如下代码
```bash
git clone git@github.com:michaelliao/gitskills.git
```
# 分支管理
### 创建分支与合并
`git branch dev`可以创建一个名为`dev`的分支,使用`git checkout dev`可以将当前分支切换为`dev`
git中的分支其实就是一个指针,所以git合并分支的速度会很快
当在`dev`中对一个文件并修改后,只能在`dev`分支中查看到,如果想在`master`分支中查看,需要先将分支切换到`master`,然后再使用`git merge dev`将`dev`分支中的修改合并到`master`分支中,在合并后可以使用`git branch -d dev`将`dev`分支删除
在新版本的git中更加鼓励使用`git switch dev`来替换`git checkout dev`,`git switch -c dev`替换`git checkout -b dev`
<font color=#f20736>**对于所有的分支,暂存区和公共区是公共的**</font>

