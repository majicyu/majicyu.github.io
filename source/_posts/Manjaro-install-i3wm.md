---
title: Manjaro install i3wm
date: 2021-07-18 21:37:38
index_img: /img/i3wm.png
tags: [Manjaro,i3wm,Linux]
categories: Manjaro
---

由于本人是在vmware workstation pro15下安装的Manjaro Xfce桌面，所以可能与部分用户配置步骤和配置软件并不完全相同，具体情况大家可以去Arch Wiki查看或者直接查看相关软件的文档

# Manjaro下安装及美化i3wm



*简单设置后的样子*

![还行吧](https://raw.githubusercontent.com/majicyu/PicGoBed/main/img/20210711221519750.png)


## 1、安装软件

### 1-1、下载i3wm

`sudo pacman -S i3wm`

### 1-2、下载Dmenu

`sudo pacman -S dmenu`

### 1-3、下载终端alacritty

`sudo pacman -S alacritty`

### 1-4、下载渲染器picom

`sudo pacman -S picom`

### 1-5、下载图片查看器feh

`sudo pacman -S feh`

### 1-6、下载状态栏polybar

`sudo pacman -S polybar`

### 1-7、下载截图软件flameshot

`sudo pacman -S flameshot`

## 2、软件配置

### 2-1、i3配置

重启后选择**i3**桌面，两次选择都直接按**Enter**继续，进桌面以后按**win + Enter**打开终端，**win + d**打开dmenu，输入**firefox**可以打开浏览器

首先查看自己的i3默认配置文件

`cd /usr/share/doc/i3/`

`ls`

应该可以看到该文件夹下的**config**文件 ，将该文件复制到**.config**目录下的**i3**目录若没有**i3**目录，先创建目录

`cd ~/.config`

`mkdir i3`

`cd i3`

`cp /usr/share/doc/i3/config ./config`

编辑该配置文件，建议使用nano（至少知道怎么退出保存文件）

`nano config`

将`bindsym $mod+Return exec i3-sensible-terminal`中的`i3-sensible-terminal`改为**alacritty**(确保已经安装alacritty)

添加以下内容美化i3以及添加软件启动

`new_window  none`

`new_float normal`

`hide_edge_borders both`

`gaps inner 8`

`gaps outer 8`

首先下载几张图片到家目录的Pictures目录下，每次启动i3**feh**可以自动随机选取壁纸然后做为桌面

`exec --no-startup-id feh  --randomize --big-fill ~/Pictures/*.jpg`

`exec  --no-startup-id picom -b`

截图软件**flameshot**设置

`bindsym Print --release  exec /usr/bin/flameshot gui`

`for_window [class="flameshot"] floating enable`

### 2-2、alacritty的配置设置

进入**alacritty**配置文件(与i3配置文件类似，若.config目录下没有alacritty目录则自己创建，并把默认配置文件复制过来)

`cd ~/.config`

`mkdir alacritty`

`cp /usr/share/doc/alacritty/alacritty.yml ./alacritty.yml`

`nano alacritty.yml`

此时你打开终端alacritty可能会出现终端字体重叠现象，所以需要更改字体，个人建议将字体monospace更改为**Source Code Pro**

将配置文件中的**font**中的**family**改为**Source Code Pro**

以及将背景不透明度改为你自己喜欢的值

`background_opacity:0.5`

### 2-3、picom的配置

与上面相似，复制文件/usr/share/doc/picom/picom.conf.example到.config目录下的picom目录(没有目录自己创建一个)

`nano picom.conf`

`inactive-opacity = 0.7`

`active-opacity = 0.9`

设置活动窗口的不透明度基本可以了

### 2-4、polybar的配置

打开i3的配置文件

将配置文件最底下的i3bar配置注释

`#bar {`

`#...`

`#}`

在**.config**目录下创建polybar目录，并将polybar默认配置文件config复制过来

在**polybar**目录下创建文件launch.sh

`touch launch.sh`

`nano launch.sh`

加入以下内容

`killall polubar`

`polybar example`

然后在**i3配置文件**中加入以下内容

`exec --no-startup-id ~/.config/polybar/launch.sh`

重启后就能看到polybar的默认状态了(win + shift + r可以直接重启i3不需要重启整个linux)

### 2-5、flameshot

需要截图直接在终端使用

`flameshot gui`

## 3、常见问题

vm虚拟机可能会遇到分辨率问题或者其他问题，如果遇到以上一些软件的设置问题建议直接bing搜索软件名称进入官网查看文档，或者直接去archwiki查看相关软件基本配置，或者github的相关软件的wiki界面均可。

polybar的设置非常多样化，大家可以去官网看一看官方教程

i3wm的进一步使用也建议直接进官网查看

最后附上本人配置文件大家可以参考https://github.com/majicyu/.config
