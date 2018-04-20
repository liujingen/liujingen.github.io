---
title: jshint W104 - 'const' is available in ES6 (use 'esversion 6') or Mozilla JS extensions(use moz)
date: 2018-04-20 17:06:24
categories: 编辑器
tags: [error]
comments: false
---

# 前言

使用sublime text编辑器编写es6代码的时候，左边出现蓝色小圆点提示，放上去提示
`jshint: W104 - 'const' is available in ES6 (use 'esversion: 6') or Mozilla JS extensions(use moz)`，我的代码如下:

```
const fs = require('fs');
const path = require('path');
const LRU = require('lru-cache');

```
<!-- more -->

经过挖掘，这里是解决这个问题
JSHint必须在项目的根目录中配置一个.jshintrc文件。只需使用以下对象在那里创建一个.jshintrc文件：
```
{ 
  "esversion": 6 
}
```
保存。问题解决了！