---
title: shiro权限注解
categories:
  - - 编程生涯
    - shiro
tags:
  - - shiro
    - 注解
toc: false
date: 2020-12-07 19:34:09
---

Shiro 提供了相应的注解用于权限控制，如果使用这些注解就需要使用AOP 的功能来进行判断，如Spring AOP；Shiro 提供了Spring AOP 集成用于权限注解的解析和验证。
<!-- more -->


```
@RequiresAuthentication
```
表示当前Subject已经通过login 进行了身份验证；即Subject.isAuthenticated()返回true。

```
@RequiresUser
```
表示当前Subject已经身份验证或者通过记住我登录的。 

```
@RequiresGuest
```
表示当前Subject没有身份验证或通过记住我登录过，即是游客身份。

```
@RequiresRoles(value={"admin", "user"}, logical= Logical.AND)
@RequiresRoles(value={"admin"})
@RequiresRoles({"admin"})
```
表示当前Subject需要角色admin 和user。

```
@RequiresPermissions (value={“user:a”, “user:b”}, logical= Logical.OR)
```
表示当前Subject需要权限user:a或user:b。

----
Shiro的认证注解处理是有内定的处理顺序的，如果有多个注解的话，前面的通过了会继续检查后面的，若不通过则直接返回，处理顺序依次为（与实际声明顺序无关）
```
1. RequiresRoles

2. RequiresPermissions

3. RequiresAuthentication

4. RequiresUser

5. RequiresGuest
```
以上注解既可以用在controller中，也可以用在service中使用；

建议将shiro注解放在controller中，因为如果service层使用了spring的事物注解，那么shiro注解将无效。
