---
tags: [advertising, chatbot, graph database, pyjom, recommendation]
title: 推荐系统 GNN
created: '2022-05-27T03:25:06.000Z'
modified: '2023-02-08T03:23:32.247Z'
---

# 推荐系统 GNN

1、muricoca/crab
https://github.com/muricoca/crab

2、ibayer/fastFM
https://github.com/ibayer/fastFM

3、Mendeley/mrec
https://github.com/mendeley/mrec

4、MrChrisJohnson/logistic-mf
https://github.com/MrChrisJohnson/logistic-mf

5、jadianes/winerama-recommender-tutorial
https://github.com/jadianes/winerama-recommender-tutorial

6、ocelma/python-recsys
https://github.com/ocelma/python-recsys

7、benfred/implicit
https://github.com/benfred/implicit

8、lyst/lightfm
https://github.com/lyst/lightfm

9、python-recsys/crab
https://github.com/python-recsys/crab

10、NicolasHug/Surprise
https://github.com/NicolasHug/Surprise

----

linkedin [gdmix](https://github.com/linkedin/gdmix) simple and memory effective personalized ranking

datawhale [fun-rec 推荐系统入门教程](https://github.com/datawhalechina/fun-rec)
datawhale [rechub](https://github.com/datawhalechina/torch-rechub)

[image to text, text to image, clip as image/text embeddings](https://github.com/jina-ai/clip-as-service)

[deep recommendation using tensorflow 1.15](https://awesomeopensource.com/project/alibaba/DeepRec)

[image recommendation system](https://medium.com/analytics-vidhya/how-create-image-recomendation-system-3dcc5edf1597)

不同的人有不同喜好
不同的人和不同的人说话
不同的产品有不同的特征
不同的产品和不同的产品被一起推荐

人对产品的接受度

youzan has an ai platform called trexpark, offering chinese NLP and image models pretrained from e-commerce databases.
https://github.com/youzanai/trexpark

session based recommendation system:
https://github.com/CRIPAC-DIG/SR-GNN

decide the feedback embeddings:
https://huggingface.co/youzanai/bert-product-comment-chinese

conversational embeddings:
https://huggingface.co/youzanai/bert-customer-message-chinese

neo4j developer build a recommendation engine:
https://neo4j.com/developer/cypher/guide-build-a-recommendation-engine/

torch_geometric(PyG) documentation:
https://pytorch-geometric.readthedocs.io/en/latest/modules/nn.html#torch_geometric.nn.conv.GatedGraphConv

setup GCN using PyG:
https://zhuanlan.zhihu.com/p/400078504

tagspace text classification via hashtags:
https://paddlerec.readthedocs.io/en/latest/models/contentunderstanding/tagspace.html

gnn is based on basic data/label models and provide high-level reasoning and predictions.

neo4j graph academy practical usage:
https://graphacademy.neo4j.com/categories/
https://neo4j.com/graphacademy/training-iga-40/12-iga-40-ingredient-analysis/

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
