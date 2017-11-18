# Git学习记录


[toc]

-------------------

##一、Git是什么
Git是目前世界上最先进的分布式版本控制系统。

## 二、SVN和Git的区别

###SVN
SVN是集中式控制系统，版本库存放在中央服务器。编辑时，在本地机器上进行，每次工作前，需要从服务器上获取最新版，进行工作。故而，需在网络环境下进行工作。
###Git
Git是分布式控制系统，不需要中央服务器，每个人的电脑都是一个完整的版本库。故而，每个人的机器上都有完整的版本库，工作时，也就可以脱离网络环境。多人协作时，只需将修改推送给对方，即可关注对方的改动。

##三、Git和GitHub的关系
Git是免费开源的分布式版本控制系统，而GitHub是用Git做版本控制的代码托管平台。
![关系图](http://img.blog.csdn.net/20171117104714099?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)


##四、安装Git
下载msysGit.exe，并安装。
安装成功后，可在开始菜单中，找到Git-->GitBash
因为Git是分布式的版本控制系统，故而需要填写用户名和邮箱作为标识。
![设置用户名邮箱](http://img.blog.csdn.net/20171117133723250?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
git config  --global 参数，有了这个参数，表示当前机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定的不同的用户名和邮箱。

##五、基本操作
###创建版本库

**什么是版本库？**
       版本库又名仓库，英文名repository,可以简单的理解为一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改，删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻还可以将文件”还原”。
创建一个版本库也非常简单，比如在D盘GitRepository目录下创建一个test的版本库。（很多基本指令类似Linux操作）
![这里写图片描述](http://img.blog.csdn.net/20171117140609577?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
通过git init指令可以把该目录编程git管理的仓库，如下图所示：
![这里写图片描述](http://img.blog.csdn.net/20171117140708019?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
当前test目录下会多了一个.git的目录，这个目录是Git来跟踪管理版本的，不要手动乱改这个目录里面的文件，否则，会把git仓库给破坏了。结果如下：
![这里写图片描述](http://img.blog.csdn.net/20171117142222116?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
（实际操作中发现.git文件夹并没有出现，可能原因有三，1.文件夹被隐藏了，2.git安装错误，3.图标优先级关系，需改注册表，通常是第一个原因，后两个可搜索解决）
###把文件添加到版本库
首先要明确下，所有的版本控制系统，只能跟踪文本文件的改动，比如txt文件，网页，所有程序的代码等，Git也不列外，版本控制系统可以告诉你每次的改动，但是图片，视频这些二进制文件，虽能也能由版本控制系统管理，但没法跟踪文件的变化，只能把二进制文件每次改动串起来，也就是知道图片从1kb变成2kb，但是到底改了啥，版本控制也不知道。
1.首先，在../test目录下新建一个readme.txt，内容为“123456”（不会vim，直接创建也可以）；
![这里写图片描述](http://img.blog.csdn.net/20171117143502684?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

![这里写图片描述](http://img.blog.csdn.net/20171117143707889?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

2.使用git add readme.txt指令，将该文件添加到暂存区；
![这里写图片描述](http://img.blog.csdn.net/20171117143759694?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

3.用git commit将文件提交到仓库；
![这里写图片描述](http://img.blog.csdn.net/20171117144001503?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

4.git status查看是否有文件未提交，发现已经全部提交；
![这里写图片描述](http://img.blog.csdn.net/20171117144110466?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

5.修改readme.txt，再次使用git status查看是否有文件未提交；
![这里写图片描述](http://img.blog.csdn.net/20171117144243647?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

发现，readme.txt已经被修改，但是未提交修改；
![这里写图片描述](http://img.blog.csdn.net/20171117144327336?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

6.使用git diff readme.txt可查看修改内容；
![这里写图片描述](http://img.blog.csdn.net/20171117144626691?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

7.明确了修改后，就可以将readme.txt提交到仓库，再提交文件，同2，3步；
![这里写图片描述](http://img.blog.csdn.net/20171117144932399?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

###版本回退
1.再次修改readme.txt为“12345678”，并提交，查看历史纪录，使用git log命令；
![这里写图片描述](http://img.blog.csdn.net/20171117145904843?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
commit后跟的是版本号。

2.版本回退有两种方式，
2.1 git reset --hard HEAD^(回退几次，就写几个^)；
2.2 git reset --hard HEAD~n,(n是回退到此之前的第几个版本)；
![这里写图片描述](http://img.blog.csdn.net/20171117150142673?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

3.通过git reflog，可以获取到每次的版本号
![这里写图片描述](http://img.blog.csdn.net/20171117150457737?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

4.可以git reset --hard 版本号来恢复
![这里写图片描述](http://img.blog.csdn.net/20171117150857452?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

###工作区与暂存区的区别
[工作区和暂存区](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013745374151782eb658c5a5ca454eaa451661275886c6000)
[git工作区、暂存区、版本库之间的关系](https://www.cnblogs.com/lianghe01/p/5846525.html)
工作区：就是电脑上看到的目录，比如目录下test里的文件(.git隐藏目录版本库除外)。或者以后需要再新建的目录文件等等都属于工作区范畴。
版本库(Repository)：工作区有一个隐藏目录.git,这个不属于工作区，这是版本库。其中版本库里面存了很多东西，其中最重要的就是stage(暂存区)，还有Git为我们自动创建了第一个分支master,以及指向master的一个指针HEAD。

使用Git提交文件到版本库有两步：
  第一步：是使用 git add 把文件添加进去，实际上就是把文件添加到暂存区。
  第二步：使用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支上。
Ex:
1.修改readme.txt内容为“123456789”，新建文件test.txt的内容为“1111”；
![这里写图片描述](http://img.blog.csdn.net/20171117151722384?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
2.使用git add添加到暂存区，再用git commit -m一次性全部提交
![这里写图片描述](http://img.blog.csdn.net/20171117152140399?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRGF2aWRfSmV0dA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

###撤销修改
1.直接手动修改，再用add，commit指令进行修改；
2.git reset --hard HEAD^直接回退到之前的版本；
3.git checkout -- filename
把文件在工作区做的修改全部撤销，这里有2种情况，如下：

文件自动修改后，还没有放到暂存区，使用 撤销修改就回到和版本库一模一样的状态。
另外一种是文件已经放入暂存区了，接着又作了修改，撤销修改就回到添加到暂存区后的状态。

###删除文件
可在工作区中直接删除文件，如rm readme.txt，如果想从版本库中删掉的话，可执行commit命令。

##六、远程仓库
##七、创建与合并分支
##八、bug分支
##九、多人协作
##十、常用指令
mkdir         XX (创建一个空目录 XX指目录名)
   pwd          显示当前目录的路径。
   git init          把当前的目录变成可以管理的git仓库，生成隐藏.git文件。
   git add XX       把xx文件添加到暂存区去。
   git commit –m “XX”  提交文件 –m 后面的是注释。
   git status        查看仓库状态
   git diff  XX      查看XX文件修改了那些内容
   git log          查看历史记录
   git reset  --hard HEAD^ 或者 git reset  --hard HEAD~ 回退到上一个版本
                        (如果想回退到100个版本，使用git reset –hard HEAD~100 )
   cat XX         查看XX文件内容
   git reflog       查看历史记录的版本号id
   git checkout -- XX  把XX文件在工作区的修改全部撤销。
   git rm XX          删除XX文件
   git remote add origin https://github.com/tugenhua0707/testgit 关联一个远程库
   git push –u(第一次要用-u 以后不需要) origin master 把当前master分支推送到远程库
   git clone https://github.com/tugenhua0707/testgit  从远程库中克隆
   git checkout –b dev  创建dev分支 并切换到dev分支上
   git branch  查看当前所有的分支
   git checkout master 切换回master分支
   git merge dev    在当前的分支上合并dev分支
   git branch –d dev 删除dev分支
   git branch name  创建分支
   git stash 把当前的工作隐藏起来 等以后恢复现场后继续工作
   git stash list 查看所有被隐藏的文件列表
   git stash apply 恢复被隐藏的文件，但是内容不删除
   git stash drop 删除文件
   git stash pop 恢复文件的同时 也删除文件
   git remote 查看远程库的信息
   git remote –v 查看远程库的详细信息
   git push origin master  Git会把master分支推送到远程库对应的远程分支上

##参考资料
[Git使用教程](http://www.cnblogs.com/tugenhua0707/p/4050072.html)、
[git工作区、暂存区、版本库之间的关系](https://www.cnblogs.com/lianghe01/p/5846525.html)
[工作区和暂存区 ](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013745374151782eb658c5a5ca454eaa451661275886c6000)
[Git 跟 GitHub 是什么关系? - 知乎](https://www.zhihu.com/question/21907548)