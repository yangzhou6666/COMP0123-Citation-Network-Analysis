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

# Data and Methodology

## Data Preparation

In this section, we are going to introduce how we extract and pre-process our data.

The original data we use is Citation Network Dataset [xx].The citation data is extracted from DBLP, ACM, MAG (Microsoft Academic Graph), and other sources. The dataset contains more than 4 million papers published within 1890 and 2018. Every paper and author will have an ID to uniquely identify them. This dataset also provides rich metadata, such as the title of the paper, the name of the conference, the publisher, etc., but we do not need these irrelevant data. All we need is the publication year and its author ID.

Our hypothesis for constructing a network is that if four authors co-author a paper, then we assume that the four authors know each other and they form a fully connected graph. We do not rule out some papers with multiple versions, but this has not affected our analysis much. Because in our network, the cooperative relationship between scholars is dual. Even if the same paper was included twice for some reason, it had no effect.

Our goal is to extract from the raw data collaboration networks formed by all papers with fewer authors published in a particular year. In order to make our research more reliable, we constructed three sets of data: a collection of papers with less than 4 collaborators, a collection of papers with fewer than 5 collaborators, and a collection of papers with fewer than 6 collaborators. The specific extraction process is as follows:

* [x] Draw a process graph

![process graph](https://i.imgur.com/2cCy01S.jpg)


1. Convert original data (.txt file) to a csv file. Each row represents a paper, including paperID, publication year, and IDs of all authors.
2. Separate the csv file in Step 1 to multiple csv files according to publication year.
3. For the file of each year, extract three csv file:
    1. Set of papers with less than 4 authors
    2. Set of papers with less than 5 authors
    3. Set of papers with less than 6 authors
4. In the last step, we get $3 * year\_range$ csv files. We convert these files to network format.


Although original data source provides paper data published between 1890 and 2018, but we only choose papers from 1975 to 2017 as our research object. Since many old papers might not be contained in the dataset and affect the data analysis results.