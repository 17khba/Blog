---
title: VIM 快速入门
date: 2019-05-03 21:52:01
tags: [vim]
---

> 默认情况下的操作均为**普通模式**，命令前带有 `:` 表示该操作在**命令行模式**下进行



### 进入命令行模式

> 在**普通**模式下输入 `:`    



### 进入插入模式

> 在**普通**模式下使用下面的键可以进入插入模式，并可以从相应的位置开始输入

| 命令  | 说明                                                         |
| :--: | :----:                                                       |
| `i`  | 在当前光标处进行编辑                                            |
| `I`  | 在行首插入                                                    |
| `A`  | 在行末插入（after row）                                        |
| `a`  | 在光标后插入（after cursor）                                   |
| `o`  | 在当前行后插入新行（换行）                                       |
| `O`  | 在当前行前插入新行（对应 `vs code` 中的 `ctrl + shift + Enter`） |
| `cw` | 替换单词（从光标所在位置后到一个单词结尾的字符）                    |



### 光标移动

| 按键  |      说明       |
| :--: | :----:           |
| `h`  |    向左移动       |
| `l`  |    向右移动       |
| `j`  |    向下移动       |
| `k`  |       上         |
| `w`  | 移动到下个单词     |
| `b`  | 移动到上个单词     |




### 保存文档

> 在**命令行**模式，输入 `w` 回车，保存文档。输入 `:w 文件名` 可以将文档另存为其他文件名或存到其他路径下



### 退出 VIM

|       命令          |                       说明                     |
|      :--:          |                  :----:                        |
|      `:q!`         |                   强制退出，不保存               |
|      `:q`          |                      退出                      |
|      `:wq!`          |                  强制保存并退出                |
| `:w <路径 + 文件名>`   | 另存为（路径可省略；加上路径为另存为；不退出编辑器） |
| `:sav <路径 + 文件名>` | 另存为（路径可省略；加上路径为另存为；不退出编辑器） |
|       `:x`           |                  保存并退出                   |
|       `:wq`          |                  保存并退出                   |
|    `shift + zz`      |                   保存并退出                  |



### 普通模式下删除文本

| 命令        | 说明                       |
| :--:        | :----:                    |
| `x`         | 删除光标所在的字符           |
| `X`         | 删除光标所在的前一个字符      |
| `Delete`    | 同 `x`                    |
| `dd`        | 删除整行                   |
| `dw`        | 删除一个单词（不适用中文）    |
| `d$` 或 `D` | 删除至行尾                  |
| `d^`        | 删除至行首                  |
| `dG`        | 删除到文档结尾处             |
| `d1G`       | 删除文档首部（删除所有）      |

**删除多行**：`2dd`



### 重复执行上次命令

> 在普通模式下，`.` 表示重复上一次的命令操作



### 执行指定次数相同的命令

> 在普通模式下，`N + <命令>` N 表示重复后面命令的次数

```bash
# 删除 10 个字符
10x

# 删除 3 行文本
3dd
```



### 光标的快速跳转

1. **行间跳转**

| 命令               |   说明                                       |
| :--:              |   :----:                                     |
| `nG`（n Shift + g）| 移动到第 n 行（命令模式，输入 `:set nu` 显示行号） |
| `gg`              | 移动到第一行                                   |
| `G`               | 移动到最后一行                                 |

   

2. **行内跳转**

| 命令              | 说明                                    |
| :--:              | :----:                                 |
| `w`               | 到**下一个**单词的开头                    |
| `e`               | 到**当前**单词的结尾                      |
| `b`               | 到前一个单词的开头                        |
| `ge`              | 到前一个单词的结尾                        |
| `0` 或 `^`        | 到行头                                  |
| `$`               | 到行尾                                  |
| `f`<字母>          | 向后搜索<字母>并跳转到第一个匹配的位置       |
| `F`<字母>          | 向前搜索<字母>并跳转到第一个匹配的位置       |
| `t`<字母>          | 移动到光标右边的指定字符之前                |
| `T`<字母>          | 移动到光标右边的指定字符之后                |



### 文本编辑

1. **选择文本**

   在普通模式下使用 `v` 键进入可视模式便可进行文本的选择；

| 命令            | 说明           |
| :--:           | :----:         |
| `v` + 光标移动   | 高亮选择文本    |
| `V`            | 按行选择        |

   `选择文本后使用 y 键，可复制文本`

2. **复制文本**

   普通模式下使用 `y` 复制

| 命令          | 说明                                  |
| :--:         | :----:                                |
| `yy`         | 复制光标所在行（`3yy` 表示复制 3 行）      |
| `y^` 或 `y0` | 复制至行首（不含光标所在处字符）            |
| `y$`         | 复制至行尾（含光标所在处字符）              |
| `yw`         | 复制一个单词                             |
| `y2w`        | 复制两个单词                             |
| `yG`         | 复制至文本末                             |
| `y1G`        | 复制至文本开头                           |

3. **粘贴文本**

   普通模式中使用 `p` 粘贴

| 命令  | 说明               |
| :--: | :----:             |
| `p`  | 粘贴至光标后（下）    |
| `P`  | 粘贴至光标前（上）    |

4. **剪切文本**

   普通模式中使用 `dd`

5. **撤销**

| 命令  | 说明           |
| :--: | :----:         |
| `u`  | 撤销            |


### 快速缩进

| 命令                      | 说明             |
| :--:                      | :----:         |
| `>>`                      | 整行将向右缩进   |
| `<<`                      | 整行将向左缩进   |
| `:sw=2` （:shiftwidth=2） | 控制缩进字符数   |
| `:ce`                     | 使本行文本居中   |
| `:ri`                     | 使本行文本右对齐 |
| `:le`                     | 使本行文本左对齐 |



### 查找

| 命令                | 说明                                   |
| :--:               | :----:                                |
| `/ + 字符串`        | 向下查找匹配内容                         |
| `? + 字符串`        | 向上查找匹配内容                         |
| `? + 字符串`  + `n` | 查找下一项匹配内容                       |
| `? + 字符串`  + `N` | 查找上一项匹配内容                       |
| `:noh`              | 取消搜索                               |
| `\*`                | 向下匹配光标所在处的单词                 |
| `\#`                | 向上匹配光标所在处的单词                 |
| `g\*`               | 向下匹配光标所在处的单词（部分匹配即可）    |
| `g\#`               | 向上匹配光标所在处的单词（部分匹配即可）    |



### 小技巧
```bash
# 普通模式下，快速回到上一次光标所在位置
ctrl + o

# 普通模式下，切换光标所在字母大小写
~

# 打开语法高亮
:syntax on

# 显示行号
:set nu
```



**参考：**

[实验楼 VIM 编辑器][vim]

[vim]: https://www.shiyanlou.com/courses/2	"vim"