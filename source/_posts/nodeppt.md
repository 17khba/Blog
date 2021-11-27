---
title: nodeppt
date: 2019-05-03 23:01:04
tags: [node, nodeppt]
---

![nodeppt.gif](/nodeppt/nodeppt.gif)

<!--more-->

[demo](http://js8.in/nodeppt/)
[nodeppt 文档](https://github.com/ksky521/nodeppt)

> 网页版PPT，适合做一些技术分享


### 安装依赖
```bash
cnpm i -g nodeppt
```

### 创建步骤
1. 创建网页幻灯片命令
```bash
nodeppt create ppt-name
```
2. 基本配置
```markdown
title: 技术分享
speaker: 狂欢
transition: slide3
files: /css/demo.css
theme: light
date: 2017年08月11日
```
3. 预览命令
```bash
nodeppt start
```
4. 以`html`文件导出
```bash
# 导出全部，包括nodeppt的js、img和css文件夹
# 默认导出在publish文件夹
nodeppt generate ./ppts/demo.md -a
# 指定导出文件夹
nodeppt generate ./ppts/demo.md output/path -a
```