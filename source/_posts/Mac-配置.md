---
title: Mac 配置
date: 2020-07-13 18:39:30
tags: [Mac]
---

**记录下自己的 Mac 配置**

+ 几个小的配置
+ **xcode-select** 安装
+ **Homebrew** 安装
+ 快速查看插件
+ **Mac** 常用软件

<!--more-->

### 几个小的配置：

1. **在 Finder 中显示路径：**

   ```shell
   defaults write com.apple.finder ShowPathbar -bool true
   ```

2. **设定按键重复速率：**

   ```shell
   defaults write NSGlobalDomain KeyRepeat -int 0.02
   ```

3. **设置字符开始重复前的等待时间：**

   ```shell
   defaults write NSGlobalDomain InitialKeyRepeat -int 12
   ```

4. **显示 Library 文件夹：**

   ```shell
   chflags nohidden ~/Library
   ```

5. **禁止 .DS_store 产生：**

   ```shell
   # 重启生效
   defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool TRUE
   ```

### xcode-select 安装：

因为有许多工具（**git**、**Homebrew**...）依赖于 Command Line Tools，直接命令行执行 **`xcode-select --install`** 就行

当然，也可以直接安装 xcode 代替，xcode 依赖 Command Line Tools

### Homebrew安装：

直接运行 **Homebrew** 官网脚本安装会特别慢

咱们分几步进行安装：

1. 下载安装脚本至本地：

   ```shell
   curl -O https://raw.githubusercontent.com/Homebrew/install/master/install.sh
   ```

2. 修改 **install.sh** 文件中的 **BREW_REPO** 信息：

   ```shell
   BREW_REPO="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git"
   ```

3. 修改 **install.sh** 文件权限：

   ```shell
   chmod 777 install.sh
   ```

4. 执行脚本：

   ```shell
   ./install.sh
   ```

5.  **Homebrew** 镜像配置，提高下载速度：

   ```shell
   git -C "$(brew --repo)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git
   git -C "$(brew --repo homebrew/core)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git
   git -C "$(brew --repo homebrew/cask)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git
   ```

### 快速查看插件：

Mac 可以直接按住空格键快速预览图片，我们可以进行下拓展

```shell
# 命令行中执行下面的命令
brew cask install qlcolorcode qlstephen qlmarkdown quicklook-json qlimagesize suspicious-package quicklookase qlvideo
```

| 名称                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [QLColorCode](https://github.com/anthonygelibert/QLColorCode) | 高亮预览文件中的代码                                         |
| [QLStephen](https://github.com/whomwah/qlstephen)            | 查看没有文件扩展名的纯文本文件，像：README, CHANGELOG等      |
| [QLMarkdown](https://github.com/toland/qlmarkdown)           | 预览 Markdown 文件                                           |
| [QuickLookJSON](http://www.sagtau.com/quicklookjson.html)    | 预览 JSON 文件                                               |
| [QLImageSize](https://github.com/Nyx0uf/qlImageSize)         | 显示图片大小及分辨率                                         |
| [Suspicious Package](http://www.mothersruin.com/software/SuspiciousPackage/) | 预览 Apple 安装包的标准内容                                  |
| [QuickLookASE](https://github.com/rsodre/QuickLookASE)       | 预览使用Photoshop，Illustrator，Prisma等生成的Adobe ASE Color色板等 |
| [QLVideo](https://github.com/Marginal/QLVideo)               | 预览大多数类型的视频文件，以及它们的缩略图，封面和元数据     |



### Mac 常用软件：

| 名称                  | 描述                                                 |
| --------------------- | ---------------------------------------------------- |
| Chrome                | 浏览器                                               |
| Typora                | Markdown文本编辑                                     |
| Gas Mask              | Hosts 修改，github 图片经常会挂，可以修改 hosts 修复 |
| Visual Studio Code    | 代码编辑                                             |
| PyCharm               | Python IDE                                           |
| Homebrew              | 代码编辑                                             |
| Transmit              | FTP/SFTP                                             |
| Typinator             | 效率输入                                             |
| PandaVpn              | vpn                                                  |
| Free Download Manager | 下载（搭配 Chrome 对应插件使用）                     |
| Item2                 | 终端                                                 |
| Beyond Compare        | 文件对比                                             |
| Charles               | 抓包工具                                             |
| MindNode              | 思维导图                                             |
| Alfred                | 效率神器                                             |
| Pap.er                | 壁纸                                                 |
| Movist                | 视频播放器                                           |
| Yoinks                | 文件中转                                             |
| Magnet                | 窗口管理                                             |
| Foxmail               | 邮件客户端                                           |
| Appcleaner            | 应用卸载                                             |
| CheatSheet            | 快速查看快捷键                                       |

**参考指南：**

[Awesome Mac](https://github.com/jaywcjlove/awesome-mac/blob/master/README-zh.md)

[强迫症的 Mac 设置指南](https://github.com/macdao/ocds-guide-to-setting-up-mac)

[Homebrew 镜像使用帮助](https://mirrors.tuna.tsinghua.edu.cn/help/homebrew/)

[快速预览插件](https://github.com/sindresorhus/quick-look-plugins)

