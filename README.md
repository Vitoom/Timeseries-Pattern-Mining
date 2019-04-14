# Timeseries-Pattern-Mining
## 1. Pattern Mining: t-SNE + VAE
### 1.1 DTW
DTW可以计算两个时间序列的相似度，尤其适用于不同长度、不同节奏的时间序列（比如不同的人读同一个词的音频序列）。DTW将自动warping扭曲时间序列(即在时间轴上进行局部的缩放)，使得两个序列的形态尽可能的一致，得到最大可能的相似度。

![image](https://github.com/Vitoom/Timeseries-Pattern-Mining/raw/master/images/images1.png)

### 1.2 t-SNE
#### 1.2.1 SNE原理
SNE是通过仿射(affinitie)变换将数据点映射到概率分布上，主要包括两个步骤：
> * SNE构建一个高维对象之间的概率分布，使得相似的对象有更高的概率被选择，而不相似的对象有较低的概率被选择。
> * SNE在低维空间里在构建这些点的概率分布，使得这两个概率分布之间尽可能的相似。

SNE是先将欧几里得距离转换为条件概率来表达点与点之间的相似度。具体来说，给定一个N个高维的数据x1,...,xN(注意N不是维度), t-SNE首先是计算概率Pij，正比于xi和xj之间的相似度(这种概率是我们自主构建的)，即：
<img src="http://chart.googleapis.com/chart?{p_{j|i}=\frac{{exp}^{(-||x_i-x_j||^2/(2\sigma_i^2))}}{\sum_{k\neq i}{exp}^{(-||x_i-x_j||^2/(2\sigma_i^2))}}}" />
这里的有一个参数是σi，对于不同的点xi取值不一样，后续会讨论如何设置。此外设置p_{x∣x}=0,因为我们关注的是两两之间的相似度。
那对于低维度下的xi，我们可以指定高斯分布为方差为1/sqrt(2)，因此它们之间的相似度如下:
<img src="http://latex.codecogs.com/gif.latex?p_{j|i}=\frac{{exp}^{(-||x_i-x_j||^2)}}{\sum_{k\neq i}{exp}^{(-||x_i-x_j||^2)}}" />
同样，设定q_{i∣i}=0.

