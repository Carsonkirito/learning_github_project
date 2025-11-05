# github_study_project
个人学习github各功能所用的测试项目  
此文档同时用于学习README文档的编写

## 功能
fork:将别人的项目仓库复制到自己的目录  

star:为项目点赞

## 在git工具中登录及配置账号与密码
```bash
git config --global user.email "you@example.com"  
git config --global user.name "Your Name"
```
## 使用Git 管理项目
### 第一步 创建一个本地的Git项目仓库
1、直接clone别人的仓库：  
在Github上点击Code复制项目地址（结尾有.git后缀），执行以下命令Git就会把整个项目仓库直接下载下来
```bash
git clone <url>      # 克隆远程仓库到本地
```
2、在电脑上新建一个文件夹：  
在文件夹内使用以下命令会自动创建一个<ins>.git</ins>文件夹，这就是代码仓库（别乱动里面东西）
```bash
git init
```
其余参考上传项目部分
## 上传项目
1.新建仓库，名称用英文简介用中文方便搜索，并钩上readme  
2.在项目所在位置右键打开open-git-bash-here  
3.初始化git
```bash
git init
```
4.将该文件夹内所有文件添加至暂存区  
```bash
git add .
```
查看暂存区文件状态
```bash
git status
```
5.确认无误后将暂存区文件正式提交
```bash
git commit -m "任意字符"
# 任意字符为提交的备注，会显示在log中
```
到此，我们将文件备份到了本地仓库

## 链接github仓库和本地仓库
1.运行以下代码  
```bash
git remote add origin https://github.com/Carsonkirito/learning_github_project.git  
git branch -M main  
git push -u origin main
# 此步骤可能需要挂梯  
```
main改为master，以匹配主分支名称  
此文档上传的C++OpenCV项目在master分支下，以后上传默认使用main分支

## 使用 Git LFS 以上传超过50MB的文件（ddl等）

### 步骤 1：下载并安装 Git LFS 
```bash
git lfs install  
```
### 步骤 2：跟踪 DLL 文件或特定文件
```bash
git lfs track "*.dll"
```
### 或者只跟踪这个特定文件
```bash
git lfs track "opencv_world480.dll"
```
### 步骤 3：检查生成的 .gitattributes 文件
```bash
cat .gitattributes  
```
应该看到：<ins>opencv_world480.dll filter=lfs diff=lfs merge=lfs -text</ins>  

### 步骤 4：重新添加并提交文件
从缓存中移除大文件（如果已添加）  
```bash
git rm --cached opencv_world480.dll
```
重新添加文件（现在会通过 LFS 处理）  
```bash
git add opencv_world480.dll  
git add .gitattributes  
```
提交更改  
```bash
git commit -m "chore: add opencv_world480.dll via Git LFS"  
```
推送到远程  
```bash
git push origin master
```

## Git 命令分类详解
### 🏁 初始化工作区
```bash
git clone <url>      # 克隆远程仓库到本地
git init            # 初始化新的 Git 仓库
```
### 📁 处理当前变更
```bash
git add <file>      # 添加文件到暂存区
git mv <file>       # 移动或重命名文件
git restore <file>  # 恢复工作区文件
git rm <file>       # 删除文件
```
### 🔍 查看历史和状态
```bash
git status          # 查看工作区状态
git log             # 查看提交历史
git log --stat      # 查看每次提交时都修改了哪些文件,可以得到commit id
git diff            # 查看差异，后面可以加上commit id
git show <commit>   # 显示特定提交详情
git grep <pattern>  # 在代码中搜索
git bisect          # 二分查找定位 Bug
```
### 🌱 管理历史记录
```bash
git commit          # 提交更改
git branch          # 管理分支
git switch          # 切换分支
git merge           # 合并分支
git rebase          # 变基操作
git reset           # 重置提交
git tag             # 管理标签
```
### 🚢 代码回溯
```bash
# 执行两条任一，将代码回退到指定的节点commit id
git reset --hard [commit id]
git checkout [commit id]
```
### 👥 协作命令
```bash
git fetch           # 下载远程更新
git pull            # 拉取并合并远程更改
git push            # 推送本地提交到远程
```
### 💡 常用命令组合示例
日常开发流程
```bash
# 1. 开始新功能
git clone https://github.com/user/repo.git
git switch -c new-feature

# 2. 开发并提交
git add .
git commit -m "添加新功能"
git push origin new-feature

# 3. 更新代码
git pull origin main
```
查看状态和信息
```bash
git status          # 当前状态
git log --oneline   # 简洁提交历史
git diff            # 未暂存的更改
```
分支管理
```bash
git branch          # 查看分支
git switch main     # 切换到主分支
git branch -b develop    # 创建新分支并使用
git branch -d old-branch # 删除分支
```
🆘 获取帮助
```bash
git help <command>      # 查看具体命令帮助
git help -a             # 列出所有子命令
git help -g             # 列出概念指南
git help git            # Git 系统概述
```
## Git的分支
同一程序的不同版本，功能略有不同，又可以互相合并  
现在基本使用main作为主分支，用来保存测试稳定的代码  
开发新功能时一般会在main的基础上复制出一个develop分支，并在这个分支上进行开发
```bash
git branch -b develop    # 创建新分支
```
发布时再把develop分支的代码合并到main上  
```bash
# 提交代码
git add .
git commit -m "新增xx功能"
# 切换到主分支
git checkout main
# 合并
git merge develop
```
## 云服务器
### 1. GitHub Pages (静态网站托管)
这是 GitHub 提供的最主要的“云服务器”功能，但它有一个关键限制：只支持静态网站  
GitHub Pages 在服务器端渲染的是静态文件（如 HTML, CSS, JavaScript, 图片等）  
[参考链接]([https://github.com](https://blog.csdn.net/m0_62979475/article/details/143818553))
### 2. GitHub Codespaces (云端开发环境)
这是一个完全不同的、功能强大的服务   
GitHub Codespaces 为你提供一个完整的、基于云的 Visual Studio Code 开发环境。它本质上是一个配置好的 Linux 虚拟机（容器）  
你可以在 Codespaces 环境中安装和配置任何你需要的软件  
Codespaces 是一个 开发环境，而不是一个 生产环境。你可以在这里开发和测试你的 PHP 应用，但它通常不用于对外提供公开访问的网站服务（虽然它提供了一个临时的公共访问URL用于测试）  
