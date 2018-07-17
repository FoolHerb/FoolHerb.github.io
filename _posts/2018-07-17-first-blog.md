---
layout: post
title:  "我的第一条博客"
categories: jekyll
tags:  markdown MYSQL
author: FoolHerb
---

* content
{:toc}

## MYSQL AES加密
```js
HEX(AES_ENCRYPT("abc123456","key"))
```

## AES 解密

```js
UNHEX("加密后的结果"),"key");
```

这里注意：当我返回解密后的信息到spring中时，会提示[B不能转换成java.String 需要使用下面的代码转码（并不一定会有这个问题）。

```js
cast(AES_DECRYPT(UNHEX("加密后的结果"),"key") as CHAR(255)) as result
```
