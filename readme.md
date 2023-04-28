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
  其次，安装完成后，鼠标右键找到 Git Bash here，会弹出一个类似命令行窗口的界面，说明 Git 安装成功  
  
 ## 2. Git 常用命令
 
 ### 2.1 设置用户签名及邮箱
  
- 由于 Git 是分布式版本控制系统，为了区分每个操作者的身份，所以首次安装 Git 后必须设置用户名（user name）和 email 地址（user email）：  
  ```
  $ git config --global user.name "Your Name"
  $ git config --global user.email "email@example.com"
  ```
  **注意**：设置的用户签名和邮箱与将来登陆任何代码托管中心的账号均无任何关系，但是不设置用户签名及邮箱将无法提交代码  
  
- 同样，我们也可以使用如下两个命令查询本机的用户名和 email 地址：  
  ```
  $ git config --global user.name
  $ git config --global user.email
  ```
  
### 2.2 初始化本地版本库  

版本库又名仓库（repository），仓库里的所有文件均可以被 Git 管理起来，每个文件的修改、删除，Git都能进行跟踪  

- git init  

  `git init` 命令可以将当前目录变成 Git 可以管理的仓库，例如：  
  ```
  $ mkdir learngit
  $ cd learngit
  $ git init
  ```
  以上命令将空目录 learngit 变成了一个空仓库（empty Git repository），且当前目录下多了一个隐藏的 .git 目录，用于跟踪管理版本库，使用 `ls -a` 命令可以查看  
  **同样，可以选择将一个非空的目录创建成为 Git 仓库**  
  
### 2.3 查看本地库状态

- git status  
  
  任何时候都可以通过 `git status` 命令查看本地库状态  
  
### 2.4 添加至暂存区  

- git add  
  
  `git add .` 将当前目录的所有文件均添加至暂存区  
  `git add <fiename>` 将指定文件 <filename> 添加至暂存区  
  
  - 1. 在 learngit 目录或子目录下，编写 readme.txt 如下：
  ```
  Git is a version control system.
  Git is free software.
  ```
  - 2. 将 readme.txt 文件添加至版本库：  
  ```
  $ git add readme.txt
  ```
  
- 删除暂存区的指定文件  

  `git rm --cached <filename>` 将提交至暂存区的指定文件删除  
  
### 2.5 提交至本地库  
  
- git commit  

  `git commit -m 'log info'` 将暂存区的**所有内容**提交到当前分支，并增加日志信息（log info）  
  `git commit -m 'log info' <filename>` 将暂存区的指定文件 <filename> 提交到当前分支，并增加日志信息（log info）  
  
  ```
  $ git commit -m "wrote a readme file"
  ```

- 查看提交的版本信息  
  
  `git reflog` 从近至远查看日志的信息（版本号缩写且不显示提交人的信息）  
  `git log` 从近至远查看详细日志的信息（版本号不缩写且显示提交人的信息）  
 
### 2.6 版本穿梭  
  
- git diff  

  `git diff`查看文本文件所做的修改  
  ```
  $ git diff readme.txt
  ```
  
- git reset  

  `git reset --hard xxx`将当前版本回退到指定版本 xxx，xxx 可以是 commit id 的前几位也可以用 HEAD 表示：  
  HEAD 表示当前版本，HEAD^ 表示上一个版本，HEAD^^ 表示上上一个版本，HEAD~100 表示前100个版本  
  ```
  $ git reset -- hard HEAD^
  $ git reset -- hard 1094a
  ```
