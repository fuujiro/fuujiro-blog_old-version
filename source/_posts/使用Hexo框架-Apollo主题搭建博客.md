---
title: 使用Hexo框架+Apollo主题搭建博客
date: 2018-02-14 23:49:33
tags:
---

### 前言

时间过得贼快啊！我一下子就要大二下学期了！想着自己以后大概率就是一名老实的程序员。按着这个程序猿们的习惯啊，一般都会有个自己的博客，也不论是追求技术还是跟风吧，我脑子一热呢，就准备搭一个自己的Blog。

脑子热的时候是2月11号晚上，然后既然热了，那就行动呗。先google了一下个人博客的主流框架和搭建入门咯。最后还是放弃了Wordpress，选择了Hexo来搭建，原因是Hexo开源，主题选择丰富，emmmm就酱。关于为啥选择apollo主题呢，主要是有天瞎逛时，误入了[phoenixlzx巨巨的blog](https://blog.phoenixlzx.com)，他用的就是Apollo主题。我定睛一看，这就是我想要的~~滑板鞋~~主题！

[Apollo](https://github.com/pinggod/hexo-theme-apollo)主题的[开发者](https://github.com/pinggod)据说是一位92年的小哥哥，开发Apollo的时候在美团前端任职，现在根据他的GitHub主页应该是在Alipay工作了。我选择Apollo主题的原因是因为它风格简约，我觉得浏览时加载体验比博客华丽的外观会重要很多，你想想等加载是很烦躁的一件事（嗯，至少来说我是这样...），何况Apollo还简约得好看一匹，果断Mark。如下图。

![hexo-apollo](https://cloud.githubusercontent.com/assets/9530963/13026956/08e76eca-d277-11e5-8bfc-2e80cea20a0d.png)

嗯！真的很耐看！清新，简约，Nice！

既然选择好了框架+主题，就进入正式阶段（以下一切安装代码，在OS X无问题，Windows可能会要稍作修改）。

### 1. 安装Hexo
因为Hexo是一款基于Node.js的静态博客框架，生成静态网页托管在GitHub。所以我们在安装Hexo前得先装上Node.js和git。

#### 1.1 安装Node.js

 * [下载Node.js](https://nodejs.org/en/)
 * [安装Node.js](http://www.runoob.com/nodejs/nodejs-install-setup.html)

#### 1.2 安装git

 * [下载git](https://git-scm.com/downloads)（可能会有墙的限制，请翻墙|在网盘or网站CSDN上都可以找到离线包）
 * [安装git](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137396287703354d8c6c01c904c7d9ff056ae23da865a000)
 * [配置自己的git](https://git-scm.com/book/zh/v1/起步-初次运行-Git-前的配置)（重要：别忘了这步）

#### 1.3 安装Hexo

因为已经装好了Node.js环境了，所以可以使用npm命令。
1. 使用npm命令安装Hexo，输入：
~~~
$ npm install -g hexo-cli 

or

$ npm install -g hexo
~~~
如果收到error，在命令行首加上`sudo`。

2. 初始化博客
找到你要放置博客的根目录（推荐建立一个文件夹用来放置，~~强迫症必须不得不这么干~~），建好了我们就开始初始化，比如我们已经了创建了一个名为blog的文件夹~~程序员最好不要创造出有中文的路径吧~~。
~~~
$ hexo init blog
~~~

3. 常规操作
接下来搭个静态界面，看看预期，满足下心脏。
~~~
$ cd blog #切到blog文件夹下
$ npm install  
$ hexo g
$ hexo s
~~~
按照正常操作，这时候命令行会抛出一个链接`http://localhost:4000/`，你复制这串网址粘贴到浏览器打开，不出错误的话，会看到第一个由Hexo框架搭建的网页。如果这时候，你没看到or失败了，可能需要google一下。

接着，普及一下Hexo框架的基本操作和作用
1. hexo generate (hexo g) 生成静态文件，会在当前目录下生成一个新的叫做public的文件
2. hexo server (hexo s) 启动本地web服务，用于博客的预览
3. hexo deploy (hexo d) 部署博客到远端（比如github平台）
4. hexo clean 清除缓存

你还会用到
~~~
$ hexo new "postName" #新建博客的文章
$ hexo new page "pageName" #新建博客的页面
$ hexo g && hexo d #生成部署
$ hexo s #生成本地预览
~~~

我写这篇文章时的本地环境，你可以参考一下（使用`hexo -v`查看，我使用的是OS X系统搭建）
~~~
hexo: 3.5.0
hexo-cli: 1.0.4
os: Darwin 17.2.0 darwin x64
http_parser: 2.7.0
node: 8.9.4
v8: 6.1.534.50
uv: 1.15.0
zlib: 1.2.11
ares: 1.10.1-DEV
modules: 57
nghttp2: 1.25.0
openssl: 1.0.2n
icu: 59.1
unicode: 9.0
cldr: 31.0.1
tz: 2017b
~~~

### 2. apollo主题配置
#### 2.1 安装 

~~~
$ cd Blog 
$ npm install
$ npm install --save hexo-renderer-jade hexo-generator-feed hexo-generator-sitemap hexo-browsersync hexo-generator-archive
$ git clone https://github.com/pinggod/hexo-theme-apollo.git themes/apollo
~~~

#### 2.2 启用

修改`_config.yml`的`theme`配置项为`apollo`
~~~
theme: apollo

archive_generator:
    per_page: 0
    yearly: false
    monthly: false
    daily: false
~~~

#### 2.3 测试

~~~
$ hexo s
~~~
浏览器打开`http://localhost:4000/`，看有没有出现apollo标准样式博客，如果没有成功，请自行Google查错。

#### 2.4 更新

~~~
$ cd themes/apollo 
$ git pull
~~~

### 3. 托管到GitHub + 链接个人域名
#### 3.1 基本准备

 * GitHub账户一个
 * 一个自定义域名（从阿里云，腾讯云等都可以购买，自带解析服务，推荐；当然也可以选择国外网站，不过国内访问速度可能会稍差一点）

 我默认你会基本git和GitHub操作，嗯！如果不会，请移步[廖雪峰老师的git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)。

#### 3.2 托管步骤 

我们利用[GitHub Pages](https://pages.github.com)来介绍托管在GitHub的项目。由于`GitHub Pages`的空间免费稳定，用来做搭建一个博客再好不过了。

 * [如何搭建一个独立博客——简明Github Pages与Hexo教程](https://www.jianshu.com/p/05289a4bc8b2)

上面这篇博文详细的介绍了`ssh key`的获取和链接，介绍了`GitHub Pages`上面搭建Hexo博客的步骤.

关键点：
##### 3.2.1 设置ssh-key

1. 配置 SSH keys
    我们如何让本地 git 项目与远程的 GitHub 建立联系呢？用 SSH keys。
2. 检查 SSH keys的设置
    首先我们需要检查电脑上是否已有ssh key：
    ~~~
    $ cd ~/.ssh 检查本机的ssh密钥
    ~~~
    如果提示的是`No such file or directory`，说明你是第一次在本机上使用，需要创建一个。
3. 生成新的 SSH Key
    ~~~
    $ ssh-keygen -t rsa -C "邮件地址@youremail.com"
    Generating public/private rsa key pair.
    Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):<回车就OK>
    ~~~
    * 此处的邮箱地址，推荐使用你的GitHub账户邮箱
    * 此处的「-C」的是大写的「C」

    然后系统会要你输入密码：
    ~~~
    $ Enter passphrase (empty for no passphrase):<输入密码>
    $ Enter same passphrase again:<再次输入密码>
    ~~~
    在回车中会提示你输入一个密码，这个密码会在你提交项目时使用，如果为空的话提交项目时则不用输入。这个设置是防止别人往你的项目里提交内容。
    * 其实没必要设置，完全可以敲两下回车；当然设置也没有关系
    * 注意：输入密码的时候没有 * 字样的，你直接输入就可以了。（我个人觉得git还可以完善的一个细节）
4. 最后看到这样的界面，就成功设置ssh key了：
    ![ssh-key](https://upload-images.jianshu.io/upload_images/32598-cf2af2bff37b1031.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/544)


##### 3.2.2 添加ssh key到GitHub

在本机设置 SSH Key 之后，需要添加到 GitHub上，以完成 SSH 链接的设置。
 * 1、打开本地 id_rsa.pub 文件（如：`/Users/fuujiro/.ssh/id_rsa.pub`）。此文件里面内容为刚才生成的密钥。如果看不到这个文件，你需要设置显示隐藏文件。准确的复制这个文件的内容，才能保证设置的成功。
 * 2、登陆 GitHub 系统。点击右上角的`Account Settings`--->`SSH Public keys`--->`add another public keys`
 * 把你本地生成的密钥复制到里面（`key`文本框中）， 点击`add key`就ok了
 ![add-ssh-key](https://upload-images.jianshu.io/upload_images/32598-c8b55d62cc0dbd07.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/470)

#### 3.2.3 测试

可以输入下面的命令，看看设置是否成功，git@GitHub.com 的部分不要修改：
~~~
$ ssh -T git@GitHub.com
~~~
按道理会显示下面的反馈：
~~~
The authenticity of host 'GitHub.com (207.97.227.239)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)?
~~~
输入`yes`就ok，按道理会显示：
~~~
Hi （你的GitHub名字）! You've successfully authenticated, but GitHub does not provide shell access.
~~~
恭喜你！SSH Key 配置成功！本机已成功连接到 GitHub。

* 当然，比较倒霉。如果没按道理，大部分可能是墙的原因，你可能需要`ping git@GitHub.com`拿d到IP地址，然后在/hosts里添加上这个解析。请自行Google解决这个`little issue`
* 一个常见错误：[GitHub Help - Error Permission denied (publickey)](https://help.github.com/articles/error-permission-denied-publickey/)

#### 3.3 将独立域名与 GitHub Pages 的空间绑定

1. `DNS`设置 or 域名解析
   我用的腾讯云的控制台，找到域名，点一下右侧的解析按钮即可解决。阿里云买的域名也可以由阿里云解析。这里也可以使用[DNSpod](https://www.dnspod.cn)，注册一个账户，即可解析域名了，但应该仅限于解析国内域名。国外的域名，如`GoDaddy`，请上`GoDaddy`自行修改DNS。
2. 如何设置DNS
    ![DNS设置](https://mc.qcloudimg.com/static/img/8231080d9d713baf5d4edf4163b23ee0/image.png)
    主要有以下几项设置需要填写（以域名fuujiro.com为例）：

    * 主机记录
        * www：解析后的域名为 `www.fuujiro.com`
        * @：直接解析主域名 `fuujiro.com`
        * *：泛解析，匹配其他所有域名 `*.fuujiro.com`
        * mail：将域名解析为 `mail.fuujiro.com`，通常用于解析邮箱服务器
        * 二级域名：如`blog.fuujiro.com`，填写blog
        * 手机网站：`m.fuujiro.com`，填写m
    * 记录类型
        * A：将域名指向云服务器，请选择「A」；
        * CNAME：将域名指向另一个域名，请选择「CNAME」；
        * MX：建立邮箱请选择「MX」，根据邮箱服务商提供的MX记录填写。
    * 记录值：填写需要链接的那个域名，如：`fuujiro.github.io`

    例：如果我们需要把`fuujiro.github.io`和`blog.fuujiro.com`链接，主机记录：`blog`，记录类型：`CNAME`，记录值：`fuujiro.github.io`。
3. 然后在你的博客根目录下，找到`/source`文件夹，进入文件夹，创建一个无格式的名为`CNAME`的文本文件，文件里填好`blog.fuujiro.com`（你的个人域名）
4. 测试
浏览器打开`你的个人域名`如~~blog.fuujiro.com~~，查看是否加载出页面，如果成功！恭喜你啊，你所有步骤基本完成，尽情地享受你的个人blog，开始码代码吧！頑張って！

### 4.后记

本来情人节当晚，~~我就完成了blog的全部搭建~~我就准备开始写这篇文章了，emmmm也就是昨晚了，结果写着写着就困了，就睡觉去了~~知道我为什么这么菜了吧我真的很懒~~。然后今天白天，按着假期规律呗，中午11点多起床，码了几行字，然后~~吃饭陪我爸聊天，买衣服，陪弟弟放鞭炮~~在大年三十完成这篇文章的`flag`就倒了，无情地倒下了！

不过我没有放弃，继续加油，还是在大年初一，emmmm完结了这篇blog！也谢谢你看到这里，祝你在狗年新年快乐～万事如意！狗年不再出bug！！hahah~


致谢：
1. [令狐葱@前端笔记](https://linghucong.js.org/2016/04/15/2016-04-15-hexo-github-pages-blog/)
2. [吴润的知乎专栏：cs专业那些事](https://zhuanlan.zhihu.com/p/26625249)
