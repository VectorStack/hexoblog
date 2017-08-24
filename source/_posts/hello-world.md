---
title: Hexo + Github Pages 搭建个人博客
toc: true
tag:
- Node.js
- git
- hexo
- yilia
---
<img src="/assets/blogImg/hexo-blog.jpg" width="50%" > 


<!--more-->

## 系统环境配置

### 安装Node.js

<a href="https://nodejs.org/zh-cn/download/" target="_blank" rel="external">下载Node.js</a>
参考地址：<a href="http://www.w3cschool.cc/nodejs/nodejs-install-setup.html" target="_blank" rel="external">安装Node.js</a>

### 安装git

[下载git](https://git-scm.com/downloads)
参考地址：[安装git](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)

### 安装hexo

``` bash
$ cd d:/project/hexo   #进入文件夹
$ npm install hexo-cli -g   #全局安装hexo-cli模块
$ hexo init blog       #初始化hexo工程
$ cd blog              #进入生成的blog工程
$ npm install          #npm 安装package.json中的dependencies
$ hexo g  # 或者hexo generate 生成静态页面
$ hexo s  # 或者hexo server, 启动服务,浏览器输入网址http://localhost:4000/即可查看　
```

显示页面如下，则安装成功

<img src="/assets/blogImg/hexo-blog-1.png" width="50%" > 

注意：如果输入网址后没有响应,则可能4000端口占用,可使用以下命令切换端口
``` bash
$ hexo server -p 4001 #-p p指port,4001是新的端口
```

##  编写博客

新建博客

``` bash
#不要关闭服务控制台,新开控制台
$ cd d:/project/hexo/blog  #进入blog工程
$ hexo new "postName" #新建文章,"postName"是文章标题,可任意修改
#新建成功会在source\_posts新生成postName.md文件
```

打开postName.md文件，即可使用[Markdown](https://markdown-zh.readthedocs.io/en/latest/overview/)语法写博客啦！
刷新页面可查看文章哦！

## 部署
``` bash
```