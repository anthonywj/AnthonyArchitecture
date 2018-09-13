# AnthonyArchitecture
common tools


#首次提交项目到github
1.在当前项目下使用git命令初始化该目录
git init
2.在GitHub上创建和本地项目的同名分支
3.使用命令关联本地库和github远程库
$ git remote add origin https://github.com/anthonywj/AnthonyArchitecture.git
4.将本地文件添加到本地缓存库
git add .
5.讲所有文件提交到本地库
git commit -m "first commit"
6.合并代码（远程库有加了个readme.rmd)
git pull--rebase origin master
7.提交本地到远程库
$ git push -u origin master //首次提交
$ git push origin master //非首次提交

