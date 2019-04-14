# Timeseries-Pattern-Mining
## 1. Pattern Mining: t-SNE + VAE
### 1.1 DTW
DTW可以计算两个时间序列的相似度，尤其适用于不同长度、不同节奏的时间序列（比如不同的人读同一个词的音频序列）。DTW将自动warping扭曲时间序列(即在时间轴上进行局部的缩放)，使得两个序列的形态尽可能的一致，得到最大可能的相似度。

![image](https://github.com/Vitoom/Timeseries-Pattern-Mining/raw/master/images/images1.png)

### 1.2 t-SNE
SNE是通过仿射(affinitie)变换将数据点映射到概率分布上，主要包括两个步骤：<br>
> * SNE构建一个高维对象之间的概率分布，使得相似的对象有更高的概率被选择，而不相似的对象有较低的概率被选择。
> * SNE在低维空间里在构建这些点的概率分布，使得这两个概率分布之间尽可能的<img src="http://latex.codecogs.com/gif.latex?\frac{a}{b}" />相似。
##
<img src="http://latex.codecogs.com/gif.latex?\frac{a}{b}" />
