继续留遗产...

UPD2019.06.15:PDF版本链接

网页较大预警。如果公式解析不正确请刷新页面。长时间加载不出来建议打开PDF用Ctrl+S键下载到本地，流量访问请谨慎。

高考完继续留遗产...

整理了一下笔记，也许是面向后来要补文化课的竞赛选手的。本来想高考前发出来的，结果本地Markdown语法和博客的Markdown语法解析不兼容，高考前不想浪费时间，现在花了较长时间调整可以放出来了。也是由于语法解析不兼容的缘故，已经尽可能修正了，最后Markdown排版还是有点小问题，凑合看吧。而且公式比较多，网页解析可能比较慢，稍等一会儿即可。

虽然自己挺菜的，不注感觉整理的比较全面，除了一些特别简单和特别超纲的知识点就没有涉及，可能存在少部分超纲内容，仅供参考（面向对象也许是全国卷570～640吧，这个说不好，主要是高考之前也不敢乱说)。

免责声明：文章中存在错误是难免的，后果自负，欢迎大佬联系指正或默默走开。且据目前统计来看有较大概率出现错别字。

数学选修极坐标单独整理了，不等式整理较少，主要在基本运算部分。

对于数学学科来说，公式应该总结的非常全面了，不过数学题更多的还是大量题目训练、计算能力和智商，仅仅掌握基础知识和公式是不够的。笔记中的一些运算技巧起码个人感觉可以说是非常有用了。也许有较多超纲内容？建议以题目训练为主，这里的笔记仅仅是提醒、提供一些技巧。

高考加油！！！

UPD2019.06.24：高考667分。所以面向对象也许是570～667(雾)。

# 基本运算

1. 立方差公式

$$
\begin{array}{r}a^{3} - b^{3} = (a - b)(a^{2} + ab + b^{2})\\ a^{3} + b^{3} = (a + b)(a^{2} - ab + b^{2}) \end{array}
$$

2. 二次方程  $ax^2 +bx + c$  韦达定理

$$
\Delta = b^{2} - 4ac
$$

$$
x_{1,2} = \frac{-b\pm\sqrt{\Delta}}{2a}
$$

$$
x_{1} + x_{2} = -\frac{b}{a}
$$

$$
x_{1}x_{2} = \frac{c}{a}
$$

$$
|x_{1} - x_{2}| = \frac{\sqrt{\Delta}}{|a|}
$$

$$
x_{1}^{2} + x_{2}^{2} = (x_{1} + x_{2})^{2} - 2x_{1}x_{2} = \frac{b^{2} - 2ac}{a^{2}}
$$

$$
|x_{1}^{2} - x_{2}^{2}| = |(x_{1} + x_{2})(x_{1} - x_{2})| = \frac{|b|\sqrt{\Delta}}{a^{2}}
$$

$$
\frac{1}{x_{1}} +\frac{1}{x_{2}} = \frac{x_{1} + x_{2}}{x_{1}x_{2}} = -\frac{b}{c}
$$

$$
|\frac{1}{x_{1}} -\frac{1}{x_{2}} | = \frac{|x_{1} - x_{2}|}{|x_{1}x_{2}|} = \frac{\sqrt{\Delta}}{|c|}
$$

$$
f(x)_{\min \text{max}} = f\left(-\frac{b}{2a}\right) = -\frac{\Delta}{4a}
$$

方程有两个正根  $\Leftrightarrow \Delta >0,x_{1} + x_{2} > 0,x_{1}x_{2} > 0,$

方程有两个负根  $\Leftrightarrow \Delta >0,x_{1} + x_{2}< 0,x_{1}x_{2} > 0_{\circ}$

方程有两个异号根  $\Leftrightarrow x_{1}x_{2}< 0_{\circ}$

方程有两个根均大于  $m\Leftrightarrow \Delta >0,x_{1} + x_{2} > 2m,(x_{1} - m)(x_{2} - m) > 0_{\circ}$

方程有两个根均小于  $m\Leftrightarrow \Delta >0,x_{1} + x_{2}< 2m,(x_{1} - m)(x_{2} - m) > 0_{\circ}$

方程有两个根在  $m$  两侧  $\Leftrightarrow (x_{1} - m)(x_{2} - m)< 0_{\circ}$

方程有两个根在  $(l,r)$  之间  $\Leftrightarrow \Delta >0,l< - \frac{b}{2a} < r,f(l)f(r) > 0_{\circ}$

方程有两个根在  $[l,r]$  之间  $\Leftrightarrow \Delta >0,l< - \frac{b}{2a} < r,a\cdot f(l)\geq 0,a\cdot f(r)\geq 0_{\circ}$

方程有两个根，一个在  $(l,r)$  之间  $\Leftrightarrow \Delta >0,f(l)f(r)< 0_{\circ}$

方程有两个根，一个在  $[l,r]$  之间

$\Leftrightarrow \Delta >0,\{f(l)f(r)< 0\}$  或  $\{f(l) = 0,\frac{l + r}{2} < - \frac{b}{2a}\}$  或  $\{f(r) = 0, - \frac{b}{2a} < \frac{l + r}{2}\}$

3. 高次不等式：穿根法，因式分解数轴标根，二次因式不穿过数轴。分式不等式可以分子分母分解因式后视作相乘，穿根后注意抠点。

4. 绝对值不等式：  $\forall x,|f(x)|< g(x)\Leftrightarrow \forall x, - g(x)< f(x)< g(x)$

5. 均值不等式链：当  $0< a< b$  时：

$$
0< a< \underbrace{\frac{2}{\frac{1}{a} + \frac{1}{b}}}_{\text{调和平均}}< \underbrace{\sqrt{ab}}_{\text{几何平均}}< \underbrace{\frac{b - a}{\ln b - \ln a}}_{\text{对数平均}}< \underbrace{\frac{a + b}{2}}_{\text{算术平均}}< \underbrace{\sqrt{\frac{a^2 + b^2}{2}}}_{\text{平方平均}}< b
$$

对数平均值结论不直接用于导数题的证明，但是证明对数平均值的方法可以作为证明导数题的思路。对数平均值的位置可以构造  $t = \frac{b}{a}$  后转化为  $t$  的函数求导加以证明，如证明对数平均大于几何平均：  $\Leftrightarrow \ln {\frac{b}{a}}< \sqrt{\frac{b}{a}} - \sqrt{\frac{a}{b}}$ 。推论：

推论：

$$
\begin{array}{r}\underbrace{ab}_{\mathbb{H}\mathbb{H}}\leq \underbrace{\frac{(a + b)^2}{4}}_{\mathbb{H}\mathbb{H}}\leq \underbrace{\frac{a^2 + b^2}{2}}_{\mathbb{H}\mathbb{H}}\\ \underbrace{2\sqrt{ab}}_{\mathbb{H}\mathbb{H}}\leq \underbrace{a + b}_{\mathbb{H}\mathbb{H}}\leq \underbrace{\sqrt{2(a^2 + b^2)}}_{\mathbb{H}\mathbb{H}}\\ \underbrace{2\sqrt{AB}}_{\mathbb{H}\mathbb{H}}\leq \underbrace{At + B\frac{1}{t}}_{\mathbb{H}\mathbb{H}} \end{array}
$$

6. 积和并存式的化简(如  $Ax + By + Cxy + D = 0$

。换元法：  $Ax + By\geq 2\sqrt{ABxy} = 2\sqrt{AB}\cdot t,$ $\begin{array}{r}t^{2} = xy = - \frac{Ax + By + D}{C}\leq - \frac{2\sqrt{AB}t + D}{C} \end{array}$  ，即可解二次不等式求出的范围，进而求出xy最小值以及  $Ax + By$  最小值。乘一法：当  $D = 0$  时有  $Ax + By = - Cxy,$  同除  $- Cxy$  得  $\begin{array}{r}\frac{1}{- C}\big(\frac{A}{y} +\frac{B}{x}\big) = 1 \end{array}$  ，则可求  $\begin{array}{r}n x + m y = \frac{1}{- C} (n x + m y)\big(\frac{A}{y} +\frac{B}{x}\big) \end{array}$  ，然后化简套用均值不等式即可。

。配方法：如

$a + 2b + 2ab - 8 = 0\Leftrightarrow a + 2b + 2ab + 1 = 9\Leftrightarrow (a + 1)(2b + 1) = 9$  ，然后对  $(a + 1)$  和  $(2b + 1)$  套用均值不等式即可。

7. 三角不等式

$$
|a| - |b||\leq |a\pm b|\leq |a| + |b|
$$

8. 柯西不等式

$$
\begin{array}{rl} & {\because (\vec{a}\cdot \vec{b})^{2}\leq (|\vec{a} |\cdot |\vec{b} |)^{2}}\\ & {\therefore (x_{1}x_{2} + y_{1}y_{2})^{2}\leq (x_{1}^{2} + y_{1}^{2})(x_{2}^{2} + y_{2}^{2})} \end{array}
$$

9. 常用不等式：  $e^{x}\geq x + 1 > x > x - 1\geq \ln x_{\circ}$

10. 等差数列快速求和及差分：

$$
\begin{array}{l}\because \sum (2i - 1) = n^2,\sum i = \frac{n(n + 1)}{2},\sum 1 = n\\ a_n = kn + b\Leftrightarrow S_n = \frac{k}{2} n(n + 1) + bn \end{array}
$$

$$
S_{n} = k n^{2} + b n\Leftrightarrow a_{n} = k(2n - 1) + b
$$

11. 等比数列快速求和：

$$
S_{n} = a_{1}\frac{q^{n} - 1}{q - 1}
$$

令  $a_{n} = c^{n}$  就得到：

$$
\Rightarrow \sum_{i = 1}^{n}c^{i} = \frac{c}{c - 1} (c^{n} - 1)
$$

求和上下界差分就得到：

$$
\Rightarrow \sum_{i = l}^{n}c^{i} = \frac{c}{c - 1} (c^{r} - c^{l - 1})
$$

这一结论常可以被用于裂项相消过程中快速求出  $k\sum_{i = 2}^{n}c^{i}$  项的通式。具体计算裂项相消化简就得到：

$$
\Rightarrow \sum_{i = 1}^{n}ic^{i} = \frac{c}{c - 1} (nc^{n} - \frac{c^{n} - 1}{c - 1})
$$

这个式子看上去没有规律，深入理解其物理意义：因为有  $\frac{c^{n} - 1}{c - 1} = \sum_{i = 0}^{n - 1}c^{i}$ ，代入整理再代入第二个式子就得到：

$$
\Rightarrow \sum_{i = 1}^{n}ic^{i} = \sum_{i = 1}^{n}\frac{c}{c - 1} (c^{n} - c^{i - 1}) = \sum_{i = 1}^{n}\sum_{i = i}^{n}c^{j}
$$

所以第三个式子的本质就是横向求和和纵向求和的转化，这样就方便记忆和使用了。

# 集合

1. 集合满足确定性、互异性、无序性。

2. 空集是任何集合的子集，是任何非空集合的真子集。

3.  $n$  个元素  $(n\geq 1)$  有  $2^{n}$  个子集，  $2^{n} - 1$  个真子集，  $2^{n} - 1$  个非空子集，  $2^{n} - 2$  个非空真子集。空集只有一个子集，没有真子集、非空子集、非空真子集。

4. 德摩根律：  $C_{U}(A\bigcap B) = (C_{U}A)\bigcup (C_{U}B), C_{U}(A\bigcup B) = (C_{U}A)\bigcap (C_{U}B)$

5. 映射：  $f:A\rightarrow B$  ，两个非空集合A和B之间存在着对应关系  $f$  ，且A中任何一个元素a(原象)有一个唯一、确定的  $B$  中元素b(象)与其对应，记做  $b = f(a)$  。A为定义域，所有b构成的集合  $f(A)$  为值域(不一定为  $B$  1

一个映射如果  $f(A) = B$  则称为满射(B中每个元素都被对应到)，如果 $|f(A)| = |A|$  则称为单射(A中每个元素对应不同元素)，既是满射又是单射的映射为双射/一—映射。

$|A| = n,|B| = m,f:A\to B$  共有  $m^n$  种；其中单射有  $A_{m}^{n} = C_{m}^{n}n!$  种；满射个数只能递推或求和求出，没有一个单项通项。

$|A| = |B| = n$  ，双射  $f:A\to B$  共有  $n!$  种。

如果  $A,B$  为非空数集，那么称一个映射  $f:A\to B$  为函数。

6. 集合的表示：

列举法：{1,2,3,5}

描述法：  $\{x|x > 1\}$

符号法：N非负整数集(自然数集)；  $\mathbb{N}^*$  或  $\mathbb{N}_{+}$  正整数集(其他正集同理，如  $①_{+}$  )；整数集；  $①$  有理数集；  $\mathbb{R}$  实数集；  $①$  复数集。

数集的区间表示。

图示法：Venn图。

# 函数

1. 单调性：  $\forall x_{1},x_{2},\frac{f(x_{1}) - f(x_{2})}{x_{1} - x_{2}}$  同号。或  $\forall x,\lim_{\Delta x\to 0}\frac{f(x + \Delta x) - f(x)}{\Delta x}$  同号。

复合函数  $f(g(x))$  单调性：同增异减。

函数单调性的推论：对于一个在一段区间内的连续函数， $\forall x_{1}\neq x_{2},f(x_{1})\neq f(x_{2})\Leftrightarrow f(x)$  单调。

2. 奇偶性：定义域对称且  $\forall x,f(x) = f(-x)$  为偶函数，定义域对称且

$\forall x,f(x) = - f(- x)$  为奇函数。只有  $f(x) = 0$  既奇又偶。

复合函数  $f(g(x))$  奇偶性：同奇才奇。  $f(x)\cdot g(x)$  奇偶性：同偶异奇。

任何一个函数都可以拆分为一个奇函数与一个偶函数之和：

$$
f(x) = \frac{f(x) + f(-x) + f(x) - f(-x)}{2} = \frac{f(x) + f(-x)}{2} +\frac{f(x) - f(-x)}{2}
$$

奇函数关于原点对称，偶函数关于y轴对称。

3. 函数的零点：  $f(x_0) = 0$  则称  $x_0$  为函数  $f(x)$  的一个零点(是一个数而不是一个点)。

$f(a)\cdot f(b)< 0$  则区间  $(a,b)$  内存在奇数个变号零点。

4. 正比例函数：  $f(x + y) = f(x) + f(y)$

幂型函数:  $f(xy) = f(x) \cdot f(y)$ 对数型函数:  $f(xy) = f(x) + f(y)$ 指数型函数:  $f(x + y) = f(x) \cdot f(y)$

5. 对数函数性质

$$
\begin{array}{c}a^{\log_{a}x} = x \\ \log_{a}(xy) = \log_{a}x + \log_{a}y \\ \log_{a^{m}}x^{n} = \frac{n}{m}\log_{a}x \\ \log_{a}b \cdot \log_{b}c = \log_{a}c \end{array}
$$

6. 反函数性质

- 将函数表达式中的  $y$  与  $x$  互换，定义域和值域互换。- 反函数图像与原图像关于  $y = x$  对称，对应位置切线斜率互为倒数，若原函数过点  $(a,b)$ ，则反函数过点  $(b,a)$ 。- 反函数对应区间单调性与原函数相同。- 非一一映射的函数没有反函数。

7. 定义域问题：

分数函数  $\longrightarrow$  分母不为0- 根号函数  $\longrightarrow$  根号下大于等于0- 对数函数  $\longrightarrow$  底数大于0且不为1，真数大于0- 指数函数  $\longrightarrow 0^0$  无意义

8. 周期问题

$f(x + a) = f(x - a)$  ，则  $f(x)$  的一个周期为  $T = 2a$  。 $f(a + x) = f(b - x)$  ，则  $f(x)$  的一个对称轴为  $\begin{array}{r}x = \frac{a + b}{2} \end{array}$  。 $f(x)$  有两条对称轴  $x = a,x = b$  ，则  $f(x)$  的一个周期为  $T = 2|a - b|$  。 $f(x)$  有两个对称中心  $(a,0),(b,0)$  ，则  $f(x)$  的一个周期为  $T = 2|a - b|$  。 $f(x)$  有对称轴  $x = a$  ，对称中心  $(b,0)$  ，则  $f(x)$  的一个周期为  $T = 4|a - b|$

# 三角函数

1. 任意角的大小比较：按照弧度制实数比较，正角  $>$  零角  $>$  负角。

锐角  $(0,\pi /2)$  、直角  $\pi /2$  与钝角  $(\pi /2,\pi)$  定义不变。和一个角共终边的所有角：  $\{\beta |\beta = \alpha +2k\cdot \pi ,k\in \mathbb{Z}\}$

2. 方位角：从正北方向顺时针旋转的角度。

坡度：坡面与水平面所成二面角的正切值。

3. 弧度制

$$
1\mathrm{rad} = \frac{180^{\circ}}{\pi}\approx 57.3^{\circ},1^{\circ} = \frac{\pi}{180^{\circ}}\approx 0.01745_{\circ}
$$

弧长与扇形面积：

$$
\begin{array}{c}{l = |\alpha |r}\\ {S = \frac{l}{2\pi r}\cdot \pi r^2 = \frac{1}{2} lr = \frac{1}{2} |\alpha |r^2} \end{array}
$$

4. 任意角三角函数，对于点  $(x,y)$  ，距离原点距离  $\rho$  ，圆心角  $\theta_{\circ}$

$$
\begin{array}{l}\sin \theta = \frac{y}{\rho}\quad \text{余割}\csc \theta = \frac{\rho}{y} = \frac{1}{\sin\theta}\\ \displaystyle \cos \theta = \frac{x}{\rho}\quad \text{正割}\sec \theta = \frac{\rho}{x} = \frac{1}{\cos\theta}\\ \displaystyle \tan \theta = \frac{y}{x}\quad \text{余切}\cot \theta = \frac{x}{y} = \frac{1}{\tan\theta} \end{array}
$$

5. 三角函数公式

$$
\begin{array}{rl} & {\tan \alpha = \frac{\sin\alpha}{\cos\alpha}}\\ & {\sin^2\alpha +\cos^2\alpha = 1}\\ & {\csc^2\alpha -\cot^2\alpha = \frac{1}{\sin^2\alpha} -\frac{1}{\tan^2\alpha} = 1}\\ & {\sec^2\alpha -\tan^2\alpha = \frac{1}{\cos^2\alpha} -\frac{1}{\tan^2\alpha} = 1}\\ & {\cos (\alpha \pm \beta) = \cos \alpha \cos \beta \mp \sin \alpha \sin \beta}\\ & {\sin (\alpha \pm \beta) = \sin \alpha \cos \beta \pm \cos \alpha \sin \beta}\\ & {\tan (\alpha \pm \beta) = \frac{\tan\alpha\pm\tan\beta}{1 + \tan\alpha\tan\beta}\quad (\pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm \pm)}\\ & {\sin 2\alpha = 2\sin \alpha \cos \alpha}\\ & {\cos 2\alpha = 2\cos^2\alpha -1 = 1 - 2\sin^2\alpha = \cos^2\alpha -\sin^2\alpha = (\cos \alpha +\sin \alpha)(\cos \alpha -\sin \alpha)}\\ & {\tan 2\alpha = \frac{2\tan\alpha}{1 - \tan^2\alpha}}\\ & {\cos^2\alpha = \frac{1 + \cos^2\alpha}{2}}\\ & {\sin^2\alpha = \frac{1 - \cos^2\alpha}{2}}\\ & {(\sin \alpha \pm \cos \alpha)^2 = 1\pm \sin 2\alpha} \end{array}
$$

万能替换公式：记  $T = \tan \frac{\alpha}{2}$

$$
\begin{array}{l}\sin \alpha = \frac{2T}{1 + T^2}\\ \displaystyle \cos \alpha = \frac{2T}{1 - T^2}\\ \displaystyle \tan \alpha = \frac{1 - T^2}{1 + T^2} \end{array}
$$

辅角公式：

$$
a\sin (\omega x) + b\cos (\omega x) = \frac{a}{|a|}\sqrt{a^2 + b^2}\sin (\omega x + \arctan \frac{b}{a})
$$

和差化积与积化和差:(以cosαcosβ为例)

$$
\cos (\alpha +\beta) = \cos \alpha \cos \beta -\sin \alpha \sin \beta \quad ① \[ \cos (\alpha -\beta) = \cos \alpha \cos \beta +\sin \alpha \sin \beta \quad ② \]
$$

$$
\frac{① + ②}{2} \Rightarrow \cos \alpha \cos \beta = \frac{1}{2} [\cos (\alpha +\beta) + \cos (\alpha -\beta)] \quad (\text{积化和差})
$$

$$
用 \(A, B \text{代} \alpha +\beta , \alpha -\beta \Rightarrow \cos \left(\frac{A + B}{2}\right) \cos \left(\frac{A - B}{2}\right) = \frac{1}{2} (\cos A + \cos B) \)
$$

UPD2019.11.05: 和差化积利用复数证明:

$$
\begin{array}{r l} & {\quad (\cos x + \cos y) + i(\sin x + \sin y)}\\ & {= e^{i x} + e^{i y}}\\ & {= e^{i\frac{x + y}{2}}\left(e^{i\frac{x - y}{2}} + e^{i\frac{y - x}{2}}\right)}\\ & {= \left(\cos \frac{x + y}{2} +i\sin \frac{x + y}{2}\right)\cdot \left(\cos \frac{x - y}{2} +\cos \frac{y - x}{2}\right)}\\ & {= 2\left(\cos \frac{x + y}{2} +i\sin \frac{x + y}{2}\right)\cdot \cos \frac{x - y}{2}}\\ & {= \left(2\cos \frac{x + y}{2}\cos \frac{x - y}{2}\right) + i\left(2\sin \frac{x + y}{2}\cos \frac{x - y}{2}\right)} \end{array}
$$

$$
(\cos x - \cos y) + i(\sin x - \sin y)
$$

=ex- ey

=ei+2 (e+2- e+2)

=cosx+y+sinx+y (i sin- y- i sin y- x)

=2 (- sinx+y+icosx+y) sin

=2sinx+ysinx- y+2cosx+ysinx- y

$$
\tan x \pm \tan y = \frac{\sin(x \pm y)}{\cos x \cos y}
$$

$$
\cot x \pm \cot y = \frac{\sin(y \pm x)}{\sin x \sin y}
$$

$$
\sin x \cos y + \cos x \sin y = \sin (x + y)
$$

$$
\sin x \cos y - \cos x \sin y = \sin (x - y)
$$

→

$$
\begin{array}{r}\sin x \cos y = \frac{1}{2} \left(\sin (x + y) + \sin (x - y)\right) \\ \cos x \sin y = \frac{1}{2} \left(\sin (x + y) - \sin (x - y)\right) \end{array}
$$

$$
\begin{array}{r}\cos x\cos y + \sin x\sin y = \cos (x - y)\\ \cos x\cos y - \sin x\sin y = \cos (x + y) \end{array}
$$

$$
\begin{array}{r}\cos x\cos y = \frac{1}{2}\Big(\cos (x - y) + \cos (x + y)\Big)\\ \sin x\sin y = \frac{1}{2}\Big(\cos (x - y) - \cos (x + y)\Big) \end{array}
$$

三角函数求值常用变换

。同乘、除  $\sin^2\alpha +\cos^2\alpha$  ，或将原式中的1与其互换。经常通过平方配成齐次式。分子分母同时乘、除sin  $\alpha$  、cosα或sinαcosα，并利用tan  $\alpha = \frac{\sin\alpha}{\cos\alpha}$  。sin  $\alpha +\cos \alpha$  ，sin  $\alpha - \cos \alpha$  ，sinαcosα相互转化。

诱导公式：

$\circ$  整圈不变：  $\sin (x + 2\pi) = \sin x$  ，  $\cos (x + 2\pi) = \cos x_{\circ}$

$\circ$  半圈相反：  $\sin (x + \pi) = - \sin x$  ，  $\cos (x + \pi) = - \cos x_{\circ}$

$\circ$  加直求导：  $\sin (x + \frac{\pi}{2}) = \cos x$  ，  $\cos (x + \frac{\pi}{2}) = - \sin x_{\circ}$

$\circ$  减直积分：  $\sin (x - \frac{\pi}{2}) = \sin (x + \frac{3\pi}{2}) = - \cos x,$

$$
\cos (x - \frac{\pi}{2}) = \cos (x + \frac{3\pi}{2}) = \sin x_{\circ}
$$

$\circ$  正奇余偶：  $\sin (- x) = - \sin x$  ，  $\cos (- x) = \cos x_{\circ}$

$\circ$  正余互余：  $\sin (\frac{\pi}{2} - x) = \cos x$  ，  $\cos (\frac{\pi}{2} - x) = \sin x_{\circ}$

$$
\tan (\frac{\pi}{2} -x) = \cot x,\cot (\frac{\pi}{2} -x) = \tan x_{\circ}
$$

$\circ$  切直负变：  $\tan (x + \frac{\pi}{2}) = - \cot x$  ，  $\cot (x + \frac{\pi}{2}) = - \tan x_{\circ}$

6. 三角函数线：有向线段

![](images/ecdc7215a42f8772230169b5c2177e5d1093c56fabe3594dd0da6dde57d5cf32.jpg)

# 7.三角函数图像

左加右减，上加下减，所有操作针对自变量  $x$  。正弦型函数：  $A\sin (\omega x + \phi) + B$ $(\omega >0)$  。频率  $\begin{array}{r}f = \frac{\omega}{2\pi} \end{array}$  ；最小正周期 $T = \frac{2\pi}{\omega}$  ；振幅  $A$  ；相位  $\omega x + \phi$  ；初相  $\phi$  。五点法：  $\begin{array}{r}\omega x + \phi = 0,\frac{\pi}{2},\pi ,\frac{3\pi}{2},2\pi_{\circ} \end{array}$

正切型函数: 注意定义域。最小正周期  $T = \frac{\pi}{\omega}$ 。

# 8. 三角形中的三角函数

。三角形中角度关系

$$
A + B + C = \pi
$$

$$
\sin C = \sin (A + B) = \sin A\cos B + \sin B\cos A
$$

$$
\tan C = -\tan (A + B)
$$

$$
\sin {\frac{C}{2}} = \cos (\frac{A + B}{2})
$$

$$
\cos {\frac{C}{2}} = \sin (\frac{A + B}{2})
$$

$$
\tan {\frac{C}{2}} = \cot (\frac{A + B}{2})
$$

$$
\cot {\frac{C}{2}} = \tan (\frac{A + B}{2})
$$

。正弦定理

$$
\frac{a}{\sin A} = \frac{b}{\sin B} = \frac{c}{\sin C} = 2r_{\mathrm{sh}}
$$

推论:

$$
\frac{a + b}{\sin A + \sin B} = \frac{a + c}{\sin A + \sin C} = \frac{b + c}{\sin B + \sin C} = \frac{a + b + c}{\sin A + \sin B + \sin C} = 2r_{\mathrm{sh}}
$$

$$
S_{\Delta ABC} = \frac{a^2 + c^2 - b^2}{2ac}
$$

$$
\sin A\geq \sin B\Longleftrightarrow a\geq b\Leftrightarrow A\geq B\Leftrightarrow \cos A\leq \cos B\Leftrightarrow \cos^2 A\leq \cos^2 B\Leftrightarrow \cos 2A\leq \cos 2B
$$

。余弦定理

$$
\begin{array}{l}a^{2} = b^{2} + c^{2} - 2bc\cos A \\ b^{2} = a^{2} + c^{2} - 2ac\cos B \\ c^{2} = a^{2} + b^{2} - 2ab\cos C \end{array}
$$

推论:

$$
\begin{array}{l}\cos A = \frac{b^2 + c^2 - a^2}{2bc} \\ \cos B = \frac{a^2 + c^2 - b^2}{2ac} \\ \cos C = \frac{a^2 + b^2 - c^2}{2ab} \end{array}
$$

。海伦公式

记  $p = \frac{C_{\Delta ABC}}{2} = \frac{a + b + c}{2}$ , 则有

$$
S_{\Delta ABC} = \sqrt{p(p - a)(p - b)(p - c)}
$$

- 射影定理

![](images/6cc07361585c410668ef4a36b5fd8eab636d555da2c66f4f57ce9904c2fef407.jpg)

$$
\begin{array}{c}{CD^2 = AD\cdot BD}\\ {BC^2 = BD\cdot BA}\\ {AC^2 = AD\cdot AB} \end{array}
$$

$$
\begin{array}{c}{c\cos B + b\cos C = a}\\ {a\cos C + c\cos A = b}\\ {a\cos B + b\cos A = c} \end{array}
$$

# 向量

1. 相等向量：共基线，方向相同且模长相等相反向量：共基线，方向相反且模长相等同向向量：共基线，方向相同反向向量：共基线，方向相反等长向量：模长相等向量垂直：基线垂直。平行向量/共线向量：基线平行或重合。0垂直、平行于任何向量，但其与另一个向量的夹角只能是0或  $\frac{\pi}{2}$  而不能是其他角度。

2.  $|\vec{a} +\vec{b} | = |\vec{a} -\vec{b} |\Leftrightarrow \vec{a}\perp \vec{b}$  (矩形对角线相等)  $|\vec{a} | = |\vec{b} |\Leftrightarrow \vec{a} +\vec{b}\perp \vec{a} -\vec{b}$  (直角三角形斜边中线)

3. 判断向量共线/三点共线：

$m = \vec{0}$  或存在入使得  $\vec{n} = \lambda \vec{m}\Leftrightarrow$  向量  $\vec{n}$ $\vec{m}$  共线。

。对于平面内任意一点  $O$  和线段  $AB$  上一点  $P$  ,存在唯一一组  $\lambda ,\mu$  ,使得 $\lambda +\mu = 1$  且:

$$
\vec{OP} = \lambda \vec{OA} +\mu \vec{OB}
$$

其中有  $\lambda = \frac{|P B|}{|A B|}$ $\mu = \frac{|P A|}{|A B|}$  (即加权重心)。

$$
\circ \vec{a},\vec{b}\sharp \sharp \sharp \Leftrightarrow \vec{a}\times \vec{b} = 0\Leftrightarrow |\vec{a} ||\vec{b} |\sin (\vec{a},\vec{b})\Leftrightarrow x_{a}y_{b} - x_{b}y_{a} = 0
$$

4. 平面向量基本定理:选择平面  $\Omega$  内任意不共线向量  $\vec{e}_{1},\vec{e}_{2}$  。向量

$$
\vec{a}\in \Omega \Leftrightarrow \exists a,b,a\vec{e}_{1} + b\vec{e}_{2} = \vec{a}_{\circ}
$$

单位正交基底:  $|\vec{a} | = |\vec{j} | = 1,\vec{t}\perp \vec{j}_{\circ}$

5. 向量点积:  $\vec{a}\cdot \vec{b} = |\vec{a} ||\vec{b} |\cos < \vec{a},\vec{b} >$  。其中  $|\vec{b} |\cos < \vec{a},\vec{b} >$  称为  $\vec{b}$  在  $\vec{a}$  上的投影。

推论:

$$
\cos < \vec{a},\vec{b} > = \frac{\vec{a}\cdot\vec{b}}{|\vec{a}||\vec{b}|}
$$

$$
\vec{a},\vec{b}\sharp \sharp \Leftrightarrow \vec{a}\cdot \vec{b} = 0\Leftrightarrow |\vec{a} ||\vec{b} |\cos < \vec{a},\vec{b} >\Leftrightarrow x_{a}x_{b} + y_{a}y_{b} = 0
$$

6. 向量与平面几何  $(\vec{A B} = \vec{a},\vec{A D} = \vec{b})$

![](images/7bdd57fd502973911ac52d60653e7cc5e3670bd2e249a35a36c6e5fe94d72099.jpg)

平行四边形四边对角线平方和定理:

$$
\begin{array}{c}{{B D^{2}+A C^{2}=A B^{2}+B C^{2}+C D^{2}+D A^{2}=2(A B^{2}+A D^{2})}}\\ {{(\because(\vec{a}+\vec{b})^{2}+(\vec{a}-\vec{b})^{2}=2(\vec{a}^{2}+\vec{b}^{2}))}}\end{array}
$$

极化恒等式:

$$
\begin{array}{c}{{\vec{A B}\cdot\vec{A D}=A E^{2}-B E^{2}=A E^{2}-C E^{2}=A E^{2}-\frac{1}{4}B C^{2}=\frac{1}{4}(A C^{2}-B D^{2})}}\\ {{(\because\vec{a}\cdot\vec{b}=\frac{1}{4}[(\vec{a}+\vec{b})^{2}-(\vec{a}-\vec{b})^{2}])}}\end{array}
$$

斯图尔特公式,对于  $BD$  上任意一点  $E$  都有存在唯一一组  $\lambda ,\mu$  ,使得  $\lambda +\mu = 1$  且:

$$
A E^{2} = \lambda A B^{2} + \mu A D^{2} - |B E|\cdot |D E|
$$

其中有  $\lambda = \frac{|E D|}{|B D|}$ ,  $\mu = \frac{|E B|}{|B D|}$  (即加权重心)。

$\left(\because \cos \angle A E B + \cos \angle A E D = 0\right.$  ，代入余弦定理)。

7. 向量旋转公式

$$
\begin{array}{r}\left[ \begin{array}{cc}\cos \theta & -\sin \theta \\ \sin \theta & \cos \theta \end{array} \right]\left[ \begin{array}{c}x\\ y \end{array} \right] = \left[ \begin{array}{c}x'\\ y' \end{array} \right] \end{array}
$$

8. 空间向量：与平面向量几乎完全相同。

$$
\begin{array}{r}\vec{A}\vec{B} = (x_1,y_1,z_1),\vec{A}\vec{C} = (x_2,y_2,z_2),\vec{A}\vec{D} = (x_3,y_3,z_3). \end{array}
$$

平面三角形面积：

$$
\begin{array}{c}{{S_{\Delta A B C}=\frac{1}{2}|\vec{A B}\times\vec{A C}|=\frac{1}{2}|x_{1}y_{2}-x_{2}y_{1}|=\frac{1}{2}\bigg|\mathrm{Det}\left[\begin{array}{c c}{{x_{1}}}&{{y_{1}}}\\ {{x_{2}}}&{{y_{2}}}\end{array}\right]\bigg|}}\\ {{S_{\Delta A B C}=\frac{1}{2}\bigg|\mathrm{Det}\left[\begin{array}{c c}{{x_{A}}}&{{y_{A}}}&{{1}}\\ {{x_{B}}}&{{y_{B}}}&{{1}}\\ {{x_{C}}}&{{y_{C}}}&{{1}}\end{array}\right]\bigg|}}\end{array}
$$

空间四面体体积：

$$
V_{A - B C D} = \frac{1}{6}\bigg|\mathrm{Det}\left[ \begin{array}{c c c}{x_{1}} & {y_{1}} & {z_{1}}\\ {x_{2}} & {y_{2}} & {z_{2}}\\ {x_{3}} & {y_{3}} & {z_{3}} \end{array} \right]\bigg|
$$

空间三角形面积：

$$
S_{\Delta ABC} = \frac{1}{2}\left|\mathrm{Det}\left[ \begin{array}{ccc}\vec{i} & \vec{j} & \vec{k}\\ x_1 & y_1 & z_1\\ x_2 & y_2 & z_2 \end{array} \right]\right| = \frac{1}{2}\left|(y_1z_2 - z_1y_2,z_1x_2 - x_1z_2,x_1y_2 - y_1x_2)\right|
$$

注意这里是向量模长而非绝对值，也可用海伦公式计算。

# 逻辑、统计与概率

1. 命题的等价形式

原命题：  $p\Rightarrow q$ 逆命题：  $q\Rightarrow p$ 否命题：  $\bar{p}\Rightarrow \bar{q}$ 逆否命题：  $\bar{q}\Rightarrow \bar{p}$ 命题的否定：  $p\Rightarrow \bar{q}$

原命题  $\Leftrightarrow$  逆否命题；逆命题  $\Leftrightarrow$  否命题；注意否命题与命题的否定不同。

2. (第一)数学归纳法

要证明：对于任意  $n\in N_+$  ，  $p_n$  为真。

(1)当  $n\leq n_0$  时，  $p_n$  为真。(2)假设当  $n = k$  时  $p_n$  为真  $(k\geq n_0)$  ，当  $n = k + 1$  时  $p_n$  (即  $p_{k + 1}$  )也为真。直接从 $p_{k + 1}$  出发运用分析法，最后得到  $p_k\Rightarrow p_{k + 1}$  。(3)由(1),(2)则对于任意  $n\in N_+$  ，  $p_n$  为真。

3. 频率分布直方图(纵轴为频率/组距，所有柱形面积和为1)平均数：每个柱形视作中值，求平均。中位数：面积恰好1/2处的值。众数：取最高的柱形中值。(注意平均数和中位数只有一个，众数可以有多个)。

4. 回归分析

检验数据的相关性(只有相关性高才有求回归直线的价值)：

$$
r = \frac{\sum_{i = 1}^{n}(x_{i} - \bar{x})(y_{i} - \bar{y})}{\sqrt{\sum_{i = 1}^{n}(x_{i} - \bar{x})^{2}}\sqrt{\sum_{i = 1}^{n}(y_{i} - \bar{y})^{2}}} = \frac{\sum_{i = 1}^{n}x_{i}y_{i} - n\bar{x}\bar{y}}{\sqrt{\sum_{i = 1}^{n}x_{i}^{2} - n\bar{x}^{2}}\sqrt{\sum_{i = 1}^{n}y_{i}^{2} - n\bar{y}^{2}}}
$$

$|r|\leq 1$  恒成立，当r趋近于1时正相关性很高，当r趋近于一1时负相关性很高，当r趋近于0时相关性较弱。

求  $\hat{y} = \hat{b} x + \hat{a}$  满足最小化  $\sum_{i = 1}^{n}(y_i - \hat{y}_i)^2$  ，称  $\hat{y} = \hat{b} x + \hat{a}$  为这组数据的回归直线。有：

$$
\hat{b} = \frac{\sum_{i = 1}^{n}(x_{i} - \bar{x})(y_{i} - \bar{y})}{\sum_{i = 1}^{n}(x_{i} - \bar{x})^{2}} = \frac{\sum_{i = 1}^{n}x_{i}y_{i} - n\bar{x}\bar{y}}{\sum_{i = 1}^{n}x_{i}^{2} - n\bar{x}^{2}}
$$

$$
\hat{a} = \bar{y} -\hat{b}\bar{x}
$$

对于  $y = ce^{dx}$  一类的函数常两边取对数后用回归曲线拟合：  $\hat{\ln y} = \hat{d} x + \hat{\ln c}_{\circ}$

5. 独立性检验

$$
\chi^2 = \frac{(a + b + c + d)(ad - bc)^2}{(a + b)(c + d)(a + c)(b + d)}
$$

$\chi^2$  越大，两者相关性越强。注意  $\chi^2$  分子为5次式，而分母为4次式，这意味着样本数目数量级越大时得出的两者相关性强的结论往往更可靠，这与常识相吻合。

6. 二项式展开式

$$
T_{r + 1} = C_n^r a^{n - r}b^r
$$

即a次数较大的项在前。

7. 分布

。两点分布：  $X\sim B(1,p)$

$$
\begin{array}{l}P(X = 1) = p, P(X = 0) = 1 - p \\ E(X) = p \\ D(X) = p(1 - p) \end{array}
$$

。二项分布:  $X \sim B(n, p)$

$$
\begin{array}{l}P(X = i) = C_n^i p^i (1 - p)^{n - i} \\ E(X) = np \\ D(X) = np(1 - p) \end{array}
$$

。超几何分布:  $X \sim H(n, M, N)$

$$
\begin{array}{l}P(X = i) = \frac{C_M^i C_{N - M}^{n - i}}{C_N^n} \\ E(X) = n \frac{M}{N} \end{array}
$$

。正态分布:  $X \sim N(\mu , \sigma^2)$

$$
\begin{array}{l}P(X = x) = \frac{1}{\sqrt{2\pi}\sigma} e^{-\frac{(x - \mu)^2}{2\sigma^2}} \\ E(X) = \mu \\ D(X) = \sigma^2 \end{array}
$$

。标准正态分布:  $X \sim N(0, 1)$

$$
\begin{array}{l}P(X = x) = \frac{1}{\sqrt{2\pi}} e^{-\frac{x^2}{2}} \\ E(X) = 0 \\ D(X) = 1 \end{array}
$$

# 立体几何

1. 投影

直观图(斜二测画法):  $Ox, Oz$  长度不变,  $Oy$  长度变成原来  $\frac{1}{2}$ , 沿  $45^\circ$  方向。 $xOy$  平面上的图形, 直观图面积是原图形面积的  $\frac{\sqrt{2}}{4}$ 。

2. 简单几何体

![](images/59ce439cef27fd13e7a2888321c2266cba9083f4cc863f974cee9476001774bd.jpg)

3. 三视图：直接构造法、补形法（交线法、删点法）。

4. 空间几何证明

0 公理

公理1：如果一条直线上的两点在一个平面内，那么这条直线上的所有点都在这个平面内。  $A\in \alpha$ $B\in \alpha \Leftrightarrow AB\subset \alpha_{\circ}$

公理2：如果两个不重合的平面有一个公共点，那么它们有且仅有一条经过该点的公共直线。

公理3：经过不在一条直线上的三点，有且只有一个平面。

$$
A,B,C\in \alpha \Leftrightarrow \exists iABC = \alpha_{\circ}
$$

推论1: 经过一条直线和这条直线外一点，有且仅有一个平面。

推论2: 经过两条相交直线，有且仅有一个平面。

推论3: 经过两条平行线，有且仅有一个平面。

平行公理：平行于同一直线的两条直线互相平行。  $l / / m$ $m / / n\Rightarrow l / / n_{\circ}$

等角定理：如果一个角的两边和另一个角的两边分别平行，那么这两个角相等或互补。

。线面平行判定定理：平面外一条直线与此平面内的一条直线平行，则该直线与此平面平行。  $l / / m$ $l\subset \alpha$ $m\not\subset\alpha\Rightarrow m / / \alpha_{\circ}$

线面平行性质：一条直线和一个平面平行，则过这条直线的任一平面与此平面的交线与该直线平行。  $l / / \alpha ,l\subset \beta ,\alpha \bigcap \beta = m\Rightarrow l / / m_{\circ}$

。面面平行判定定理：如果一个平面内有两条相交直线与另一个平面平行，那么这两个平面平行。  $l,m\subset \alpha ,l / / \beta ,m / / \beta ,l\bigcap m = O\Rightarrow \alpha / / \beta_{\circ}$

推论：如果一个平面内有两条相交直线分别与另一个平面内的两条相交直线平行，那么这两个平面平行。

$$
a,b\subset \alpha ,c,d\subset \beta ,a / / b,c / / d,a\cap b = A,c\cap d = B\Rightarrow \alpha / / \beta_{\circ}
$$

面面平行传递性：平行于同一平面的两个平面互相平行。

$$
\alpha / / \beta ,\beta / / \gamma \Rightarrow \alpha / / \gamma_{\circ}
$$

面面平行性质：两个平面平行，在一个平面内的任意一条直线平行于另外一个平面。  $\alpha / / \beta ,a\subset \alpha \Rightarrow a / / \beta_{\circ}$

。线面垂直判定定理：如果一条直线与平面内两条相交直线都垂直，那么这条直线与这个平面垂直。  $l\perp m,l\perp n,m,n\subset \alpha ,m\cap n = O\Rightarrow l\perp \alpha_{\circ}$

线面垂直性质：如果一条直线垂直于一个平面，那么该直线垂直于平面内的所有直线。  $l\perp \alpha ,m\subset \alpha \Rightarrow l\perp m_{\circ}$

。面面垂直判定定理：一个平面过另一平面的垂线，则这两个平面相互垂直。  $l\perp \alpha ,l\subset \beta \Rightarrow \alpha \perp \beta_{\circ}$

面面垂直性质：如果两个平面相互垂直，那么在一个平面内垂直于它们交线的直线垂直于另一个平面。  $\alpha \perp \beta ,\alpha \bigcap \beta = l,m\subset \alpha ,m\perp l\Rightarrow m\perp \beta$

# 5.空间角

订正：异面直线所成角一般被称为线线角，范围是  $(0,\frac{\pi}{2} ]$  而不是  $[0,\frac{\pi}{2} ]$  。感谢@xizeyoupan提醒。

![](images/a72ac6ed018197209aca594fc6ab9d88bdd7fc1fe82ec3991f2430fede0458c9.jpg)

6. 外接圆和外接球

- 直接构造：利用中垂线相交求出圆心、球心。- 补形法。- 正弦定理。- 正四面体  $r_{\text{外}} = \frac{3}{4} h = \frac{3}{4} \cdot \frac{\sqrt{6}}{3} a = \frac{\sqrt{6}}{4} a$ 。

内接圆和内接球

- 直接构造：利用角平分线相交求出圆心、球心。- 等面积/体积法：  $S = \frac{1}{2} r \sum C$ ，  $V = \frac{1}{3} r \sum S$ 。- 正四面体  $r_{\text{内}} = \frac{1}{4} h = \frac{1}{4} \cdot \frac{\sqrt{6}}{3} a = \frac{\sqrt{6}}{12} a$ 。

。内心性质:  $\Delta ABC$  的三边为  $a, b, c$ , 内心  $P \Leftrightarrow a \overrightarrow{PA} + b \overrightarrow{PB} + c \overrightarrow{PC} = 0$ 。

# 解析几何

1. 直线解析式

点斜式:  $y = k(x - x_0) + y_0$  斜截式:  $y = kx + b$  两点式:  $\frac{y - y_0}{x - x_0} = \frac{y_0 - y_0}{x_0 - x_0} = k$  一般式:  $Ax + By + C = 0$  截距式:  $\frac{x}{a} + \frac{y}{b} = 1$

2. 直线一般式

$\begin{array}{r}\circ k = - \frac{A}{B};b = - \frac{C}{B};a = - \frac{C}{A} \end{array}$  。直线的一个法向量  $\vec{n} = (A,B)$

直线平行或重合:  $\vec{n}_1 \times \vec{n}_2 = 0 \Leftrightarrow A_1B_2 - A_2B_1 = 0$ 。注意如果只考虑平行时要排除重合情况。

直线垂直:  $\vec{n}_1 \cdot \vec{n}_2 = 0 \Leftrightarrow A_1A_2 + B_1B_2 = 0$ 。

点到直线距离:有向距离  $d = \frac{Ax_0 + By_0 + C}{\sqrt{A^2 + B^2}}$ ，其中以  $\vec{n}$  的方向为正方向。

平行直线间的距离:  $|d| = \frac{|C_2 - C_1|}{\sqrt{A^2 + B^2}}$ 。

平行直线间的铅垂高差:  $|\Delta h| = \frac{|C_2 - C_1|}{|B|}$ 。

关于点的对称变换:

$$
(x,y)\xrightarrow{(x_0,y_0)}(x,y)-2(x-x_0,y-y_0)=(2x_0-x,2y_0-y)
$$

关于直线的对称点:

$$
(x,y)\xrightarrow{Ax+By+C=0}(x,y)-2d(\cos\theta,\sin\theta)=(x,y)-2\frac{Ax_0+By_0+C}{A^2+B^2}(A,B)
$$

过两条直线交点的直线系:

$$
A_1x + B_1y + C_1 + \lambda (A_2x + B_2y + C_2) = 0
$$

3. 线性规划

$Ax + By$  转为直线切口包。 $x^2 + y^2$

转为到原点距离。 $\frac{y - a}{x - b}$ 转为过一点斜率。其余情况先变换为以上三种或其他几何意义。

4. 圆

标准方程：  $(x - a)^2 +(y - b)^2 = r^2$  一般方程：  $x^{2} + y^{2} + Dx + Ey + F$  其中  $\begin{array}{r}a = - \frac{D}{2},b = - \frac{D}{2},r = \frac{1}{2}\sqrt{D^2 + E^2} - 4F, \end{array}$

圆的位置情况：

$d > r_{1} + r_{2}$  相离有4条公切线 $d = r_{1} + r_{2}$  外切有3条公切线 $r_1 + r_2 > d > |r_1 - r_2|$  相交有2条公切线 $d = |r_{1} - r_{2}|$  内切有1条公切线 $d< |r_{1} - r_{2}|$  内含有0条公切线

当两圆外切时两圆方程作差即可得到垂直于圆心连线的公切线方程；相交时两圆方程作差即可得到相交弦方程；内切时两圆方程作差即可得到公切线方程。

切点弦方程

对于任意圆和圆锥曲线上一点  $P(x_{0},y_{0})$  ，用  $\frac{x + x_0}{2}$  代  $x$  ，用  $\frac{y + y_0}{2}$  代  $y$  ，用  $xx_0$  代  $x^{2}$  ，用  $yy_{0}$  代  $y^{2}$  就得到过点  $(x_0,y_0)$  的切线方程。对于圆来说，如果点  $P(x_{0},y_{0})$  不在圆上而在圆外，那么得到切点弦方程。如果在圆内同样得到一条直线方程  $l$  ，满足  $d_{O,l}\cdot d_{O,P} = r^2$  。

直径圆方程

以  $(x_{1},y_{1})$  和  $(x_{2},y_{2})$  为直径的圆：

$(x - x_{1})(x - x_{2}) + (y - y_{1})(y - y_{2}) = 0$  。本质是圆周上点到直径端点连线垂直，对应向量点积为0。

# 5.圆锥曲线

椭圆：平面内与两点  $F_{1}$ $F_{2}$  距离和为定值  $2a$  的曲线  $(2c = |F_{1}F_{2}|,a > c > 0$  )。方程：  $\begin{array}{r}\frac{x^2}{a^2} +\frac{y^2}{b^2} = 1\exists \frac{y^2}{a^2} +\frac{x^2}{b^2} = 1(a^2 >b^2 >0)_\circ \end{array}$  离心率：  $\begin{array}{r}e = \frac{c}{a}\in (0,1) \end{array}$  ，离心率越大椭圆越扁。特殊点：  $(c,\pm \frac{b^2}{a})$  或  $(\pm \frac{b^2}{a},c)$  在椭圆上。

通径:  $\frac{2b^2}{a}$ ，同时为过椭圆焦点的最短弦长。

焦点三角形：椭圆上任意一点  $P(x_0,y_0)$  ，有  $\Delta F_1F_2P$  ，其中  $\angle F_1PF_2 = \theta$

$$
\begin{array}{l}C_{\Delta F_1F_2P} = 2(a + c) \\ S_{\Delta F_1F_2P} = b^2\tan \frac{\theta}{2} \end{array}
$$

焦半径：椭圆上任意一点  $P(x_0,y_0)$  ，  $\left|PF_1\right| = a + ex_0$  ，  $\left|PF_2\right| = a - ex_0$

$>$  双曲线

方程:  $\begin{array}{r}\frac{x^2}{a^2} - \frac{y^2}{b^2} = 1\exists \frac{y}{a^2} - \frac{x^2}{b^2} = 1(a^2,b^2 >0)_\circ \end{array}$  离心率:  $e = \frac{c}{a}\in (1, + \infty)$  ，离心率越大双曲线开口越大。特殊点:  $(c,\pm \frac{b^2}{a})$  或  $(\pm \frac{b^2}{a},c)$  在双曲线上。通径:  $\frac{2b^2}{a}$  ，同时为过双曲线焦点的最短弦长。渐近线:  $y = \pm \frac{b}{a} x$  或  $y = \pm \frac{a}{b} x$  即  $x = \pm \frac{b}{a} y)$  焦点三角形：双曲线上任意一点  $P(x_0,y_0)$  ，有  $\Delta F_1F_2P$  ，其中 $\angle F_1PF_2 = \theta .$

$$
S_{\Delta F_1F_2P} = b^2\cot \frac{\theta}{2} = \frac{b^2}{\tan\frac{p}{2}}
$$

$>$  抛物线

方程:  $y^{2} = \pm 2px$  或  $x^{2} = \pm 2py(p > 0)$

离心率:  $e = 1$

准线:  $y = \mp \frac{p}{2}$  或  $x = \mp \frac{p}{2}$

特殊点:  $(\frac{p}{2},\pm p)$  或  $(\pm p,\frac{p}{2})$  在抛物线上；  $(2p,\pm 2p)$  或  $(\pm 2p,2p)$  在抛物线上。

通径:  $2p$  ，同时为过抛物线焦点的最短弦长。

切线性质:以  $y^{2} = 2px$  为例:  $\forall a\geq 0$  ，抛物线过  $(- a,0)$  的切线切点为  $(a,\sqrt{2pa})$

![](images/92d611153d82bdb54d34f00548f8ff7e0bbe63c97982ca9d5be0f31fe827e63f.jpg)

圆切性质: 以  $y^{2} = 2px$  为例:

以AB为直径的圆与CD相切于点N, 且AN,BN与抛物线相切。

以CD为直径的圆与AB相切于点F。  $\Rightarrow \angle CFD = 90^{\circ}$

以AF为直径的圆相切于y轴。(对BF也成立)

以OE为直径的圆相切于AF。(对BF也成立)

焦半径: 以  $y^{2} = 2px$  为例: 记直线倾斜角为  $\theta$

$$
\begin{array}{r l} & {|A F| = \frac{p}{1 - \cos\theta} = \frac{p}{2} +x_{A}}\\ & {|B F| = \frac{p}{1 + \cos\theta} = \frac{p}{2} +x_{B}}\\ & {\Rightarrow |A F| + |B F| = \frac{2p}{\sin^{2}\theta} = x_{A} + x_{B} + p}\\ & {\Rightarrow \frac{1}{|A F|} +\frac{1}{|B F|} = \frac{2}{p}}\\ & {\Rightarrow S_{\Delta O A B} = \frac{p^{2}}{2\sin\theta}}\\ & {x_{A}x_{B} = \frac{p^{2}}{4}}\\ & {y_{A}y_{B} = -p^{2}} \end{array}
$$

$0$  圆锥曲线

第二定义:  $\frac{\sqrt{(x - c)^2 + y^2}}{|a - \frac{a^2}{c}|} = \frac{c}{a}$ 。当  $a > c$  时为椭圆,  $a < c$  时为双曲线,  $a = c$  时为直线  $y = 0$ 。

椭圆和双曲线焦点三角形涉及面积问题的几何法, 设

$$
|PF_{1}| = m, |PF_{2}| = n:
$$

$$
\left\{ \begin{array}{ll}\text{几何定义:} m\pm n = 2a \\ \text{余弦定理:} 4c^2 = m^2 +n^2 -2mn\cos \theta \\ \text{面积公式:} S_{\Delta PF_1F_2} = ch = \frac{1}{2} mn\sin \theta = \frac{1}{2} r_{\text{外}}C_{\Delta ABC} \end{array} \right.
$$

6. 解析几何常用结论

。角平分线性质对于角平分线平行于  $x$  或  $y$  轴时，  $k_{1} + k_{2} = 0$  内/外角平分线定理(△ABC角A的内/外角平分线AD交BC所在直线于  $D$  都有  $\frac{|AB|}{|DB|} = \frac{|AC|}{|DC|}$  角平分线上对称两点到角平分线距离相等(定义，不常用)。

。圆定义

到一个点  $(a,b)$  距离为定值的所有点  $P$

对两个点  $A,B,$  满足  $\frac{|PA|}{|PB|} = k(k > 0\mathbb{H}k\neq 1)$  的所有点  $P$

对两个点  $A,B,\overrightarrow{PA}\cdot \overrightarrow{PB} = 0$  的所有点  $P$

对  $\Delta ABC$ $\angle APC = \pi - \angle B$  且ABCP为凸四边形的所有点  $P$

。相交弦定理

![](images/6b9857861796ede7265b7bcf9485c16bad898c472a11101ccc2a142b8bd57e71.jpg)

$|PA|\cdot |PB| = |PC|\cdot |PD|$  恒成立(包括点  $P$  在圆内的情况)

。快速联立运算

$$
\left\{ \begin{array}{l}\frac{x^2}{a^2} +\frac{y^2}{b^2} = 1 \\ y = kx + m \end{array} \right.\Rightarrow \left(\frac{1}{a^2} +\frac{k^2}{b^2}\right)x^2 +\frac{2km}{b^2} x + \frac{m^2}{b^2} -1 = 0
$$

$$
\Delta = 4\left[(\frac{1}{a^2} +\frac{k^2}{b^2}) - \frac{m^2}{a^2b^2}\right]
$$

$$
y_{1} + y_{2} = k(x_{1} + x_{2}) + 2m
$$

$$
y_{1}y_{2} = k^{2}x_{1}x_{2} + km(x_{1} + x_{2}) + m^{2}
$$

对于形似  $k_{1} + k_{2} = C$  的条件往往直接通分运算，而当左右倍数相同，如  $\lambda k_{1} + \mu k_{2} = (\lambda +\mu)k_{3}$  则直接提取公因式  $k$  ，如：

$$
\frac{y_1 - 3}{x_1 - 2} +\frac{y_2 - 3}{x_2 - 2} = 2k + (2k + m - 3)\left(\frac{1}{x_1 - 2} -\frac{1}{x_2 - 2}\right)
$$

垂直的转化

1.  $k_{1}k_{2} = -1$

2.  $\vec{n}\cdot \vec{m} = 0$

3. 转化为圆周上的点根据圆的性质计算

对称构造

对于椭圆外一点T作一条椭圆的线  $AB$  ，讨论  $\vec{T} A = \lambda \vec{T} B$  时，构造关于入的对称式：

$$
\lambda +\frac{1}{\lambda} = \frac{(x_B - x_T)^2 + (x_A - x_T)^2}{(x_A - x_T)(x_B - x_T)}
$$

然后再由对勾函数的单调性求出入的范围条件。

对于不对称的多条直线问题，如AN和BM交于一点，往往可以交换两条直线要求AM和BN同时交于一点，然后利用这四条直线即可构造对称式。

一些非对称式可以直接代入韦达定理，如  $3x_{1} + x_{2} = 3(x_{1} + x_{2}) - 2x_{2}$  最后的理想结果是分子分母同时含有带有  $x_{2}$  的等比项，直接约分消去。

抛物线

当直线与抛物线联立的时候，求值代入时更多用  $y^{2} = 2px$  而非椭圆和圆锥曲线时用  $y = kx + m$  进行  $y$  和  $x$  的转化，这个技巧往往对运算量有巨大影响！

# 导数与积分

1. 导数：

$$
f^{\prime}(x) = \lim_{\Delta x\to 0}\frac{f(x + \Delta x) - f(x)}{\Delta x}
$$

在数形结合方面常有  $\begin{array}{r}f^{\prime}(x) = \lim_{\Delta x\to 0}\frac{\Delta y}{\Delta x} = k = \tan \theta . \end{array}$

奇函数的导数是偶函数，偶函数的导数是奇函数。

较少用公式：  $\begin{array}{r}(a^{x})^{\prime} = a^{x}\ln a;(\log_{a}x)^{\prime} = \frac{1}{x\ln a} \end{array}$

2. 切线方程：

在点  $(x_0,f(x_0))$  处的切线：  $y = f^{\prime}(x_0)(x - x_0) + f(x_0)$

过点  $(x_{1},y_{1})$  处的切线，设切点  $(x_0,y_0)\colon y_1 = f'(x_0)(x_1 - x_0) + f(x_0)$  ，就可以解出  $x_0$  ，进而求出切线。

3. 极值点：函数在该点左右两侧邻近位置值都大/小于该点。区间端点不是极值点。同零点，极值点是一个横坐标。

最值点  $=$  所有极值点和区间端点中函数最大/小值点。

4. 双变量偏移问题：对称和问题

![](images/9873ebe03b16edd883a71d2e2d7f3806ed2566f456e46a7c83e6df929926b703.jpg)

Date

![](images/5ea8f0bdee4bd2b1a41439ee65f058092139d65afd2c886400646c9ce3306d74.jpg)

5. 积分：记  $F^{\prime}(x) = f(x)$  ，则

$$
\int_{l}^{r}f(x)dx = F(x)|_{l}^{r} = F(r) - F(l)
$$

较少用公式：  $\begin{array}{r}\int_{l}^{r}a^{x}dx = \frac{a^{x}}{\ln a}\bigg|_{l}^{r} \end{array}$

求积分：

·利用奇偶性求积分：当  $a,b$  关于原点对称时奇函数积分为0。·利用几何法求积分

如  $\int_{0}^{6}\sqrt{9 - (x - 3)^{2}} = \int_{- 3}^{3}\sqrt{9 - x^{2}}$  几何意义为所有到原点距离为3的点的纵坐标之和，即  $r = 3$  的半圆面积  $\frac{9}{2}\pi$ 。

- 原函数的构造

$$
n f(x) + f'(x) = \frac{1}{e^{nx}} [e^{nx} f(x)]
$$

$$
f'(x) g(x) + f(x) g'(x) = [f(x) g(x)]'
$$

$$
f'(x) g(x) - f(x) g'(x) = \left[\frac{f(x)}{g(x)}\right]'
$$

$$
f(x) + f'(x) \tan x = \frac{1}{\cos x} [f(x) \sin x]'
$$

6. 麦克劳林级数

$$
f(x) = \sum \frac{f^{(n)}(0)}{n!} x^n
$$

常见函数：

$$
\begin{array}{c} e^{x} = \sum \frac{1}{n!} x^{n} \\ \displaystyle \frac{1}{1 - x} = \sum x^{n} \\ \displaystyle \sin x = \sum \frac{(-1)^{n}}{(2n + 1)!} x^{2n + 1} \\ \displaystyle \cos x = \sum \frac{(-1)^{n}}{(2n)!} x^{2n} \\ \displaystyle \ln (1 + x) = -\sum \frac{(-1)^{n}}{n} x^{n} \\ \displaystyle \ln (1 - x) = -\sum \frac{1}{n} x^{n} \end{array}
$$

# 极坐标与参数方程

1.  $(\rho ,\theta)$

2.  $S_{\Delta AOB} = \frac{1}{2} \rho_{A}\rho_{B} \sin (|\theta_{A} - \theta_{B}|)$ 。（正弦定理推论）。

3. 过原点的圆的极坐标通式：  $\rho = 2r\cos (\theta -\phi)$ ，表示以  $x$  轴为起始逆时针旋转  $\phi$  弧度得到的圆（顺加逆减）。

4. 直线的参数方程：  $\left\{ \begin{array}{l}x = x_{0} + \cos \theta \cdot t \\ y = y_{0} + \sin \theta \cdot t \end{array} \right.$  (t为参数)。直线过点  $(x_{0},y_{0})$ ，倾斜角  $\theta$ ，斜率  $\tan \theta$ 。

t的几何意义是  $(x_0, y_0)$  到  $(x, y)$  的有向距离，注意判断t的符号。

对于非标准的直线参数方程  $\left\{ \begin{array}{l}x = x_0 + a \cdot t \\ y = y_0 + b \cdot t \end{array} \right.$  (t为参数)使用t的几何意义时一定要保证  $a^2 + b^2 = 1$ 。

5. 椭圆的参数方程：  $\left\{ \begin{array}{l}x = a \cos \theta \\ y = b \sin \theta \end{array} \right.$  (θ为参数)。注意对于椭圆上一点P，θ并不是  $\angle POx$ 。

扫描二维码即可在手机上查看这篇文章，或者转发二维码来分享这篇文章：

![](images/8429f56e2cfb3069a70acfc726af08eb2d941a77c87ae29cff230d03fa400597.jpg)
