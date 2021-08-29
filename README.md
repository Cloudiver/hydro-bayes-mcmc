# 水文中的贝叶斯推断与MCMC

水文水资源不确定性问题中经常见到“贝叶斯”、“MCMC”这些概念，但是他们到底是什么意思却很少见到有文章能讲清楚。

本repo就是为了帮助解决这里面涉及的困惑，正好本人数学水平也很有限，所以希望以一种更直接逻辑的方式来简单解释其中的概念。

主要参考资料如下，其中最主要参考了第一个Courseara上的课程，绝大部分内容是翻译其中的课程课件。

- [Introduction to Computational Statistics for Data Scientists 专项课程](https://www.coursera.org/specializations/compstats)
- [Computational Statistics for Bayesian Inference with PyMC3¶](https://sjster.github.io/introduction_to_computational_statistics/docs/index.html)
- [Bayesian Methods for Hackers](https://github.com/CamDavidsonPilon/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers)
- [Bayesian inference problem, MCMC and variational inference](https://towardsdatascience.com/bayesian-inference-problem-mcmc-and-variational-inference-25a8aa9bce29)
- [Introduction to Bayesian statistics](https://www.youtube.com/watch?v=0F0QoMCSKJ4)
- [pymc-devs/pymc3](https://github.com/pymc-devs/pymc3)

为了便于接下来的描述，首先简单认识一些概念，有个印象即可。

## 我们要认识什么

### Inference

本repo下涉及的知识属于 Ieferential Statistics 范畴，它和 Descriptive Statistics 是不一样的。我们感兴趣的要了解的group中所有样本组成了一个population总体。Populations可以由像均值、方差这样能代表数据的parameters 参数 描述。通常我们是不能获取到总体中的所有数据的，必须从总体中去采样。用这些采样的样本来计算均值和方差得到的度量值是不称作参数的，而是称之为数据的statistics 统计。

描述性统计就是总结数据使得我们有一种定量的方式来理解数据。这能帮助我们定量地理解和可视化数据。我们能得出关于数据的性质的结论。描述性统计应用于总体，因此能提供数据的均值和方差的衡量。他们不能帮助我们预测我们没有分析的数据。

而推断性统计则可以让我们从样本向总体泛化。由于采样肯定不是数据的完美的表达，采样过程肯定会引入误差。所以计算的统计值是对真正的总体参数的一种估计。它允许我们 通过考虑抽样中的误差 来**根据抽样数据 形成总体分布**，从而**使得我们能对尚未看到或尚未抽样的数据进行预测**。

也就是说推断是**learning about what we do not observe based on what we observe**，它基于总体中的一些observed variables（offen effects）或总体中的样本来获取关于latent variables（often causes）的分布估计等。

### Inference v.s. Prediction

如果你多少了解过一点机器学习，肯定知道我们用机器学习的主要目的之一就是预测。预测是用一个模型在没见过的数据上去运行，它包括：

- 构建模型
- 根据一些指标，比如准确率，来选择最好的模型
- 在新数据上测试执行

而推断则是去建模一个分布，理解生成数据的“过程”！它典型地包括：

- 构建模型，通常会包含对数据生成过程的先验理解
- 使用拟合度衡量指标，比如残差分析等选择模型
- 通过生成描述数据或数据生成过程的分布来执行推断

## 主要内容

前言部分以0.x开头，主要是一些概率统计基础，如果这方面基础很好的可以不管。

第一部分开始进入和贝叶斯以及MCMC更直接相关的内容部分，不过仍然是基本概念。

接着第二部分开始进入正题，讨论Bayesian推断和MCMC。

第三部分开始进入实操部分，介绍PyMC3，并给一个相对完整的实例。

## 环境配置

运行该repo的话，请安装python环境：

```Shell
conda env create -f environment.yml
```

安装后，激活环境，并运行jupyter lab，就可以查看各文件内容了：

```Shell
conda activate HBM
jupyter lab
```

注：目前中文内容基本都成形了，英文的是还没整理的内容。
