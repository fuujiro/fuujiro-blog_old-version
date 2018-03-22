---
title: Vim-蓝色星球迄今为止最强大的编辑器（持续更新
date: 2018-03-10 22:06:11
tags:
---

### Vim - 编辑器之神

#### 故事
为什么`Vim`被称为编辑器之神？话说啊，远古时候，有两大神仙，地上很多猿类大多分成两派，一部分仰慕`Vim`大神，另一部分崇拜`Emacs`大仙，这两派互相挖苦比较，只相信自己的信仰之神是最强大的！~~我呢，暂时站`Vim`神的，不排除以后叛变啦！~~

好了，正经说话吧！我默认看我博客的大部分是计算机或相关专业的同学，我们第一次编程序用到的软件，你还记得嘛？高校里教学c语言时，应该是用的`VC++6.0` or `VS2010`，这两个是编辑器嘛？当然，不是的！他们都是集成开发环境（`IDE`，`Integrated Development Environment`）,我今天介绍的`Vim`才是编辑器，与`vim`一起称作编辑器还有啥子呢？比如，`Emacs`（Vim在这个世界上的最强大对手）,`VS code`（Microsoft推出的开源编辑器，是我最近使用的最频繁的编辑器，可以说面对学习曲线陡峭的Vim来说，`VS code`是最容易上手的编辑器，我现在在写的这篇blog就是用`VS code`写的，插件十分丰富，除了由于GUI界面的存在，可能在内存上稍高于`Vim`，但比起鬼畜的`Atom`来说，那是好到不知道哪里去了的存在）,`Atom`（Google推出的开源编辑器，同样因为开源的原因，插件十分丰富）,`Sublime Text`（前端engineer一定经历过的编辑器，插件丰富，性能极优）等等......

好了，你现在肯定会问我，为啥我这次blog只介绍Vim呢？因为，Vim难学啊！这里有一张网上嘲讽几大编辑器的学习曲线～
![vim-line](https://raw.githubusercontent.com/fuujiro/pictures/master/主流編輯器學習曲線圖.jpg)

#### 学习Vim能给你带来什么？
从图上我们能看出，vim（vi）的学习曲线入门是十分陡峭的，Emacs的略显鬼畜2333～！那，学习Vim对于我来说，到底有什么什么好处呢？我在刚刚学习Vim时，也是有抱着这个疑惑的，后来总是强迫自己去学+在网上了解Vim，我觉得学习对你可能会有这些好处：
* 熟悉命令行工具：Vim是在终端（Terminal）上运行的编辑器，学习Vim无疑你会在命令行下进行频繁操作，而命令行工具对于程序员来说，是十分重要的！也许大部分同学的开发环境大部分还是Windows，使用命令行工具的机会很少！但是以后科研or工作，开发平台就不一定是Windows了，也不一定会有带图形界面的开发工具给你使用。比如：
  * 你科研跑TensorFlow，进行深度学习方面的科研，大概率会需要在linux上跑；做机器学习离不开Linux～我最近在做计算机视觉（Computer Vision）的研究，小方向现在做的是对机械臂进行视觉定位，然而这个机械臂的ROS操作工具，就必须在Linux下进行~～macOS&Windows都没提供~~
  * 你是EE爱好者（robot开发方向的爱好者），而ROS (Robot Operating System, 机器人操作系统) 恰恰只提供给你Linux的开发工具（且只保证Ubuntu（Linux的一个发行版）能够完美兼容），你作为机器人方向开发者，无法避免命令行工具的使用
  * 除了科研界，工程界对于命令行工具的使用不要太多！各大互联网的大厂的每一个开发岗offer，无论你是c/c++/java/python/c#/前端/运维等，哪个岗位要求都会有这么一句“熟悉使用命令行操作工具”or“熟悉shell脚本语言编程”，可以说，使用命令行工具是一位合格的计算机专业大学生应该具有的。

* Vim具有其他编辑器不具有的与生俱来的特殊功能，比如轻松运用SSH（SSH指：. Secure Shell（缩写：SSH），即“安全壳协议”，一项计算机上的安全协议）；Vim内存占用很低，对于开发配置要求极低，比起具有图形界面的VS code，Atom，Sublime来说，可以说能开机的电脑都能顺溜地跑Vim～！

* 最后一个：Vim能帮助乌干达的贫苦儿童，这是个梗2333～！不过，认真讲哦～你用Vim写代码，是在帮助世界上的其他小孩子呢！还有什么理由，不好好写代码233～！
![Uganda](https://raw.githubusercontent.com/fuujiro/pictures/master/4170551-f560a9916f58202d.jpg)

相信前面的大串理由，你一定拒绝不了Vim的诱惑，不如和我一起来学习Vim工具吧～啦啦啦～！

### Vim介绍以及如何入门
####  Vim和Vi的关系
通过搜索引擎了解一下，就简单黏上来了！自己写的没有这么全面～
~~~
Vim和Vi都是多模式编辑器，不同的是vim 是vi的升级版本，它不仅兼容vi的所有指令，而且还有一些新的特性在里面。
vim的这些优势主要体现在以下几个方面：
1、多级撤消
我们知道在vi里，按 u只能撤消上次命令，而在vim里可以无限制的撤消。
2、易用性
vi只能运行于unix中，而vim不仅可以运行于unix,windows ,mac等多操作平台。
3、语法加亮
vim可以用不同的颜色来加亮你的代码。
4、可视化操作
就是说vim不仅可以在终端运行，也可以运行于x window、 mac os、 windows。
5、对vi的完全兼容
某些情况下，你可以把vim当成vi来使用。
~~~
所以，我们通常就把Vim包括了Vi啦～！

#### Vim安装
按道理来说，现如今的操作系统（除Windows）都已经自带好了Vim。为了避免古老版本只安装Vi的gg情况，我们可以先敲
~~~
$ vim -version
~~~
来确定计算机是否已经安装好了Vim，一般出现的结果就是：
~~~
fuujiro-Mac:~ fuujiro$ vim -version
VIM - Vi IMproved 8.0 (2016 Sep 12, compiled Jul 26 2017 19:10:24)
~~~
如上结果的话，你的计算机就已经安装好了Vim，版本是8.0。
当然如果提示`command not found`，那也不慌，我们装上就好：
* Linux用户：
    因为Linux存在两大派系，Debian和Redhat，对于不同派系，安装命令也不相同。
    ~~~
    ubuntu系统（基于Debian）：
    普通用户下输入命令：sudo apt-get install vim-gtk
    centos系统（基于Redhat）：
    普通用户下输入命令：yum -y install vim*
    ~~~
* macOS用户：
    macOS是自带Vim的，但由于随系统版本的原因，可能版本落后，那就讲一下Vim的升级吧～！
    我是推荐用Homebrew（Homebrew是一款自由及开放源代码的软件包管理系统，用以简化Mac OS X系统上的软件安装过程）来升级的。
    1. 安装Homebrew
    ~~~
    $ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    ~~~
    2. 安装or升级Vim
    ~~~
    安装Vim
    $ brew install vim
    升级Vim
    $ brew update vim
    ~~~
* Windows用户
    Windows因为不是*nix类系统，所以不会自带Vim，不过已经有大牛开发出了vim在Windows上的编辑器-gvim
    * [gvim+w7+vundle安装教程](http://blog.csdn.net/myloveqingmu/article/details/52518563)
   上面这个文章清晰的解释了每一步，跟着做就好。

#### Vim入门
##### 

致谢：
1. [令狐葱@前端笔记](https://linghucong.js.org/2016/04/15/2016-04-15-hexo-github-pages-blog/)
2. [吴润的知乎专栏：cs专业那些事](https://zhuanlan.zhihu.com/p/26625249)