# 入职第二天
## 1安装配置git
直接终端输入git，如果未安装将会出现安装提示。
### git基本命令：
#### 本地
1. git init   -------将一个目录进行初始化变成git可以管理的目录
2. git add '你想要add的文件名称' ------- 将文件添加到本地仓库
3. git commit -m '本次提交的说明' -------  将文件提交到本地仓库 -m 后面跟的是本次提交的说明，务必添加
#### 远程
1. git remote add '远程仓库的名字' git@github.com:'自己的git账户名称'/'仓库名称'.git ----将本地仓库和远程仓库关联
2. git push -u '远程仓库名称' master --------将本地仓库内容推送到远程仓库
3. git clone '项目git链接' ------从远程clone一个本地库
4. git pull ------将远程仓库的修改合并到当前分支
#### 分支
1. git checkout -b dev --------创建一个dev分支,并切换到dev分支
2. git branch dev --------创建分支
3. git checkout dev -------切换分支
4. git branch --------查看当前分支
5. 把dev分支的工作结果合并到master分支上 
* 首先需要切换回master分支  git checkout master
* git merge dev 合并dev分支到当前分支
* git branch -d dev 删除dev分支   
## 2安装配置maven
先下载maven安装包。解压下载的安装包到某个目录
将这个目录下的bin目录添加到PATH中。
例如:export PATH=/解压到的那个目录/apache-maven-版本号-/bin:$PATH。
1. 执行mvn -v查看是否安装成功。
2. mvn compile 编译源代码
3. mvn test-compile 编译测试代码
4. mvn test 运行测试
5. mvn package 打包
6. mvn install 将项目安装到本地仓库，安装jar包
7. mvn clean 清除产生的项目
## 3安装idea
访问intellij idea官网下载就可以啦。下载完成直接安装便可
## 使用idea新建一个项目，并提交到gitHub
1. idea新建SpringBoot项目。
2. github上新建一个仓库。
3. create git repository--add--commit--push
4. gitHub项目地址。https://github.com/Notcontrol/demo



