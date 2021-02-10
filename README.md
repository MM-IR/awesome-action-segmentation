# awesome-action-segmentation
action segmentation上面的工作

首先时序上的关系among action segments有非常大的意义，尤其是当observation是limited的时候。（action被其他的objects occlude了或者happen outside a field of view）

# 任务的本质
就是首先temporally locating each action segment in the video and 分类对应的action category based on the segment。

## 1.Improving Action Segmentation via Graph Based Temporal Reasoning
### 1.Motivation
1.对于现有方法在background上进行segment的效果不是很好，尤其是有阻挡的时候。但是人们可以推断出它到底是什么。这是因为我们的大脑可以推理action之间的关系。但是事实上cnn的方法很难做的很好。
2.GCN的话就是可以operate on a flexible temporal receptive field，那么对于capture both short and long-range temporal relations就很有意义啦～

### 2.Novelty
1.我们提出一个网络模块叫做Graph-based Temporal Reasoning Module(GTRM) 可以建立在现有的action segmentation的基础上学习多个action segment的关系various time spans。

2.这里的关系使用的两个GCNs where each node represents an action segment。两个graph主要的区别就是不同的edge属性，1个解释的事boundary regression，一个则是分类任务。

我们的算是第一个显示建模关系among more than two relations for action recognition。

![](GTRM.png)

### 3.1 R-GCN
这里就是temporal proximity定义，middle frames的距离/整个video length～来表示edge。

### 3.2 c-GCN
这里就是推出对于action segment而言，用前后的action来推断当前的action的话，可以成功。
这里就是设置了一个threshold k。来定义i-j的距离是否符合k之内～


follow前人的工作咱们的使用two activation函数包括LN+ReLU。



