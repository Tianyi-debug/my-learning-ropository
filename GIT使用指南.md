# GIT使用指南

## GIT Bash

Git Bash 是一个命令行工具，提供了类似于 Linux Shell 的环境，使用户能够在 Windows 系统上使用类Unix命令。
**用途**： 通过 Git Bash，用户可以使用 Git 的命令行功能，执行版本控制任务，例如克隆仓库、提交更改等。

## GIT CMD

**描述**： Git CMD 是一个在 Windows 命令提示符中运行的命令行工具。与 Git Bash 不同，Git CMD 更接近于 Windows 命令行环境。
**用途**： 类似于 Git Bash，Git CMD 也允许用户在命令行中执行 Git 命令，进行版本控制操作。

## GIT GUI

**描述**： Git GUI 是 Git 的图形用户界面工具，提供了一个可视化的界面，使用户能够执行版本控制操作而无需使用命令行。
**用途**： 通过 Git GUI，用户可以更直观地查看仓库状态、提交更改、查看历史记录等，适用于那些不太习惯使用命令行的用户

## GIT名词概念

![image-20250908135420985](C:\Users\zty\AppData\Roaming\Typora\typora-user-images\image-20250908135420985.png)

![image-20250908135746870](C:\Users\zty\AppData\Roaming\Typora\typora-user-images\image-20250908135746870.png)

关于http和ssh的选择，http对远程仓库操作有限制，例如输入密码等，ssh密钥只需要初始配置一次即可

git fetch 和 git pull的区别

git fetch是取来后做决定后要不要合并

git pull是直接拉下来合并

## GIT命令和操作步骤

git init

初始化本地仓库

git clone

拉取别人的远程仓库

git add .

git add file2.txt 

提交到暂存区

git status

查看状态

git commit -m "new file hello.txt"

添加到本地仓库，文本说明提示为双引号中内容

git config --list

查看配置例如邮箱和用户名git

$ git config --global --replace-all user.email "输入你的邮箱" 

$ git config --global --replace-all user.name "输入你的用户名"

可以用来修改

这时候，你的本地 Git 仓库与 GitHub 远程仓库还没有办法传输的，由于使用的是 SSH 加密，需要进行以下设置。

1. 创建 SSH Key。在用户主目录下，看看有没有 .ssh 目录，如果有，再看看这个目录下有没有 id_rsa 和 id_rsa.pub 这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开终端（Windows 下打开 Git Bash），创建 SSH Key：
2. 然后在github中输入ssh key内容将电脑和远程仓库关联

git remote add origin git@github.com:Tianyi-debug/my-learning-ropository.git

将本地与远程仓库相关联，后面部分是密钥，关联一个远程库时必须给远程库指定一个名字，`origin`是默认习惯命名；

git rm example.txt

用来删除文件

git ls-files

列出所有被git跟踪的文件

```
git branch -M main
git push -u origin main
```

将本地的仓库推送到远程

由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。

git push origin master

以后推送都用这个

```plain
git remote -v
```

查看远程库信息

git remote rm origin

删除绑定关系，此处的“删除”其实是解除了本地和远程的绑定关系，并不是物理上删除了远程库。远程库本身并没有任何改动。要真正删除远程库，需要登录到GitHub，在后台页面找到删除按钮再删除。

要关联一个远程库，使用命令`git remote add origin git@server-name:path/repo-name.git`；

关联一个远程库时必须给远程库指定一个名字，`origin`是默认习惯命名；

关联后，使用命令`git push -u origin master`第一次推送`master`分支的所有内容；

此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改；

**这上面是方式一，即本地已经有代码需要上传远程，下面是方式二，即远程有代码需要拉到本地**

git clone git@github.com:weiyigeek/learngit.git

git pull #从远程服务器仓库上拉取项目

当然了，在实际工作中，我们脑子里怎么可能记得一个几千行的文件每次都改了什么内容，不然要版本控制系统干什么。版本控制系统肯定有某个命令可以告诉我们历史记录，在Git中，我们用`git log`命令查看：