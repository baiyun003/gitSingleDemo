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
   + **add和commit的区别，add反复提交，commit一次性提交所有add的文件
+ 查看状态
   + git status (查看有哪些文件进行可修改)
   + git diff(查看文件修改了哪些部分)
+ 版本的回退
   + git log (查看提交的历史版本)
   + git log --pretty=oneline(规范整齐显示)
   + git reset --hard HEAD^(回退到上个版本，HEAD^^上上个版本)
   + git reflog(显示所有操作过的版本，从过去回到未来)
   + **这里有一个问题要注意在使用cmder和cmd时^符号默认是换行符不识别，所有要加引号，或者多写一个^