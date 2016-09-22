# GIT的一些总结

##git初始
- 添加一个远程的repository(这个托管网络的rep创建就不在这里一一赘述了)
``git remote add git@github.com:用户名/远程的rep名.git``

##从远程仓库clone一个本地库
``git clone git@github.com:用户名/远程rep名.git``就会从远程库clone一个工程到本地目录下。

##分支变动管理
- ``git diff HEAD -- 文件名``可以查看工作区里面的文件与版本库中有什么区别
- ``git log``查看一下我们所有的更改信息。
- ``git reset --hard 在log中找到的你想回退的变动``回退到固定版本
- ``git reflog``其中记录了你``git``所有的操作，这样子你就可以找到所有版本，你就可以通过上一条命令跳到所有你trak过的变动。
- ``git checkout -- 文件名``这个是让你工作区里面的文件与库文件保持一致，变相舍弃了本地你所有的更改。
- ``git reset HEAD 文件名``撤销当前暂存区的修改，工作区修改不变。

##提交变动文件到远程库
``git push -u origin master``将master（本地）提交到origin（远程）上去。

##远程库的管理
- ``git remote -v``查看远程库的信息
- 在多人协作开发的时候``git push``之前一定要``git pull``拿到别人的变动,如有冲突解决。再提交。
- ``git checkout -b 分支名 origin(远程主分支名，对应的是你本地master分支)/分支名``本地创建和远端一样的分支
- 建立本地远程之间的分支关联``git branch --set-upstream branch-name origin/branch-name``;

##分支的管理
- 分支的管理``git branch``查看当前的分支状态； ``git checkout -b 分支名``创建一个分支；``git checkout 分支名``转换分支;
- ``git pull``本地与远程文件统一(远程 --> 本地)如果你本地落后远程，必须用pull。如果你本地超前远程,必须用push。
- 分支提交冲突``git status``查看冲突的状态,手动解决冲突。再次提交变动。
- 带参数的``git-log``
``git log --graph --pretty=oneline --abbrev-commit``
- 快速合并分支
``git merge 分支名``将该分支合并到当前的分支上去。
- 禁用快速合并
``git merge --no-ff -m"你的自定义注释" 分支名``这个好处就是可以自定义一个分支合并的注释出来，方便后期的维护更新。
- Bug分支的使用
``git stash``保持当前工作场景。主要针对那些未提交的更改。
``git stash list``可以查看当时的工作现场
``git stash apply``恢复工作现场，stash内容并不删除，如果想删除需要``git stash drop``来删除
``git stash pop``恢复工作现场后，把``stash``内容也删除了。

##版本管理
- 因为``commit id``是一串字符串不是很友好，我们就引入了tag版本作为关联，``git tag v1.0 commitID``给当前命名为commitID的分支添加一个版本号
- ``git tag -a <tagname> -m "注释信息"``指定标签信息。

##添加忽略文件的教程
- 创建一个``.gitignore``文件，将你想忽略的文件格式放入这个文件中。这里有个实例文件参考：

````
<span style="font-size: small;"># Compiled source #
###################
*.com
*.class
*.dll
*.exe
*.o
*.so

# Packages #
############
# it's better to unpack these files and commit the raw source
# git has its own built in compression methods
*.7z
*.dmg
*.gz
*.iso
*.jar
*.rar
*.tar
*.zip

# Logs and databases #
######################
*.log
*.sql
*.sqlite

# OS generated files #
######################
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
Icon?
ehthumbs.db
Thumbs.db
</span>
````
- 首先要利用``git rm --cached filename``先将已经track在git中的文件从索引端移除掉。
- 然后再将``.gitignore``文件提交git。
- 打完收工。

##配置别名
- 常常因为git中的一些命令行太长不好记而烦恼，``git config --global alias.别名 你要替换的命令``
- 一个比较好玩的配置：

````
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
````
- ``--global``针对当前用户，不加只对当前仓库起作用。
- 这些别动都在``.git/config``文件中可以找到。如果要删除别名，直接删除文件中对应行就可以了。

##搭建Git服务器
可以参考大神的教程：http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137583770360579bc4b458f044ce7afed3df579123eca000


