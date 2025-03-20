## AdaBoost

### 加法模型（Additive Model）和指数损失函数（Exponential Loss）

$f(x)=\sum\limits_{m=1}^{M} \alpha_m G_m(x)$，其中$G_m(x)$为基学习器，$\alpha_m$​为系数。

优化的第M步最小化目标是一个指定的损失函数$L(y,f(x))$​，即：

$L(y,f(x))=e^{-y(f(x))}$

$\mathop{\min}\limits_{(\alpha_m,G_m)} \sum\limits^N_{i=1}L(y_i,\sum\limits^M_{m=1}\alpha_m G_m(x_i))$​

这是一个复杂的全局优化问题

$f_m(x)=f_{m-1}(x)+\alpha_mG_m(x)$

### 算法原理

>输入：训练数据集T：${(x_1, y_1), (x_2, y_2), ..., (x_N, y_N), y\in\{-1+1\}}$，基学习器$G_m(x)$​​，训练轮数M
>
>1. 初始化权值分布：$\omega_i^{(1)}=\frac 1N, i=1,2,3,...,N$
>
>2. for m=1 to M:
>
>(a) 使用带有权重分布的训练集学习得到基学习器$G_m(x)$:
>
>$G_m(x)=\mathop{\arg\min}\limits_{G(x)} \sum\limits_{i=1}^{N} \omega_i^{(m)}[y_i \neq G(x_i)]$​
>
>让误分类样本的权重之和最小
>
>(b) 计算$G_m(x)$​在训练集上的误差率
>
>$$
>\epsilon_m = \frac{\sum\limits_{i=1}^{N} \omega_i^{(m)} [y_i \neq G(x_i)]}{\sum\limits_{i=1}^{N}\omega_i^{(m)}}
>$$
>误差率为误分类的权重之和与总体权重之和的比值
>
>(c) 计算$G_m(x)$​的系数：
>$$
>\alpha_m = \frac{1}{2}ln\frac{\sum_{y_i=k_m(x_i)}\omega_i^{(m)}}{\sum_{y_i \neq k_m(x_i)}\omega_i^{(m)}}
>$$
>
>$$
>\alpha_m = \frac{1}{2}ln\frac{1-\epsilon_m}{\epsilon_m}
>$$
>
>$\epsilon_m$越小，最后得到的$\alpha_m$就越大，表明在最后的线性组合中，准确率越高的基学习会被赋予较大的系数
>
>(d) 更新样本权重分布：
>$$
>\omega_i^{(m+1)}=\frac{\omega_i^{(m)}e^{-y_i\alpha_m G_m(x_i)}}{Z^{(m)}},   i=1,2,3,...,N
>$$
>其中$Z^{(m)}$是规范化因子，$Z^{(m)} = \sum\limits_{i=1}^{N}\omega^{(m)}_ie^{-y_i\alpha_mG_m(x_i)}$，以确保所有的$\omega_i^{m+1}$构成一个分布。
>
>注意 $Z$​ 是一个常数，其目的是对权重进行归一化，使得它们加起来等于1
>
>选择恰当的权重：$\sum_{positive}=\frac{1}{2}and\sum_{negative}=\frac{1}{2}$
>
>
>
>3. 输出最终模型：$G{(x)}=sign[\sum\limits_{m=1}^M \alpha_m G_m(x)]$



参考：

[集成学习之Boosting —— AdaBoost原理 - 知乎](https://zhuanlan.zhihu.com/p/37358517)

[机器学习中最最好用的提升方法：Boosting 与 AdaBoost - 知乎](https://zhuanlan.zhihu.com/p/57689719)