# Git 学习笔记
## 2026-09-19
### 初始化
- git config --global user.name "Your Name"：设置全局用户名
- git config --global user.email email@email.com：设置全局邮箱
- git config --global credential.helper store：保存凭证

### 创建仓库
- git init <project-name>：创建本地仓库
- git clone <url>：下载远程仓库

### Git的四个区域
- 工作区（Working Directory）：电脑里能看到的目录
- 暂存区（Stage/Index）：存放待提交改动，又叫索引
- 本地仓库（Repository）：本地.git版本库
- 远程仓库（Remote）：托管在服务器上的仓库

### Git的三种状态
- 已修改（Modified）：修改文件，未放入暂存区
- 已暂存（Staged）：修改放入暂存区
- 已提交（Committed）：暂存内容提交到本地仓库

### 基本概念
- main：默认主分支
- origin：默认远程仓库
- HEAD：指向当前分支的指针
- HEAD~1：上一个版本
- HEAD~4：上4个版本

### 特殊文件
- .git：Git仓库元数据和对象数据库
- .gitignore：忽略不需要提交的文件
- .gitattributes：指定文件属性
- .gitkeep：保留空目录提交
- .gitmodules：记录子模块信息
- .gitconfig：仓库配置信息

### 添加和提交
- git add <file>：添加单个文件到暂存区
- git add .：添加所有文件到暂存区
- git commit -m "message"：提交暂存区文件到本地仓库
- git commit -am "message"：提交所有已修改文件

### 分支
- git branch：查看本地分支，-r查看远程分支，-a查看所有分支
- git branch <branch-name>：创建新分支
- git checkout <branch-name>：切换分支
- git checkout -b <branch-name>：新建并切换分支
- git branch -d <branch-name>：删除已合并分支
- git branch -D <branch-name>：强制删除分支
- git tag <tag-name>：给当前提交打标签

### 合并分支
- git merge --no-ff -m "message" <branch-name>：合并分支，保留分支历史
- git merge --squash <branch-name>：合并分支，压缩所有提交为一个

### Rebase
- git checkout dev：切换到dev分支
- git rebase main：把dev分支rebase到main

### 撤销
- git mv <file> <new-file>：移动/重命名文件
- git rm <file>：删除文件并移除跟踪
- git rm --cached <file>：仅从暂存区删除，保留本地文件
- git checkout <file> <commit-id>：恢复文件到指定提交版本
- git revert <commit-id>：新建提交，撤销指定提交
- git reset --mixed <commit-id>：重置HEAD，重置暂存区
- git restore --staged <file>：撤销暂存，保留本地修改

### 查看
- git status：查看工作区/暂存区状态
- git log --oneline：简洁查看提交历史
- git diff：查看暂存区文件改动
- git diff <commit-id> <commit-id>：查看两个提交差异

### Stash
- git stash save "message"：储藏当前工作现场
- git stash list：查看所有stash记录
- git stash pop：恢复最近stash并删除记录
- git stash apply stash@{2}：恢复指定stash，不删除记录
- git stash apply：恢复最近stash，不删除记录
- git stash drop stash@{2}：删除指定stash
- git stash clear：清空所有stash

### 远程仓库
- git remote add <remote-name> <remote-url>：添加远程仓库
- git remote -v：查看远程仓库信息
- git remote rm <remote-name>：删除远程仓库
- git remote rename <old-name> <new-name>：重命名远程仓库
- git pull <remote-name> <branch-name>：拉取远程代码并合并
- git pull：拉取origin当前分支代码并合并
- git pull --rebase：拉取远程代码，使用rebase合并
- git push <remote-name> <branch-name>：推送本地分支到远程
- git fetch <remote-name>：拉取远程所有分支
- git branch -r：查看远程分支
- git fetch <remote-name> <branch-name>：拉取指定远程分支

### Git Flow
- 主分支（main/master）：项目稳定版本
- 开发分支（develop）：开发新功能
- 功能分支（feature）：开发单独功能
- 发布分支（release）：准备版本发布
- 修补分支（hotfix）：线上紧急bug修复

### Linux命令
- ls：list 的缩写，列出当前文件夹里所有文件/目录（Git Bash 命令，不是git命令）
- ls -a：列出全部文件，包含隐藏文件（可以看到.git文件夹）
- ls -l：列出文件详细信息（权限、大小、修改时间）
- ls -la：列出全部文件+详细信息，最常用