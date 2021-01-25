---
title: JWT Token
categories:
  - - 编程生涯
tags:
  - - JWT
  - - token
toc: true
date: 2020-01-25 10:10:25
---
{% raw %}<div class="post-summary">{% endraw %}

* ### 为什么使用JWT？
随着技术的发展，分布式web应用的普及，通过session管理用户登录状态成本越来越高，因此慢慢发展成为token的方式做登录身份校验，然后通过token去取redis中的缓存的用户信息，随着之后jwt的出现，校验方式更加简单便捷化，无需通过redis缓存，而是直接根据token取出保存的用户信息，以及对token可用性校验，单点登录更为简单。

{% raw %}</div>{% endraw %}

<!--more-->
<style type="text/css">
.post-summary { display: none; }
</style>

* ### 什么时候你应该用JSON Web Tokens
**下列场景中使用JSON Web Token是很有用的：**

* **Authorization (授权)**
这是使用JWT的最常见场景。一旦用户登录，后续每个请求都将包含JWT，允许用户访问该令牌允许的路由、服务和资源。单点登录是现在广泛使用的JWT的一个特性，因为它的开销很小，并且可以轻松地跨域使用。
* **Information Exchange (信息交换)**
对于安全的在各方之间传输信息而言，JSON Web Tokens无疑是一种很好的方式。因为JWTs可以被签名，例如，用公钥/私钥对，你可以确定发送人就是它们所说的那个人。另外，由于签名是使用头部和有效负载计算的，您还可以验证内容没有被篡改。

* ### JSON Web Token的结构是什么样的
JSON Web Token由三部分组成，它们之间用圆点(.)连接。这三部分分别是：
* Header（头部）
* Payload（载荷）
* Signature（签证）


因此，一个典型的JWT看起来是这个样子的：
```
xxxxx.yyyyy.zzzzz
```
接下来，具体看一下每一部分：
* **Header**（头部）
jwt的头部承载两部分信息：
 * typ（声明类型），这里是jwt
 * alg（声明加密的算法），通常直接使用 HMAC SHA256

 例如：

``` json
{
"typ":"JWT",
"alg":"HMAC"
}
```



然后，用Base64对这个JSON编码就得到JWT的第一部分

* **Payload**（载荷）
载荷就是存放有效信息的地方。这个名字像是特指飞机上承载的货品，这些有效信息包含三个部分

 * Registered claims（标准中注册的声明,建议但不强制使用）
        * iss: jwt签发者
        * sub: jwt所面向的用户
        * aud: 接收jwt的一方
        * exp: jwt的过期时间，这个过期时间必须要大于签发时间
        * nbf: 定义在什么时间之前，该jwt都是不可用的.
        * iat: jwt的签发时间
        * jti: jwt的唯一身份标识，主要用来作为一次性token,从而回避重放攻击。   
 * Public claims（公共的声明）
    公共的声明可以添加任何的信息，一般添加用户的相关信息或其他业务需要的必要信息.但不建议添加敏感信息，因为该部分在客户端可解密.


 * Private claims（私有的声明）
     私有声明是提供者和消费者所共同定义的声明，一般不建议存放敏感信息，因为base64是对称解密的，意味着该部分信息可以归类为明文信息。

 
下面是一个例子：
```json
{
"name":"wangcx",
"age":"18",
"sex":"男"
}
```
对payload进行Base64编码就得到JWT的第二部分
{% raw %}<div class="notification is-danger">{% endraw %}
注意，不要在JWT的payload或header中放置敏感信息，除非它们是加密的
{% raw %}</div>{% endraw %}

* **Signature**（签证）
jwt的第三部分是一个签证信息，这个签证信息由三部分组成：
 * header (base64后的)
 * payload (base64后的)
 * secret

这个部分需要base64加密后的header和base64加密后的payload使用.连接组成的字符串，然后通过header中声明的加密方式进行加盐secret组合加密，然后就构成了jwt的第三部分

密钥secret是保存在服务端的，服务端会根据这个密钥进行生成token和验证，所以需要保护好。


* ### JSON Web Tokens是如何工作的
* 应用（或者客户端）向授权服务器请求授权。
* 当授权被许可以后，授权服务器返回一个access token给应用
* 应用使用access token访问受保护的资源（比如：API）