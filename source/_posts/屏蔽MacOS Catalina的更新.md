---
title: 屏蔽MacOS Catalina的更新
categories: 编程生涯
tags:
- 屏蔽更新
- MacOS Catalina
toc: true
abbrlink: 3029381453
date: 2019-11-14 09:05:59
---
MacOS Mojave软件更新变为独立的功能存在于系统偏好设置里面，并且可以直接自动检测大版本的升级。Catalina系统刚放出还有不少bug，而且从Catalina开始不支持32程序了。所以我并不想升级到MacOS Catalina，但是每次看到软件更新的小红点，强迫症发作。以下这个办法可以屏蔽已经检测到的升级，并且去掉烦人的小红点。
<!--more-->

### 在终端输入

```bash
defaults write com.apple.systempreferences AttentionPrefBundleIDs 0
```
### 然后输入

```bash
killall Dock
```

注意：这个不是永久性屏蔽，只要点软件更新就会再次出现。Catalina的更新提示是会和Mojave补丁的一起出现的，升级了安全更新再用终端屏蔽一次就好了。
