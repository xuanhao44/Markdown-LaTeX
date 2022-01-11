# 第一篇博客 & Markdown 学习

*实话说写这个让我有点犹豫。因为我在数不清的博客平台上写下了像这样的“第一篇博客”的文字，还是有一点心虚的。*

## 前言

今天主要是记录一下很久一段时间以来的 Markdown 的学习历程。

我在很久之前就已经听说了有 Markdown 这种标记语言，但是没有时间去细学。好不容易放假了，那我自然是不会放过学习 Markdown 的机会的。

我学习 Markdown 的主要动力其实是看到了在 GitHub 上创建一个 repo 时总会有的 **readme.md**，发现这种语言编写的文档有很多，也很流行。有别于 Word 这样的富文本编辑器，我觉得不用费心于格式这一点非常好。

*我很讨厌 Word 那些奇奇怪怪的格式，不过也可能是自己没用好的原因。*

我是在 <https://www.runoob.com/> 上学习 Markdown 的，教程写的还算不错，也可以在这个网站上学习其他的很多知识；另外我也参考了另外两个比较系统的 Markdown 教程：

> 1. [Markdown 语法及原理从入门到高级](https://zhuanlan.zhihu.com/p/99319314)
> 2. [Markdown 语法总结](https://blog.alexxinzhe.co/2020/08/03/markdown-yu-fa-zong-jie/)

在前一段时间，我主要是学习了 Markdown 的基础知识：标题、段落、列表、区块、链接和表格。至于 Markdown 的图床设置和内嵌的 HTML 的功能，我今天最大的成果是设置好了**腾讯云COS**的图床，以及初步了解学习了 **HTML**。

*看起来学的东西不多哈，主要是今天睡了很久。*

## 图床相关

### 插入图片

在说什么是图床之前还是先复习一下怎么插入图片吧。

*下面是我自己的语言描述的，如有不准确之处请指出。*

插入图片的**方式**有两种（另一说是三种，后面会提到）。一种是插入图片的本地路径（相对路径/绝对路径），另一种是插入图片的网址。前一种办法不灵活也不好分享，而后一种更适合发布分享以及管理。
插入图片的**语法**和插入链接的语法类似，有两种样式：

1. 行内式

   ```markdown
   ![Alt pic](/path/to/img.jpg)
   ```

2. 参考式

    ```markdown
    ![Alt pic]
    [id] [id]: url/to/image  "Optional title attribute"
    ```

最后谈一种神奇的把图片存入 Markdown 文件的办法，是我在 [Markdown语法及原理从入门到高级](https://zhuanlan.zhihu.com/p/99319314)里看到的：

> 用 base64转码工具把图片转成一段字符串
>  
> 把字符串填到基础格式中链接的那个位置
>  
> 由于图片转成 base64编码，会非常的大，一般至少都要上千行，这个时候会发现插入的这一长串字符串会把整个文章分割开，非常影响编写文章时的体验。这时候就可以用参考式，把大段的 base64字符串放在文章末尾，然后在文章中通过一个 id 来调用，文章就不会被分割的这么乱了。
>  
> 这种方法的优点就是图片真的是不会丢啊，相当于直接将图片编码嵌入到文档中，但缺点也是显而易见的，就是 base64编码实在是太长了啊，太长了，虽然可以放到文章结尾，但还是太长了，所以目前我还没找到更好的解决方法。

### 设置图床

将图片上传到网络服务器上得到这个图片的网址，这个服务器就是图床。图床有很多种，比如 SM.MS图床、腾讯云COS、GitHub图床、七牛图床、Imgur图床、阿里云OSS、又拍云图床等等。我这里选择的是腾讯云COS。

![腾讯云][腾讯云]

*腾讯云好像是有 50G的免费流量，具体的收费规则还没有细看，不过应该只是一笔小钱，而为方便的图床付费是值得的。*

设置流程在腾讯云的**产业人才培养中心**里有详细的讲解。[利用腾讯云COS作为图床为 Markdown 文档提供图片链接]

![利用腾讯云COS作为图床为Markdown文档提供图片链接][利用腾讯云COS作为图床为Markdown文档提供图片链接]

### PicGo插件

在查阅资料的时候了解了设置图床的插件 PicGo。能很方便的插入图片并得到图片的网址。

![PicGo][PicGo]

至于方便的程度还有待考量，如果像我一样使用腾讯云的话，其产品 **COSBrowser** 也是一个不错的选择。

![COSBrowser][COSBrowser]

## 后记

这是我第一次用 Markdown 来写文章，还是有点小小的成就感的。确实要多看多练。

虽然这在别人的眼里可能是微不足道的事情，但是我觉得对我来说意义重大。毕竟每个人生下来不是什么都会的，就是那些牛人们也是一步一个脚印的进步着的。我并不会无脑的膜拜他们，因为我知道我和这些人之间的距离只是时间和积累，而不是什么魔法和天赋之类的。

在选择图床的时候我首先考虑的是在 GitHub 上建立一个仓库，但是设置了很久之后还是没成功，目前不是很清楚是什么原因造成的这样的问题。之后才转而使用腾讯云，跟着产业人才培养中心的教程确实学习的很快，设置也很方便。

在 Markdown 写作软件的选择上，我主要是在考虑 **VS Code** 和 **Typora** 之间到底选择哪个的问题。Typora 很清爽，但是我并不是很喜欢所见即所得的模式；最后还是选择 VS Code，原因有二。

- 我本来就喜欢 VS Code 的界面布局，很顺手。

![VSCode界面][VSCode界面]

- 有方便的**插件**可供使用。比如 **markdownlint**，可以监督我 Markdown 语法的正确性和规范性。
正确性且不提，Markdown 语法的规范性确实是很重要的一点。我开始学习 Markdown 的时候，我就对标题的类Setext 语法和换行的语法的**随意程度**表示震惊。前者是使用“**任何数量**的 = 和 -”，后者是“按入**两个以上**的空格然后回车”。这样是极不规范的，所以可以使用 markdownlint 插件规范 Markdown 书写格式，此外阅读[语法规范提示内容](https://yijiebuyi.com/blog/79347d0e8c1739bd1f9d9d7c1dcbcccf.html#md001---heading-levels-should-only-increment-by-one-level-at-a-time)，可以找到不合规范的内容的代号和语法规范提示内容。

![不合规范的内容][不合规范的内容]

![语法规范提示内容][语法规范提示内容]

<!-- 图片 -->

[腾讯云]:https://typora-1304621073.cos.ap-guangzhou.myqcloud.com/typora/%E8%85%BE%E8%AE%AF%E4%BA%91.png
[腾讯云]:../_images/腾讯云.png

[利用腾讯云COS作为图床为 Markdown 文档提供图片链接]:https://typora-1304621073.cos.ap-guangzhou.myqcloud.com/typora/%E5%88%A9%E7%94%A8%E8%85%BE%E8%AE%AF%E4%BA%91COS%E4%BD%9C%E4%B8%BA%E5%9B%BE%E5%BA%8A%E4%B8%BAMarkdown%E6%96%87%E6%A1%A3%E6%8F%90%E4%BE%9B%E5%9B%BE%E7%89%87%E9%93%BE%E6%8E%A5.png
[利用腾讯云COS作为图床为Markdown文档提供图片链接]:../_images/利用腾讯云COS作为图床为Markdown文档提供图片链接.png

[PicGo]:https://typora-1304621073.cos.ap-guangzhou.myqcloud.com/typora/PicGo.png
[PicGo]:../_images/PicGo.png

[COSBrowser]:https://typora-1304621073.cos.ap-guangzhou.myqcloud.com/typora/COSBrowser.png
[COSBrowser]:../_images/COSBrowser.png

[VSCode界面]:https://typora-1304621073.cos.ap-guangzhou.myqcloud.com/typora/VSCode%E7%95%8C%E9%9D%A2.png
[VSCode界面]:../_images/VSCode界面.png

[不合规范的内容]:https://typora-1304621073.cos.ap-guangzhou.myqcloud.com/typora/%E4%B8%8D%E5%90%88%E8%A7%84%E8%8C%83%E7%9A%84%E5%86%85%E5%AE%B9.png
[不合规范的内容]:../_images/不合规范的内容.png

[语法规范提示内容]:https://typora-1304621073.cos.ap-guangzhou.myqcloud.com/typora/%E8%AF%AD%E6%B3%95%E8%A7%84%E8%8C%83%E6%8F%90%E7%A4%BA%E5%86%85%E5%AE%B9.png
[语法规范提示内容]:../_images/语法规范提示内容.png
