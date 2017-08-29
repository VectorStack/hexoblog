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

### 新建博客

``` bash
#不要关闭服务控制台,新开控制台
$ cd d:/project/hexo/blog  #进入blog工程
$ hexo new "postName" #新建文章,"postName"是文章标题,可任意修改
#新建成功会在source\_posts新生成postName.md文件
```

打开postName.md文件，即可使用[Markdown](https://markdown-zh.readthedocs.io/en/latest/overview/)语法写博客啦！
刷新页面可查看文章哦！

### 添加目录

找到hemes/landscape/layout/_partial/article.ejs文件,在**<%- post.content %>**之前加入如下代码：
```bash
<!-- Table of Contents -->
<% if (!index && post.toc){ %>
<div id="toc" class="toc-article">
<strong class="toc-title">文章目录</strong>
<%- toc(post.content) %>
</div>
<% } %>
```

找到themes/landscape/source/css/_partial/article.styl,在文件的最后，添加如下代码：
```bash
/*toc*/
.toc-article
background #eee
border 1px solid #bbb
border-radius 10px
margin 1.5em 0 0.3em 1.5em
padding 1.2em 1em 0 1em
max-width 28%

.toc-title
font-size 120%

#toc
line-height 1em
font-size 0.9em
float right
.toc
padding 0
margin 1em
line-height 1.8em
li
list-style-type none

.toc-child 
margin-left 1em
```

打开新建的markdown文件,在文件开头添加**toc:true**
```bash
---
title: Hexo + Github Pages 搭建个人博客
toc: true
---
```

### 添加tag

打开新建的markdown文件,在文件开头添加tag
```bash
---
title: Hexo + Github Pages 搭建个人博客
toc: true
tag:    
- Node.js   #Node.js分类
- git       #git分类
- hexo      #hexo分类
- yilia     #yilia分类
---
```
## 部署

### 在github上新建Repository

建立与你用户名对应的仓库，仓库名必须为【your_user_name.github.io】，固定写法

### 修改_config.yml

翻到最下面，改成我这样子的
```bash
deploy:
     type: git
     repo: git@github.com:vectorstack/vectorstack.github.io.git
     branch: master
```
然后执行命令：
```bash
$ npm install hexo-deployer-git --save #安装模块
$ hexo generate  #生成静态页面
$ hexo deploy #部署到github上
```

## 更换主题

根据自己的喜好,选择不同的[主题](https://github.com/hexojs/hexo/wiki/Themes),我用的是[yilia](https://github.com/litten/hexo-theme-yilia)，使用如下：

### 安装
```bash
$ git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
```

### 配置
修改hexo根目录下的_config.yml  
```bash
theme: yilia
```
修改主题配置文件在主目录下的_config.yml,可根据自己需要修改使用,我的配置如下
```bash
# Header

menu:
  主页: /


# SubNav
subnav:
  github: "https://github.com/vectorstack"
  #weibo: "#"
  #rss: "#"
  #zhihu: "#"
  #qq: "#"
  weixin: "295253797"
  jianshu: "http://www.jianshu.com/users/b1de11fb5ecc/timeline"
  #douban: "#"
  #segmentfault: "#"
  #bilibili: "#"
  #acfun: "#"
  mail: "mailto:295253797@qq.com"
  #facebook: "#"
  #google: "#"
  #twitter: "#"
  #linkedin: "#"

rss: /atom.xml

# 是否需要修改 root 路径
# 如果您的网站存放在子目录中，例如 http://yoursite.com/blog，
# 请将您的 url 设为 http://yoursite.com/blog 并把 root 设为 /blog/。
root: 

# Content

# 文章太长，截断按钮文字
excerpt_link: more
# 文章卡片右下角常驻链接，不需要请设置为false
show_all_link: '展开全文'
# 数学公式
mathjax: false
# 是否在新窗口打开链接
open_in_new: false

# 打赏
# 打赏type设定：0-关闭打赏； 1-文章对应的md文件里有reward:true属性，才有打赏； 2-所有文章均有打赏
reward_type: 2
# 打赏wording
reward_wording: '谢谢你请我吃糖果'
# 支付宝二维码图片地址，跟你设置头像的方式一样。比如：/assets/img/alipay.jpg
alipay: 
# 微信二维码图片地址
weixin: 

# 目录
# 目录设定：0-不显示目录； 1-文章对应的md文件里有toc:true属性，才有目录； 2-所有文章均显示目录
toc: 1
# 根据自己的习惯来设置，如果你的目录标题习惯有标号，置为true即可隐藏hexo重复的序号；否则置为false
toc_hide_index: true
# 目录为空时的提示
toc_empty_wording: '目录，不存在的…'

# 是否有快速回到顶部的按钮
top: true

# Miscellaneous
baidu_analytics: ''
google_analytics: ''
favicon: /img/photo.png

#你的头像url
avatar: /img/photo.png

#是否开启分享
share_jia: true

#评论：1、多说；2、网易云跟帖；3、畅言；4、Disqus 不需要使用某项，直接设置值为false，或注释掉
#具体请参考wiki：https://github.com/litten/hexo-theme-yilia/wiki/

#1、多说
duoshuo: false

#2、网易云跟帖
wangyiyun: false

#3、畅言
changyan_appid: false
changyan_conf: false

#4、Disqus 在hexo根目录的config里也有disqus_shortname字段，优先使用yilia的
disqus: false

# 样式定制 - 一般不需要修改，除非有很强的定制欲望…
style:
  # 头像上面的背景颜色
  header: '#4d4d4d'
  # 右滑板块背景
  slider: 'linear-gradient(200deg,#a0cfe4,#e8c37e)'

# slider的设置
slider:
  # 是否默认展开tags板块
  showTags: false

# 智能菜单
# 如不需要，将该对应项置为false
# 比如
#smart_menu:
#  friends: false
smart_menu:
  innerArchive: '所有文章'
  friends: ''
  aboutme: '关于我'

friends:
  友情链接1: http://localhost:4000/
  友情链接2: http://localhost:4000/
  友情链接3: http://localhost:4000/
  友情链接4: http://localhost:4000/
  友情链接5: http://localhost:4000/
  友情链接6: http://localhost:4000/

aboutme: 很惭愧<br><br>只做了一点微小的工作<br>谢谢大家

archive: 2
```

