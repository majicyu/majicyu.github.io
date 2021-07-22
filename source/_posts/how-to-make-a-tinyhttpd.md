---
title: how to make a tinyhttpd
date: 2021-07-21 22:59:39
tags: [C++,Linux,HTTP]
categories: HTTP
index_img: /img/httpd.png
banner_img: /img/httpd.png
---
最近在寻找项目时看到了一关于TinyHttpd的介绍，于是自己就去GitHub上找了找，然后试着运行了一下。

# Manjaro下运行tinyhttpd

## 1、事前准备

### 1-1： 从GitHub下载项目

`git clone https://github.com/cbsheng/tinyhttpd.git `(这是一份对新手更加友好的多注释版本)

### 1-2： 若下载运行时，出现 no cgi module错误，需要先安装CGI 。同时htdocs下的两个.cgi文件的`！#/usr/bin/local/perl`改为`!#/usr/bin/perl`(若是local文件夹下无文件时，需要更改否则无需更改)

可以先运行`perl -v`查看Perl版本，然后输入`perl -MCPAN -e shell`

此时会出现CPAN的安装确认，输入`yes`即可

最后在CPAN下，输入`install CGI`,到此为止项目应该可以正常运行且返回页面

## 2、原理解析











