# LaTeX 公式学习

## 前言

### 学习参考

向同学学习是一个很好的办法。这里向 [SoraShu] 和 [ghj1222] 取经:smile:。

![SoraShu和ghj1222][SoraShu和ghj1222]

网上的教程也有，这里推荐一个[耿楠教授授权发布]的 LaTeX 的 B站视频教程。

![耿楠教授授权发布-LaTeX][耿楠教授授权发布-LaTeX]

再就是刘海洋写的超厚的一本书[《LaTeX入门》]。

![LaTeX入门][LaTeX入门]

可以供参考的内容有很多，但是要找到适合自己的内容却很难。不再多说，这里引用一句谚语，望大家记住。

> **博采众长,自成一体。**

### 学习目的

照例还是针对当前的学习情况进行分析，确定一下当前的学习目的。（学习新知后带来的认知和目的的变化且先不谈）

作为一个**计算机系**的学生，我将今后使用 LaTeX 的场景定位为：

1. 仅使用 LaTeX 处理数学公式，只将 LaTeX 作为 Markdown 文档中的一部分
2. 预计在 VS Code 中安装一系列的插件以支持 LaTeX 使用的各个方面的问题
3. 处理好 LaTeX 在各个平台上的渲染问题

认识虽是浅显或缺乏某些常识的，但是是我今后学习的一个指向，至少在完成此阶段的学习后要能很好的达成这些目的。

### 学习内容概述

同样是大致阅读了这本书。作出如下的判断。

《LaTeX入门》这本书确实很系统的讲了 LaTeX 的各个方面的知识，但是在该阶段只需要**把序、前言、第一章和第四章看或者学完**就可以了。下面说一下原因和学习的办法。

从序和前言我们就可以了解到 LaTeX 代表了**专业排版**，用于制作学术投稿、一般的学术书籍、学术报告幻灯片等等。说专业是因为其对排版的处理到达了**苛刻**的程度。为什么说苛刻呢?是因为它对文档的各种字符的字体、字号、间距、行距、段落等等都有十分详尽的设定要求，非常严谨。

接下来谈 **LaTeX 和 Markdown 之间的关系**。可以说关系不大。Markdown 可以说是简单的标记语言，而 LaTeX 是专业的标记语言（甚者算是编程语言），LaTeX 能做到的事情比 Markdown 多，也更复杂。例如《了不起的Markdown》和《LaTeX入门》这两本书，前者是**以 Markdown 为载体编写**的，后者则是**用 LaTeX 写的**（注意一下区别）；两者都提到了如何用 Markdown/LaTeX 来绘制图表、制作幻灯片等等。这些都是相似的。如果说 Markdown 比 LaTeX 明显的少了什么功能的话，那就是对数学公式的支持。这便是要**学习 LaTeX 的数学公式输入作为 Markdown 学习的补充**的原因。该书的作者本人也是这样说的。

> 排版数学公式是 TeX 系统设计的初衷，它在 LaTeX 中占有特殊的地位，也是 LaTeX 最为人所称道的功能之一。或许你已经尝试过许多在电子文档中输入公式的办法而不满意，或许你使用 LaTeX 就是冲着它输入公式的功能来的。

这本书的第一章是从熟悉 LaTeX，是从安装软件、编辑器和周边工具开始的。说真的，看完第一小节我头都大了。什么 CTeX，TeX Live 啊，TeXworks，SumatraPDF 之类的。复杂到就是把它当作介绍，我都不愿意去看。想想这只是个开始，后面的章节还有更多复杂的东西，我就心情十分复杂。

那么我为什么要你去看第一章呢？我知道光说道理是不够的，总有人觉得自己强到可以一次性完整的学完 LaTeX。看完第一章就能自己体会到上面说的道理了。（估计认真看完后学习 LaTeX 的信心能少一大半）

那么再回忆一下你为什么要学习 LaTeX。你是为了下载一些奇奇怪怪的软件，安装数不胜数的、奇奇怪怪的、多年不更新的宏包来学习 LaTeX 的吗？是为了从头开始对一个文档进行排版，死扣那一两个像素的间距来学习 LaTeX 的吗？不是的，**你是来学习如何在 Markdown 里使用 LaTeX 输入数学公式的**！粗略的说，LaTeX 在 Markdown 中的使用就如同行内代码和代码块一样，你只需要知道怎么用 LaTeX 输入数学就行了。

你又看向目录，发现整本书有用的是玩转数学公式这一章，其他的都暂时不用学......所以，**需要重点学习的部分就是第四章——玩转数学公式**。

## 正文

### VS Code 中 LaTeX 插件

要注意的是由于文档主体是 Markdown，LaTeX 只是其中的一部分，所以网上介绍的很多针对 .tex，也就是纯 LaTeX 的插件是不管用的。典型的如：LaTeX Workshop 和 LaTeX language support。

所以实际上有用的应该是一些支持 LaTeX 渲染的 Markdown插件，如 [Markdown Preview Enhanced] 插件，其使用 KaTex（或 MathJax）进行渲染，具体介绍见 [Markdown Preview Enhanced-数学]中的介绍。

> KaTeX 拥有比 MathJax 更快的性能，但是它却少了很多 MathJax 拥有的特性。

这里说明一下，**最好使用 MathJax 渲染**。需要到插件的设置中进行更改。原因是 KaTex 支持的数学公式的类型太少，不如 MathJax 全面；虽然 MathJax 的渲染速度比 KaTex 慢，但是两者相比，肯定是支持公式种类的多少更为重要。而且，大多数网站都是支持 MathJax 的，如博客园。

![选择MathJax渲染][选择MathJax渲染]

最后再啰嗦一句：**插件的文档好好看啊！不要嫌长就不看了**！

**[Markdown Preview Enhanced 中文文档]**

### LaTeX 数学公式

这个部分因为**太长了**，所以准备专门用一期的博客展示出来。**纯纯的手打**，把各种公式都熟悉了一遍。

传送门：[LaTeX公式学习]

### LaTeX 在各个平台上的渲染

在大多数博文平台上都是支持有限的 LaTeX 的，至于支持哪些，细节如何就不好一一列举了。正确的做法应该是自己去试一试。

举一个例子：[博客园对 LaTeX 的支持说明]

GitHub 对 LaTeX 的支持很差劲，并不支持 KaTeX 的渲染。SoraShu 给出的办法是本地生成了 PDF 再传上去。

为了应对某些无法支持 LaTeX 的编辑器，可以选择插入图片的方式将公式插入。这里推荐一个[在线 LaTeX 公式编辑器]，输入公式后可以导出渲染之后的公式的图片。

## 后记

学了这么多之后回头来看：自己真的学会 LaTeX 了吗？只拿 LaTeX 来输入公式做笔记有点大材小用了？

但我要说的是，我们目前学的内容其实是非常浅显的，真的不算很多。但是考虑到我们学习 LaTeX 的目的而言，早已经够用，已经算作是合格的入门了。还没有学习的部分，在实际的运用中是能学会的，所以不用担心。

以往在笔记中加入公式的办法是插入图片。而现在我们可以选择使用 LaTeX 来输入笔记。对于简单的公式尚可以如此，那更复杂的公式呢？估计很难处理。但实际上你不需要费劲心思自己想用什么命令和环境去输入，你可以去借鉴前人的工作成果。比如我们接下来将要学习的概率论和数理统计，网上现成的公式和符号的 LaTeX 公式数不胜数，直接复制过来就行了。

还有这样的例子[【无脑Latex数学公式】女朋友都能轻松掌握的公式大法]。这个人算是把**怎么输入公式而不是怎么用 LaTeX** 玩明白了。原则应该是怎么方便怎么来，不要被工具所束缚！

不过，一个很明显的前提是你要能大概看得懂 LaTeX 的语法，知道怎么将这段 LaTeX 代码插入，知道如何修改其中的一些小细节...我想这就是入门 LaTeX 的作用吧。

<!-- 网址和引用 -->

[SoraShu]:https://github.com/SoraShu

[ghj1222]:https://github.com/ghj1222

[耿楠教授授权发布]:https://www.bilibili.com/video/BV15b411j7Au

[《LaTeX入门》]:http://www.broadview.com.cn/book/1461

[Markdown Preview Enhanced]:https://github.com/shd101wyy/markdown-preview-enhance
[Markdown Preview Enhanced-数学]:https://shd101wyy.github.io/markdown-preview-enhanced/#/zh-cn/math

[Markdown Preview Enhanced 中文文档]:https://shd101wyy.github.io/markdown-preview-enhanced/#/

[博客园对 LaTeX 的支持说明]:https://www.cnblogs.com/cmt/p/3279312.html

[在线 LaTeX 公式编辑器]:https://latex.91maths.com/

[LaTeX公式学习]:https://www.cnblogs.com/xuanhao44/p/15039524.html

[【无脑Latex数学公式】女朋友都能轻松掌握的公式大法]:https://zhuyulab.blog.csdn.net/article/details/111302019

<!-- 图片 -->

[SoraShu和ghj1222]:https://typora-1304621073.cos.ap-guangzhou.myqcloud.com/typora/SoraShu%E5%92%8Cghj1222.png
[SoraShu和ghj1222]:../_images/SoraShu和ghj1222.png


[耿楠教授授权发布-LaTeX]:https://typora-1304621073.cos.ap-guangzhou.myqcloud.com/typora/%E8%80%BF%E6%A5%A0%E6%95%99%E6%8E%88%E6%8E%88%E6%9D%83%E5%8F%91%E5%B8%83-LaTeX.png
[耿楠教授授权发布-LaTeX]:../_images/耿楠教授授权发布-LaTeX.png

[LaTeX入门]:https://typora-1304621073.cos.ap-guangzhou.myqcloud.com/typora/LaTeX%E5%85%A5%E9%97%A8.jpg
[LaTeX入门]:../_images/LaTeX入门.png

[选择MathJax渲染]:https://typora-1304621073.cos.ap-guangzhou.myqcloud.com/typora/%E9%80%89%E6%8B%A9MathJax%E6%B8%B2%E6%9F%93.png
[选择MathJax渲染]:../_images/选择MathJax渲染.png
