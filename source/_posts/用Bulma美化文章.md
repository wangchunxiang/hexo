---
title:  用bulma美化文章
categories: 
- [编程生涯,hexo]
tags:
- hexo
- icarus
- 美化
toc: true
date: 2020-06-01 13:15:25
abbrlink: 5a32d9d
---
{% raw %}<div class="post-summary">{% endraw %}

 使用`bulma`的样式来美化`icarus`的文章内容，有时候我们希望在文章中用特别的样式注明一些内容，`markdown`语法就不够用了，可以使用`bulma`来对文章样式进行美化

{% raw %}</div>{% endraw %}

<!-- more -->

<style type="text/css">
.post-summary { display: none; }
</style>
### 按钮
<div class="buttons">
  <button class="button is-info">Info</button>
  <button class="button is-success">Success</button>
  <button class="button is-warning">Warning</button>
  <button class="button is-danger">Danger</button>
</div>
```html 点击展开代码 >folded
<div class="buttons">
  <button class="button is-info">Info</button>
  <button class="button is-success">Success</button>
  <button class="button is-warning">Warning</button>
  <button class="button is-danger">Danger</button>
</div>
```

#### 给按钮添加事件
<button class="button is-info" onclick="showHitokoto(event)">显示一言</button>
<blockquote class="hitokoto">↑↑↑ 试着点击“显示一言”！</blockquote>

<script>
function showHitokoto (event) {
    event.target.classList.add('is-loading');
    $.ajax({
        type: 'GET',
        url: 'https://v1.hitokoto.cn/',
        success: function (data) {
            $('.hitokoto').text(data.hitokoto);
            event.target.classList.remove('is-loading');
        }
    });
}
</script>
```html 点击展开代码 >folded
<button class="button is-info" onclick="showHitokoto(event)">显示一言</button>
<blockquote class="hitokoto">↑↑↑ 试着点击“显示一言”！</blockquote>

<script>
function showHitokoto (event) {
    event.target.classList.add('is-loading');
    $.ajax({
        type: 'GET',
        url: 'https://v1.hitokoto.cn/',
        success: function (data) {
            $('.hitokoto').text(data.hitokoto);
            event.target.classList.remove('is-loading');
        }
    });
}
</script>
```

### 进度条
<progress class="progress is-info" value="20" max="100"></progress>
<progress class="progress is-success" value="40" max="100"></progress>
<progress class="progress is-warning" value="60" max="100"></progress>
<progress class="progress is-danger" value="80" max="100"></progress>
<progress class="progress is-info" max="100"></progress>
```html 点击展开代码 >folded
<progress class="progress is-info" value="20" max="100"></progress>
<progress class="progress is-success" value="40" max="100"></progress>
<progress class="progress is-warning" value="60" max="100"></progress>
<progress class="progress is-danger" value="80" max="100"></progress>
<progress class="progress is-info" max="100"></progress>
```

### 标签页

<div class="tabs is-toggle"><ul>
<li class="is-active"><a onclick="onTabClick(event)">
<span class="icon is-small"><i class="fas fa-image" aria-hidden="true"></i></span>
<span>Pictures</span>
</a></li>
<li><a onclick="onTabClick(event)">
<span class="icon is-small"><i class="fas fa-music" aria-hidden="true"></i></span>
<span>Music</span>
</a></li>
<li><a onclick="onTabClick(event)">
<span class="icon is-small"><i class="fas fa-film" aria-hidden="true"></i></span>
<span>Videos</span>
</a></li>
<li><a onclick="onTabClick(event)">
<span class="icon is-small"><i class="far fa-file-alt" aria-hidden="true"></i></span>
<span>Documents</span>
</a></li>
</ul></div>

{% raw %}<div id="Pictures" class="tab-content" style="display: block;">{% endraw %}
[Pixabay](https://pixabay.com/zh/) 是全球知名的图库网站及充满活力的创意社区,拥有上百万张免费正版高清照片素材,涵盖风景、人物、动态、静物等多种分类,你可以在任何地方使用 Pixabay 图库中的素材...
{% raw %}</div>{% endraw %}
{% raw %}<div id="Music" class="tab-content">{% endraw %}
[网易云音乐](https://music.163.com/) 是一款专注于发现与分享的音乐产品,依托专业音乐人、DJ、好友推荐及社交功能,为用户打造全新的音乐生活。
{% raw %}</div>{% endraw %}
{% raw %}<div id="Videos" class="tab-content">{% endraw %}
[哔哩哔哩](https://www.bilibili.com/) 是国内知名的视频弹幕网站,这里有最及时的动漫新番,最棒的ACG氛围,最有创意的Up主。大家可以在这里找到许多欢乐。
{% raw %}</div>{% endraw %}
{% raw %}<div id="Documents" class="tab-content">{% endraw %}
[石墨文档](https://shimo.im/) 是全新一代云 Office 办公软件,支持多人在线协作编辑文档和表格,独有内容级安全,全过程留痕可追溯。PC 端和移动端全覆盖,随时随地远程办公。即写即存...
{% raw %}</div>{% endraw %}

<style type="text/css">
.content .tabs ul { margin: 0; }
.tab-content { display: none; }
</style>

<script>
function onTabClick (event) {
    var tabTitle = $(event.currentTarget).children('span:last-child').text();
    $('.article .content .tab-content').css('display', 'none');
    $('.article .content .tabs li').removeClass('is-active');
    $('#' + tabTitle).css('display', 'block');
    $(event.currentTarget).parent().addClass('is-active');
}
</script>

```html 点击展开代码 >folded
<div class="tabs is-toggle"><ul>
<li class="is-active"><a onclick="onTabClick(event)">
<span class="icon is-small"><i class="fas fa-image" aria-hidden="true"></i></span>
<span>Pictures</span>
</a></li>
<li><a onclick="onTabClick(event)">
<span class="icon is-small"><i class="fas fa-music" aria-hidden="true"></i></span>
<span>Music</span>
</a></li>
<li><a onclick="onTabClick(event)">
<span class="icon is-small"><i class="fas fa-film" aria-hidden="true"></i></span>
<span>Videos</span>
</a></li>
<li><a onclick="onTabClick(event)">
<span class="icon is-small"><i class="far fa-file-alt" aria-hidden="true"></i></span>
<span>Documents</span>
</a></li>
</ul></div>

{% raw %}<div id="Pictures" class="tab-content" style="display: block;">{% endraw %}
[Pixabay](https://pixabay.com/zh/) 是全球知名的图库网站及充满活力的创意社区,拥有上百万张免费正版高清照片素材,涵盖风景、人物、动态、静物等多种分类,你可以在任何地方使用 Pixabay 图库中的素材...
{% raw %}</div>{% endraw %}
{% raw %}<div id="Music" class="tab-content">{% endraw %}
[网易云音乐](https://music.163.com/) 是一款专注于发现与分享的音乐产品,依托专业音乐人、DJ、好友推荐及社交功能,为用户打造全新的音乐生活。
{% raw %}</div>{% endraw %}
{% raw %}<div id="Videos" class="tab-content">{% endraw %}
[哔哩哔哩](https://www.bilibili.com/) 是国内知名的视频弹幕网站,这里有最及时的动漫新番,最棒的ACG氛围,最有创意的Up主。大家可以在这里找到许多欢乐。
{% raw %}</div>{% endraw %}
{% raw %}<div id="Documents" class="tab-content">{% endraw %}
[石墨文档](https://shimo.im/) 是全新一代云 Office 办公软件,支持多人在线协作编辑文档和表格,独有内容级安全,全过程留痕可追溯。PC 端和移动端全覆盖,随时随地远程办公。即写即存...
{% raw %}</div>{% endraw %}

<style type="text/css">
.content .tabs ul { margin: 0; }
.tab-content { display: none; }
</style>

<script>
function onTabClick (event) {
    var tabTitle = $(event.currentTarget).children('span:last-child').text();
    $('.article .content .tab-content').css('display', 'none');
    $('.article .content .tabs li').removeClass('is-active');
    $('#' + tabTitle).css('display', 'block');
    $(event.currentTarget).parent().addClass('is-active');
}
</script>
```

### 彩色突出
{% raw %}<div class="notification is-info">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div>{% endraw %}

```html 点击展开代码 >folded
{% raw %}<div class="notification is-info">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div>{% endraw %}
```
{% raw %}<div class="notification is-success">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div>{% endraw %}
```html 点击展开代码 >folded
{% raw %}<div class="notification is-success">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div>{% endraw %}
```
{% raw %}<div class="notification is-warning">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div>{% endraw %}
```html 点击展开代码 >folded
{% raw %}<div class="notification is-warning">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div>{% endraw %}
```
{% raw %}<div class="notification is-danger">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div>{% endraw %}
```html 点击展开代码 >folded
{% raw %}<div class="notification is-danger">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div>{% endraw %}
```
{% raw %}<article class="message is-info"><div class="message-body">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div></article>{% endraw %}
```html 点击展开代码 >folded
{% raw %}<article class="message is-info"><div class="message-body">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div></article>{% endraw %}
```
{% raw %}<article class="message is-success"><div class="message-body">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div></article>{% endraw %}
```html 点击展开代码 >folded
{% raw %}<article class="message is-success"><div class="message-body">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div></article>{% endraw %}
```
{% raw %}<article class="message is-warning"><div class="message-body">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div></article>{% endraw %}
```html 点击展开代码 >folded
{% raw %}<article class="message is-warning"><div class="message-body">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div></article>{% endraw %}
```
{% raw %}<article class="message is-danger"><div class="message-body">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div></article>{% endraw %}
```html 点击展开代码 >folded
{% raw %}<article class="message is-danger"><div class="message-body">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div></article>{% endraw %}
```
{% raw %}<article class="message is-info"><div class="message-header">{% endraw %}
活用 Bulma 美化 Icarus 文章
{% raw %}</div><div class="message-body">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div></article>{% endraw %}
```html 点击展开代码 >folded
{% raw %}<article class="message is-info"><div class="message-header">{% endraw %}
活用 Bulma 美化 Icarus 文章
{% raw %}</div><div class="message-body">{% endraw %}
[Icarus](https://blog.zhangruipeng.me/hexo-theme-icarus/) 主题以白色的简洁为主，但有时候我们希望在文章中用**特别的样式**注明一些内容，*markdown* 语法就不够用了，所以在此分享一下我的高级玩法。
{% raw %}</div></article>{% endraw %}
```

### 黑色块
{% raw %}
<style type="text/css">
.heimu { color: #000; background-color: #000; }
.heimu:hover { color: #fff; }
</style>
{% endraw %}
这是正常的一段文字，刮开可见{% raw %}<span class="heimu">谢谢惠顾</span>{% endraw %}

```html 点击展开代码 >folded
{% raw %}
<style type="text/css">
.heimu { color: #000; background-color: #000; }
.heimu:hover { color: #fff; }
</style>
{% endraw %}
这是正常的一段文字，刮开可见{% raw %}<span class="heimu">谢谢惠顾</span>{% endraw %}
```

### 让简介不出现在正文
我们知道Hexo用`<!-- more -->`可以风格简介和正文，但是这样简介也会再出现在正文中，如果我们不想让简介部分出现在正文呢？
```html 点击展开代码 >folded
这里的内容会出现在 **简介和正文**

{% raw %}<div class="post-summary">{% endraw %}

这里的内容只会出现在 **简介**

{% raw %}</div>{% endraw %}

<!-- more -->

<style type="text/css">
.post-summary { display: none; }
</style>

这里的内容只会出现在 **正文**
```

