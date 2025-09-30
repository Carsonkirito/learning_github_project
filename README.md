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

## 上传项目
1.新建仓库，名称用英文简介用中文方便搜索，并钩上readme  

2.在项目所在位置右键打开open-git-bash-here  

3.输入<ins>git init</ins>，初始化git  

4.输入<ins>git add .</ins>，将该文件夹内所有文件添加至暂存区  

4.1输入<ins>git status</ins>，可查看暂存区文件状态  

5.确认无误后输入<ins>git commit -m "任意字符"</ins>，将暂存区文件正式提交  

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
git diff            # 查看差异
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
git branch -d old-branch # 删除分支
```
🆘 获取帮助
```bash
git help <command>      # 查看具体命令帮助
git help -a             # 列出所有子命令
git help -g             # 列出概念指南
git help git            # Git 系统概述
```
