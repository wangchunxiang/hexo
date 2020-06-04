---
title: VUE学习笔记二
categories: 
- [编程生涯,vue]
tags:
- VUE
- 学习
toc: true
abbrlink: 6077009d
date: 2020-05-29 11:15:25
---

### 单向双向数据流及事件绑定
#### 单向数据流绑定属性值`v-bind:(属性)`简写为`:(属性)`
```html
<input v-bind:value="name"  :class="name" />
```
    
#### 双向数据流`v-model`只作用于有value属性的元素
    
```html
<input v-model="name" v-bind:class"name" />
```
    
<!--more-->
    

#### 事件绑定`v-on:事件名="表达式||函数名"`简写`@名事件名="表达式||函数名"` 

*  事件名可以是原生也可以是自定义

### 所有示例如下
```html 点击展开代码 >folded
<!DOCTYPE html>
<html lang="en">
    
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title></title>
    <script type="text/javascript" src="vue.js"></script>
</head>
    
<body>
    <div id="app"></div>
    <script>
        var vm=new Vue({
           el:'#app',
           template:`<div>
                单向数据绑定：
                <input type="text" v-bind:value="name" :class="name" />
                <br>
                双向数据绑定
                <input type="text" v-model:value="name" />
                <br>
                {{name}}
                <br>
                <button v-on:click="change"> click me </button>
            </div>`,
           data:function(){
               return {name:"hello"}
           },
           methods:{change:function(){
               this.name='change ok'
           }}
        });
    </script>
</body>
    
</html>
```

