# Methods for analyzing anisotropic flow in relativistic nuclear collisions

<center>A. M. Poskanzer and S. A. Voloshin</center>

## 事件平面关联

### 傅立叶展式

粒子发射方位角对反应平面的依赖可以写成傅里叶级数的形式，

$$
E \frac{d^{3} N}{d^{3} p}=\frac{1}{2 \pi} \frac{d^{2} N}{p_{t} d p_{t} d y}\left(1+\sum_{n=1}^{\infty} 2 v_{n} \cos \left[n\left(\phi-\Psi_{r}\right)\right]\right)
$$

$\Psi_{r}$ 代表真实的反应平面，正弦项由于反应平面的对称性消失。采用傅里叶方法的主要优点是利用事件平面算得的傅里叶系数可以用有限多重数造成的事件平面分辨率进行修正，这种修正通常会增大流系数。

这一点非常重要，经过了修正后，在某一相空间区域的粒子的流的计算结果可以直接与理论值比较，或者与未对探测器接受情况进行过滤的模拟进行比较，对于这些模拟，反应平面被视为包含理论影响参数的平面。

请注意每个 $v_{n}$ 前面都写有常数2，带上该系数可以使 $v_{n}$ 的意义非常清晰。 $v_{n} = \langle \cos[n(\phi-\Psi_r)] \rangle$ ，其中 $\langle\rangle$ 代表对在所有事件的所有粒子取平均, $v_1$ 是 $\langle p_{x}/p_{\mathrm{T}}\rangle$ ， $v_{2}$ 是 $\langle (p_{x}/p_\mathrm{T})^2-(p_{y}/p_\mathrm{T})^2 \rangle$

### 反应平面的估计

该方法使用各向异性流本身来确定事件平面。

这意味着事件平面可以由各阶的流分别确定。 $n$ 阶流矢量 $Q_{n}$ 和事件平面 $\Psi_{n}$ 由下式定义：

$$
\begin{aligned}
&Q_{n} \cos \left(n \Psi_{n}\right)=X_{n}=\sum_{i} w_{i} \cos \left(n \phi_{i}\right) \\
&Q_{n} \sin \left(n \Psi_{n}\right)=Y_{n}=\sum_{i} w_{i} \sin \left(n \phi_{i}\right)
\end{aligned}
$$

$$
\Psi_{n}=\left(\arctan \frac{\sum_{i} w_{i} \sin \left(n \phi_{i}\right)}{\sum_{i} w_{i} \cos \left(n \phi_{i}\right)}\right) / n
$$

求和第 $i$ 个粒子， $w_{i}$ 代表权重。一般来说， $w_{i}$ 的设置是为了使反应平面分辨率尽可能好。有时可以通过选择特定类型的粒子，或使用粒子的横向动量加权等方法来实现。通常情况下，奇数和偶数阶平面的权重是不同的。对于对称碰撞，镜像对称性导致如果所有粒子的方位角移动，质量中心后半球的粒子分布应该与前半球相同。这解释了为什么对于奇数阶来说，权重的符号在后半球是相反的，而对于偶数阶来说，权重的符号不变。注意第 $n$ 阶确定的事件平面角度范围为 $0 \leqslant \Psi_{n}<2 \pi / n$ 。当 $n=1$ 时， $Q = \sum{w \frac{\bf{p_{\mathrm{T}}}}{|p_{\mathrm{T}}|}}$ 。

### 粒子对事件平面的分布

下一步是研究粒子方位角对事件平面的分布。注意只要 $n>m$ 而且 $n$ 是 $m$ 的倍数，可以采用任意 $m$ 阶的平面去计算任意 $n$ 阶的流系数 $v_{n}$。当 $n>m$ 时，$v_{n}$的符号是由 $v_{m}$ 确定的，即一阶的平面可以用来确定任意阶的 $v_{n}$ ，二阶的平面可以确定 $v_{2},v_{4}$ 。对于 $m$ 阶的平面，傅立叶展开式是

$$
\frac{d(wN)}{d(\phi-\Psi_{m})}=\frac{\langle wN \rangle}{2\pi}(1+\sum_{k=1}^{\infty}{2v_{km}^\mathrm{obs}\cos[km(\phi-\Psi_{m})]})
$$

在这里利用 $km$ 代替 $n$，注意当 $m=1$ 时所有项都保留，但是当 $m=2$ 时只有奇次项保留。 $w$ 代表权重，当研究横动量流时可以用粒子的 $p_{\text{T}}$ ，当研究粒子多重数与流的关系就取为1。   $v^{\mathrm{obs}}_{n}$ 通过 $\langle\cos[n(\phi-\Psi_{m})]\rangle$ 计算。 $\phi-\Psi_{m}$ 最小周期为 $2\pi/m$。可以将负值移动 $2\pi$ ，然后按照其周期性进行折叠。当粒子用于计算事件平面时，需要重新计算扣除了该粒子的平面，消除自相关效应。这一点可以通过先记录正（余）弦的总和，然后减去粒子的正（余）弦值和权重方便的做到。这种去除自相关方法基于来动量守恒的贡献很小的假设。

### 事件平面的分辨率

将 $v_{\mathrm{obs}}$ 除以事件的分辨率就得到了真实的 $v_{n}$ ，

$$
v_{n} = v^{\mathrm{obs}}_{n}/\langle \cos(\Psi_{m}-\Psi_{r}) \rangle
$$

平均余弦值小于1，因此这种变化总是会增大流系数。

分辨率取决于事件平面的阶数 $m$ 以及计算的阶数 $n$ 。通常来讲利用本阶平面计算本阶的 $v_{2}$ 具有最好的精度 （ $m=n,k=1$ ），因为分辨率会随着 $k$ 的增加而变差。例如，即使有时候椭圆流比定向流弱一些，依然可以使用 $\Psi_{2}$ 计算 $v_{2}$ 来实现更好的精度。

可以从 $m(\Psi_{m}-\Psi_{r})$ 的分布为出发点计算分辨率， $m(\Psi_{m}-\Psi_{r})$ 的分布可以写成，

$$
\frac{d P}{d\left[m\left(\Psi_{m}-\Psi_{r}\right)\right]}=\int \frac{v_{m}^{\prime} d v_{m}^{\prime}}{2 \pi \sigma^{2}} \times \exp \left(-\frac{v_{m}^{2}+v_{m}^{\prime 2}-2 v_{m} v_{m}^{\prime} \cos \left[m\left(\Psi_{m}-\Psi_{r}\right)\right]}{2 \sigma^{2}}\right)。
$$


 $\sigma$ 适用于任意的 $m$ ，与 $\sqrt{N}$ 成反比，$N$ 是用于确认用于确认反应平面的粒子数目，
 
$$
\sigma^{2}=\frac{1}{2 N} \frac{\left\langle w^{2}\right\rangle}{\langle w\rangle^{2}}
$$

积分 $\frac{d P}{d\left[m\left(\Psi_{m}-\Psi_{r}\right)\right]}$ 可以被解析的给出，然后事件分辨率可以写成

$$
\left\langle\cos \left[k m\left(\Psi_{m}-\Psi_{r}\right)\right]\right\rangle = \frac{\sqrt{\pi}}{2 \sqrt{2}} \chi_{m} \exp \left(-\chi_{m}^{2} / 4\right)  \times\left[I_{(k-1) / 2}\left(\chi_{m}^{2} / 4\right)+I_{(k+1) / 2}\left(\chi_{m}^{2} / 4\right)\right]
$$

其中 $\chi_{m} \equiv v_{m} / \sigma$ （ $=v_{m}\sqrt{2N}$ ）， $I_{\nu}$ 是 $\nu$ 阶的 modified 贝塞尔方程，如图xxx。 注意本文中的 $\chi$ 比Ollitrault所使用的大 $\sqrt{2}$。

注意，如果事件平面和流是同阶的 （ $k=1$ ）采用 $\langle \cos[m(\Psi_{m}-\Psi_r)]\rangle$ 。当阶次不同，例如采用一阶的流矢量确定平面计算椭圆流（ $m=1,k=2$ ），关系式应该写成 $\langle \cos[2(\Psi_{1}-\Psi_r)]\rangle$ 。

早期 Bevalac 采用的分辨率关系式接近曲线 $\chi_{1} = v_{1}\sqrt{2N}$ 的1.5倍。然而在 AGS 或 SPS 的高束流能量下使用旧的程序将大大高估分辨率并使流系数太小。

### 独立粒子集之间流的关系

如果在两个不同的运动学窗口，或者在不同子事件中构建反应平面，他们的关系也可以解析地写出，但是更加重要的是如下关系，

$$
\left\langle\cos \left[n\left(\Psi_{m}^{a}-\Psi_{m}^{b}\right)\right]\right\rangle = \left\langle\cos \left[n\left(\Psi_{m}^{a}-\Psi_{r}\right)\right]\right\rangle \times\left\langle\cos \left[n\left(\Psi_{m}^{b}-\Psi_{r}\right)\right]\right\rangle
$$

这里假设了出了流到值的关联之外，没有其他的关联，或者其他的关联可以被忽略。（例如由共振态衰变产生的两粒子关联也应该scale上 $1/N$ ，通常可以忽略。）如果该假设不成立，必须采用某些方法避免或者修正这些关联。细节参见《非流关联》一章。

注意，这两个平面之间的关联（ $\Psi_{a}-\Psi_{b}$ 的分布）无法很好的用傅立叶展开式描述。如果两个平面存在很强的关联，$\Psi_{a}-\Psi_{b}$ 应该呈高斯分布，如果完全无关，应该呈现三角分布，此时对 $\Psi_{a}-\Psi_{b}$ 取绝对值并按照 $\pi/n$ 的角度折叠，三角分布就会变成平分布。这不会影响  $\left\langle\cos \left[n\left(\Psi_{m}^{a}-Psi_{m}^{b}\right)\right]\right\rangle$ 的值，但是会更容易在图中不平坦的部分看到真实的来自流效应的影响。

来自不同子事件的不同阶流也可以写出类似的关系，例如 $\Psi^a_1-\Psi^b_2$ 的关系可以写成

$$
\langle \cos[2(\Psi_{1}^{a}-\Psi_{2}^{b})] \rangle = \langle \cos[2(\Psi_{1}^{a}-\Psi_{r})] \rangle \times \langle \cos[2(\Psi_{2}^{b}-\Psi_{r})] \rangle。
$$

这个表达式正比于 $v^{2}_{1}v_{2}/\sigma^{3}$  ，取值非常小，但是它对确定不同的阶流之间的相对取向非常有用，参见《近似》一章。另一角度上说，相对取向可以利用（7）式确定，此时 $k>1$    。

### 确定事件平面分辨率

上一章介绍的关系式可以用于直接从数据计算事件平面的分辨率。例如，如果已知两个**相同多重数**子事件（理论上他们的分辨率是相同的），利用式12可知他们的分辨率均为

$$
\langle \cos[n(\Psi^{a}_{m}-\Psi_{r})] \rangle=\sqrt{\langle\cos[n(\Psi^{a}_{m}-\Psi_{m}^{b})] \rangle}，
$$

其中 $n=km$ ， $k$ 并不必要等于1。如果子事件之间有关联，平方根式中的值恒为正（当总 $p_{\mathrm{T}}$ 固定为零时，流很小、涨落很大、非流效应可能使该值为负）。注意，以这种方式确定的事件平面分辨率是子事件的事件平面分辨率。如果想要利用整个事件中的所有粒子确定事件平面，整体的事件平面可以通过式11或者下面的近似方法式23、24，考虑到整个事件的分辨率是子事件的两倍。因为 $\chi_{m}=v_{m}/\sigma$ 正比于 $\sqrt{N}$，在较低的分辨率下图1中的曲线是接近线性的，可以得到总分辨率

$$
\langle \cos[n(\Psi_{m}-\Psi_{r})] \rangle = \sqrt{2} \langle\cos[n(\Psi^a_m-\Psi_r]\rangle
$$


总分辨率是 $\sqrt{2}$ 倍的子事件分辨率。如果子事件不“相等”，或者两个运动学窗口的粒子分辨率不同，则至少需要三个子窗口去得到每一个部分的分辨率。例如，第一个窗口中的分辨率为

$$
\left\langle\cos \left[n\left(\Psi_{m}^{a}-\Psi_{r}\right)\right]\right\rangle = \sqrt{\frac{\left\langle\cos \left[n\left(\Psi_{m}^{a}-\Psi_{m}^{b}\right)\right]\right\rangle\left\langle\cos \left[n\left(\Psi_{m}^{a}-\Psi_{m}^{c}\right)\right]\right\rangle}{\left\langle\cos \left[n\left(\Psi_{m}^{b}-\Psi_{m}^{c}\right)\right]\right\rangle}}
$$

### 近似

我们考虑两种极端情况。

当流很小的时候 $\chi_m \ll 1$ （ $v\ll\sigma$ ，意味着分辨率很小），可以在积分以前展开积分中的指数，此时

$$
\frac{d P}{d\left(m\left(\Psi_{m}-\Psi_{r}\right)\right)} \propto 1+\sqrt{\frac{\pi}{2}} \chi_{m} \cos \left[m\left(\Psi_{m}-\Psi_{r}\right)\right]
$$

当 $k=1$时分辨率可以解析地写成

$$
\left\langle\cos \left[m\left(\Psi_{m}-\Psi_{r}\right)\right]\right\rangle \approx \sqrt{\frac{\pi}{8}} \chi_{m}
$$

这种情况下，分辨率对于 $\chi$ 是线性的，由于 $\sigma$ 对所有的 $m$ 都相同，不同 $m$ 阶的分辨率正比于 $v_{m}$ 。

联立式14 10 18，可以直接从两个子事件中得到流的表达式

$$
v_{m} = \sqrt{(4/\pi) \frac{\langle w^2 \rangle}{\langle w \rangle ^2}} \sqrt{\frac{\langle \cos[m(\Psi_m^a-\Psi_m^b)] \rangle}{N_{\mathrm{sub}}}}
$$

其中 $N_\mathrm{sub}$ 是子事件的多重数。

保留式9中的二次项，

$$
\langle \cos[2m(\Psi_m-\Psi_r)]\rangle\approx \frac{\chi_m^2}{4} \approx 
\frac{2}{\pi} \{\langle \cos[m(\Psi_m-\Psi_r)] \}^2
$$

在事件的分辨率由一阶流（ $m=1$ ）确定的情况下，计算 $v_{2}$ 需要取 $k = 2$ 的情况下上面的关系式为修正。当 $\chi_{m}<0.5$ 时，以上的近似是相对准确的。

使用上述近似，两个子事件（ $m=1$ 与 $m=2$ ）不同阶事件平面的关联可以写成

$$
\left\langle\cos \left[2\left(\Psi_{1}^{a}-\Psi_{2}^{b}\right)\right]\right\rangle \approx  \pm \frac{2}{\pi}\left\langle\cos \left(\Psi_{1}^{a}-\Psi_{1}^{b}\right)\right\rangle \times \sqrt{\left\langle\cos \left[2\left(\Psi_{2}^{a}-\Psi_{2}^{b}\right)\right]\right\rangle}
$$

如上文所述，等式子左侧的符号表明了不同阶流的相对方向，而等式右侧 $\pm$ 之后的部分总是正的。注意这些量都独立地取自数据本身，所以分别计算其值的大小进行对比是一种对结果一致性的检验。

第二种极限情况是在流很大 $\chi \gg 1$ 时，可以展开式9中的余弦项得到如下近似式

$$
\frac{d P}{d\left(m\left(\Psi_{m}-\Psi_{r}\right)\right)} \approx \frac{\chi_{m}}{\sqrt{2 \pi}} \exp \left[-\frac{\chi_{m}^{2}\left(m\left(\Psi_{m}-\Psi_{r}\right)^{2}\right)}{2}\right]
$$

较强的流在相对低能量下的研究中非常重要，我们暂不讨论其细节。注意当且仅当这种情况下 $m(\Psi_m-\Psi_r)$ 可以被高斯分布描述。

这里我们列出当 $k=1,2$ 时式11的插值公式

$$
\left\langle\cos \left[m\left(\Psi_{m}-\Psi_{r}\right)\right]\right\rangle = 0.626657 \chi_{m}-0.09694 \chi_{m}^{3} + 0.02754 \chi_{m}^{4}-0.002283 \chi_{m}^{5}
$$

$$
\left\langle\cos \left[2 m\left(\Psi_{m}-\Psi_{r}\right)\right]\right\rangle = 0.25 \chi_{m}^{2}-0.011414 \chi_{m}^{3}-0.034726 \chi_{m}^{4} + 0.006815 \chi_{m}^{5}
$$

插值适用于 $\chi_m < 3$ 的情况。

为了使用上述方程从子事件辨率到全事件分辨率，必须带入该方程计算子事件分辨率，并取平方根以得到 $\chi_m$。然后对该 $\chi_{m}$ 乘以 $\sqrt{2}$ ，因为  $\chi_{m}$ 正比于  $\sqrt{N}$ ，进而利用同一关系式得到全事件的分辨率。我们利用迭代的方法求这些方程的解。 误差传播需要在输入中改变很小的值观察结果的变化。

另一种近似方法计算全事件的 $\chi_m = v_m /\sigma$ 是通过统计 $m |\Psi_{m}^{a}-\Psi_{m}^{b}| > \pi/2$ 的事件占总事件的比例

$$
\frac{N_{\text {events }}\left(m\left|\Psi_{m}^{a}-\Psi_{m}^{b}\right|>\pi / 2\right)}{N_{\text {total }}}=\frac{e^{-\chi_{m}^{2} / 4}}{2}
$$

只有当 $\chi_{m}$ 很小时该方法可行。

## 角分布的逐事件分析

我们研究在一个相当大的快度范围内的方位角分布各向异性。计算 $ \bf{Q}_{n}$ 时，每一个事件的有限多重数导致了有限的事件平面分辨率与 $Q_{n}$ 的涨落。在没有流的情况下 $\langle Q_n\rangle =\langle N \rangle$ （ $w_{i}$ 设为 $1$ ）。各向异性流使得每个事件中的 $ \bf{Q}_{n}$ 产生了 $v_{n}N$ 的涨落，有效地展宽了 $Q_{n}$ 的分布。保留流影响下的没有消失的头阶项

$$
\langle Q_n^2 \rangle = \langle N \rangle + \bar{v}_n^2 \langle N^2 \rangle
$$

该式可以被用以计算 $ \bar{v}_{n} $  $ \bar{v}_{n} $  表示在全局快度区计算 $Q_{n}$ 的 $v_{n}$ 的平均值。

另一种方法需要根据理论公式去拟合$r_n=Q_n/N$的分布，$ \bar{v}_{n} $ （准确的说是其绝对值）作为一个拟合参数。$r_{n}$ 应当被如下公式拟合，

$$
\frac{d P}{r_{n} d r_{n}}=\frac{1}{\sigma^{2}} \exp \left(-\frac{\bar{v}_{n}^{2}+r_{n}^{2}}{2 \sigma^{2}}\right) I_{0}\left(\frac{r_{n} \bar{v}_{n}}{\sigma^{2}}\right)
$$

其中 $I_0$ 是modified贝塞尔方程，$\bar{v}_n$ 是要得到的值，$\sigma$ 是相关于有限多重数的参数。上式由中心极限定理导出。需要多重数 $N$ 很大。原则上 $\langle Q^2 \rangle = \langle N \rangle + \bar{v}_n^2 \langle N^2 \rangle$ 没有这种限制，尽管事实上信噪比正比于 $N$ ，$N$ 较大时候才可以用于数据分析。

另需注意，这两种方法都不需要确定事件平面，并且可以在一个快速窗口中执行，但它们确实要求该窗口相当宽，以便具有相对较多的粒子。上面的分布可用于选择流较大或者流较小的事件。

## 非流关联的贡献

只有当流的关联于其他关联相比占据主导地位时，本文的分析才是适用的。这里所说的其他关联包含例如长程、短程、两体、多体关联（由量子统计、共振态、minijet或者jet等产生）等等。下面我们讨论这些非流相关性对由两个独立子事件确定的事件平面相关性的贡献。通常非流相关量的贡献正比于 $1/N$，其中 $N$ 是用于确定事件平面的粒子的多重数。但人们应该记住，动量守恒的贡献随着探测到的粒子比例而增加而增加，玻色-爱因斯坦相关性的相对贡献可以独立于多重数（如果子事件是通过将同一相空间区域的所有粒子随机划分为两个子群得到，那么后者可能很重要，因为其中贡献不同子事件的粒子在相空间中可能非常接近）。从对真实数据中的流分析发现，非流量相关性的影响相当复杂，因此我们从蒙特卡洛事件的分析开始。

### 蒙特卡洛事件的非流关联

......

### 实验数据中的非流关联

......

## 在蒙特卡洛模型中引入流的简单方法

为了研究不同的探测器效果或方法的可靠性，有时需要将各向异性流引入蒙特卡洛模型。可以通过改变每个粒子的方位角（改变方位角的相空间分布）来引入

$$
\phi \rightarrow \phi^{\prime}=\phi+\Delta \phi
$$

其中

$$
\Delta \phi=\sum_{n} \frac{-2}{n} \widetilde{v}_{n} \sin \left[n\left(\phi-\psi_{0}\right)\right]
$$

 $\widetilde{v}_{n}$ 是 $n$ 个参数， $\psi_{0}$ 是所添加的流的方位角。 $\widetilde{v}_{n}$ 可以是快度和横动量的函数。特别地，奇数阶的 $\widetilde{v}_{n}$ 应该在后半球面反号。可以检查方位角的这种变化是否会导致所需的分布变化。对于一阶的 $\widetilde{v}_{n}$ ， $v_{ n} = \langle \cos[n(\phi^{’}-\Psi_{r})]\rangle =  \widetilde{v}_{n}$  。如果需要，也可以利用数值方法计算出高阶修正。

## 讨论

### 高阶流（ $n \geq 3$ ）

本文提出的流分析方法适用于各向异性的所有阶次。更高的阶数是在更精细的尺度上以更高的对称性看待对撞事件。$n \geq 3$ 的各向异性流研究值得关注。例如，流体力学模型和级联类的模型对高阶段流的预测存在很大差异。还有一些物理过程可能导致非零的更高阶流。人们普遍认为，pi介子“反流”（定向流与质子相反）的主要原因是其收到了核子移动的影响。这种影响将在高阶方位角分布中体现出来，而且在不同的快度区域影响不同。另一个效应是从在低能量下非常重要的远离平面的椭圆流（挤压）到高能量下的在平面椭圆流的转变。在过渡束流能量下，这两种效应可能都很重要，四阶流可能会在这种能量下达到峰值。即使在高束流能量下，远离平面挤出效应也可能在短时间内占主导地位，而在很长一段时间内膨胀中占主导地位，从而导致整体的四阶流。

### 横向流与各向异性流

还要强调，上述方法允许重建相对于反应平面的三维微分分布，特别是便于分析各向异性流对 $p_T$ 的依赖性。在某些研究中认为横向的定向流是有效发射源在横平面上移动的结果，该研究认为在源静止坐标系中，一阶方位角分布（ $v_{1}$ ）为零，并且最终的各向异性仅由于源的横向运动。

在这种情况下， $v_{1}$ 的横动量依赖具有相当特殊的形状。 径向膨胀导致 $v_{1}$ 在低 $p_{\mathrm{T}}$ 处减小。 对于某些参数集（温度、径向和定向速度）， $v_{1}$ 变为负值。当具有这样一个 $p_{\mathrm{T}}$ 值的粒子产生更可能来自于有效源沿着流方向相反的方向移动，此时定向流和径向流倾向于互相补偿。

同样的考虑也可以应用于椭圆流。如果假设椭圆流是有效源在某个平面上更快速扩展的结果，那么 $v_{2}$ 的 $p_{\mathrm{T}}$ 依赖将表现出与在定向流的情况下观察到的 $v_{1}$ 完全相同的特征。

### 粒子对角关联

双粒子大角度方位相关性经常被用来研究各向异性流。在不拒绝这种可能性的情况下，我们注意到这种相关性中的预期信号可能非常小。粒子对方位角分布的差（ $\Delta\phi=\phi_1-\phi_2$ ）可以写成

$$
\frac{d N^{\text {pairs }}}{d \Delta \phi} \propto\left(1+\sum_{n=1}^{\infty} 2 v_{n}^{2} \cos (n \Delta \phi)\right)
$$

然而这并不意味着“信噪比”很小，原则上，该方法可以成功应用于数据以获取流量信号。然而，关于反应平面的三重微分分布的重建（流分析的目标）变得更加复杂。

这种方法不需要确定事件平面。通常，这种分布是在每个事件中使用所有可能的对组合构建的。注意，在这种情况下每个粒子都将成对很多次，这些对在统计学上并不独立。因此需要谨慎的估计结果的误差。

