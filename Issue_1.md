
# Issue 1  - graph thinking
[TOC]


# Graph thinking

**Exploring the World of Computational Propaganda and Graph Models**

Welcome to my new newsletter where I share my thoughts, experiences, and reflections on various topics. This edition focuses on my recent fixation, computational propaganda and graph models. As a self-proclaimed search junkie, I've been diving deep into this subject, and I'm excited to share my findings with you.

Tabulare data has always seemed like a strange concept to me. The idea of taking elements of the world and assuming their value is independent of other values is tempting but ultimately reductionist. With the rapid advancements in computational power and storage techniques, it's becoming increasingly clear that we need a more representative model of the world that takes into account the relationships and connections between different elements.

Over the past few months, I've been exposing myself to a variety of techniques and technologies that allow me to work with representative data in a more relational and centered way, specifically graph and network models. In this newsletter, I've compiled a selection of resources on these topics and added a touch of digital propaganda, which is another theme that I'm passionate about.

I hope you enjoy this edition, and I look forward to your feedback as I continue to co-develop this newsletter. The format and structure are still a work in progress, but I'm eager to find a balance between my passions and your interests. So, let's dive in and explore the world of computational propaganda and graph models together. 

**So if graph algorithms and computational social science are not something that you may be interested in, you may ignore the rest of this newsletter.**

# Resources [^blog]
i will keep update the page with new resources
Let start with our school resource.

##  [Institut Polytechnique](https://www.ip-paris.fr/rechercher?s=home%20en) de Paris resaerchers
* [Thomas Bonald](https://www.telecom-paris.fr/thomas-bonald?l=en) Professor, at Institut Polytechnique de Paris

* [Tiphaine Viard](https://www.telecom-paris.fr/tiphaine-viard), Associate Professor, at Institut Polytechnique de Paris
 
* [Simon Delarue](https://www.linkedin.com/in/simon-delarue-98aa045a/), Ph.D. Candidate, at Institut Polytechnique de Paris
 
* [Haileleul Haile](https://www.linkedin.com/in/haileleul-haile/), Masters Student at Institut Polytechnique de Paris
 
* Telecom Graph Mining [course](https://moodle.r2.enst.fr/moodle/course/view.php?id=111)
## scikit-network
![](https://hackmd.io/_uploads/HkuiS_4no.png)

Python package for the analysis of large graphs

## Interesting tutorials/package : 

### Geometric graphs

A pedagogical resource for beginners and experts to explore the design space of [Graph Neural Networks for geometric graphs](https://github.com/chaitjo/geometric-gnn-dojo).
![](https://hackmd.io/_uploads/ByTZ8v42o.png)



[A Gentle Introduction](https://github.com/chaitjo/geometric-gnn-dojo/blob/main/geometric_gnn_101.ipynb) to Geometric Graph Neural Networks
![](https://hackmd.io/_uploads/HJUVIvNhs.png)

> practical notebook on Geometric GNNs 101, prepared for MPhil students at the University of Cambridge.





[Graph-tool](https://graph-tool.skewed.de/) is an efficient Python module for manipulation and statistical analysis of graphs (a.k.a. networks). Contrary to most other Python modules with similar functionality, the core data structures and algorithms are implemented in C++, making extensive use of template metaprogramming, based heavily on the Boost Graph Library. This confers it a level of performance that is comparable (both in memory usage and computation time) to that of a pure C/C++ library. 

### Apache TinkerPop™
[Apache TinkerPop™](https://tinkerpop.apache.org/index.html) is a graph computing framework for both graph databases (OLTP) and graph analytic systems (OLAP).
![](https://hackmd.io/_uploads/r19k8r4ni.png)

### NetworKit
NetworKit is a growing [open-source toolkit](https://networkit.github.io/) for large-scale network analysis. Its aim is to provide tools for the analysis of large networks in the size range from thousands to billions of edges. For this purpose, it implements efficient graph algorithms, many of them parallel to utilize multicore architectures. These are meant to compute standard measures of network analysis, such as degree sequences, clustering coefficients, and centrality measures. In this respect, NetworKit is comparable to packages such as NetworkX, albeit with a focus on parallelism and scalability.

### Boost
The [Boost Graph Library](https://www.boost.org/doc/libs/1_76_0/libs/graph/doc/index.html?utm_source=rss&utm_medium=rss) (BGL) 

the Boost Graph Library is a generic interface that allows access to a graph's structure, but hides the details of the implementation. This is an “open” interface in the sense that any graph library that implements this interface will be interoperable with the BGL generic algorithms and with other algorithms that also use this interface. The BGL provides some general purpose graph classes that conform to this interface, but they are not meant to be the “only” graph classes; there certainly will be other graph classes that are better for certain situations. We believe that the main contribution of the The BGL is the formulation of this interface. 
## Interesting papers

[Stream Graphs](https://arxiv.org/pdf/1710.04073.pdf) and Link Streams for the Modeling of Interactions over Time

- BERT with [Entity Mapping for Propaganda](https://arxiv.org/pdf/2008.09894v2.pdf) Classification 
> This paper used shallow Natural Language Processing (NLP) preprocessing techniques to reduce the noise in the dataset, feature selection methods, and common supervised machine learning algorithms. The final model is based on using the BERT system with entity mapping. To improve our model’s accuracy, we mapped certain words into five distinct categories by employing word-classes and entity recognition.

- [GNNExplainer: ](https://arxiv.org/pdf/1903.03894v4.pdf)Generating Explanations for Graph Neural Networks
![](https://hackmd.io/_uploads/ByjXvv4hs.png)

> GNNEXPLAINER as an optimization task that maximizes the mutual information between a GNN’s prediction and distribution of possible subgraph structures. Experiments on synthetic and real-world graphs show that our approach can identify important graph structures as well as node features, and outperforms alternative baseline approaches by up to 43.0% in explanation accuracy. ([+](https://github.com/RexYing/gnn-model-explainer))

- A [collection](https://github.com/shaoxiongji/knowledge-graphs) of knowledge graph papers, codes, and reading notes.
> A collection of knowledge graph papers, codes, and reading notes.

- [A Review](https://arxiv.org/pdf/1503.00759v3.pdf) of Relational Machine Learning for Knowledge Graphs
> A review of how such statistical models can be
“trained” on large knowledge graphs, and then used to predict new facts about the world (which is equivalent to predicting new edges in the graph). 

- [Synthetic Graph Generation](https://arxiv.org/pdf/2204.01376v1.pdf) to Benchmark Graph Learning
> This papaer propose to generate synthetic graphs, and study the behaviour of graph learning algorithms in a controlled scenario. We develop a fully featured synthetic graph generator that allows deep inspection of different models. We argue that synthetic graph generations allows for thorough investigation of algorithms and provides more insights than overfitting on three citation datasets. In the case study, we show how our framework provides insight into unsupervised and supervised graph neural network models.

- [Text Generation](https://arxiv.org/pdf/1904.02342.pdf) from  Knowledge Graphs with Graph Transformers
![](https://hackmd.io/_uploads/HJH3jN43j.png)

> A novel graph transforming encoder which can leverage the relational structure of such knowledge graphs without imposing linearization or hierarchical constraints.Incorporated into an encoder-decoder setup, we provide an end-to-end trainable systemfor graph-to-text generation

- [Synthetic Graph Generation](https://arxiv.org/pdf/2204.01376v1.pdf) to Benchmark Graph Learning
![](https://hackmd.io/_uploads/ry0DHvN3j.png)

- Study the behaviour of graph
> learning algorithms in a controlled scenario. We develop a fully-
featured synthetic graph generator that allows deep inspection of
different models. We argue that synthetic graph generations allows
for thorough investigation of algorithms and provides more insights
than overfitting on three citation datasets. In the case study, we
show how our framework provides insight into unsupervised and
supervised graph neural network models.

- Node-Level Differentially [Private Graph Neural Networks](https://arxiv.org/pdf/2111.15521v3.pdf)
![](https://hackmd.io/_uploads/BkHVHPVni.png)

> This paper define the problem of learning GNN parameters with node-level privacy, and provide an algorithmic solution with a strong
differential privacy guarantee. We employ a careful sensitivity analysis and provide a non-trivial extension of the privacy-by-amplification technique to the GNN setting. An empirical evaluation on standard benchmark datasets demonstrates that our method is indeed able to learn accurate privacy–preserving GNNs which outperform both private and non-private methods that completely ignore graph information.

- Towards Detecting [Persuasive Texts and Images](https://arxiv.org/pdf/2106.00240v1.pdf) using Textual and Multimodal Ensemble
![](https://hackmd.io/_uploads/BJMxSDN2s.png)

>The task, Detection of Persuasion Techniques in Texts and Images, is to detect these persuasive techniques in memes. It consists of three subtasks: (A) Multi-label classification using textual content, (B) Multi-label classification and span identification using textual content, and (C) Multi-label classification using visual and textual content. In this pa-per, we propose a transfer learning approach to fine-tune BERT-based models in different modalities. 

- [Context-Aware Rich Feature Representations](https://arxiv.org/pdf/2007.10827.pdf) For Propaganda Classification
![](https://hackmd.io/_uploads/rJH0BPN3o.png)


> Detection of Propaganda Techniques in News Articles for each of the two subtasks of Span Identification and Technique Classification. We make use of pre-trained BERT language model enhanced with tagging techniques developed for the task of Named Entity Recognition (NER), to develop a system for identifying propaganda spans in the text. For the second subtask, we incorporate contextual features in a pre trained RoBERTa model for the classification of propaganda techniques. ([+](https://github.com/paramansh/propaganda_detection))

- Risks of [Propaganda-As-A-Service](https://arxiv.org/pdf/2112.05224.pdf) and Countermeasures
 ![](https://hackmd.io/_uploads/ByYY9ENho.png)

> An Investigatatiom on threat to neural sequence-to-sequence (seq2seq) models: training-time attacks that cause models to “spin” their outputs so as to support an adversary chosen sentiment or point of view—but only when the input contains adversary-chosen trigger words. For example, a spinned1 summarization model outputs positive summaries of any text that
mentions the name of some individual or organization. https://github.com/ebagdasa/propaganda_as_a_service/blob/master/Spinning_Language_Models_for_Propaganda_As_A_Service.ipynb
Spinned models are located on [HuggingFace Hub](https://huggingface.co/ebagdasa).

https://github.com/ebagdasa/propaganda_as_a_service

Other KNOWLEDGE-GRAPH-PAPERS [^KNOWLEDGE-GRAPH-PAPERS]

[One-Class Graph Neural Networks](https://arxiv.org/pdf/2002.09594v2.pdf) for Anomaly, Detection in Attributed Networks
>one-class classification framework for graph anomaly
detection. OCGNN is designed to combine the powerful representation ability of Graph Neural Networks along with the classical one-class objective. Compared with other baselines, OCGNN achieves significant improvements in extensive ex-periments. ([+](https://github.com/WangXuhongCN/OCGNN))

## Text books/ Courses


1. Spectral and [Algebraic Graph Theory](https://www.cs.mcgill.ca/~wlh/grl_book/)

1. * Current version available at http://cs-www.cs.yale.edu/homes/spielman/sagt.

1. * Graph Representation Learning by William L. Hamilton
1. * [Networks, Crowds, and Markets](http://www.cs.cornell.edu/home/kleinber/networks-book/): Reasoning About a Highly Connected World by David Easley and Jon Kleinberg

1. [Network Science](http://networksciencebook.com/) by Albert-László Barabási

1. [Stanford CS224W](http://web.stanford.edu/class/cs224w/index.html): Machine Learning with Graphs | 2021

1. The Structure of [Information Networks Computer Science 6850](https://www.cs.cornell.edu/courses/cs6850/2008fa/) Cornell University Fall 2008

1. [Networks Economics ](https://courses.cit.cornell.edu/info2040_2018fa/)2040 / Sociology 2090 / Computer Science 2850 / Information Science 2040 Cornell University, Fall 2018

1. [Networks](https://dspace.mit.edu/bitstream/handle/1721.1/119628/14-15j-fall-2009/contents/index.htm?sequence=247) (Daron Acemoglu and Asu Ozdaglar, MIT)
 
1. [Topics in Social Data ](http://web.stanford.edu/~jugander/mse334/)(Johan Ugander, Stanford)

1. [Network Theory](http://www-personal.umich.edu/~mejn/courses/2015/cscs535/index.html) (Mark Newman, University of Michigan)
 
1. [Graphs and Networks](https://sites.google.com/a/yale.edu/462-562-graphs-and-networks/) (Dan Spielman, Yale)
 
 
1. [Parallel Graph](http://www.cs.rpi.edu/~slotag/classes/FA16/) Analysis (George Slota, RPI)

1. [Large-Scale Graph Mining](https://sariyuce.com/seminar.html) (A. Erdem Sariyuce, University of Buffalo)
 
1. [Mining Large-scale](Mining Large-scale Graph Data ) Graph Data (Danai Koutra, University of Michigan)

1. Data Mining meets Graph Mining (Leman Akoglu, Stony Brook) 
1. [Graphs and Networks](https://tsourakakis.com/t-79-7003-graphs-and-networks/) (Charalampos Tsourakakis, Aalto University)

1. Large-Scale Graph Processing (Keval Vora, Simon Fraser University)

1. [Applied Social Network Analysis](https://www.coursera.org/learn/python-social-network-analysis) in Python of University of Michigan

1. T[he Human Network](https://www.amazon.com/Human-Network-Position-Determines-Behaviors/dp/1101972963/ref=tmm_pap_swatch_0?_encoding=UTF8&qid=1540174871&sr=1-5): How Your Social Position Determines Your Power, Beliefs, and Behaviors

1. Social and Economic Networks [Matthew O. Jackson](https://web.stanford.edu/~jacksonm/books.html)



## Labs

### [DIG](https://www.telecom-paris.fr/en/research/laboratories/information-processing-and-communication-laboratory-ltci/research-teams/data-intelligence-graphs) 
Data, Intelligence and Graphs
>The DIG team aims at making data and knowledge easy to extract, exploit and understand. The research conducted by the team covers both theoretical and practical aspects. The outcomes of this research include new algorithms (for data mining, graph analysis, processing of data streams), new data structures and languages (for storing and querying data) and new learning techniques (for question answering, content recommendation, trend and anomaly detection).

### Sciences Po [Medialab](https://medialab.sciencespo.fr/en/)
The médialab is an interdisciplinary research laboratory which conducts thematic and methodological research to investigate the role of digital technology in our societies. Sicnce po media lab also developpe severl open source backage. [^Medialab]

### [ISC-PIF](https://cssociety.org/home)

The ISC-PIF (Institut des Systèmes Complexes, Paris Île-de-France – Paris Île-de-France Complex Systems Institute) is an interdisciplinary research and training center that promotes the development of French, European and international strategic projects on complex adaptive systems, understood as large networks of elements interacting locally and creating macroscopic collective behavior.

### Complex Networks
[Complex Networks](https://www.complexnetworks.fr/) is a LIP6 team, hosted at Sorbonne Université and a member of the CNRS

## Intresting podcast/video

- [David Chavalarias](https://twitter.com/chavalarias) talk on [Toxic Data](https://www.youtube.com/watch?v=i9jUTI6yS8c) 
{%youtube i9jUTI6yS8c %}

- [Graph Mining & Learning ](https://videos.neurips.cc/)at the Neural Information Processing Systems Conference

> The Neural Information Processing Systems Foundation is a non-profit corporation whose purpose is to foster the exchange of research advances in Artificial Intelligence and Machine Learning, principally by hosting an annual interdisciplinary academic conference with the highest ethical standards for a diverse and inclusive community.

- [Conferance](https://vimeo.com/showcase/7808751) of Science po médialab (in french)
[![](https://hackmd.io/_uploads/HJ2aUrN3j.jpg =200x200)](https://vimeo.com/showcase/7808751)

- Fast And [Educational Exploration](https://www.pythonpodcast.com/graph-tool-graph-data-analysis-episode-322/) And Analysis Of Graph Data Structures With graph-tool
![](https://hackmd.io/_uploads/ry5sDHV3j.jpg =200x200)

- Between Two Nodes: A Conversation with [Peter Hinssen](https://shows.acast.com/between-two-nodes/episodes/archive-peter-hinssen)
![](https://hackmd.io/_uploads/Sy5X5HVnj.png =200x200)

>Acclaimed author Peter Hinssen – also a serial entrepreneur – has penned five bestselling books, and has given many keynote speeches around the world, including for Google Think Performance, Nimbus Ninety, Tedx, Paypal, SAS, Accenture, and Apple. He also lectures at renowned business schools like the London Business School, MIT Sloan School of Management, and more.

- [Categories, Graphs, Reasoning](https://podcasts.google.com/feed/aHR0cHM6Ly9hbmNob3IuZm0vcy8xZTRhMGVhYy9wb2RjYXN0L3Jzcw/episode/MjI1YjUzMTAtOWQ1ZC00MWFkLWFlMDItYWFjOGY5MTExNzM2?sa=X&ved=0CAUQkfYCahcKEwjI0umtwe38AhUAAAAAHQAAAAAQEQ)

> Dr. Petar Veličković  is a Staff Research Scientist at DeepMind, he has firmly established himself as one of the most significant up and coming researchers in the deep learning space. He invented Graph Attention Networks in 2017 and has been a leading light in the field ever since pioneering research in Graph Neural Networks, Geometric Deep Learning and also Neural Algorithmic reasoning. If you haven’t already, you should check out our video on the Geometric Deep learning blueprint, featuring Petar. I caught up with him last week at NeurIPS. In this show, from NeurIPS 2022 we discussed his recent work on category theory and graph neural networks.

## Interesting data set
- [Propaganda](https://github.com/annabechang/Propaganda_Tech_Twitter_PRC) Tech Twitter PRC

- [A Study](https://jonmillward.com/blog/studies/deep-inside-a-study-of-10000-porn-stars/) of 10,000 Porn Stars and Their Careers

- Twitter dataset for 2022 [Russian and Ukrainian](https://github.com/ehsanulhaq1/russo_ukraine_dataset) crisis

- [Stanford](https://snap.stanford.edu/data/) Large Network Dataset Collection

> The SNAP library is being actively developed since 2004 and is organically growing as a result of our research pursuits in analysis of large social and information networks. Largest network we analyzed so far using the library was the Microsoft Instant Messenger network from 2006 with 240 million nodes and 1.3 billion edges.

The datasets available on the website were mostly collected (scraped) for the purposes of our research.

The website was launched in July 2009.

### FrameNet
The [FrameNet project](https://framenet.icsi.berkeley.edu/fndrupal/about) is building a lexical database of English that is both human- and machine-readable, based on annotating examples of how words are used in actual texts. 

### Open Graph Benchmark

The [Open Graph Benchmark](https://ogb.stanford.edu/) (OGB) is a collection of realistic, large-scale, and diverse benchmark datasets for machine learning on graphs. OGB datasets are automatically downloaded, processed, and split using the OGB Data Loader. 






Recommender Systems and Personalization [Datasets](https://cseweb.ucsd.edu/~jmcauley/datasets.html#amazon_reviews) maintined by [Julian McAuley](https://cseweb.ucsd.edu/~jmcauley/) 




[^KNOWLEDGE-GRAPH-PAPERS]: KNOWLEDGE-GRAPH-PAPERS 
    - Entity Extraction: From Unstructured Text to DBpedia RDF Triples LINK: http://ceur-ws.org/Vol-906/paper7.pdf

    - An Automatic Knowledge Graph Creation Framework from Natural Language Text LINK: https://www.jstage.jst.go.jp/article/transinf/E101.D/1/E101.D_2017SWP0006/_pdf

    - Representation Learning of Knowledge Graphs with Entity Descriptions LINK: https://dl.acm.org/citation.cfm?id=3016100.3016273

    - A Review of Relational Machine Learning for Knowledge Graphs LINK: https://arxiv.org/abs/1503.00759

    - Seq2RDF: An end-to-end application for deriving Triples from Natural Language Text LINK: https://arxiv.org/abs/1807.01763


    - Learning beyond datasets: Knowledge Graph Augmented Neural Networks for Natural language Processing LINK: https://aclweb.org/anthology/N18-1029

    Building and Using a Knowledge Graph to Combat Human Trafficking LINK: https://usc-isi-i2.github.io/papers/szekely15-iswc.pdf

[^Medialab]: Médialab packages

    - Table 2 Netmade by the médialab
    An online tool that allows users to create a network graph in a few clicks from a csv file https://medialab.github.io/table2net/


    - minet is a webmining command line tool & library for python (>= 3.7) that can be used to collect and extract data from a large variety of web sources such as raw webpages, Facebook, CrowdTangle, YouTube, Twitter, Media Cloud etc.
    https://github.com/medialab/minet


    - Web application enabling users to publish and visually analyse networks
    https://medialab.github.io/minivan/#/

    - HeatGraphmade
    A visualization tool allowing to produce heatmaps from the density of nodes in a spatialized network
    https://github.com/medialab/heatgraph

    - A Python library to handle, read and write GEXF format, the XML file formats for network graphs https://github.com/paulgirard/pygexf


    - sigma.jsmade
    JavaScript library used to visualize network graphs in the browser
    https://github.com/jacomyal/sigma.js

    - Gazouilloiremade 
    a backend tool to run massive Twitter data harvesting on the long term
    https://github.com/medialab/gazouilloire

    - Manylinesmade
    web application allowing to display, spatialize and categorize a network, then to write and share an interactive     story composed of specific views of the visualization
    https://github.com/medialab/manylines
    
[^blog]: Please check https://github.com/hghalebi/Blog