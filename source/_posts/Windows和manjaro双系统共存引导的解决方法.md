---
title: Windows和manjaro双系统共存引导的解决方法
date: 2018-05-22 01:35:52
tags:
---

### 前言

> Q: What do the **Ninja-fuujiro** do?
> A: 简单来说，就是替换引导文件。我安装的是 Manjaro Linux，名称就是 Manjaro，打开之后会发现里面有一个名为 grubx64.efi 的文件，这就是启动 Linux 的引导文件。和 Windows 10 的 bootmgfw.efi 类似，我们想要用 grubx64.efi 引导代替掉 bootmgfw.efi，这样就可以用 GRUB 引导了。

（为什么要替换？因为Manjaro太弱鸡，Windows是攻，我们帮Manjaro一把。我们是平权主义者！拒绝霸道2333！ε=ε=ε=┏(゜ロ゜;)┛

### 1. 打开Windows Powershell(Administrator)

1. `win + x`
2. `a`

### 2. 将grubx64.efi 引导代替掉 bootmgfw.efi

* 输入 
    ~~~
    bcdedit /set '{bootmgr}' path \EFI\Manjaro\grubx64.efi
    ~~~

如果不好意思，你的Powershell对你有意见。你可能需要把`'{bootmgr}'`换成`{bootmgr}`。原因是可能你没听话，用的是cmd，没见着我说用Powershell了嘛~！

### 感谢

> * [Linux 与 Windows 10 用 GRUB 引导教程](https://blog.itswincer.com/posts/ad42f575/)