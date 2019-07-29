# **git的简单使用**
## **一.从github上拉项目**
 首先你要有一个你的github账号，然后在你的本地配置github的秘钥，相当于将你的本地电脑和github账号绑定。
 1. git config --global user.name "Your Name"（创建全局的用户名）
 2. git config --global user.email "email@163.com"（创建全局的邮箱地址）**这个邮箱地址可以和你的github地址不一样**
 3. ssh-keygen -t rsa -C "youremail@example.com"(生成秘钥)，**在你用cmd窗口打开的文件夹下，文件名和密码由你来定**
 4. 打开github下的setting右侧的ssh and gpgkeys 将生成好的秘钥复制粘贴title随意
 5. 在本地新建文件夹使用 `git clone 你想要拉的项目` 就ok了。
 ## **二.git的使用**
 **教程是看的廖雪峰的，讲的很好，地址在这[git教程](https://www.liaoxuefeng.com/wiki/896043488029600/897013573512192)**
 **总结一下**
 <br/>
&#160; &#160; &#160; &#160;**git是分布式版本控制工具**,
他是没有中央版本控制器的，每个人的电脑上都有完整的项目，对于同一个文件，a同学修改了，b同学也修改了，两位只要分别把他们各自修改的内容推送给对方就可以保证版本的一致性。不过在实际开发中为了开发的进行，一般会新建一个中央仓库来管理所有代码。
<font color="black">具体操作</font>
+ 新建一个文件夹
   + git init (新建仓库)
+ 新建文件
   + read.md
+ 文件上传到仓库
   + git add read.md
   + git commit -m "提交的注释"
   + git push -u origin master   （注：此操作目的是把本地仓库push到github上面，此步骤需要你输入帐号和密码）** -u的作用除了把本地的master推到远程仓库，还可以把本地仓库和远程仓库关联，以后推送可以不写。
   + **add和commit的区别，add反复提交，commit一次性提交所有add的文件
+ 查看状态
   + git status (查看有哪些文件进行可修改)
   + git diff(查看文件修改了哪些部分)
+ 版本的回退（针对的是已经commit的版本）
   + git log (查看提交的历史版本)
   + git log --pretty=oneline(规范整齐显示)
   + git reset --hard HEAD^(回退到上个版本，HEAD^^上上个版本)
   + git reflog(显示所有操作过的版本，从过去回到未来)
   + **这里有一个问题要注意在使用cmder和cmd时^符号默认是换行符不识别，所有要加引号，或者多写一个^**
+ 工作区和暂存区
   + 工作区就是你本地工作的文件夹，暂存区（stage）是add后的区域，commit后一次性把暂存区的内容推到master
+ 撤销修改
   1. 从工作区撤销修改 git checkout -- readme.txt 撤销你在工作区进行的修改**回退后和暂存区一样**
   2. 从暂存区撤销修改 git reset HEAD readme.txt 重新放回到工作区，然后继续使用一步骤。
+ 删除文件
   + 在本地删除后rm file1.txt是不够的，使用git rm file1.txt,然后git commit，
   如果删除错了，可以使用git checkout -- file1.txt从版本库拿到。**所以checkout命令的实质就是讲工作区的文件和版本库的文件一致**
+ 分支的管理
   + 分支master和提交，HEAD的区别。每次提交就是一条时间线，HEAD是指向master的，master指向提交，新建一个分支devHEAD就指向dev然后提交dev，dev指针向前移一步，master不变，此时就要将master和dev合并。
      1. **git checkout -b dev** 新建一个分支 -b表示切换
      2. **git branch**查看当前有哪些分支
      3. **git checkout master** 切回master分支
      4. **git merge dev**合并dev分支
      5. **git branch -d dev**删除分支
   + 解决冲突
      1. 两个不同的分支修改同一份文件合并的时候会冲突，方法就是解决冲突
   + 分支管理策略
      + 实际开发过程中会见一个主版本稳定的master，然后所有人在dev下创建分支在dev上合并最后在合并到master上
      + 使用git merge --no-ff -m '' dev形成分支信息
      + git log --graph --pretty=oneline --abbrev-commit查看结构图
   + bug分支
      + 使用git stash保存当前工作区，新建分支修复bug后再切回原来工作区，使用git status查看工作区是干净的，使用git stash list命令查看
      + 使用git stash pop或者 git stash apply 和git stash drop组合命令将stash存储的工作区删除，然后恢复原来的工作区
