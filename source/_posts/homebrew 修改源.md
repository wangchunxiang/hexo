---
title: homebrew 修改源
categories:
  - - 编程生涯
    - homebrew
tags: 
- homebrew
- 国内镜像站
toc: true
abbrlink: 44c9996b
date: 2020-05-14 17:07:04
---
### 切换brew源为国内镜像站
#### 替换brew.git

```bash
cd "$(brew --repo)"
```

* 中国科大源

```bash
git remote set-url origin https://mirrors.ustc.edu.cn/brew.git
```

* 清华大学源

```bash
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git
```

<!--more-->

#### 替换homebrew-core.git:

```bash
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
```

* 中国科大源

```bash
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git
```

* 清华大学源

```bash
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git
```

#### 替换homebrew-bottles:

* 中国科大源

```bash
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile
source ~/.bash_profile
```
* 清华大学源

```bash
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.bash_profile
source ~/.bash_profile
```
#### 应用生效

```bash
brew update
```

### 切换brew源为默认值

#### 重置brew.git

```bash
cd "$(brew --repo)"
git remote set-url origin https://github.com/Homebrew/brew.git
```

#### 重置homebrew-core.git

```bash
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://github.com/Homebrew/homebrew-core.git
```