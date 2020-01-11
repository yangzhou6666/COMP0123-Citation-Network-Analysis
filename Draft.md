
    Analysis of Scientific Collaboration Trends in Papers with Fewer Authors

# To-Do

* [x] Introduction Part
* [x] Related Work
* [ ] 我们的网络并不是增长的关系，而是合作模式的变化

# Abstract

在这篇报告中，我们主要分析了Scientific Collaboration Trends in Papers with Fewer Authors. 和其他工作不同，我们并不探究同一个学术网络如何随着时间演化,ershi 独立分析每一年发表的文章。这更能体现学者每一年合作行为的变化趋势。另外，我们并没有分析这个领域的所有论文数据，而是根据论文的合作者人数对数据进行分组。针对这个特定子集的研究的确是学界所暂时缺少的，以及我们想验证学术合作网络中的一些常见性质，如Power law和Rich-Club是否与论文合作者的数量有关。

我们统计了1950年至2017年的计算机相关论文中，在每一年，不同作者数量的论文所占的比例。我们发现了非常明显的结论：论文的合作者数量一直在增加，且这个趋势将持续下去。

为了更细致地探究合作模式的变化，我们计算了共120个学术合作网络的Degree distribution并得出推论：即使只考虑papers with fewer authors,学者也在倾向于和更多的人合作。

通过计算与分析Rich club coefficient，我们并没有得出低度节点之间合作模式的变化，但是可以得出如下推论：Rich node之间的合作正在变得更加频繁。

# Introduction

互联网在联系世界的同时，也连接起了学者们，使其更方便地展开合作。学者可以使用很多工具来方便地进行学术合作，比如使用Overleaf共同地撰写论文，使用Github共同的撰写代码。
而且现在的学术研究很多是跨学科的，需要不同领域的人进行合作。现在有些任务的工作量很大，需要多个人共同参与才能完成。

另一方面，现在有太多的博士生，每个人都想申请到好的职位。而作为衡量科学家能力表现的论文数量，通常可以通过学术合作来以更小的成本增加。这些学者会积极参与到不同组的工作中，希望自己的简历能更加出色。而且合作通常是双向的，即你参与我的项目，我也可能要参加你的其他项目。在不考虑其他因素的情况下，这是一种互惠关系，学者们都会倾向于这么做。年轻学者希望与有名望的人合作，借此来提升自己的名声；已经成功的人也可以因此收获更多的研究成果。如果将发表学术论文看作一个市场，似乎在当前的时代倾向于合作是一个占优策略。而且学者的成功并不是只由可以衡量的论文数量与引用量决定，学者本身所出的网络也同样影响了学者是否成功。因而从这个角度来说，学者现在也更倾向于合作。这些因素都促成了现在学术合作的快速增长。

本报告的研究对象就是学者之间的合作增长模式。大量的研究者将学者的合作关系视为Simple Graph。图中的点表示学者，如果两个学者共同发表过一篇论文，则他们之间会有一条边。在这个问题上最经典的论文是xxx，尝试去分析几个领域学者的合作模式，包括xxxxxx指标。作者发现了一些有趣的性质。他们划分通常是以领域进行划分，如不同的学科，然后发现了不同学科领域间的共性。这些性质在现在的学者合作网络中也能被验证。

但是这些和学术合作网络相关的研究通常没有刻意关注有着不同作者数量论文的合作关系。比如当我们只关注作者数量少于4的论文集合时，合作网络是否还存在power-law现象？这种研究Analysis of Scientific Collaboration Trends in Papers with Fewer Authors的想法主要源于我们这样的思考：既然学术合作在增加，比如有有更多合作者数量的论文比例在上升，那么对应的那么fewer authors的论文肯定也发生了一些变化。我们可以通过简单的数据分析就知道，少合作者论文所占总论文的比例在降低。但是一些合作模式上的变化，需要针对这些论文组成和合作网络进行分析。而这也正是本报告的研究重点。


我们想关注少合作者论文的另一个原因是，现在出现了很多合作人数超高的论文，有些合作人数甚至超过了50。考虑一篇有50个合作者的论文，当我们将其放到合作网络中时，网络中就会出现50个度至少为49的节点。即使有其中的一个作者是一个只发表过一篇论文的学生，他在网络中也将是一个度为49，clustering coefficiency为1的节点，看起来就像一个超级学术明星。这些现象都是我们想尽力避免的。

在报告中，我们主要探究了如下的研究问题：
1. 拥有不同作者数量的论文，几十年来占当年论文数量的比例如何变化？
2. 对于合作者数量少于6的论文，他们所组成的合作网络中各项指标(如Power Law)如何变化？

* [ ] 需要补全解释

本报告的结构如下：第二节我们主要探讨了在与这个问题相关的研究工作。第三节我们介绍了如何对我们的数据进行预处理。第四节我们将展示计算的结果并分析合作模式的变化。最后一节我们总结这篇报告。

# Related Work
在这一节中，我们主要介绍相关的研究工作。主要分为三个部分，学术合作网络中通常分析的属性，研究者将其应用在哪些领域，以及网络如何演化。

Newman first studied the structure of scientific collaboration networks in different research fields. He showed that these collaboration networks form “small worlds” [1]. In this paper, many indicators were investigated, including: number of authors, mean papers per author, number of collaborators (node degree), the giant component and average degrees of separation. Then Newman analyzed more detailed statistical properties of scientific co-authorship networks [2], including size of giant component, closeness, betweenness and clustering coefficient.

Many papers were inspired by Newman’s initial work. People started to analyze the co-authorship in different domains. Hou et al. studied the structure of scientific collaboration networks in Scientometrics [3]. Tomassini et al. paid attention to genetic programming collaboration network [4]. Some researchers used countries to separate the network, e.g. collaboration network in Turkey [5].

Some researchers also try to identify how the scientific collaboration networks evolve. Barabsi et al. [6] are the first to infer the dynamic and the structural mechanisms that govern the evolution and topology of this complex system. Tomassini [7] studied the genetic programming network and found that degree distribution tends to stabilize toward an exponentially truncated power-law. Huang et al analyze different fields in computer science and found that major observations are that the database community is the best connected while the AI community is the most assortative. Lara-Cabrera et at [8] chose an interdisciplinary domain in computer science as research objects and also observed sub-linear preferential attachment for new nodes. 



# Data and Methodology

## Data Preparation

在本小节中我们将介绍如何准备数据。

我们的原始数据是Citation Network Dataset [xx]。这些饮用数据是从DBLP, ACM, MAG (Microsoft Academic Graph)和其他地方提取而来的。我们使用的数据集包含了1890年到2018年发表的超过4百万篇计算机领域的论文。每一篇论文和作者都会有一个ID来唯一标识他们。这个数据集还提供了非常丰富的metadata，比如论文标题、会议名称、出版商等，但是我们不需要这些数据。我们只需要一篇论文的发表年份，和它的作者ID。

我们构建网络的假设是，如果如果4个作者合著了一篇论文，那么我们就认为这4个作者相互认识，他们之间是一个完全连通图。我们不排除有些论文有多个版本的情况，但是这对我们的分析并没有太大的影响。因为在我们的网络中，学者之间的合作关系是二元的。即使同一篇论文因为一些原因被收录了两次，也没有任何影响。

我们的目标是是，从这些原始数据中提取出，在不同的年份，那一年发表的所有少作者论文组成的合作网络。为了使我们的研究更加的可靠，我们构建了三组数据：合作者数量少于4的论文集合，合作者数量少于5的论文集合，合作者数量少于6的论文集合。具体的提取流程如下：

* [ ] 画一张图表示这个过程

1. 将原数据(.txt file)存为一个csv file，每一行表示一篇论文，数据包括论文ID，年份，以及所有的合作者ID
2. 将此csv文件中的论文，按照年份分别存到不同的csv文件中
3. 对于每一个年份的文件，提取数据并创建三个csv file，分别是：
    1. 作者数量少于4的论文集合
    2. 作者数量少于5的论文集合
    3. 作者数量少于6的论文集合
4. 在上一步中我们会得到3*year_range个csv文件，根据这些文件创建网络合作网络，存储在csv files中，每一行表示一个合作关系
5. 对第四步中得到的csv文件进行数据去重，来缩减文件的大小。

* [ ] Statistics of Data

Although original data source provides paper data published between 1890 and 2018, but we only choose papers from 1975 to 2017 as our research object.

## Analysis Methodology

在本小节我们简要地介绍我们如何分析这些数据，以及相关的工具和第三方库。

我们使用Python的第三方库networkx [xx]来计算合作网络的相关property。networkx提供了丰富的API来计算degree distribution, rich club coefficient, xxx等属性。network还提供了简单的网络可视化功能，但是并不能方便地展示这些属性。因此我们写了python脚本使用mlxxx库来进行数据可视化。

在复杂网络领域另一个常用的工具是Gephi [xx]. Gephi是一个非常强大的工具，也有着易于使用的界面。用于不但只需要通过a few clicks来计算属性，他还能很好地plot这些数据。但是我们的研究对象接近120个网络，Gephi并没有提供合适的比较网络的功能。因此我们还是选择了自己撰写脚本处理数据的方式。

## Potential Ethical Issues

毫无疑问本研究的数据是来自Human，此研究是典型的secondary data analysis，我们无法对此项研究做到informed consent。。。巴拉巴拉参照一下另一份report。

# Analysis of Trends in Network

## RQ1. 合作在变的更加频繁吗？

我们首先要回答的问题就是，学术合作正在增加吗？我们统计出，不同年份，不同合作者数量的论文的数量及其所占当年总论文数量的比例，将他们画在了一张Fig 2里。

![WX20200109-120056](https://i.imgur.com/ghD6KwW.png)

我们可以从这张图断言：从1950年以来，计算机领域的学术合作论文一直在增加。从图中可以看出，在1950年左右，没有合作者的论文比例非常的高——接近90%。但是直到2017年，独立作者的论文比例几乎是匀速下降，到了几乎只有7%。与之对应的则是多合作者论文的持续增长。两合作者的论文一直在增长，直到1995年左右达到了顶峰(35%)，然后也开始下降。尽管到达顶峰的年份不同，三合作者的论文的比例变化表现出了相似的模式：增长到2007年左右，然后开始下降。而且从图中我们可以看到，四合作者的论文比例也在2017年达到了顶峰(斜率为0)，很有可能在之后四合作者论文的比例也会开始下降。

这些论文比例的下降也意味着更多作者数量论文比例的上升。如图所示，合作者数量为5，6，7的论文比例正在加速增加(曲线的slope在变大)。

尽管我们不能预测增长的尽头，但是这张图非常清楚地说明了计算机领域的学术合作一直在增加，而且会持续地增加。

* [x] 画一张好看的图
* [x] 描述这张图


## RQ2. 

尽管从宏观的数据上看，学术合作一直在增长。但是我们从看看学术合作网络如何变化。我们主要关注几个参数：

* Degree Distribution
* Clustering Coefficient
* Rich-Club
* Betweenness
* Closeness Centrality

### Degree Distribution

* [x] 计算Degree Distribution
* [x] 在对数坐标中画图
* [x] 画三个图，根据合作者数量进行划分。
* [x] 回归曲线
* [x] 对比斜率的变化
* [x] 斜率的变化到底代表了什么？
* [x] 程序有Bug 修改

我们想知道这些网络的Degree Distribution是怎么样的。我们计算了从1975到2017年，不同论文(<= 3, 4, 5)所组成的合作网络的degree distribution。为了便于清洗地可视化，我们在下面的图中只展示了其中6年的数据。对于任何种类论文的任何一年，我们都观察到了明显power-law现象。

我们使用一元线性回归拟合了这些数据，观测到了一个有趣的现象：尽管存在波动，但是这些曲线的slope总体上随着年份的增加在减少。而且如果对比不同种类论文的slope，总能观测到合作者数量5>4>3. 而且结合上面的图看，合作论文所占总论文比例的变化和slope的变化并无显著的关系。我们认为，slope变的更平缓其实说明了学者一致在更倾向于和更多的人合作。我们举一个简单的例子来阐明。

现在只分析作者数量小于等于3的论文。假如说研究者们都只和固定的人合作，无论他们发表多少篇论文，这个会充满了互相不联通的图，每个点的度通常是2或三。如果我们去拟合，就会得到一条非常陡峭的直线。

如果他们开始和不同的人合作，那么就会有更多的人有更高的度；换言之直线会变的更加平缓。

因而我们可以指出合作模式的一个变化：学者在倾向于和更多不同的人合作。当然我们可以plot出所有论文的变化趋势，但是我们觉得我们的这张图更能体现上面的结论。因为在考虑所有论文时，多合作者论文的增加肯定会影响度的分布；尽管我们并未观测到论文比例的变化和slope的变化有相关性，但是这张图更能体现上述的结论。而且这并不是总的趋势，而是每一年的变化。

![Unknown](https://i.imgur.com/wkePMXK.png)


![Unknown-4](https://i.imgur.com/DmpGaSY.png)


### Average Clustering Coefficient

我们还需要计算这些网络的average clustering coefficient。clustering coefficient的定义是xxxx。是一个点的邻接点之间相互连接的程度。例如生活社交网络中，你的朋友之间相互认识的程度。有证据表明，在各类反映真实世界的网络结构，特别是社交网络结构中，各个结点之间倾向于形成密度相对较高的网群。而平均聚集系数的定义是xxx(公式)。

从图中我们可以明显地看出，这些网络的平均聚集系数都在不断地增加。


### Rich-Club Coefficient

我们研究学术合作网络中的富人俱乐部现象是来分析那些学术领域的超级明星之间是如何合作的。

Rich-club phenomenon is first discovered by Zhou [xxx](The rich-club phenomenon in the Internet topology) in the Internet topology. The rich nodes are a small number of nodes with large numbers of links and are very well connected to each other. In the original paper, the rich-club coefficient was defined as:

$\phi(r) = \frac{2E(r)}{r(r-1)}$

In this equation, $r$ is a node's position in a sorted list of decreasing degrees. Modified definition replace rank $r$ with node degree $k$. For each degree $k$, the rich-club coefficient is the ratio of the number of actual to the number of potential edges for nodes with degree greater than $k$ [xxx](The rich-club phenomenon across complex network hierarchies).

$\phi(k) = \frac{2E(k)}{k(k-1)}$

In our report we use the latter one mainly because the networkx library also uses this definition. 

![](https://i.imgur.com/LNjhmOa.jpg)

我们计算了从1975年到2017年以来，每一年中不同种类的论文构成的学术合作网络的Rich-club系数，并将他们在Figure 4中展示出来。为了清晰的可视化，我们每间隔四年展示一个网络。从这些图中，我们可以观测到在由任何作者数量组成的论文集合中，富人俱乐部现象都存在。而且他们展示出了一种相似的变化模式：

1. 当节点的度比较少时，拥有同样度的节点，随着年份的增加，富人俱乐部系数却下降了。
2. 拥有相同度的节点，随着年份的增加，每四年之间富人俱乐部系数的差在减少
3. 2008年以来的这十年，富人俱乐部系数曲线已经非常接近

这样的变化是可以解释的。我们认为第一点主要是由于论文数量与作者数量的上升导致的。因为这意味着度大于$k$的节点数量大大增加了。这个公式$\phi(k) = \frac{2E(k)}{k(k-1)}$这个公式中分母的增长速度要远快于分子。因此拥有同样度的节点，随着年份的增加，富人俱乐部系数却下降了。而且这个当$k$固定时，相邻年份间这个公式的差值会随着年份增加而越来越小。

但是有趣的是，对于度$k$更高的节点，甚至出现了相反的情况。这正是说明了公式$\phi(k) = \frac{2E(k)}{k(k-1)}$中分子的增速更快了。即富人之间的连接正在快速的增加。从我们的简单分析中并不能得出低度节点之间合作模式的变化，但是可以得出如下推论：

富人之间的合作正在变得更加频繁。

![Rich-Club Coefficient Paper -Authors <= 5-](https://i.imgur.com/p4IYQcy.png)

![Rich-Club Coefficient Paper -Authors <= 3-](https://i.imgur.com/bA1uUOS.png)

![Rich-Club Coefficient Paper -Authors <= 4-](https://i.imgur.com/iCf149i.png)

## Data Visualisation


# Threats to Vadility

文章缺少坚实的理论基础

# Conclusion and Discussion

在这篇报告中，我们主要分析了Scientific Collaboration Trends in Papers with Fewer Authors. 和其他工作不同，我们并不探究同一个学术网络如何随着时间演化,ershi 独立分析每一年发表的文章。这更能体现学者每一年合作行为的变化趋势。另外，我们并没有分析这个领域的所有论文数据，而是根据论文的合作者人数对数据进行分组。针对这个特定子集的研究的确是学界所暂时缺少的，以及我们想验证学术合作网络中的一些常见性质，如Power law和Rich-Club是否与论文合作者的数量有关。

我们统计了1950年至2017年的计算机相关论文中，在每一年，不同作者数量的论文所占的比例。我们发现了非常明显的结论：论文的合作者数量一直在增加，且这个趋势将持续下去。

为了更细致地探究合作模式的变化，我们计算了共120个学术合作网络的Degree distribution并得出推论：即使只考虑papers with fewer authors,学者也在倾向于和更多的人合作。

通过计算与分析Rich club coefficient，我们并没有得出低度节点之间合作模式的变化，但是可以得出如下推论：Rich node之间的合作正在变得更加频繁。