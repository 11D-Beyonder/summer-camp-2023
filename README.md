# 量子金融项目

## 任务布置

选取任意任务完成，若时间足够可进一步探索拓展内容，编程语言不限。最后需要提交任务报告（Markdown、LaTeX、Word文档皆可），并准备最后阶段的汇报。**可围绕任务设计实验，把一切所思所想和实验结果写进报告；即使时间关系没有完成任务，也建议把所有所做的工作写进报告**。

- 量子计算软件包：Qiskit、TensorCircuit
- 量子金融软件包：Qiskit Finance

### 任务一：基于 Python 的量子金融编程框架初探——期权定价应用

> 难点：阅读文档、熟悉`Qiskit`和`Qiskit Finance`
> 
> 难度：初级

Qiskit Finance是目前做的相对较为成熟的软件包。`example1`中展示了一个投资组合优化问题的简单例子，大致过程是将投资组合优化问题转化为一个二次规划问题，再用QAOA求解。

**你需要做：**

1. 仿照`example1`，用`Qiskit Finance`做一个欧式看涨期权定价的简单流程：将原问题转化为一个振幅估计问题，再用振幅估计的电路求解；
2. 测试不同的概率模型以及相同概率模型不同参数下的定价结果；
3. 清楚理解算法中各变量的含义，探究算法中参数对最终结果的影响，定性地或定量地。

参考资料：

- [Pricing European Call Options](https://qiskit.org/ecosystem/finance/tutorials/03_european_call_option_pricing.html)
- [Quantum computational finance: Monte Carlo pricing of financial derivatives](https://journals.aps.org/pra/abstract/10.1103/PhysRevA.98.022321)


### 任务二：量子金融算法的进阶优化——组合优化问题

> 难点：约束处理、参数更新
>
> 难度：中级

我们通过调整电路上的参数来使得测量得到的结果最好。`example2`中展示了一个使用参数化电路求函数最值的简单例子，虽然利用参数化电路解决`example2`中的问题显得多此一举，但有助于同学们理解参数化电路的思想。参数化量子电路是变分量子算法（VQE、QAOA等）的重要组成部分，在面对复杂的组合优化问题时能体现量子优势。

投资组合优化问题可表示为一个最优化问题。

$$
\begin{aligned}
\min_{x \in \{0, 1\}^n}\quad&  q x^T \Sigma x - \mu^T x\\
\text{s.t. }\quad& 1^T x = B
\end{aligned}
$$

**你需要做：**

1. 假设上式约束不存在，求最小值；
2. 上式约束存在，求最小值。

若自行构建电路并调整参数，可尝试：

- 梯度下降
- 群体智能
- 常用的优化器（如scipy.optimize）

也可直接利用常用的量子变分算法QAOA、VQE等。

参考资料：

- [IBM® Decision Optimization CPLEX® Modeling for Python](http://ibmdecisionoptimization.github.io/docplex-doc/)
- [GradientDescent](https://qiskit.org/documentation/stubs/qiskit.algorithms.optimizers.GradientDescent.html)
- [Qiskit Gradient Framework](https://qiskit.org/documentation/tutorials/operators/02_gradients_framework.html)
- [梯度计算效率比较](https://tensorcircuit.readthedocs.io/zh/stable/tutorials/gradient_benchmark_cn.html)
- [梯度和变分优化](https://tensorcircuit.readthedocs.io/zh/stable/tutorials/gradient_benchmark_cn.html)

### 拓展

> 难点：论文阅读、算法细节
>
> 难度：高级

#### 任务一拓展

期权的价格分布一般通过训练量子生成对抗网络（QGAN）制备，请实现这一过程。

参考资料：

- [Quantum Generative Adversarial Networks for learning and loading random distributions](https://www.nature.com/articles/s41534-019-0223-2)
- [Quantum Generative Adversarial Networks](https://learn.qiskit.org/course/machine-learning/quantum-generative-adversarial-networks)

#### 任务二拓展

在任务二中，我们只能用0或1确定买或不买，该怎么样确定每只股票购买多少份额呢？

参考资料：

- [Quantum computational finance: quantum algorithm for portfolio optimization](https://arxiv.org/abs/1811.03975)
- [Solving linear systems of equations using HHL and its Qiskit implementation](https://learn.qiskit.org/course/ch-applications/solving-linear-systems-of-equations-using-hhl-and-its-qiskit-implementation)

## 环境配置

给出的例程主要基于Qiskit实现，这里以在VSCode中配置Python编程环境为例。

建议使用Python的版本为3.10。

```shell
conda install -n "summer-camp-qf-2023" python=3.10
conda activate summer-camp-qf-2023
```

安装`Qiskit Finance`。

```shell
pip install "qiskit[finance]"
```

安装必要的画图工具。

```shell
pip install matplotlib
pip install pylatexenc
```

安装必要的优化算法包。

```shell
pip install scikit-opt
```

安装可用于`Jupyter`的`IPython`内核，即可在`VSCode`中运行`Jupyter Notebook`。

```shell
pip install ipykernel
```




