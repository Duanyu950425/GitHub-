GitHub基础操作步骤
============

一、GitHub与git的一些基础知识
-------------------

### 1.什么是GitHub？ ###

&emsp;GitHub是一个面向开源及私有软件项目的托管平台，因为只支持git 作为唯一的版本库格式进行托管，故名GitHub。

&emsp;GitHub于2008年4月10日正式上线，除了Git代码仓库托管及基本的 Web管理界面以外，还提供了订阅、讨论组、文本渲染、在线文件编辑器、协作图谱（报表）、代码片段分享（Gist）等功能。目前，其注册用户已经超过350万，托管版本数量也是非常之多，其中不乏知名开源项目 Ruby on Rails、jQuery、python 等。

&emsp;2018年6月4日，微软宣布，通过75亿美元的股票交易收购代码托管平台GitHub。

&emsp;2019年05月，《个人电脑杂志》网站报道，GitHub正遭到一名黑客的入侵。据称，这名黑客先擦除代码资源库，然后向用户索要赎金，作为恢复数据的交换。

### 2.什么是git？ ###

&emsp;git是一个开源的分布式版本控制系统，可以有效、高速地处理从很小到非常大的项目版本管理。Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。

### 3.git与GitHub之间的关系？ ###

&emsp;git是软件,它可在本地建立仓库,你写的代码的各个版本都可以存着；

&emsp;github是网上仓库,你写的代码的各个版本都可以存着。

#### 1）git ####

&emsp;是一个版本管理工具，是可以在你电脑不联网的情况下，只在本地使用的一个版本管理工具，其作用就是可以让你更好的管理你的程序，比如你原来提交过的内容，以后虽然修改了，但是通过git这个工具，可以把你原来提交的内容重现出来，这样对于你后来才意识到的一些错误的更改，可以进行还原。

#### 2）GitHub ####

&emsp;关于github，这是一个网站，就是每个程序员自己写的程序，可以在github上建立一个网上的仓库，你每次提交的时候可以把代码提交到网上，这样你的每次提交，别人也都可以看到你的代码，同时别人也可以帮你修改你的代码，这种开源的方式非常方便程序员之间的交流和学习。

&emsp;总结来说，git可以认为是一个软件，能够帮你更好的写程序，github则是一个网站，这个网站可以帮助程序员之间互相交流和学习。

二、GitHub教程
----------

### 1.注册GitHub账户以及创建仓库 ###

&emsp;登录GitHub官网[https://github.com/](https://github.com/)注册，登录成功后，点击Create a New Repository，创建新仓库。

### 2.下载安装git ###

&emsp;安装好后，点击 "Git Bash"图标，配置Git。

### 3.配置Git ###

1）首先在本地创建ssh key；

	$ssh-keyfen -t rsa -C "your_email@youremail.com"

&emsp;your_email@youremail.com即为GitHub上注册的邮箱，之后会要求确认路径和输入密码，无需确认，一路回车。成功的话会在~/下生成.ssh文件夹，

	$ cd ~/
	$ cd ./.ssh
	$ ls -al
    total 21
    drwxr-xr-x 1 12201 1976090 5月   7 10:05 ./
    drwxr-xr-x 1 12201 1976090 5月   7 17:58 ../
    -rw-r--r-- 1 12201 197609 1831 5月   8 11:54 id_rsa
    -rw-r--r-- 1 12201 197609  403 5月   8 11:54 id_rsa.pub
    -rw-r--r-- 1 12201 197609 1197 5月   7 14:23 known_hosts

打开id_rsa.pub,复制里面的key。

	$ cat id_rsa.pub

&emsp;回到GitHub上，进入Account Setting（账户配置），选择SSH keys，点击 New SSH key。随意给其起个title，将刚刚复制的key粘贴进去，点击Add SSH key。

&emsp;为了验证是否成功，在git bash下输入：

	$ssh -T git@github.com

&emsp;若出现：You've successfully authenticated, but GitHub does not provide shell access 。这就表示已成功连上github。

&emsp;接下来设置username和email，

	$git config --global user.name "your name"
	$git config --global user.email "your _email@youremail.com"


&emsp;查看配置信息

	$git config --list

4.建立本地仓库
--------

### 1）创建一个文件 ###

&emsp;在本地找到一个空的目录，新建一个仓库：

	$mkdir <仓库名>

&emsp;进入仓库

	$cd ./<仓库名>

&emsp;创建一个README.md的文件，也可以之间到目录下新建一个文件而不是用命令行

	$echo "文件内容" >> README.md

&emsp;初始化一个空目录

	$git init

&emsp;暂存文件

	$git add README.md

&emsp;提交文件

	$git commit -m "提交说明"

&emsp;查看查看版本库的状态

	$git status

&emsp;此时在本地仓库就创建了一个文件。

### 2）对已创建的文件进行修改 ###

&emsp;例如上述创建的README.md文件，我们想修改其中的内容，可采用vi命令对其进行修改；也可以之间到目录下打开README.md文件（我使用的是MarkdownPad编辑.md格式的 文件）对其内容进行修改。

	$vi README.md

&emsp;此时我们在git status就会发现README.md文件修改了还没有暂存提交。

&emsp;如果我们想查看文件被修改了哪些地方，就可以使用如下命令进行查看

	$git diff <文件名>

&emsp;修改成功后，我们依旧采取暂存提交命令对其进行提交到本地版本库。

### 3）版本回滚 ###

&emsp;如果我们对版本修改了多次，但想回滚到之前某一次的版本，或者误删了一些文件，想回到上一个commit中去。由于git版本控制中，所有的操作都是有历史记录的，我们可以用git log命令查看一下

![](https://i.imgur.com/ZnDRto7.png)

&emsp;如果内容过多，可使用命令查看

	$ git log --pretty=oneline

&emsp;我们所看到的的一大串数字就是commit id。git当前是哪个版本，在git中就用HEAD表示当前版本。我们有了commit id就可以回滚到之前的版本中去，复制你想要回滚到的版本id，使用命令 git reset

	$git reset --hard commit_id

&emsp;或者，在git中HEAD表示当前版本，HEAD^表示上一版本，HEAD^^表示上两个版本，以此类推。想要回到第几个版本，就按几个^。

	$git reset --hard HEAD^^

&emsp;在查看一下文件，就会发现版本回滚了。

&emsp;但是我们版本回滚之后，会发现修改少了一个版本，也就是最后提交的版本不见了。我们可以使用命令

	$git reflog

来查找版本。

- 删除文件

&emsp;删除文件使用rm命令或者直接在目录中删除掉，

	$git rm -rf <文件名>

如果确定删除该文件，则暂存提交；

如果删错了，可以使用命令git log或git reflog版本回滚。

5.添加远程连接
--------

&emsp;将本地仓库上传至GitHub：

	$git remote add origin git@github.com:yourName/yourRepo.git
	$git push -u origin master

6.克隆仓库
------

克隆远端服务器上的仓库：

	$ git clone git@github.com:Duanyu950425/MySQL_studying.git

&emsp;进入该仓库，可以将远程仓库中的文件进行修改完善，也可以添加新的文件等。修改或添加完成后，要暂存提交，并上传至远程仓库。

例如：

进入MySQL_studying仓库：

	$ cd ./MySQL_studying/

查看仓库文件，使用命令`ls`

对文件进行修改完善或是添加文件，随后
	
	$git add README.md
	$git commit -m "说明"
	$ git clone git@github.com:Duanyu950425/MySQL_studying.git
	$git push -u origin master

登录GitHub刷新后，就会有新的文件添加至仓库。