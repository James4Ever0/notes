---
created: 2022-05-27T11:25:06+08:00
modified: 2022-05-28T12:57:19+08:00
---

# 推荐系统 GNN

不同的人有不同喜好
不同的人和不同的人说话
不同的产品有不同的特征
不同的产品和不同的产品被一起推荐

人对产品的接受度

video segments have different features and orders. predict missing links. predict categories semi-supervised or unsupervised.

video-image-text-music correlation and predict internal relationships, categories.

recommendation system:
paddlerec(multimodal), torchrec(cuda==11.3, build failed due to unable to find ATen from torch/include.)
https://neo4j.com/docs/graph-data-science/current/end-to-end-examples/fastrp-knn-example/

link prediction:
https://github.com/Orbifold/pyg-link-prediction/blob/main/run.py

how to use pyg for link prediction:
https://github.com/pyg-team/pytorch_geometric/issues/634

dgl, install from source, with link prediction:
https://docs.dgl.ai/tutorials/blitz/4_link_predict.html
https://github.com/dmlc/dgl
https://docs.dgl.ai/guide_cn/training-link.html#guide-cn-training-link-prediction

gnn intro:
https://cnvrg.io/graph-neural-networks/

gnn applications:
    Node classification: The objective here is to predict the labels of nodes by considering the labels of their neighbors. 
    Link prediction: In this case, the goal is to predict the relationship between various entities in a graph. This can for example be applied in prediction connections for social networks. 
    Graph clustering: This involves dividing the nodes of a graph into clusters. The partitioning can be done based on edge weights or edge distances or by considering the graphs as objects and grouping similar objects together. 
    Graph classification: This entails classifying a graph into a category. This can be applied in social network analysis and categorizing documents in natural language processing. Other applications in NLP include text classification, extracting semantic relationships between texts, and sequence labeling. 
    Computer vision: In the computer vision world, GNNs can be used to generate regions of interest for object detection. They can also be used in image classification whereby a scene graph is generated. The scene generation model then identifies objects in the image and the semantic relationship between them. Other applications in this field include interaction detection and region classification. 

