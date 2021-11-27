---
title: Hello World
tags: [hexo]
---
hexo： 

1. 发布文章
2. 插入图片

<!--more-->

### 发布文章

1. `hexo` 根目录执行命令：

  ``` bash
  hexo new "My New Post"
  ```

2. 生成静态资源，执行命令：

  ``` bash
  hexo generate
  ```


3. 发布至线上：

  ``` bash
  hexo deploy
  ```



### 插入图片

1. 编辑根目录下的配置文件 `_config.yml`，将  `post_asset_folder` 选项设置为 `true` ，新建文章的时候会同时创建一个同名文件夹用于放图片

2. 安装一个可以上传本地图片的插件，Hexo 根目录下执行命令：

   ```
   cnpm i hexo-asset-image -S
   ```

   