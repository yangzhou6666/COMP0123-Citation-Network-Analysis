# Title:  Analysis of Scientific Collaboration Trends in Papers with Fewer Authors

# Introduction

It is a common sense that the scientific collaboration has been increasing. There are many reasons to such increase. While the Internet connects the world, it also connects scholars and makes it more convenient for them to collaborate with each other. More and more tools are available for scholars, e.g. Overleaf for writing drafts and Github for contributing to codebase. Besides, many scientific research nowadays is interdisciplinary and requires researchers from different domains to collaborate.

On the other side, the number of researchers (e.g. PhDs) is increasing, and many of them want to apply for competitive positions. As an optional measurement for the performance of scientists, the number of papers published can increase via scientific collaboration at a relatively low cost. Scholars often tend to participate in work of different groups to make their resume more outstanding. This kind of collaboration is also double-way: you join my papers and I should join your other work. This is a reciprocal relationship if not consider other factors. The young scholars hope to collaborate with famous scientist to boost their reputation. The scientist of fame can also produce more research achievements. We do not judge whether such motivation is fair, but if we view scientific collaboration network as a market, tending to collaboration more seems to be a dominant strategy. Besides, the success of scholars is not only decided by the number of papers and citations. The networks that scholars are in also influence whether scholars are successful or not. These factors all contributes to the fast increasing in scientific collaboration. 

The main research object in this report is the patterns of trends in scientific collaboration. Many researchers view the collaboration relationship as Simple Graph. Nodes in the graph represent scholars. If two scholars co-published a paper, there is an edge between corresponding nodes. With regarding to with problem, the most classic paper is xxx by *Newman*. *Newman* analysed the collaboration patterns of scholars from different domains and studied some measurements, including: degree distribution, balabalab,  ... and .... He find the common pattern existing in different science fields and such patterns also exist in current collaboration networks [xx].

However, these research work usually did not focus on the co-authorship of papers with different number of authors. A sample questions could be: does the power law phenomena still exists if we only consider the papers with authors less than 4? The idea to analyse collaboration trends in papers with fewer authors originates in our thoughts that since academic cooperation is increasing, for example, the proportion of papers with more collaborators is rising, the papers fewer collaborators with must have also changed. We can know through simple data analysis that the proportion of papers with fewer collaborators has been decreasing. But knowledge about the changes in collaboration patterns requires in-depth analysis of the collaborative network of these papers. This is exactly the research focus of this report.

Another reason we want to focus on fewer collaborator papers is that there are many papers with a very high number of collaborators. Consider a paper with 50 collaborators. When we put it into a cooperative network, there will be 50 nodes with a degree of at least 49 in the network. Even if one of the authors is a student who has published only one paper, he will be a node with a degree of 49 and a clustering coefficient of 1 in the network, which looks like a super academic star. These phenomena are all we try to avoid.

In this report, we mainly investigate in the following research questions:
1. How has the proportion of papers with different numbers of authors changed over these decades?
2. For papers with less than 6 collaborators, how do the indicators (such as Power Law) in the collaboration network change?


The structure of this report is as follows: In Section 2, we mainly discuss the research work related to this question. In Section 3 we introduce how to extract and pre-process the data. In the fourth section, we show the results of the calculations and analyze the changes in the cooperation pattern. We conclude this report in the final section.

# Related Work

In this section, we mainly introduce the research papers related to our topic, including common statistical properties of scientific collaboration networks, domains that are analyzed and work on evolution of collaboration network.

Newman first studied the structure of scientific collaboration networks in different research fields. He showed that these collaboration networks form “small worlds” [1]. In this paper, many indicators were investigated, including: number of authors, mean papers per author, number of collaborators (node degree), the giant component and average degrees of separation. Then Newman analyzed more detailed statistical properties of scientific co-authorship networks [2], including size of giant component, closeness, betweenness and clustering coefficient.

Many papers were inspired by Newman’s initial work. People started to analyze the co-authorship in different domains. Hou et al. studied the structure of scientific collaboration networks in Scientometrics [3]. Tomassini et al. paid attention to genetic programming collaboration network [4]. Some researchers used countries to separate the network, e.g. collaboration network in Turkey [5].

Some researchers also try to identify how the scientific collaboration networks evolve. Barabsi et al. [6] are the first to infer the dynamic and the structural mechanisms that govern the evolution and topology of this complex system. Tomassini [7] studied the genetic programming network and found that degree distribution tends to stabilize toward an exponentially truncated power-law. Huang et al analyze different fields in computer science and found that major observations are that the database community is the best connected while the AI community is the most assortative. Lara-Cabrera et at [8] chose an interdisciplinary domain in computer science as research objects and also observed sub-linear preferential attachment for new nodes. 



# Data and Methodology

## Data Preparation

In this section, we are going to introduce how we extract and pre-process our data.

The original data we use is Citation Network Dataset [xx].The citation data is extracted from DBLP, ACM, MAG (Microsoft Academic Graph), and other sources. The dataset contains more than 4 million papers published within 1890 and 2018. Every paper and author will have an ID to uniquely identify them. This dataset also provides rich metadata, such as the title of the paper, the name of the conference, the publisher, etc., but we do not need these irrelevant data. All we need is the publication year and its author ID.

Our hypothesis for constructing a network is that if four authors co-author a paper, then we assume that the four authors know each other and they form a fully connected graph. We do not rule out some papers with multiple versions, but this has not affected our analysis much. Because in our network, the cooperative relationship between scholars is dual. Even if the same paper was included twice for some reason, it had no effect.

Our goal is to extract from the raw data collaboration networks formed by all papers with fewer authors published in a particular year. In order to make our research more reliable, we constructed three sets of data: a collection of papers with less than 4 collaborators, a collection of papers with fewer than 5 collaborators, and a collection of papers with fewer than 6 collaborators. The specific extraction process is as follows:

![process graph](https://i.imgur.com/2cCy01S.jpg)


1. Convert original data (.txt file) to a csv file. Each row represents a paper, including paperID, publication year, and IDs of all authors.
2. Separate the csv file in Step 1 to multiple csv files according to publication year.
3. For the file of each year, extract three csv file:
    1. Set of papers with less than 4 authors
    2. Set of papers with less than 5 authors
    3. Set of papers with less than 6 authors
4. In the last step, we get $3 * year\_range$ csv files. We convert these files to network format.


Although original data source provides paper data published between 1890 and 2018, but we only choose papers from 1975 to 2017 as our research object. Since many old papers might not be contained in the dataset and affect the data analysis results.

## Methodology

In this section we briefly describe how we analyze this data, as well as related tools and third-party libraries.

We use Python's third-party library networkx [xx] to calculate the relevant properties in scientific collaboration networks. Networkx provides rich APIs to calculate network attributes such as degree distribution, rich club coefficient, betweenness centrality and more.
It also provides simple network visualization functions, but it is not convenient to plot the properties, so we wrote Python scripts to visualize data with the matplotlib library.

Another commonly used tool in the field of complex networks is Gephi [xx]. Gephi is a very powerful tool with an easy-to-use interface. Not only can users calculate attributes with just a few clicks, Gephi can also plot this data well. But our research object is 120 networks. Gephi does not provide a suitable function for comparing attributes in different networks, so we chose to write our own script to process the data.

# Analysis of Trends in Network

## Changes in the Proportion of Papers with Different Numbers of Authors

The first question we have to answer is, is academic cooperation increasing? 

We counted the number of papers in different years and the number of collaborators and their proportion in the total number of papers in that year.

We counted the proportion of papers with different number of authors between 1950 and 2017 and plot the data in Figure 2. The x-axis represents year, and the y-axis represent the proportion. Data of papers with different number of authors is displayed in different colors. 

![WX20200109-120056](https://i.imgur.com/ghD6KwW.png)

We can assert from this picture that academic cooperative papers in the computer field have been increasing since 1950. It can be seen from the figure that around 1950, the proportion of papers without collaborators was very high(close to 90%). But until 2017, the proportion of independent authors' papers dropped almost uniformly, to almost 7%.

Corresponding to this is the continuous growth of multi-collaborative papers.The papers of the dual collaborators continued to grow until they peaked (35%) around 1995 and then began to decline. Although the years to the peak were different, the percentage change in the papers of the three collaborators showed a similar pattern: it grew to around 2007 and then began to decline. From the figure, we can also observe that the proportion of the papers of the four collaborators also peaked in 2017 (slope 0), and it is likely that the proportion of the papers of the four collaborators will start to decline in the future.

The decline in the proportion of these papers with fewer authors also means an increase in the proportion of papers with more authors. As shown in the figure, the proportion of papers with 5, 6, 7 collaborators is increasing (the slope of the curve is also increasing).

Although we can't predict the end of growth, this chart very clearly illustrates that academic cooperation in the computer field has been increasing and will continue to increase.


## Statistical Properties of Collaboration Networks Categorized by Number of Authors

From a macro perspective, academic cooperation has been growing. But let's take a look at how academic cooperation networks have changed. We mainly focus on the following properties:

* Degree Distribution
* Clustering Coefficient
* Rich-Club
* Betweenness
* Closeness Centrality

### Degree Distribution

We want to examine how degree distribution of these networks looks like. We calculated the degree distribution of cooperation networks composed of different papers (number of authors <= 3, 4, 5) from 1975 to 2017. For more clear visualization, we only illustrate 6 years of network data in the following figure. We have observed significant power-law phenomena for any year of any type of paper.

![Unknown-4](https://i.imgur.com/DmpGaSY.png)

We fitted these data using univariate linear regression and observed an interesting phenomenon: despite fluctuations, the slope of these curves generally increased with increasing year. If you compare slopes of different kinds of papers, you can always observe that the slope increases with the number of authors. If we look at Figure 1 and Figure 2 together, we can find that there is no significant correlation between the proportion of (number of authors <= 3, 4, 5)papers and the slope of power-law phenomena.

![Unknown](https://i.imgur.com/wkePMXK.png)

We believe that the gentler slope actually indicates that scholars are more inclined to cooperate with more people. Let us give a simple example to illustrate.

We only consider the network composed by papers with 3 or fewer authors. 
If researchers are only working with fixed people, no matter how many papers they publish, their only neighbors are each other.

The degree of each point in this network is usually 2 or 3, and the network will be filled with a large number of components that are not connected to each other. If we plot the degree distribution, we get a very steep straight line.

If they start to work with different people, then more people will have a higher degree; in other words, the curve will become flatter. We can therefore point to a change in the pattern of cooperation: scholars tend to collaborate with more people.




