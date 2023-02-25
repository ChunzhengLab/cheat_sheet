## Sub-Sample Method

### 1. 中心值
Sub-Sample Method 中心值依然采用全体样本的均值

### 2. 误差
Sub-Sample Method 误差采用**子样均值的标准误差**，**注意：方差项要带入样本方差 $S^{2}$**

$$
\mathrm{error} = \frac{\sqrt{S^2}}{\sqrt{n}}= \frac{\sqrt{\frac{\sum_{i}{(x_i-\bar{x_i})^2}}{n-1}}}{\sqrt{n}} = \sqrt{\frac{\sum_{i}{(x_i-\bar{x_i})^2}}{n(n-1)}}
$$

对于 ```TProfile``` 类，

- 当 error option 设置为 ```""```时，```GetBinError``` 返回**标准偏差，方差项带入总体方差$\sigma^2$**，即 

$$
\mathrm{bin\_error(option= s)} = \frac{\sigma}{\sqrt{n}}= \frac{\sqrt{\frac{\sum_{i}{(x_i-\bar{x_i})^2}}{n-1}}}{\sqrt{n}} = \frac{\sqrt{\sum_{i}{(x_i-\bar{x_i})^2}}}{n}
$$

- 当 error option 设置为 ```“s”``` 时，```GetBinError``` 返回**标准差**，**此时方差项也带入总体方差 $\sigma^2$** ，即

$$
\mathrm{bin\_error(option=default)} = \sigma= \sqrt{\frac{\sum_{i}{(x_i-\bar{x_i})^2}}{n}}
$$

所以可以利用 ```TProfile``` 类计算 Sub-Sample 误差：先将 error option 设置为 ```“s”``` 得到带入了总体方差的标准差，再乘上 $\frac{1}{\sqrt{n-1}}$ 因子：

```c++
//现将所有subsample的中心值（假设有n_subs个字样）fill入profile
profile->SetErrorOption("s");
double sigma = profile->GetBinError(ibin);
double error = 1./sqrt{n_subs} * sigma;
```

