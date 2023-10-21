### 前言

目前latex编辑器不少，一些主流的编辑器有：

1. overleaf，优点很多就不说了，但是他有个让我完全无法接受的缺点：卡，写的越多交互界面越卡。尤其是肉身在国内的时候，有的时候半个小时连不上overleaf，还有写了一半连接断了没保存，着实令人崩溃。
  
2. texshop，丑
  
3. texpad，除了付费，没有缺点，富哥富姐不用往下看了
  
4. vscode+latex workshop，优点是基于vscode，可定制化程度高，可以把它变成任何你想要的样子，还可以做数值实验、写报告一个环境搞定。缺点就是配置起来麻烦。
  

综上，作为一个要求高的穷逼，除了vscode 配置麻烦这个缺点可以克服，其他的都不在我的考虑范围之内。根据教程感觉可以20分钟内搞定。

### 基础安装

首先我们先让vscode能编译latex文件

##### step1: 下载安装Tex Live

Windows装texlive，mac装mactex，windows用户记得把texlive可执行文件加入系统路径（加入之后重启电脑）。

[MacTeX - TeX Users Group](https://www.tug.org/mactex/mactex-download.html)

[Windows - TeX Live - TeX Users Group](https://www.tug.org/texlive/windows.html)

##### step2: 安装vscode和latex workshop

[vscode](vhttps://code.visualstudio.com/)

在左边栏点extension（拓展），搜latex，安装latex workshop

### 配置latex workshop

![WeChatddca1a09ea7e9701de24680d78e27aa0jpg](file:///Users/zhangxuanxi/Desktop/WeChatddca1a09ea7e9701de24680d78e27aa0.jpg?msec=1697902991544)

这里进去，点开配置文件是写json配置，或者点设置是交互式配置。按shift+cmd+P(windows shift+ctrl+P)拉下菜单栏，也可以进入配置。我把我的配置文件放在github上了，可以直接复制粘贴进你的json配置文件，一键搞定。

说几个重要的：

1. Tools 和recipes只能json编辑
  
2. autoBuild.run可以设置为“onSave”，保存时编译，同时搭配"files.autoSave": "onFocusChange"，真的很丝滑
  
3. recipe.default设置为“lastUsed”，使用上次一的recipe，方便来回切换
  
4. autoClean.run 建议为“onSucceeded”，方便debug，还看着干净。clean.fileTypes建议抄我的，不改的话，使用bib时会出问题。
  

### 配置 Snippests

这个玩意是用来设置模版，形成之前那个视频里的效果。shift+cmd+P(windows shift+ctrl+P)拉下菜单搜索snippests，进入后选择latex.json

![WeChat14eb57e7f328af8e7ad14214cec8253bjpg](file:///Users/zhangxuanxi/Desktop/WeChat14eb57e7f328af8e7ad14214cec8253b.jpg?msec=1697903770444)

可以直接复制我的配置，我放github了，大家也可以自己定制，大概说下怎么搞：

![WeChatbe8bc8630be83260dbf25a8a02f4f39fjpg](file:///Users/zhangxuanxi/Desktop/WeChatbe8bc8630be83260dbf25a8a02f4f39f.jpg?msec=1697903894296)

先随便起个名字（如“Simple Template”），prefix是确定这个模版的关键字，比如我打late打到一半系统会提示，按下tab键就填充模版了。body是填充的内容。我的配置文件里包含main tex、插入图片（以及subfigure）、插入表格、插入代码片段的模版。

### 配置Latex

我把所有的latex编译的配置信息都放在了math_commands.tex中，这个文件也在github自行下载，记得把input后的绝对路径改成你电脑中保存这个文件的路径。我的这个配置需要使用xelatex编译。因为是作业模版没有加引用文件。

这个是基于iclr的math command改的，可以提前熟悉一下，比如\vx是加粗的x，表示vector x；\sR是mathbb{R}，表示set R；\gB是mathcal{B}，表示graph B，一般用于集合的集合比如borel set。

我还在其中加入了listings的style配置，让输出的代码片段稍微好看一点，大家可以自己配置。引入代码使用\lstinputlisting{${file path}}，直接引用代码文件，不用复制。不过模版目前不支持中文，代码里有中文编译不了
