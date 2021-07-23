---
title: how to make a tinyhttpd
date: 2021-07-21 22:59:39
tags: [C++,Linux,HTTP]
categories: HTTP
index_img: /img/httpd.png
banner_img: /img/httpd.png
---
最近在寻找项目时看到了一关于TinyHttpd的介绍，于是自己就去GitHub上找了找，然后试着运行了一下。

<!-- more -->

# Manjaro下运行tinyhttpd

## 1、事前准备

### 1-1：从GitHub下载项目

`git clone https://github.com/cbsheng/tinyhttpd.git `(这是一份对新手更加友好的多注释版本)

### 1-2： 若下载运行时，出现 no cgi module错误，需要先安装CGI 。同时htdocs下的两个.cgi文件的`！#/usr/bin/local/perl`改为`!#/usr/bin/perl`(若是local文件夹下无文件时，需要更改否则无需更改)

可以先运行`perl -v`查看Perl版本，然后输入`perl -MCPAN -e shell`

此时会出现CPAN的安装确认，输入`yes`即可

最后在CPAN下，输入`install CGI`,到此为止项目应该可以正常运行且返回页面

## 2、原理解析

![](/img/picture.png)

### 2-1：建立套接字，确定端口号和ip地址等

### 2-2：监听请求

### 2-3：读取HTTP请求行信息，确定请求方法GET or POST

### 2-4：若是GET方法且不带传送的数据，则返回所请求的文件（文件部委可执行文件）（或者默认index.html）文件

### 2-5： 若是GET方法带传送的数据或POST方法，则运行CGI程序

### 2-6：GET方法读取内容并忽略请求剩下的内容

### 2-7：若是POST读取到Content-Length，若长度存在则返回状态码200

### 2-8：建立两个管道用于进程间通信

### 2-9：子进程中将标准输出重定向到写端，标准输入重定向到读端

### 2-10：父进程关闭写端和读端，若是POST方法，将body中内容写入管道，让子进程读取。从管道中读取子进程的输出，发送到客户端，关闭管道。

![](/img/httpdDetail.png)









