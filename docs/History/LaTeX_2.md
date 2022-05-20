# $\LaTeX$ 公式

## 1 数学模式和文本模式

### 1.1 行内公式 / 正文数学公式

使用**单个美元符号** `$...$` 来表示。

交换律是 $ a+b=b+a $，如 $ 1+2=2+1=3 $

### 1.2 行间公式 / 显示数学公式 / 列表公式

使用 `\[ ... \]` 或者 `$$...$$` 来表示。

交换律
$$
a+b=b+a,
$$
如
$$
1+2=2+1=3.
$$

虽然书上说用 `$$...$$` 不够严谨，应当避免使用，但是大多数的编译器只能识别 `$$...$$` 而不能识别 `\[ ... \]`，比如博客园和 VS Code 自己的 OpenPreview 都是无法识别的。考虑到本身使用的并不是多么严谨的 $\LaTeX$，就还是使用 `$$...$$` 了；另外最好**把单独占据一行的显示公式放在单独的行内**。

### 1.3 数学模式和文本模式混合

数学模式和文本模式不同。数学模式会**改变字符字体和间距**，还会**忽略空格**，汉字和西文文本也**不能直接输入**。

在数学公式中插入汉字：**\text{汉字...}** 命令

$$
\text{被减数} - \text{减数} = \text{差}
$$

## 2 数学结构

### 2.1 上标和下标

上标和下标是常见的数学结构。上标可位于符号的右上方或者正上方；下标可位于符号的右下方或者正下方。

#### 2.1.1 单字符和多字符

上标用特殊字符 **^** 表示，下标用特殊字符 **_** 表示。

$$
a_0 = 3^2
$$

当上标和下标多于一个字符时，需要使用 **{...}** 分组确定上下标范围。

$$
A_{ij} = 2^{i+j}
$$

式子中的空格（包括单个换行）是没有实际作用的，但是适当的空格可以将代码分隔的好看些。

*我建议都使用 **{...}** 的，毕竟这也很符合编程的规范。*

#### 2.1.2 上下标的同时使用和嵌套

同时使用

$$
A_{i}^{k}
$$

嵌套

$$
3^{3^{\cdot^{\cdot^{\cdot^3}}}}
$$

#### 2.1.3 特殊的两种上标

##### 撇号

要注意四点：

1. 可用符号 **\prime** 表示
2. 可以连续使用
3. 可以与下标混用
4. 不能与上标直接混用，要加上 **{...}**

一般撇号

$$
a = a'
$$

与下标混用 & 连续使用

$$
b_0' = b_0''
$$

不能与上标直接混用

$$
{c'}^2 = (c')^2
$$

##### 角度

没有直接表示角度的符号，用符号 **\circ** 的上标表示。

$$
A = 90^\circ
$$

#### 2.1.4 其他

在显示公式中，多数数学算子的上下标在正下方或者正上方；

$$
\max_n f(n) = \sum_{i=0}^n A_i
$$

但对积分号等个别算子，显示公式中的上下标也在右上右下角。

$$
\int_0^1 f(t) d\ t = \iint_D g(x,y) d\ x d\ y
$$

在行内公式中，所有数学算子的上下标都在角标的位置，如将上面一个式子放入行内将得到 $ \max_n f(n) = \sum_{i=0}^n A_i $ 。

#### 2.1.5 上下划线和花括号

上划线：**\overline**；下划线：**\underline**

$$
\overline{a+b} = \overline a + \overline b
$$

$$
\underline a = (a_0, a_1, a_2, \dots)
$$

而且这种结构可以任意嵌套或与其他数学结构组合。

$$
\overline{\underline{\underline a} + \overline{b}^2} - {\underline n}
$$

在公式上下加箭头的命令，使用方法与 **\overline** 和 **\underline** 没有区别。

上左箭头：**\overleftarrow**

$$
\overleftarrow{a+b}
$$

上右箭头：**\overrightarrow**
$$
\overrightarrow{a+b}
$$

下左箭头：**\underleftarrow**

$$
\underleftarrow{a+b}
$$

下右箭头：**\underrightarrow**

$$
\underrightarrow{a+b}
$$

使用 **\overbrace** 和 **\underbrace** 带上花括号。

$$
\overbrace{a+b+c} = \underbrace{1+2+3}
$$

使用上下标在花括号上作标注。

$$
( \overbrace{a_0,a_1,\dots,a_n}^{\text{共 $n+1$ 项}}) = ( \underbrace{0,0,\dots,0}_{n},1)
$$

花括号交错暂时不考虑。

### 2.2 分式

分式也是很常见的结构。分式用 **\frac 分子分母** 得到。

$$
\frac 12 + \frac 1a = \frac{2+a}{2a}
$$

在行内公式中,分式的分子分母都会用较小的字号排版,以免超出文本行高度。如：通分计算 $ \frac 12 +\frac 1a $ 得 $ \frac{2+a}{2a} $

已经在分子或者分母内的公式，也会按行内公式大小排版。

$$
\frac {1}{\frac 12 {(a+b)}} = \frac {2}{a+b}
$$

如果还是需要指定较大或者较小的样式，则使用显示样式命令 **\dfrac** 和 **\tfrac**。

$$
\tfrac 12 f(x) = \frac {1}{\dfrac 1a + \dfrac 1b + c}
$$

连分式使用 **\cfrac**。~~还有三个参数 **l**，**c**，**r**表示左中右对齐，并且默认是居中。~~ 并不是所有地方支持，谨慎使用。

*注：博客园中可使用，但是 OpenPreview 中无法识别参数。*

无参数

$$
\cfrac{1}{1+\cfrac{2}{1+\cfrac{3}{1+x}}}
$$

有参数
$$
\cfrac[r]{1}{1+\cfrac{2}{1+\cfrac[l]{3}{1+x}}}
$$

#### 2.2.1 二项式系数

类似分数分成上下两半的数学结构。使用 **\binom** 来输入二项式系数，其用法和 **\frac** 相似。

$$
(a+b)^2 = \binom 20 a^2 +\binom 21 ab + \binom 22 b^2
$$

也有指定大小的形式 **\tbinom** 和 **\dbinom**。

$$
(a+b)^2 = \tbinom 20 a^2 \tbinom 21 ab + \tbinom 22 b^2
$$

#### 2.2.2 其余类分式数学结构

略。

### 2.3 根式

使用单参数指令 **\sqrt** 得到，可用 $[number]$ 在 **sqrt** 后带一个参数，表示开方次数。

$$
\sqrt 4 =\sqrt[3]{8} =2
$$

嵌套使用根式是相当常见的。

$$
\sqrt[n]{\frac{x^2+\sqrt 2}{x+y}}
$$

开方的次数表示若复杂则应使用等价的指数形式。

$$
(x^p+y^q)^{\frac{1}{1/p+1/q}}
$$

### 2.4 矩阵和行列式

#### 2.4.1 矩阵环境

矩阵的括号可以是方括号，也可以是圆括号，还可以是大括号,甚至没有括号等等。括号的不同就是矩阵环境的不同。

matrix 环境

$$
\begin{matrix}
a & b \\
c & d
\end{matrix}
$$

bmatrix 环境

$$
\begin{bmatrix}
a & b \\
c & d
\end{bmatrix}
$$

vmatrix 环境

$$
\begin{vmatrix}
a & b \\
c & d
\end{vmatrix}
$$

pmatrix 环境

$$
\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
$$

Bmatrix 环境

$$
\begin{Bmatrix}
a & b \\
c & d
\end{Bmatrix}
$$

Vmatrix 环境

$$
\begin{Vmatrix}
a & b \\
c & d
\end{Vmatrix}
$$

#### 2.4.2 常规表示

不同的列用符号 **&** 分隔，行用 **\\\\** 分隔。

$$
A =
\begin{pmatrix}
a_{11} & a_{12} & a_{13} \\
0 & a_{22} & a_{23} \\
0 & 0 & a_{33}
\end{pmatrix}
$$

矩阵中常常使用各种省略号，即 **\dots**，**\vdots**，**\ddots** 等。

$$
A =
\begin{bmatrix}
a_{11} & \dots & a_{1n} \\
& \ddots & \vdots \\
0 &  & a_{nn}
\end{bmatrix}_{n \times n}
$$

#### 2.4.3 分块矩阵

分块矩阵可以理解为矩阵的嵌套。

$$
\begin{pmatrix}
    \begin{matrix}
    1 & 0\\
    0 & 1
    \end{matrix}
    & \text{\Large 0}\\
    \text{\Large 0} &
    \begin{matrix}
    1 & 0\\
    0 & -1
    \end{matrix}
\end{pmatrix}
$$

#### 2.4.4 矩阵的其他用法

在行内公式中使用很小的矩阵，用的矩阵环境是 **smallmatrix** 环境。

矩阵在行内表示 $
\begin{smallmatrix}
x & -y \\
y & x
\end{smallmatrix}
$，但是没有括号。

用 **\substack** 命令排版列矩阵，用以处理多行内容的插入。

$$
\sum_{\substack{0<i<n \\0<j<i}} A_{ij}
$$

或者是用 **\subarray** 指令，还必须指定对齐方式为 **l（左对齐）**，**c（居中）**，**r（右对齐）**。

$$
\sum_{
\begin{subarray}{l}
i<10 \\
j<100 \\
k<1000
\end{subarray}
} X(i,j,k)
$$

## 3 符号和类型

数学结构是数学公式的骨架，而数学符号是数学公式的骨肉。

数学符号的输入：一小部分符号是可以直接从键盘上输入的，如字母 $a$，$b$，$x$，$+$，$=$，$()$；但是大多数符号需要使用 $\LaTeX$ 命令来输入。

数学符号总共有 $8$ 个类别：普通符号、巨算符、二元运算符、关系符、开符号。闭符号、标点和变量族。

思想准备：虽然我一直在说要避免去涉及到 $\LaTeX$ 的粗斜体、字体、字号、间距和行距等细节的问题，但是在符号和类型这一节就不得不去考虑这些问题了。因为这些规定有数学或者物理含义。

### 3.1 字母和普通符号

数学符号的最基本内容就是**字母表**。

#### 3.1.1 拉丁字母

也就是拉丁字母 $A$，$B$，$C$，$D$，$x$，$y$，$z$。它们都可以**直接**从键盘输入，**默认**使用意大利**形状**（注意是形状而不是字体/体）。

数学字母可以使用多种字体。使用命令就可以为字母确定字体。

数学环境的默认字体 **\mathnormal**

$$
ABCHIJXYZabchijxyz12345
$$

意大利体 **\mathit**

$$
\mathit{ABCHIJXYZabchijxyz12345}
$$

罗马体 **\mathrm**

$$
\mathrm{ABCHIJXYZabchijxyz12345}
$$

粗体 **\mathbf**

$$
\mathbf{ABCHIJXYZabchijxyz12345}
$$

无衬线体 **\mathsf**

$$
\mathsf{ABCHIJXYZabchijxyz12345}
$$

打字机体 **\mathtt**

$$
\mathtt{ABCHIJXYZabchijxyz12345}
$$

手写体 **\mathcal**

$$
\mathcal{ABCHIJXYZabchijxyz12345}
$$

花体 **\mathscr**

$$
\mathscr{ABCHIJXYZabchijxyz12345}
$$

黑板粗体 **\mathbb**

$$
\mathbb{ABCHIJXYZabchijxyz12345}
$$

哥特体 **\mathfrak**

$$
\mathfrak{ABCHIJXYZabchijxyz12345}
$$

再就是要明白为什么要使用不同的字体，以及字体之间细微的差别。

比如只有变量使用默认的意大利体；数学常数通常使用直立的罗马体，如数学常数 $\mathrm{e}$ ，类似的还有虚数单位 $\mathrm{i}$。当然这里也只是举了几个很简单的例子。

默认的数学字母字体 **\mathnormal** 不仅使用了和正文不同的数学字体，而且字母之间的间距比正文也要大。而其他数学字体字母的间距和正文几乎没有区别。所以使用 `$xyz$` 通常表示三个字母的乘积（间距较大），而如果要表示一个多字母的长变量名 $\mathit{xyz}$，则应该使用 `$\mathit{xyz}$` 等形式。

#### 3.1.2 希腊字母

希腊字母同样有大写/小写，也有直立体/倾斜体的区别。不像拉丁字母有统一的字体命令，每个希腊字母都有自己单独的命令。但是命令是有规律可循的。我们就以 $\pi$ 为例来讲。

首先是 **\pi** 命令：$\pi$，这个是小写的、斜体的，一般用作变量。*可以发现命令就是这个希腊字母的读法，是最基础的命令。*

再就是 **\Pi** 命令：$\Pi$，这个是大写的希腊字母。*在基础的命令上把首字母大写就是大写的命令了。*

还有 **\varpi** 命令：$\varpi$。这个是小写希腊字母的变体；还有 **\varPi** 命令：$\varPi$，这个是大写希腊字母的变体。*加上 var 的前缀就是变体的命令。*

而 **\uppi** 命令：$\uppi$，这个是小写的、直立的，一般用作常数，如圆周率。***\uppi** 命令需要数学字体宏包 upgreek。可能会有无法显示的情况。*

常用希腊字母列表（不完全）：

| 字母名称 |   大写    |        小写         |    基本命令     |
| :------: | :-------: | :-----------------: | :-------------: |
|  alpha   |     A     |      $\alpha$       |     \alpha      |
|   beta   |     B     |       $\beta$       |      \beta      |
|  delta   | $\Delta$  |      $\delta$       |     \delta      |
| epsilon  |     E     |     $\epsilon$      |    \epsilon     |
|          |           |    $\varepsilon$    |   \varepsilon   |
|   zeta   |     Z     |       $\zeta$       |      \zeta      |
|   eta    |  $\Eta$   |       $\eta$        |      \eta       |
|  gamma   | $\Gamma$  |      $\gamma$       |     \gamma      |
|  theta   | $\Theta$  |      $\theta$       |     \theta      |
|  sigma   | $\Sigma$  |      $\sigma$       |     \sigma      |
|  omega   | $\Omega$  |      $\omega$       |     \omega      |
|  lambda  | $\Lambda$ |      $\lambda$      |     \lambda     |
|    mu    |   $\Mu$   |        $\mu$        |       \mu       |
|   phi    |  $\Phi$   | $\phi$ 或 $\varphi$ | \phi 或 \varphi |
|    pi    |   $\Pi$   |        $\pi$        |       \pi       |
|   psi    |  $\Psi$   |       $\psi$        |      \psi       |
|  ksi(?)  |   $\Xi$   |        $\xi$        |       \xi       |

#### 3.1.3 希伯来字母

“阿列夫 $0$”：**\aleph** 命令：**$\aleph_0$** (此处举显然的例子)

**\beth** 命令：**$\beth$**

**\daleth** 命令：**$\daleth$**

**\gimel** 命令：**$\gimel$**

#### 3.1.4 普通符号

普通符号通常是一些字母的变形、一元运算符或者是单纯的图形符号。这里举几个常见的普通符号。

无穷：**\infty** 命令：$\infty$

角度：**\angle** 命令：$\angle$

垂直：**\bot** 命令：$\bot$

三角形 或 拉普拉斯算子：**\triangle** 命令：$\triangle$

**\hbar** 命令：$\hbar$

偏导数：**\partial** 命令：$\partial$

向量微分算子：**\nabla** 命令：$\nabla$

任意：**\forall** 命令：$\forall$

存在：**\exists** 命令：$\exists$

空集：**\varnothing** 命令：$\varnothing$

非：**\neg** 命令：$\neg$

#### 3.1.5 数学重音

这里举几个常见的重音。

##### 单字母

**\hat a** 命令：$\hat a$

**\bar a** 命令：$\bar a$

**\vec a** 命令：$\vec a$

**\dot a** 命令：$\dot a$

##### 多字母

**\widehat{abc}** 命令：$\widehat{abc}$

### 3.2 数学算子

数学算子分为三种（自定），第一类是巨算子，第二类是单字符算子，第三类是文字名称算子。

#### 3.2.1 巨算子

它们的大小是随显示公式和行内公式变化的，而且通常比一般的数学符号大一些。下面举一些常见的例子。

求和：**\sum** 命令：$\sum$

求积：**\prod** 命令：$\prod$

积分：**\int** 命令：$\int$

二重积分：**\iint** 命令：$\iint$

**\oint** 命令：$\oint$

三重积分：**\iiint** 命令：$\iiint$

**\bigcup** 命令：$\bigcup$

**\bigcap** 命令：$\bigcap$

**\bigvee** 命令：$\bigvee$

**\bigwedge** 命令：$\bigwedge$

**\bigoplus** 命令：$\bigoplus$

**\bigotimes** 命令：$\bigotimes$

注意不要把巨算子和形状相似的其他类型符号混淆。典型的例子就是大写希腊字母 **$\Sigma$**（\Sigma）与求和号 $\sum$（\sum）。它们在各个方面都有区别。

数学算子通常可以带上下标。在显示公式中，积分号的上下标默认在角标位置，而其他巨算子则在上下方（作为上下限），例如。

$$
\mathcal{F}(x) = \sum_{k=0}^\infty \oint_0^1 f_k(x,t) \,\mathrm{d}t
$$

#### 3.2.2 单字符算子

积分式的写法。微分算子 $\mathrm{d}$ 应该使用直立罗马体，后面的变量则仍是使用默认的意大利体，并且用 **\\,** 与前面的被积函数分开。

$$
\int f(x) \,\mathrm{d} x
$$

但是一般不添加单字符算子和变元之间的间距。不过微分与被积函数、多个微分变元之间，仍然需要留有间距。

$$
\iiint\limits_{0<x,y,z<1} f(x,y,z) \,\mathrm{d} x \,\mathrm{d} y \,\mathrm{d} z
$$

这类只有一个字符的数学算子，还有 Laplace 算子 $\triangle$ （大写希腊字母 **\Delta**，也可用 **\triangle**）、偏微分算子 $\partial$ （**\partial**）、梯度算子 $\nabla$（**\nabla**）等一般都只作为一个普通数学符号排版，没有提供额外的间距，需要自己添加。

#### 3.2.3 文字名称算子

文字名称算子用直立罗马体排印，如 $\log x$，$\lim f(t)$ 中的 $\log$ 和 $\lim$。

前者是不带上下限的“纯”算子，一般就是常用的数学函数。其上标是角标形式。

对数：

- **\log** 命令：$\log$

- **\lg** 命令：$\lg$

- **\ln** 命令：$\ln$

三角函数：

- **\sin** 命令：$\sin$

- **\cos** 命令：$\cos$

- **\tan** 命令：$\tan$

- **\csc** 命令：$\csc$

- **\sec** 命令：$\sec$

- **\cot** 命令：$\cot$

- **\arcsin** 命令：$\arcsin$

- **\arccos** 命令：$\arccos$

- **\arctan** 命令：$\arctan$

- **\sinh** 命令：$\sinh$

- **\cosh** 命令：$\cosh$

- **\tanh** 命令：$\tanh$

- **\coth** 命令：$\coth$

带上下限的数学算子，使用起来和巨算子相似。

**\lim** 命令：$\lim$

**\max** 命令：$\max$

**\min** 命令：$\min$

**\inf** 命令：$\inf$

**\gcd** 命令：$\gcd$

**\det** 命令：$\det$

$$
\varlimsup_{k\to\infty} A_k =
\lim_{J\to\infty}
\lim_{K\to\infty}
\bigcap_{j=1}^J \bigcup_{k=j}^K A_k
$$

#### 3.2.4 取模和同余

略。

### 3.3 二元运算符和关系符

首先说一下什么是二元运算符和关系符。常见的，能从键盘上直接输入的二元运算符有加号 $+$，减号 $-$，星号 $*$；二元关系符有等号 $=$，大于号 $>$，小于号 $<$ 和表示集合的关系的符号 $:$ 。

它们和普通符号是有区别的，在公式使用中会产生间距。比如斜线形式的除号 $/$ 并不是二元运算符，只是普通符号，即使表示除法也不额外增加间距；表示差集的符号 **\setminus** 与普通符号 **\backslash** 是同一个字符，但类型不同，因而会产生不同的间距，见下面的例子。

$$
  H\backslash G \text{和} H\setminus G
$$

二元运算符和关系符有不同和相同的地方。它们都用在公式中间，在符号的两边留有一定的间距。运算符的间距小一些，关系符的间距**略**大一些，例如。

$$
0-2=-2
$$

都是一样的符号却产生了不同的间距。原因是左边的是减号，是运算符，而右边的是负号，是关系符。当然在大多数情况下，我们不需要去关注这些 $\LaTeX$ 会自动处理的细节。

#### 3.3.1 二元运算符

下面列举常见的二元运算符。

乘法：**\times** 命令：$\times$

点乘：**\cdot** 命令：$\cdot$

除法：**\div** 命令：$\div$

正负号：**\pm** 命令：$\pm$

**\mp** 命令：$\mp$

**\circ** 命令：$\circ$

**\wedge** 或 **\land** 命令：$\wedge$

**\vee** 或 **\lor** 命令：$\vee$

并：**\cup** 命令：$\cup$

交：**\cap** 命令：$\cap$

**\otimes** 命令：$\otimes$

异或：**\oplus** 命令：$\oplus$

同或：**\odot** 命令：$\odot$

#### 3.3.2 二元关系符

二元关系符是 $\LaTeX$ 中数量最为庞大的一类数学符号：除了有普通的二元关系符及它们的否定形式外，关系符中各种箭头通常也单独列为一类。

一般地，二元关系符的否定可以在关系符前加 **\not** 得到，如使用 **\$s\not\in T\$** 就得到：

$$
s\not\in T
$$

此外，$\LaTeX$ 也为很多二元关系符的否定形式单独定义了命令，单独定义的命令有时会使用单独的字体符号，比直接使用 **\not** 得到的效果更好，如使用 **\$s \notin T\$** 就得到：

$$
s \notin T
$$

斜线的位置更加合理一些。因此在使用否定的二元关系符的时候，应该尽量使用单独的符号命令，在没有单独的符号的时候，才使用 **\not** 组合符号。

下面列举常见的二元关系符。

因为：**\because** 命令：$\because$

所以：**\therefor** 命令：$\therefore$

包含于：**\subseteq** 命令：$\subseteq$

不等于：**\neq** 或 **\ne** 命令：$\neq$

小于等于：**\leq** 或 **\le** 命令：$\leq$

大于等于：**\geq** 或 **\ge** 命令：$\geq$

**\ll** 命令：$\ll$

**\gg** 命令：$\gg$

属于：**\in** 命令：$\in$

不属于：**\notin** 命令：$\notin$

**\ni** 或 **\owns** 命令：$\ni$

恒等 或者 同或：**\equiv** 命令：$\equiv$

**\sim** 命令：$\sim$

约等于：**\approx** 命令：$\approx$

相似：**\simeq** 命令：$\simeq$

全等：**\cong** 命令：$\cong$

包含：**\subseteq** 命令：$\subseteq$

**\supseteq** 命令：$\supseteq$

真包含：**\subset** 命令：$\subset$

**\supset** 命令：$\supset$

垂直：**\perp** 命令：$\perp$

**\parallel** 命令：$\parallel$

下面列举常见的箭头符号。基本上都是 **\arrow** 的变体。

单、双向箭头

**\leftarrow** 或 **\gets** 命令：$\leftarrow$

**\rightarrow** 或 **\to** 命令：$\rightarrow$

**\leftrightarrow** 命令：$\leftrightarrow$

首字母大写

**\Leftarrow** 命令：$\Leftarrow$

**\Rightarrow** 命令：$\Rightarrow$

**\Leftrightarrow** 命令：$\Leftrightarrow$

上面箭头的加长形式：**加 long**（举出一例）（双杠仍然是首字母 L 大写）

**\Longrightarrow** 命令：$\Longrightarrow$

上面箭头的否定形式：**加 n**（仅举一例）

**\nRightarrow** 命令：$\nRightarrow$

可逆箭头

**\rightleftharpoons** 命令：$\rightleftharpoons$

上下箭头

**\uparrow** 命令：$\uparrow$

**\downarrow** 命令：$\downarrow$

**\updownarrow** 命令：$\updownarrow$

首字母大写

**\Uparrow** 命令：$\Uparrow$

**\Downarrow** 命令：$\Downarrow$

**\Updownarrow** 命令：$\Updownarrow$

斜向箭头

**\nearrow** 命令：$\nearrow$

**\searrow** 命令：$\searrow$

**\swarrow** 命令：$\swarrow$

**\nwarrow** 命令：$\nwarrow$

这组命令很有规律。

- 东南 -> south-east -> se
- 东北 -> north-east -> ne
- 西北 -> north-west -> nw
- 西南 -> south-west -> sw

添加说明的可延长箭头

使用 **\xleftarrow** 和 **\xrightarrow** 命令，可以在上下方添加说明，参数是上方说明，可选参数是下方说明。

$$
A \xleftarrow{0<x<1>} B \xrightarrow[x \leq 1]{x \geq 1} C
$$

逻辑符号命令

使用 **\iff**，**\implies**，**\impliedby**，**\And** 命令用于逻辑表达式。符号和一般的箭头相同，但是间距比一般的运算符和关系符大一些，意义也更明显。

**\iff** 命令：$\iff$

**\implies** 命令：$\implies$

**\impliesby** 命令：$\impliedby$

**\And** 命令：$\And$

一个例子。

$$
x=y \implies x+a=y+a \\
x=y \impliedby x+a=y+a \\
x=y \iff x \le y \And x \ge y
$$

### 3.4 括号和定界符

#### 3.4.1 括号

数学公式离不开括号的使用。括号种类大致有圆括号 $(\,)$、方括号 $[\,]$、花括号 $\{\,\}$、尖括号 $\langle\,\rangle$ 等等。在 $\LaTeX$ 中，括号被分为开括号和闭括号，显然，开括号是左边的括号，闭括号是右边的括号。

能从键盘上直接输入的符号有圆括号 $(\,)$、方括号 $[\,]$、花括号 $\{\,\}$，其余均有用命令输入。

尖括号：**\langle** 和 **\rangle** 命令：$\langle\, \And \,\rangle$

向下取整：**\lfloor** 和 **\rfloor** 命令：$\lfloor\, \And \,\rfloor$

向上取整：**\lceil** 和 **\rceil** 命令：$\lceil\, \And \,\rceil$

#### 3.4.2 定界符

定界符的概念更为广泛。定界符通常就是公式两侧的括号，但也有时表示其他的符号。定界符有一个特别有用的性质，就是它可以按需要改变大小。

使用 **\left** 和 **\right** 命令得到的。它们分别把作为其参数的定界符转换为开符号和闭符号，同使得定界符可以按中间的内容的高度自动调节大小。

$$
\partial_x \partial_y \left[
\frac 12 \left(
x^2+y^2
\right)^2 + xy
\right]
$$

**\left** 和 **\right** 命令用来配对的定界符可以不是同一种符号，甚至可以用一个句号 $.$ 表示空的定界符。例如：

$$
\left.
\int_0^x f(t,\lambda) \,\mathrm{d}t
\right|_{x=1}, \qquad
\lambda \in
\left[\frac 12,\infty\right).
$$

还有一个 **\middle** 命令，它可以在 **\left** 和 **\right** 的中间再加一个定界符，如：

$$
\Pr \left(
X>\frac 12 \middle \vert Y=0
\right)
=\left.
\int_0^1 p(t) \,\mathrm{d}t \middle/ (N^2+1)
\right.
$$

手动调整定界符略。

### 3.5 标点

#### 3.5.1 数学标点

数学标点只有 5 个。逗号、分号、叹号、问号和冒号，前面四个都可以从键盘上输入，冒号的命令是：**\colon**，注意它和直接从键盘上输入的二元关系符 $:$ 的区别（略，因为用的不多）。

键盘上的圆点 $.$ 在数学公式中是普通符号，通常表示为小数点。不过在显示公式的末尾也常常用它表示句号，在行末无须为后面的间距问题困扰。

#### 3.5.2 数学省略号

省略号并不属于 $TeX$ 的数学标点类型，但确是公式中常用的标点符号。

在数学公式中，水平的省略号有两种：

1. 圆点在基线位置的 **\ldots** ($\ldots$)
2. 圆点在中间位置的 **\cdots** ($\cdots$)

位置较低的 **\ldots** 主要用在逗号之间，如：

$$
(1,\cdots,n)
$$

位置在中间的 **\cdots** 则用在二元运算符、关系符之间，如：

$$
1+\cdots+n
$$

或者表示没有乘号的连乘积，如：

$$
a_1 \cdots a_n
$$

或者连接多个积分号，如：

$$
\int_0^1 \cdots \int_0^1
$$

下面给出其他省略号的命令。

首先是不同方向的省略号，多用于排版矩阵。

**\vdots** 命令：$\vdots$

**\ddots** 命令：$\ddots$

再是依照具体情形设定的省略号类型，分别是：

逗号（comma）：**\dotsc** 命令：$\dotsc$

二元运算或关系符（binary）：**\dotsb** 命令：$\dotsb$

乘法运算（multiplication）：**\dotsm** 命令：$\dotsm$

积分（integral）：**\dotsc** 命令：$\dotsi$

其他情形（other）：**\dotso** 命令：$\dotso$

虽然 **\dots** 有一定的自动识别功能，但是在 **\dots** 无法正常识别的时候就可以使用上面的命令，如连乘和积分：

$$
\prod_{i=1}^n a_i = a_1 \dotsm a_n
\qquad \int_0^1 \dotsi \int_0^1
$$

## 4 多行公式

我们经常会遇到线性方程组、分段函数、以及非常长的公式。下面来探究如何用显示公式来表示它们。

### 4.1 多个公式

在 Typora 中，最简单的换行方法是直接使用 **\\\\** 换行。

输入多行数学公式最基本的方法是：使用 **gather** 和 **gather*** （不编号）环境，使用 **\\\\** 换行，如：

**gather** 环境：

$$
\begin{gather}
a + b = b + a \\
a \times b = b \times a
\end{gather}
$$

**gather*** 环境：
$$
\begin{gather*}
3+5 = 5+3 = 8 \\
3 \times 5 = 5 \times 3
\end{gather*}
$$

**gather** 环境得到的公式是每行居中的，**align** 和 **align*** 环境则允许公式按等号或者其他关系符对齐，在关系符前加 **&** 表示对齐。例如：

$$
\begin{align}
x &= t + \cos t + 1 \\
y &= 2 \sin t
\end{align}
$$

**align** 和 **align*** 环境还允许排列**多列**对齐的公式，列与列之间仍使用 **&** 分隔：

$$
\begin{align*}
x &= t & x &= \cos t & x &= t \\
y &= 2t & y &= \sin(t+1) & y &= \sin t
\end{align*}
$$

需要注意的是，**align** 环境中的列分隔符 **&** 一般应该放在二元关系符的前面，但有时候也可以放在后面。如果个别需要在关系符后面或其他地方对齐的，则应该注意使用的符号类型。下面举一个连等公式的例子。

*实话说这个例子记住就好了。关系符后对齐，需要使用空的分组代替关系符右侧符号，保证间距。*

$$
\begin{align*}
& (a+b)(a^2-ab+b^2) \\
={} & a^3 - a^2b + ab^2 + a^2b - ab^2 +b^2 \\
={} & a^3 + b^3
\end{align*}
$$

### 4.2 拆分单个公式

首先是 **\multline** 环境和 **\multline*** 环境，可使用 **\\\\** 换行。各行对齐的方式是：第一行左对齐，最后一行右对齐，中间的部分居中。不过左右两边和版心边界都留有一小段间距。这种环境特别适合排版非常长的连续运算，如：

$$
\begin{multline}
a+b+c \\
+d+e+f \\
+j+k+l
\end{multline}
$$

给多行公式只产生一个编号要使用 **\split** 环境。**\split** 环境并不开始一个数学公式，它是使用在 **equation**、**gather** 等数学环境里的；**\split** 环境不产生编号，编号仍然由外面的数学环境产生。因此多行公式只产生了一个编号。

$$
\begin{equation}
\begin{split}
\cos 2x &= \cos^2 x - \sin^2 x \\
&= 2\cos^2 x - 1
\end{split}
\end{equation}
$$

比如这里数字逻辑设计中逻辑代数的一个公式，有两个变形，三个等式合起来算一个公式,因此只有一个编号。

$$
\begin{equation} \begin{split}
AB + A'C + BC &= AB + A'C \\
AB + A'C+ BCD &= AB+ A'C \\
(A + B)(B + C)(A' + C) &= (A + B)(A' + C)
\end{split} \end{equation}
$$

### 4.3 将公式组合成块

最为常见的是 **\cases** 环境，它在几行公式前面用花括号括起来，用来表示几种不同的情况。每行公式使用 **&** 分隔为两部分，通常表示值和后面的条件，例如：

$$
\begin{equation}
D(x) = \begin{cases}
1, & \text{if } x \in \mathbb{Q}; \\
0, & \text{if } x \in \mathbb{R} \setminus \mathbb{Q}.
\end{cases}
\end{equation}
$$

还有几个常见的组合公式块的环境，它们的环境名通常是在原来的环境名的动词后面加 **ed**，包括 **gathered** 环境、**aligned** 环境和 **alignedat** 环境等。

**gathered** 环境把几行公式居中排列，组合为一个整体，如：

$$
\left.
\begin{gathered}
S \subseteq T \\
S \supseteq T
\end{gathered}
\right\}
\implies S = T
$$
