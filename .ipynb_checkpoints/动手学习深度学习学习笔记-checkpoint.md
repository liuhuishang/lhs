# 遇到的问题和解决办法

---

1.由于我之前已经安装anaconda并且安装完python和pytorch，但是在此处直接运行pip install d2l==0.17.6却遇到了问题。原因是我的python版本过高，但是又因为conda中的python无法降级，此外更新numpy也行不通，所以在此我又重新按照手册的方法继续：使用下面的命令创建一个新的环境：
conda create --name d2l python=3.9 ，rd
现在激活 d2l境：

conda activa。再接着把pytorch进行安装，我的电脑的安装代码为：pip install torch==2.6.0 torchvision==0.21.0 torchaudio==2.6.0 --index-url https://download.pytorch.org/whl/cu126。

# 1. d2l

---
配置好相应的pytorch和gpu之后，在anaconda中的d2l的环境里cd到李沐的深度学习的这个文件夹下然后打开jupyter notebook然后可以进行在jupyter notebook中进行运行代码等便于学习。

# 2.第二章：预备知识

---

1.数据操作：（1）张量，如x.shape，查看张量个数x.numel() （2）运算符：包括加减乘除等等 （3）广播机制：如a = torch.arange(3).reshape((3, 1))，b = torch.arange(2).reshape((1, 2)) （4）索引和切片：选定范围 （5）节省内存。
 
2.数据预处理：（1）读取数据：以csv文件为例，导入pandas包并调用read_csv函数。（2）处理缺失值：可以使用 dummy_na=True来解决。 （3）转换张量格式。

3.线性代数：（1）标量：x = torch.tensor(3.0)此时x为一个表量可以进行相应的算术运算。 （2）向量：x = torch.arange(4)即为一个向量。 （3）长度：len(x)，维度，形状。 （4）形状：A = torch.arange(20).reshape(5, 4) ，此时A为一个矩阵。 （5）张量的运算：B = A.clone()  # 通过分配新内存，将A的一个副本分配给B，A * B为矩阵相乘的乘积， （6）降维： A_sum_axis0 = A.sum(axis=0) A_sum_axis0, A_sum_axis0.shape，其中axis即时需要降的维度。

4.微积分

5.自动微分：（1）自动计算导数：x.requires_grad_(True)  # 等价于x=torch.arange(4.0,requires_grad=True) x.grad。 （2）非标量变量反向传播：当y不是标量时，向量y关于向量x的导数的最自然解释是一个矩阵。 对于高阶和高维的y和x，求导的结果可以是一个高阶张量。（3）分离计算：将某些计算移动到记录的计算图之外。

6.概率：（1）基本概率论：取样和随机变量 （2）处理多个随机变量：联合概率，条件概率，贝叶斯定理（3）期望和方差

7.查阅文档：（1）查找模块中的所有函数和类：import torch print(dir(torch.distributions))  （2）查找特定函数和类的用法：help(torch.ones) 

# 3.第三章：线性神经网络

---

1.线性回归：（1）线性模型：线性假设是指目标可以表示为特征的加权和，机器学习中通常使用的是高维数据集，建模时采用线性代数表示法会比较方便。（2）损失函数：拟合程度的度量，量化目标的实际值与预测值之间的差距。（3）解析解：线性回归的解可以用一个公式简单地表达出来， 这类解叫作解析解。（4）随机梯度下降：优化所有深度学习模型。 它通过不断地在损失函数递减的方向上更新参数来降低误差。最简单的用法是计算损失函数（数据集中所有样本的损失均值） 关于模型参数的导数（可以称为梯度）。（5）矢量化加速：不适应for循环而是矢量化代码通常会带来数量级的加速。

2.softmax回归：（1）分类问题：进行标签分类（2）网络架构：单层神经网络。（3）softmax运算：优化参数以最大化观测数据的概率。 （4）小批量样本的矢量化：对小批量样本的数据执行矢量计算。 （5）交叉熵损失。

3.图像分类数据集：（1）读取数据集：mnist_train = torchvision.datasets.FashionMNIST(root="../data",train=True, transform=trans, download=True)，mnist_test = torchvision.datasets.FashionMNIST( root="../data", train=False, transform=trans, download=True)

# 4.第四章多层感知机

---

1.多层感知机：（1）隐藏层：在输入层和输出层之间，处理更普遍的函数关系模型。 （2）激活函数：通过计算加权和并加上偏置来确定神经元是否应该被激活。如relu函数，sigmoid函数，tanh函数

2.模型选择、欠拟合和过拟合：（1)训练误差和泛化误差:训练误差（training error）是指， 模型在训练数据集上计算得到的误差。 泛化误差（generalization error）是指， 模型应用在同样从原始样本的分布中抽取的无限多数据样本时，模型误差的期望。(2)模型选择:评估几个候选模型后选择最终的模型。 (3)验证集和测试集 （4）欠拟合还是过拟合？由于我们的训练和验证误差之间的泛化误差很小， 我们有理由相信可以用一个更复杂的模型降低训练误差。 这种现象被称为欠拟合（underfitting）。当我们的训练误差明显低于验证误差时要小心， 这表明严重的过拟合（overfitting）

3.权重衰减：主要是使用正则化的方式来进行权重衰减（1）暂退法：也称dropout即是正则化。

4.前向传播、反向传播和计算图：（1）前向传播（forward propagation或forward pass） 指的是：按顺序（从输入层到输出层）计算和存储神经网络中每层的结果。（2）反向传播（backward propagation或backpropagation）指的是计算神经网络参数梯度的方法。 简言之，该方法根据微积分中的链式规则，按相反的顺序从输出层到输入层遍历网络。

5.数值稳定性和模型初始化：（1）梯度消失和梯度爆炸：不稳定的梯度会导致梯度消失或者梯度爆炸（误差变得非常大）。要么完全激活要么完全不激活（就像生物神经元）是导致梯度消失问题的一个常见的原因。当sigmoid函数的输入很大或是很小时，它的梯度都会消失。

6.环境和分布偏移：模型表现得非常出色。 但是当数据分布突然改变时，模型在部署中会出现灾难性的失败。