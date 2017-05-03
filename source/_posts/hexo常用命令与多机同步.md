---
title: hexo常用命令与多机同步
category: Hexo
date: 2017-05-02
tags:
- Hexo
- 常用命令
- 多机同步
featured: true
---
hexo 极大地方便了博客的书写，并且能提供多种多样的主题😁。对于hexo常用的几个命令当然要非常熟练。

但是将hexo博客托管在github上后，发现多机同步跟想象中的不一样啊。hexo的deploy并没有在本地初始化git仓库，用的貌似是另外一套机制，而且博客原文并没有传到github上，传上去的是一些编译之后的html等文件，这样对于多机同时管理博客就有点不方便了。看样子有必要在本地重新配置一个git仓库，把必要的一些文件都传上去，这样子在另外一台电脑也可以开心地写博客了。

<!-- more -->

# hexo 常用命令
1. 初始化一个新博客
`hexo new post "name"`

2. 有必要的话可以先清除public文件夹
`hexo clean`

3. 编译博客
`hexo generate` or `hexo g`

4. 本地预览
`hexo server` or `hexo s`

5. 部署到远程服务器（一般为github）
`hexo deploy` or `hexo d`

# hexo设置多机同步
网上的[一些做法](http://www.jianshu.com/p/6fb0b287f950)将源文件和编译好的文件都放在一起，感觉有点乱，个人建议在github上还是重开一个仓库比较好。

所以在github上，新建一个repo，比如叫Blog-Hexo。

在本地你的Blog所在文件夹，初始化一个git仓库，修改 .gitignore 将必要的文件加入到该仓库中。
哪些文件是必要的呢？看一下本地，假设博客根目录记为‘／’，那么保证下面文件加入到repo中：
```
/_config.yml  ## 配置文件
/source/  ## 源文件夹
/themes/  ## 主题文件夹
/package.json  ## 应用程序的信息
/scaffolds/  ## 模版文件夹
```
主要命令如下:
```
git init
git add .
git remote add origin YOUR-GITHUB-REPO
git push -u origin master
```

接下去就可以在另外一台电脑上将刚刚的repo克隆下来，然后进入这个文件夹。

假设已经在这台电脑上安装好了hexo，安装教程在[这儿](https://hexo.io/docs/index.html)。

那么我们可以在该文件夹下执行：
```
npm install
npm generate
npm server
```
就可以验证我们在这台新机子上能不能正常编译和现实博客了～


