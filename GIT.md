# GIT

## 简介

​	Git的诞生确实是一个有趣的故事，当年Linus创建了开源的Linux，从此，Linux系统不断发展，现在已经成为最大的服务器系统软件了。

​    但是随着Linux的不断壮大，就需要各种版本控制了，起初Linus带着他的小弟们使用的是BitKeeper(商业版本控制系统),之后呢由于某种原因BitKeeper的公司不让他们使用了，于是Linus自己花了两周时间写出了Git并且开源了(BitKeeper已哭晕在厕所)。

​    之后的岁月里，渐渐有了github,coding等一些可以使用git存储的网站，Git的江湖地位变得无可替代了，Git几乎成了开发者必备的技能。



### Git 的作用

+ 是一个源代码管理工具
+ 让源代码可以被追溯，记录每次变更发生了什么，谁主导这些变化



工作原理：


![image.png](https://upload-images.jianshu.io/upload_images/6784887-d3a98a81a81bd59c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- Workspace:工作区，执行`git add *`命令就把改动提交到了暂存区，执行`git pull`命令将远程仓库的数据拉到当前分支并合并，执行`git checkout [branch-name]`切换分支

- Index:暂存区，执行`git commit -m '说明'` 命令就把改动提交到了仓库区（当前分支）。这里保存了下次将提交的文件列表信息，一般在Git仓库目录中。

- Repository:仓库区（或本地仓库），是对项目的某个版本独立提取出来的内容。这些从Git仓库的压缩数据库中提取出来的文件，放在磁盘上供你使用或修改。执行 `git push origin master` 将本地数据提交到远程仓库，执行 `git clone 地址` 将克隆远程仓库到本地

- Remote:远程仓库，就是类似github，coding，gitee等网站所提供的仓库，用来保存项目的元数据和对象数据库的地方。 这是Git 中最重要的部分，从其它计算机克隆仓库时，拷贝的就是这里的数据。

- 基本的工作流程

  1、在工作目录中修改文件

  2、暂存文件，将文件的快照放入暂存区域

  3、提交文件，找到暂存区域的文件，将快照永久性的存储到Git仓库目录



### Git 术语

| 术语               | 定义                                                         |
| ------------------ | ------------------------------------------------------------ |
| 仓库（Repository） | 一个仓库包括了所有的版本信息、所有的分支和标记信息。在Git中仓库的每份拷贝都是完整的。仓库让你可以从中取得你的工作副本。 |
| 分支（Branches）   | 一个分支意味着一个独立的、拥有自己历史信息的代码线（code line）。你可以从已有的代码中生成一个新的分支，这个分支与剩余的分支完全独立。默认的分支往往是叫master。用户可以选择一个分支，选择一个分支执行命令`git checkout branch`. |
| 标记（Tags）       | 一个标记指的是某个分支某个特定时间点的状态。通过标记，可以很方便的切换到标记时的状态，例如2009年1月25号在testing分支上的代码状态 |
| 提交（Commit）     | 提交代码后，仓库会创建一个新的版本。这个版本可以在后续被重新获得。每次提交都包括作者和提交者，作者和提交者可以是不同的人 |
| 修订（Revision）   | 用来表示代码的一个版本状态。Git通过用SHA1 hash算法表示的id来标识不同的版本。每一个 SHA1 id都是160位长，16进制标识的字符串.。最新的版本可以通过HEAD来获取。之前的版本可以通过"HEAD~1"来获取，以此类推。 |



### 忽略文件

可以配置Git忽略特定的文件或者是文件夹。这些配置都放在`.gitignore`文件中。这个文件可以存在于不同的文件夹中，可以包含不同的文件匹配模式。

**忽略之后的文件或是文件夹，Git就不去提交里面的内容了**

比如`.gitignore`内容可以如下：

```txt
忽略某文件
npm-debug.log
忽略文件夹
dist/
node_modules/
.idea/
```



每次提交的时候Git会忽略空的文件夹，如果想要版本控制包括空文件夹，根据惯例会在空文件夹下放置`.gitkeep`文件。其实对文件名没有特定的要求。一旦一个空文件夹下有文件后，这个文件夹就会在版本控制范围内。



### 配置文件

Git的设置文件为`.gitconfig`，它可以在用户主目录下（全局配置），也可以在项目目录下（项目配置）。

```node
# 显示当前的Git配置
$ git config --list
# 编辑Git配置文件，只是配置用户信息的话直接看下面两行命令即可
$ git config -e [--global]
# 设置提交代码时的用户信息，是否加上全局--global自行决定，一般是直接设置全局的。另外用户邮箱需要注意最好使用gmail,QQ也可以，需要和你远程仓库保持一致不然你的contribution是不会被记录在远程仓库的
$ git config [--global] user.name "[name]"
$ git config [--global] user.email "[email address]"
```



## 基础命令

### 1、配置用户

+ git config --global user.name "自已的名字"
+ git config --global user.email "自已的邮箱地址"

> --global 配置当前用户所有仓库
> --system 配置当前计算机上所有用户的所有仓库

**注：配置用户只需要执行1次，可以重复使用。**



### 2、初始化仓库

在文件夹中执行命令 `git init` ，创建了一个名为 .git 的隐藏目录，这个目录就是存储我们历史版本的仓库，ls -al 可以查看。



### 3、查看文件状态

通过命令 `git status` 可以检测当前仓库文件的状态



### 4、添加文件到暂存区

命令 `git add 文件名/文件路径` 或 -A 代表所有，常使用 `git add .` 代表添加所有

使用此命令后被提交的文件会变成<font color="green">绿色</font>，等待提交，如果配置了.gitignore 文件，在 .gitignore 中的文件不会被提交



### 5、撤销更改

修改文件，再次 `git status` 可以再次查看仓库状态，被修改的文件会被标记为红色。如果想要回到之前的状态，可以使用 `git checkout 文件名` 命令，将暂存区的文件还原到工作区



### 6、提交文件

使用 `git commit -m '备注信息'` 可以将暂存的文件提交到<font color="orange">本地仓库</font>存储。这时再次使用 `git status` 命令会显示 `nothing to commit, working tree clean`



### 7、查看提交历史

使用 `git log` 可以查看提交的历史，黄色的 `commit ab70206749e292e86a11918c032b1d0de5ebc2be` 中后面的一串英文是本次提交的唯一ID，一般称为 SHA值。按 q 键退出



### 8、恢复至某一次提交的状态

通过 SHA值可以回到之前的某一次提交的状态（时光倒流），命令 `git reset --hard SHA值`。这里的SHA值可以仅写前7位

可以使用 `git reflog` 命令打印所有操作记录（包括 reset 事件），可以根据操作前面7位SHA值回退到某一个修改时的状态



## Git 分支

在Git的使用过程中所有的提交（commit）实际上都是在分支（branch）的基础上进行的，当我们在初始化仓库的时候（实际上是产生第1次提交时），Git会默认帮我们创建了一个master的分支，并且有指针（HEAD）指到了末端。

### 1、创建分支

命令 `git branch` 可以查看当前所有分支。使用命令 `git branch 分支名` 可以创建一个分支。新的分支会在当前分支原有历史版本的节点上进行创建，我们称其为子分支。新的子分支会继承父分支的所有提交历史



### 2、切换分支

使用命令 `git checkout 分支名` 可以切换分支



### 3、子分支的修改

修改某一文件，再次提交，这次的提交记录就会保存在新创建的分支上，并且HEAD指针会伴随着新的分支移动。再次切换回 master 分支，之前在分支上的提交记录并没有出现在主分支上。此时，在主分支上发生新的提交或修改事件也不会反映在子分支上，两个分支就完全的撇开了关系。



### 4、合并分支

可以通过命令 `git merge 分支名` 将该分支合并到主分支上，这时如果两者修改了同一文件，需要手动合并冲突。

**注意：这里如果存在冲突可能会进入蓝框，只需要按键盘上的ESC，然后输入 :wq 即可**



### 5、删除分支

使用命令 `git branch -d 分支名` 即可删除相应的分支。



## Github的使用

之前讲的git都是在本地工作，github是一个网站，一个git服务提供商，可以通过git将本地的文件托管在github上面。相当于一个远端仓库。因为可以开源自己的代码与世界上的其它开发者交流，GitHub走出了社交化编程的道路，也被戏称为程序员的同性交友网。因为GitHub访问速度有时比较慢，可以使用码云代替。

使用步骤：

1. 注册

2. 生成密钥 `ssh-keygen -t rsa -C 'youremail@example.com'`
3. 创建仓库，复制项目地址
4. 在本地使用 `git clone 项目地址` 将创建的仓库拉取到本地
   + 在本地做出修改，使用 `git add .` 命令将文件提交
   + 使用 `git commit -m '修改标识'` 将文件提交到暂存区
   + 使用 `git push -u origin master` 将本地项目提交到GitHub仓库主分支上，首次推送加上 -u 之后就可以不加了。master 是远程的分支，如果你创建了分支，要往分支上提交，那么就需要将master改成分支的名字
5. 如果本地已有 git 项目
   + `git remote add origin xxxgit@xxx.git` 添加远程仓库地址
   + `git push -u origin master` 将本地项目以流的形式提交到GitHub仓库主分支上
   + 如果是合作开发，在 push 之前需要先执行 `git pull origin master` 将远端的更新获取到本地，然后修改冲突文件，在重新提交到暂存区，最后 push 到远端

6. 更新仓库



### 示例

假定我们创建好了一个远程仓库地址为：https://coding.net/u/zhangguo5/p/project7/git，现在我们在本地创建一个项目并同步到远程仓库中。

1）、创建文件添加到暂存区

![image](https://upload-images.jianshu.io/upload_images/6784887-94635357f0041ae6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2）、提交到本地仓库

![image](https://upload-images.jianshu.io/upload_images/6784887-d78983bd58f0fc0b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3）、提交到远程仓库

添加远程主机地址：

![image](https://upload-images.jianshu.io/upload_images/6784887-bb9a661846240b43.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

推送文件：

![image](https://upload-images.jianshu.io/upload_images/6784887-eb2426387b8dfb8e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



## Git 常用命令集合

### 基础命令

```
# 添加指定文件到暂存区
$ git add [file1] [file2] ...
# 添加指定目录到暂存区，包括子目录
$ git add [dir]
# 添加当前目录的所有文件到暂存区
$ git add *
# 添加每个变化前，都会要求确认
对于同一个文件的多处变化，可以实现分次提交
$ git add -p
# 删除工作区文件，并且将这次删除放入暂存区
$ git rm [file1] [file2] ...
# 停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached [file]
# 改名文件，并且将这个改名放入暂存区
$ git mv [file-original] [file-renamed]
# 提交暂存区到仓库区
$ git commit -m [message]
# 提交暂存区的指定文件到仓库区
$ git commit [file1] [file2] ... -m [message]
# 提交工作区自上次commit之后的变化，直接到仓库区
$ git commit -a
# 提交时显示所有diff信息
$ git commit -v
# 使用一次新的commit，替代上一次提交
如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]
# 重做上一次commit，并包括指定文件的新变化
$ git commit --amend [file1] [file2] ...
# 提交更改到远程仓库
$ git push origin master
# 拉取远程更改到本地仓库默认自动合并
$ git pull origin master
```



### 分支命令

> 但如果是多人协作的话，git的魅力就开始提现出来了，每个人有自己的一个分支，各自在自己的分支上工作互不干扰。具体的看这：[Git教程-创建合并分支](https://link.juejin.im/?target=http%3A%2F%2Fwww.liaoxuefeng.com%2Fwiki%2F0013739516305929606dd18361248578c67b8067c8c017b000%2F001375840038939c291467cc7c747b1810aab2fb8863508000)

```
# 列出所有本地分支
$ git branch
# 列出所有远程分支
$ git branch -r
# 列出所有本地分支和远程分支
$ git branch -a
# 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]
# 新建一个分支，并切换到该分支
$ git checkout -b [branch]
# 新建一个分支，指向指定commit
$ git branch [branch] [commit]
# 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch] [remote-branch]
# 切换到指定分支，并更新工作区
$ git checkout [branch-name]
# 切换到上一个分支
$ git checkout -
# 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]
# 合并指定分支到当前分支，如果有冲突需要手动合并冲突（就是手动编辑文件保存咯），然后add,commit再提交
$ git merge [branch]
# 选择一个commit，合并进当前分支
$ git cherry-pick [commit]
# 删除分支
$ git branch -d [branch-name]
# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
```



### 标签

> 标签的作用主要是用来做版本回退的，关于版本回退，这也是Git的亮点之一，起到了后悔药的功能

```
# 列出所有tag
$ git tag
# 新建一个tag在当前commit
$ git tag [tag]
# 新建一个tag在指定commit
$ git tag [tag] [commit]
# 删除本地tag
$ git tag -d [tag]
# 删除远程tag
$ git push origin :refs/tags/[tagName]
# 查看tag信息
$ git show [tag]
# 提交指定tag
$ git push [remote] [tag]
# 提交所有tag
$ git push [remote] --tags
# 新建一个分支，指向某个tag
$ git checkout -b [branch] [tag]
```



### 后悔药

>想一下在你写完N个文件代码后，commit到了本地仓库，突然发现出现重大bug导致整个应用崩溃了！Git给了我们吃后悔药的机会：

```
# 恢复暂存区的指定文件到工作区
$ git checkout [file]
# 恢复某个commit的指定文件到暂存区和工作区
$ git checkout [commit] [file]
# 恢复暂存区的所有文件到工作区
$ git checkout .
# 回退到上一个版本，在Git中，用HEAD表示当前版本
$ git reset --hard HEAD^
# 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
$ git reset [file]
# 重置暂存区与工作区，与上一次commit保持一致
$ git reset --hard
# 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
$ git reset [commit]
# 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
$ git reset --hard [commit]
# 重置当前HEAD为指定commit，但保持暂存区和工作区不变
$ git reset --keep [commit]
# 新建一个commit，用来撤销指定commit
# 后者的所有变化都将被前者抵消，并且应用到当前分支
$ git revert [commit]
# 暂时将未提交的变化移除，稍后再移入
$ git stash
$ git stash pop
```



### 查看文件信息

```
# 显示当前分支的版本历史
$ git log
# 显示commit历史，以及每次commit发生变更的文件
$ git log --stat
# 搜索提交历史，根据关键词
$ git log -S [keyword]
# 显示某个commit之后的所有变动，每个commit占据一行
$ git log [tag] HEAD --pretty=format:%s
# 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
$ git log [tag] HEAD --grep feature
# 显示某个文件的版本历史，包括文件改名
$ git log --follow [file]
$ git whatchanged [file]
# 显示指定文件相关的每一次diff
$ git log -p [file]
# 显示过去5次提交
$ git log -5 --pretty --oneline
# 显示所有提交过的用户，按提交次数排序
$ git shortlog -sn
# 显示指定文件是什么人在什么时间修改过
$ git blame [file]
# 显示暂存区和工作区的差异
$ git diff
# 显示暂存区和上一个commit的差异
$ git diff --cached [file]
# 显示工作区与当前分支最新commit之间的差异
$ git diff HEAD
# 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]
# 显示今天你写了多少行代码
$ git diff --shortstat "@{0 day ago}"
# 显示某次提交的元数据和内容变化
$ git show [commit]
# 显示某次提交发生变化的文件
$ git show --name-only [commit]
# 显示某次提交时，某个文件的内容
$ git show [commit]:[filename]
```



### 其它命令

```
# git blame清楚的记录某个文件的更改历史和更改人，简直是查看背锅人的利器，filepath是需要查看的文件路径
$ git blame filepath
```



## 搭建个人博客

### 安装hexo

`npm install -g hexo-cli`



### 第一步：创建仓库

进入github/bitbucket（后续都以github为例）新建repo，这里要注意repo的名字一定要满足`your Account Name`/github.io。如果是bitbucket那就是`your Account Name`/bitbucket.io，因为只有这样的仓库名称最后才能以静态页面展示。如图：XXX的内容一定要与红色的框里的文本一致。



![img](https://user-gold-cdn.xitu.io/2018/2/7/1616f33f4f1658c0?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)



### 第二步：创建本地文件夹

创建文件夹之后CD到你创建的文件夹中执行hexo的初始化相关命令

```
$ hexo init
$ npm install
```

执行完毕之后你的文件夹里就有内容了，标准的目录结构是这样（只列出几个必要的文件夹及其子目录）

```
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

+ config.yml： 其中我们以后的大部分操作都会在`_config.yml`中进行，这个文件是我们的站点的 [配置](https://hexo.io/zh-cn/docs/configuration) 文件。

+ scaffolds： 模板文件，规定了我们创建一篇文章的时候最开始的样子。

+ source： 可以暂时的理解成我们文章的存放处。除 `_posts` 文件夹之外，开头命名为 `_` (下划线)的文件 / 文件夹和隐藏的文件将会被忽略。Markdown 和 HTML 文件会被解析并放到 `public` 文件夹，而其他文件会被拷贝过去。

+ themes： 主题文件。Hexo 会根据主题来生成静态页面。



### 第三步：部署到Git

修改我们的的站点配置文件`_config.yml`中如下字段

```
deploy:
  type: git
  repo: XXXXX
  branch: master
```

其中：

- `type`值对应的是你所部署的的服务器类型，我们这里填写git就可以
- `repo`是你的仓库地址，也就是仓库克隆的地址，推荐用https的链接
- `branch`不写默认是master，通常我们写成master就可以



**以上配置完成后保存 然后回到终端执行 `npm install hexo-deployer-git --save` 安装一个插件，这样才能将你写好的文章部署到github服务器上并让别人浏览到。**

安装完成后在终端中依次执行如下代码

+ `hexo clean`  清理缓存

+ `hexo generate` 进行渲染 简写 `hexo g`

+ `hexo server` 部署到本地(调试使用) 简写 `hexo s`。然后浏览器输入 `http://localhost:4000` 就可以看到你博客的效果啦，不过这是本地调试用，其他人是看不到的。(调试完毕后记得 `control + C` 关闭本地端口，不然下次就进不去啦)

+ 调试完毕后使用 `hexo deploy` 简写为 `hexo d`来部署到git服务器。

  执行完以上操作后打开浏览器地址了输入`http://你github名字.github.io`就可以看看到效果啦，这回是所有人都能看到的，用手机也可以。至此第三步已经完成,最终的结果如下图：

![img](https://user-gold-cdn.xitu.io/2018/2/7/1616f33f7d058b60?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)



### 第四步：写文章

使用如下命令 `hexo new post “文章名字”` 就可新建文章啦，建立好的文章在 `source/_posts` 中，你可以用markdown语法编辑内容就可以。编辑完成后执行第三步中终端的操作就可以啦，刷新下浏览器就可看到你的新文章啦。如下图:


![img](https://user-gold-cdn.xitu.io/2018/2/7/1616f33f8203089d?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)