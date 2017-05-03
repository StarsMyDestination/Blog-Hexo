title: 使用Markdown写简历
category: Markdown
date: 2017-04-14
tags:
- Markdown
- 简历
lede: "转眼就要毕业，以前用学校模版写的简历现在看着怎觉得不顺眼，想着是不是可以用Markdown重新写一个。但是markdown的默认排版显然不够看的，可以用pandoc润色下，还能导出许多格式。但是自己一步步做挺麻烦的，还是去网上找模版吧，嘿哈～"
featured: true
---

转眼就要毕业，以前用学校模版写的简历现在看着怎觉得不顺眼，想着是不是可以用Markdown重新写一个。但是markdown的默认排版显然不够看的，可以用pandoc润色下，还能导出许多格式。但是自己一步步做挺麻烦的，还是去网上找模版吧，嘿哈～

<!-- more -->

# 万事Google起
直接看图片找吧，直接点。
![resume-google](/post_imgs/markdown-resume/1.png)
我从中圈出了几个自己看着还挺合适的，图片点进去一般都能找到相应的github仓库。
就选[这个](http://mszep.github.io/pandoc_resume/)吧！这是其[github](https://github.com/mszep/pandoc_resume)。

# 使用模版制作简历

参照github说明，先安装dependencies，ubuntu底下可以使用

```
sudo apt-get install pandoc context
```

然后

```
git clone https://github.com/mszep/pandoc_resume
cd pandoc_resume
vim resume.md   #insert your own resume info
make
```
便可以生成模版里面的简历。

接下去修改模版里的内容，英文简历改完后直接编译就可以。而中文简历修改完后可以成功编译但是pdf中中文不能正常显示，但是html可以正常显示中文，一个不是很完美的方案就是从html打印，另存为pdf。

下面这是我的简历截图：

resume-zh                    |  resume-en                 |
:----------------------------:|:-----------------------------:|
![](/post_imgs/markdown-resume/2.png)  |  ![](/post_imgs/markdown-resume/3.png) |

很遗憾这个简历没有照片，自己加的话貌似很麻烦，想要照片都是可以用[这个](https://github.com/barraq/pandoc-moderncv)模版。
