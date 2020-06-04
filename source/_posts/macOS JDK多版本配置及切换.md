---
title: macOS JDK多版本配置及切换
categories: 编程生涯
tags:
- JDK多版本
toc: true
abbrlink: b11ab823
date: 2019-10-11 14:11:41
---

### 首先安装需要的JDK版本
略.
### 配置JDK
#### 创建.bash_profile配置文件（已经有该文件就跳过此步骤）

```bash
touch ~/.bash_profile
```
#### vim编辑.bash_profile文件
```bash
vim ~/.bash_profile
```
#### 如果不习惯vim命令就使用自带的文本编辑器打开
```bash
open ~/.bash_profile
```
#### 设置jdk版本
```bash
export JAVA_11_HOME=/Library/Java/JavaVirtualMachines/jdk-11.0.4.jdk/Contents/Home
export JAVA_8_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_221.jdk/Contents/Home
export JAVA_HOME=$JAVA_8_HOME
```
<!--more-->

#### alias命令动态切换JAVA_HOME的配置
```bash
alias jdk8='export JAVA_HOME=$JAVA_8_HOME'
alias jdk11='export JAVA_HOME=$JAVA_11_HOME'
```
#### 输入完成后保存执行下面命令,重新执行.bash_profile文件
```bash
source ~/.bash_profile
```

这样以后即可在终端中使用`jdk8`或者`jdk11`切换jdk版本了

