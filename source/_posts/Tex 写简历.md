title: 使用Tex写简历
category: Tex
date: 2017-04-16
tags:
- Tex
- 简历
lede: "上一期写的简历被吐槽了，只好再寻思着改进一下。还是不愿意用word，那就更近一步，用Tex写吧。之后写论文估计也得用LaTex，先入坑再说吧～"
featured: true
---

上一期写的简历被吐槽了，只好再寻思着改进一下。还是不愿意用word，那就更近一步，用Tex写吧。之后写论文估计也得用LaTex，先入坑再说吧～

<!-- more -->

# 装软件😵
比较推荐下面的Tex发行版

1. TeXLive (Unix/Linux/Windows)
2. MacTeX (Mac OSX)
3. MiKTeX (Windows)

装完后一般Tex引擎有pdfTex，TeTeX，LuaTeX等，我也是小白，不会用，基本上知道TeTex引擎是pdfTeX的一个升级版，更具体的信息可以看看自带的`READ ME FIRST.pdf`。前端可以用自己喜欢的编辑器或者是LaTeXiT和TeXShop编辑自己的简历，我用的是subliem再加个Latexing插件。
# 使用模版制作简历
当然不是从零写起，还是从模版里面改。

Tex有个有名的简历模版，叫[mordencv](http://www.ctan.org/pkg/moderncv)。如果我们安装完整版的Tex，那么moderncv这个宏包是已经安装好了的，在目录/usr/local/texlive/2016/texmf-dist/doc/latex下。将example拷出来到一个你喜欢的位置，我们使用template.tex进行修改。
```Tex
\documentclass[11pt,a4paper,sans]{moderncv}        % possible options include font size ('10pt', '11pt' and '12pt'), paper size ('a4paper', 'letterpaper', 'a5paper', 'legalpaper', 'executivepaper' and 'landscape') and font family ('sans' and 'roman')

% moderncv themes
\moderncvstyle{casual}                             % style options are 'casual' (default), 'classic', 'banking', 'oldstyle' and 'fancy'
\moderncvcolor{blue}                               % color options 'black', 'blue' (default), 'burgundy', 'green', 'grey', 'orange', 'purple' and 'red'
%\renewcommand{\familydefault}{\sfdefault}         % to set the default font; use '\sfdefault' for the default sans serif font, '\rmdefault' for the default roman one, or any tex font name
%\nopagenumbers{}                                  % uncomment to suppress automatic page numbering for CVs longer than one page

% character encoding
%\usepackage[utf8]{inputenc}                       % if you are not using xelatex ou lualatex, replace by the encoding you are using
%\usepackage{CJKutf8}                              % if you need to use CJK to typeset your resume in Chinese, Japanese or Korean

% adjust the page margins
\usepackage[scale=0.75]{geometry}
%\setlength{\hintscolumnwidth}{3cm}                % if you want to change the width of the column with the dates
%\setlength{\makecvtitlenamewidth}{10cm}           % for the 'classic' style, if you want to force the width allocated to your name and avoid line breaks. be careful though, the length is normally calculated to avoid any overlap with your personal info; use this at your own typographical risks...

% personal data
\name{John}{Doe}
\title{Resumé title}                               % optional, remove / comment the line if not wanted
\address{street and number}{postcode city}{country}% optional, remove / comment the line if not wanted; the "postcode city" and "country" arguments can be omitted or provided empty
\phone[mobile]{+1~(234)~567~890}                   % optional, remove / comment the line if not wanted; the optional "type" of the phone can be "mobile" (default), "fixed" or "fax"
\phone[fixed]{+2~(345)~678~901}
\phone[fax]{+3~(456)~789~012}
\email{john@doe.org}                               % optional, remove / comment the line if not wanted
\homepage{www.johndoe.com}                         % optional, remove / comment the line if not wanted
\social[linkedin]{john.doe}                        % optional, remove / comment the line if not wanted
\social[twitter]{jdoe}                             % optional, remove / comment the line if not wanted
\social[github]{jdoe}                              % optional, remove / comment the line if not wanted
\extrainfo{additional information}                 % optional, remove / comment the line if not wanted
\photo[64pt][0.4pt]{picture}                       % optional, remove / comment the line if not wanted; '64pt' is the height the picture must be resized to, 0.4pt is the thickness of the frame around it (put it to 0pt for no frame) and 'picture' is the name of the picture file
\quote{Some quote}       
```
这是一个大致的导言，相应的说明已经很详细了。如果有什么不明白的也可以参考[这篇博文](https://www.xiangsun.org/tex/notes-on-moderncv)。
我选择的是classic这个模版，一个原因是因为这个模版有照片，排版也比较舒服；另外一个是这个模版对中文支持比较好，后面写中文简历遇到了字体麻烦，没时间解决。恰好classic模版不需要安装新字体也能编译，就先用这个模版，后面还总是要填这个坑，先把几个找好的链接放上，估计有用，[字体安装](https://github.com/sebschub/FontPro)，另外还有[中文版Tex](http://www.ctex.org/HomePage)。

这是我的英文版简历导言设置：

```Tex
\documentclass[11pt,a4paper,sans, colorlinks, linkcolor=true]{moderncv}        % possible options include font size ('10pt', '11pt' and '12pt'), paper size ('a4paper', 'letterpaper', 'a5paper', 'legalpaper', 'executivepaper' and 'landscape') and font family ('sans' and 'roman')

% moderncv themes
\moderncvstyle{classic}                             % style options are 'casual' (default), 'classic', 'banking', 'oldstyle' and 'fancy'
\moderncvcolor{green}                               % color options 'black', 'blue' (default), 'burgundy', 'green', 'grey', 'orange', 'purple' and 'red'
%\renewcommand{\familydefault}{\sfdefault}         % to set the default font; use '\sfdefault' for the default sans serif font, '\rmdefault' for the default roman one, or any tex font name
\nopagenumbers{}                                  % uncomment to suppress automatic page numbering for CVs longer than one page

% character encoding
% \usepackage[utf8]{inputenc}                       % if you are not using xelatex ou lualatex, replace by the encoding you are using
% \usepackage{CJKutf8}                              % if you need to use CJK to typeset your resume in Chinese, Japanese or Korean

% adjust the page margins
\usepackage[scale=0.75]{geometry}
\setlength{\hintscolumnwidth}{2.65cm}                % if you want to change the width of the column with the dates
%\setlength{\makecvtitlenamewidth}{10cm}           % for the 'classic' style, if you want to force the width allocated to your name and avoid line breaks. be careful though, the length is normally calculated to avoid any overlap with your personal info; use this at your own typographical risks...

\AfterPreamble{\hypersetup{baseurl={}}}

% personal data
\name{Jianyun}{Xu}
\title{Shanghai Jiao Tong University}                               % optional, remove / comment the line if not wanted
\address{Minhang, Shanghai}% optional, remove / comment the line if not wanted; the "postcode city" and "country" arguments can be omitted or provided empty
\phone[mobile]{+86~18817519583}                   % optional, remove / comment the line if not wanted; the optional "type" of the phone can be "mobile" (default), "fixed" or "fax"
% \phone[fixed]{+2~(345)~678~901}
% \phone[fax]{+3~(456)~789~012}
\email{xujianyun1001@sjtu.edu.cn}                               % optional, remove / comment the line if not wanted
\homepage{starsmydestination.github.io}                         % optional, remove / comment the line if not wanted
\social[linkedin][www.linkedin.com/in/\%E5\%BB\%BA\%E4\%BA\%91-\%E5\%BE\%90-a3bab3140/?locale=en_US]{Jianyun Xu}                        % optional, remove / comment the line if not wanted
% \social[twitter]{jdoe}                             % optional, remove / comment the line if not wanted
\social[github][https://github.com/StarsMyDestination]{StarsMyDestination}                              % optional, remove / comment the line if not wanted
% \extrainfo{additional information}                 % optional, remove / comment the line if not wanted
\photo[60pt][0.2pt]{avatar}                       % optional, remove / comment the line if not wanted; '64pt' is the height the picture must be resized to, 0.4pt is the thickness of the frame around it (put it to 0pt for no frame) and 'picture' is the name of the picture file
\quote{Enthusiastic with \textbf{self-driving system}, \textbf{machine learning}, \textbf{deep learning} and \textbf{data science}}   
```
这是我的中文版简历导言设置：

```Tex
\documentclass[11pt,a4paper,sans, colorlinks, linkcolor=true]{moderncv}        % possible options include font size ('10pt', '11pt' and '12pt'), paper size ('a4paper', 'letterpaper', 'a5paper', 'legalpaper', 'executivepaper' and 'landscape') and font family ('sans' and 'roman')

% moderncv themes
\moderncvstyle{classic}                             % style options are 'casual' (default), 'classic', 'banking', 'oldstyle' and 'fancy'
\moderncvcolor{green}                               % color options 'black', 'blue' (default), 'burgundy', 'green', 'grey', 'orange', 'purple' and 'red'

% adjust the page margins
\usepackage[scale=0.75]{geometry}
\setlength{\hintscolumnwidth}{2.65cm}                % if you want to change the width of the column with the dates
%\setlength{\makecvtitlenamewidth}{10cm}           % for the 'classic' style, if you want to force the width allocated to your name and avoid line breaks. be careful though, the length is normally calculated to avoid any overlap with your personal info; use this at your own typographical risks...

\AfterPreamble{\hypersetup{baseurl={}}}

\usepackage{fontspec}
\usepackage{xunicode}
\usepackage{xeCJK}
% \setmainfont{Minion Pro}
% \setsansfont{Myriad Pro}
\setmonofont{Courier New}
% \setCJKmainfont{SimSun}
% \setCJKsansfont{KaiTi}
% \setCJKmonofont{SimHei}
%\setCJKmathfont{}


% personal data
\name{徐建云}{}
\title{上海交通大学}                               % optional, remove / comment the line if not wanted
\address{上海, 闵行}% optional, remove / comment the line if not wanted; the "postcode city" and "country" arguments can be omitted or provided empty
\phone[mobile]{+86~18817519583}                   % optional, remove / comment the line if not wanted; the optional "type" of the phone can be "mobile" (default), "fixed" or "fax"
% \phone[fixed]{+2~(345)~678~901}
% \phone[fax]{+3~(456)~789~012}
\email{xujianyun1001@sjtu.edu.cn}                               % optional, remove / comment the line if not wanted
\homepage{starsmydestination.github.io}                         % optional, remove / comment the line if not wanted
\social[linkedin][www.linkedin.com/in/\%E5\%BB\%BA\%E4\%BA\%91-\%E5\%BE\%90-a3bab3140/]{Jianyun Xu}                        % optional, remove / comment the line if not wanted
% \social[twitter]{jdoe}                             % optional, remove / comment the line if not wanted
\social[github][https://github.com/StarsMyDestination]{StarsMyDestination}                              % optional, remove / comment the line if not wanted
% \extrainfo{additional information}                 % optional, remove / comment the line if not wanted
\photo[60pt][0.2pt]{avatar}                       % optional, remove / comment the line if not wanted; '64pt' is the height the picture must be resized to, 0.4pt is the thickness of the frame around it (put it to 0pt for no frame) and 'picture' is the name of the picture file
\quote{热爱\textbf{自动驾驶技术}, \textbf{机器学习}, \textbf{深度学习} 以及 \textbf{数据科学}}                                 % optional, remove / comment the line if not wanted
```

其中

	\AfterPreamble{\hypersetup{baseurl={}}}
这句话是为了让各个链接在pdf中能正常打开，去掉moderncv里内置的`baseurl=http://`
	
选颜色可以参考[这个网站](http://colorblender.com/)

对于Latex中的各种语法可以参照[这张cheatsheet](https://wch.github.io/latexsheet/latexsheet.pdf)


# 编译
编译生成PDF文件。LaTeX专用的编辑器，比如上文中提到的Latexit和TeXShop中是自带相关生成选项的，也可以在Terminal中运行。一般情况下，使用pdflatex，xelatex就好，已生成的个人简历PDF文件会存放在与你所编译的*.tex文件的所存放的目录（同级目录）。（在编译过程中会有一些其他的文件，可以把这些文件删除掉。）我用的是xelatex，如在terminal中输入：
	
	xelatex template.tex


# 最后的预览图：

resume-zh                    |  resume-en                 |
:----------------------------:|:-----------------------------:|
![](/post_imgs/tex-resume/1.png)  |  ![](/post_imgs/tex-resume/2.png) |

