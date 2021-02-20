# study-Git
Introduction and syntax of Git

## 1.安装  

- Linux 上安装 Git  

  可以在终端上输入`git`，查看系统是否安装 Git  
  如果输出`The program 'git' is currently not installed.` 我们可以使用如下语句进行安装：  
  ```
  $ sudo apt-get install git
  ```
  
- Windows 上安装 Git  

  首先，直接可以从 Git 官网 <https://git-scm.com/downloads> 上下载安装程序，然后默认选项安装即可  
  其次，安装完成后，在开始菜单里找到 Git -> Git Bash，会弹出一个类似命令行窗口的界面，说明 Git 安装成功  
  最后，进行设置，在命令行输入：  
  ```
  $ git config --global user.name "Your Name"
  $ git config --global user.email "email@example.com"
  ```
  由于 Git 是分布式版本控制系统，所以每个机器必须自报家门：用户名和 email 地址  
  同样，我们也可以使用如下两个命令查询本机的用户名和 email 地址：
  ```
  $ git config --global user.name
  $ git config --global user.email
  ```
## 2.创建版本库  

版本库又名仓库（repository），仓库里的所有文件均可以被Git管理起来，每个文件的修改、删除，Git都能进行跟踪  

- git init  

  `git init`命令可以将当前目录变成 Git 可以管理的仓库，例如：  
  ```
  $ mkdir learngit
  $ cd learngit
  $ git init
  ```
  以上命令将空目录 learngit 变成了一个空仓库（empty Git repository），且当前目录下多了一个隐藏的 .git 目录，是 Git 用于跟踪管理版本库的，使用`ls -ah`命令可以查看  
  同样，可以选择将一个非空的目录创建成为 Git 仓库  
  
## 3.工作区和暂存区  

- 工作区（Working Directory）  

  指在电脑里能看到的目录，比如 learngit 目录就是一个工作区  
  
- 暂存区（stage 或 index）  

  隐藏目录 .git 不算作工作区，而是 Git 的版本库，版本库中最终要的就是暂存区（stage 或 index）和 Git 自动创建的第一个分支（master）以及指向 master 的指针（HEAD）  
  
## 4.添加文件至版本库  

- 写在前面  

  所有的版本控制系统，其实只能跟踪文本文件的改动，比如：Txt文件、网页、程序代码等。而 Microsoft 的 Word 格式是二进制格式，版本控制系统无法跟踪 Word 文件的改动  
  Windows 系统建议使用 Notepad++ 代替自带的记事本编辑任何文本文件，并将 Notepad++ 默认的编码设置为 UTF-8 without BOM  
  
- git add  

  `git add`把文件添加进版本库，实际上是将文件修改添加至暂存区  
  在 learngit 目录或子目录下，编写 readme.txt 如下：
  ```
  Git is a version control system.
  Git is free software.
  ```
  将 readme.txt 文件添加至版本库：  
  ```
  $ git add readme.txt
  ```
  
- git commit  

  `git commit`提交修改，实际上是将暂存区的**所有内容**提交到当前分支  
  `git commit -m “xxx”`-m后面是本次提交的说明
  ```
  $ git commit -m "wrote a readme file"
  ```
 
## 5.版本回退

- git status  

  `git status`时刻掌握仓库的状态  
  ```
  $ git status
  ```
  
- git diff  

  `git diff`查看文本文件所做的修改  
  ```
  $ git diff readme.txt
  ```

- git log  

  `git log`显示从最近到最远的提交日志  
  `git log --pretty=oneline`只显示从最近到最远每次提交的 commit id  
  ```
  $ git log
  $ git log --pretty=oneline
  ```
  
- git reset  

  `git reset --hard xxx`将当前版本回退到指定版本 xxx，xxx 可以是 commit id 的前几位也可以用 HEAD 表示：  
  HEAD 表示当前版本，HEAD^ 表示上一个版本，HEAD^^ 表示上上一个版本，HEAD~100 表示前100个版本  
  ```
  $ git reset -- hard HEAD^
  $ git reset -- hard 1094a
  ```
