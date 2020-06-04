---
title: VUE学习笔记一
categories: 
- [编程生涯,vue]
tags:
- VUE
- 学习
- 笔记
toc: true
abbrlink: 8609795e
date: 2020-05-27 15:32:53
---
### 下载安装node
### 执行如下命令安装vue(如需下载特定版本在vue后边加上@版本号，例如：`vue@2.5`)
```bash
cnpm install vue #cnpm为国内镜像站
```

<!--more-->

### 页面引入`vue.js`
```html
<script type="text/javascript" src="vue.js"></script>
```
### 页面上预留vue模板插入的位置
```html
<div id="app"></div>
```
### 实例化vue
```script
new Vue({el:预留位置,template:模板内容}); #实例化传入的是一个对象options
```

options：
* el 对应上边预留的vue模板位置，可通过id，类名，标签名查找，方式等同jquery；
* template 内容
* data 数据，值为函数形式，也可以是对象，但都是用函数，因为用的函数最后也是return一个对象

### 插值表达式
* 插值表达式内填入data里面的变量即可在页面取到变量值{{data里的变量}}

### 代码示例
```html 点击展开代码 >folded
<html>
    <head>
        <title>test</title>
        <script type="text/javascript" src="vue.js"></script>

    </head>
    <body>
		<div id="app"></div>
        <script>
            new Vue({
                el:'#app',
                template:`
                <div>你好，世界，{{text}}</div>
                `,
                data:function(){
                    return{
                        text:'这是vue的测试',
                    }
                }
            })
        </script>
    </body>
</html>
```

