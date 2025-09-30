# learning_github_project
个人学习github各功能所用的测试项目

## 功能
fork:将别人的项目仓库复制到自己的目录  

star:为项目点赞

## 在git工具中登录及配置账号与密码
git config --global user.email "you@example.com"  

git config --global user.name "Your Name"

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

git remote add origin https://github.com/Carsonkirito/learning_github_project.git  

git branch -M master  

git push -u origin master//此步骤可能需要挂梯  

//main改为master，以匹配主分支名称  

## 使用 Git LFS 以上传超过50MB的文件（ddl等）

### 步骤 1：下载并安装 Git LFS  
git lfs install  

### 步骤 2：跟踪 DLL 文件或特定文件
git lfs track "*.dll"
### 或者只跟踪这个特定文件
git lfs track "opencv_world480.dll"  

### 步骤 3：检查生成的 .gitattributes 文件
cat .gitattributes  

应该看到：opencv_world480.dll filter=lfs diff=lfs merge=lfs -text  

### 步骤 4：重新添加并提交文件
从缓存中移除大文件（如果已添加）  

git rm --cached opencv_world480.dll

重新添加文件（现在会通过 LFS 处理）  

git add opencv_world480.dll  

git add .gitattributes  

提交更改  

git commit -m "chore: add opencv_world480.dll via Git LFS"  

推送到远程  

git push origin master

```bash
npm install
npm start
```
