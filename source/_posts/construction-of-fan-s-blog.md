title: Hexo博客搭建
date: 2015-12-20 05:22:56
categories: [Hexo]
tags: [Hexo, Github]
---
该博客是通过Hexo搭建，部署在Github Pages上，并托管在Github。之前没接触过版本管理，趁这次机会一起学习了Git。

## [Hexo](https://hexo.io/)

> Hexo实际上是一个静态博客的框架。其搭建简单快速，仅需要几条命令，轻量级，并且功能比较全也比较优雅简洁，提供的主题也比较丰富。

### 安装配置

``` bash
$ npm install hexo-cli -g
$ hexo init [blog] #不指定目录则默认当前CWD
$ [cd blog]
$ npm install
$ hexo server #本地测试，localhost:4000
``` 

1. 安装Hexo前需要先安装[Node.js](https://nodejs.org/en/)和[Git](http://git-scm.com/)
2. 在命令行输入上方命令进行安装
3. Hexo博客配置，修改博客目录下`_config.yml`（全站配置）及主题目录`/themes`下`_config.yml`（主题相关配置）
4. [Hexo博客主题](https://github.com/hexojs/hexo/wiki/Themes)更换，将整个主题目录拷贝到你的Hexo博客目录下`/themes`中，修改全站配置`_config.yml`中字段：
`theme: your-theme-name`

<!--more-->

### 默认目录结构
	
	.
	├── .deploy
	├── public
	├── scaffolds
	├── scripts
	├── source
	|   ├── _drafts
	|   └── _posts
	├── themes
	├── _config.yml
	└── package.json

- .deploy：执行hexo deploy命令部署到GitHub上的内容目录
- public：执行hexo generate命令，输出的静态网页内容目录
- scaffolds：layout模板文件目录，其中的md文件可以添加编辑
- scripts：扩展脚本目录，这里可以自定义一些javascript脚本
- source：文章源码目录，该目录下的markdown和html文件均会被hexo处理。该页面对应repo的根目录，404文件、favicon.ico文件，CNAME文件等都应该放这里，该目录下可新建页面目录。
- _drafts：草稿文章
- _posts：发布文章
- themes：主题文件目录
- _config.yml：全局配置文件，大多数的设置都在这里
- package.json：应用程序数据，指明hexo的版本等信息，类似于一般软件中的关于按钮

### Hexo博客使用

	hexo --help                      #查看帮助
	hexo new [layout] "post-name"    #在_/posts下新建一篇博客文件post-name.md，使用Markdown语法在该文件中写入你的博客；简写hexo n
	hexo new page "page-name"        #新建一个网站页面文件
	hexo generate                    #编译生成静态网站文件，输出到/public；简写hexo g
	hexo deploy                      #将/public下的网站文件部署到全局配置中指定的git库；简写：hexo d
	hexo server                      #启动本地服务器测试 ；简写hexo s


## [Github Pages](https://pages.github.com/)

> 当你成功注册一个Github账号时，Github就给你分配了一个公网域名`your-account-name.github.io`，并自动与你账号下的库`your-account-name.github.io.git`关联起来。只需把网站文件部署在该库中，通过该公网域名即可访问你的网站。

### 部署Hexo博客到Github Pages

编辑全站配置文件`_config.yml`，修改deploy项，绑定你要部署的git库：

	deploy:
  	  type: git
  	  repository: https://github.com/your-account-name/your-account-name.github.io.git
  	  branch: master

使用命令`hexo deploy`将`/public`下网站文件部署到绑定的git库。

## 参考文献
* [Hexo系列教程](http://www.zipperary.com/categories/hexo/)
* [Hexo你的博客](http://ibruce.info/2013/11/22/hexo-your-blog/)
* [NexT使用文档](http://theme-next.iissnan.com/)
* [认识与入门Markdown](http://sspai.com/25137)