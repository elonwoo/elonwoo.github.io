---
title: MacOS WiFi Dropping When Waking From Sleep
layout: blog.njk
date: 2019-07-24
tags: blog
categories:
  - mac
---

## 症状

合盖睡眠再次唤醒后没有WiFi连接。点WiFi图表转菊花。

需要重新启动才能解决。问题不定时出现，而且并不限于某一个WiFi。


## 临时解决方案

>sudo killall airportd


## 彻底解决方案

打开系统偏好设置，选择网络，选择位置里的『编辑位置』，新建一个位置，比如「work」，并选择「work」。反正不要选「自动」

打开系统设置里隐私-位置，关掉「Wi-Fi Networking」的位置获取权限 
  
![](https://gt-toolbox.oss-cn-beijing.aliyuncs.com/8bS5dK.png)

重启