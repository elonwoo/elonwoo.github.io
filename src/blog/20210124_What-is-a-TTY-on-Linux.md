---
title: What Is A TTY On Linux
layout: blog.njk
date: 2021-01-24
tags: blog
categories:
  - Linux
---

## @zhujinliang
shell 指外壳程序，意思是与系统内核沟通的程序，对应的内核叫 kernel，就是 bash 、zsh 这样的程序

逻辑上是我们通过输入输出设备连接到计算机硬件，通过 shell，调用 kernel 提供的接口，完成操作。

tty 是电传打字机，早期计算机的输出设备，计算机通过串口线输出信号，电传打字机像人按动打字机似的，在纸上打出文字（据说 CR LF 也是电传打字机时代遗留下来的，CR 表示把打字头位置移到行首，LF 表示走一行纸）

终端的概念，早期计算机体积大、造价高，所以一个机构或院校购买一台，然后通过终端设备（键盘、tty 、modem 等）接入，通过分时等形式供多人使用。各类操作系统就在这种操作逻辑上发展起来，以至于现在个人计算机仍保留这种原始的操作方式。现在已经没有了电传打字机之类的硬件设备，为了兼容，或者说情怀，于是在操作系统上虚拟了一个硬件。


## @billlee
基本上就分为两类：shell 和 terminal

terminal 负责底层的输入输出，例如：缓冲一行数据，直到 enter 按下的时候才把数据发送给前台进程、把 backspace, 方向键等转换成对应的转义序列，收到 ctrl+c 时给前台进程发送 SIGINT; 根据程序输出的转义序列给输出的文字设置颜色、粗体、闪烁、下划线等不同的格式。

shell 负责解释用户输入的命令，根据输入的命令建立管道、fork, 调整 stdin/stdout/stderr 描述符，exec

tty, pty, windows 超级终端都是各种不同的 terminal. bash, zsh, dash 等都是各种不同的 shell.

至于 tty 是哪个进程负责的，如果这里的 tty 是指 linux 的虚拟 tty (ctrl + alt + F1-F6 调出来的那些) ，那只能说是内核本身负责的，不管对键盘输入的转义、还是对程序输出转义的解读，都是由内核内的虚拟 tty 驱动负责的。


## 延伸阅读
* [为什么终端有那么多的名称？ - V2EX](https://www.v2ex.com/t/747815#reply15)
* [What is a TTY on Linux? (and How to Use the tty Command)](https://www.howtogeek.com/428174/what-is-a-tty-on-linux-and-how-to-use-the-tty-command/)