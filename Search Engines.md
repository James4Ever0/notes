---
tags: [diy, search engine, self-hosted]
title: Search Engines
created: '2022-06-08T13:57:58.000Z'
modified: '2022-09-26T15:30:21.321Z'
---

# Search Engines DIY

search engine optimization
[advertools](https://advertools.readthedocs.io/en/master/readme.html)

[zinc search](https://github.com/zinclabs/zinc)

[markuplm markup language model](https://huggingface.co/microsoft/markuplm-base) used for feature rich information extraction, [webqa](https://github.com/susht3/webQA_sequence_labelling_pytorch), arxiv paper: [reading wikipedia to answer open domain questions](https://arxiv.org/abs/1704.00051)

[zinc search, go implementation of elastic search alternative](https://github.com/zinclabs/zinc)

I bet there are many many alternatives. even for a relational database or graph database it can be a search engine by its nature.

how the heck can i search my own notes? slice it into little segments? standard excerpt included.

search for search engine in github.

search engines are related to spiders/crawlers.

how to utilize these search engines is a problem/challenge. use url filters, generic extractors, readbility.js, summarizers like sumy.

many specialized search engines that can search image, video and audio. one example is Jina

semantic search tool, multimedia search tool, neural search tool

https://github.com/searxng/searxng

parse popular search engine results like baidu, bing:
https://github.com/bisohns/search-engine-parser

search and scrape news
https://github.com/01joy/news-search-engine

image search engine
https://github.com/matsui528/sis

search engines used by hackers, social engineering, onion sites:
https://github.com/edoardottt/awesome-hacker-search-engines

search engine with customized recommendation:
https://github.com/mtianyan/FunpySpiderSearchEngine

seo tools 百度下拉词获取 推荐词相关词
https://github.com/marcobiedermann/search-engine-optimization

a self-hosted search engine that can be deployed on heroku, google alike:
https://github.com/benbusby/whoogle-search

txtai:
semantic search tool
pip3 install txtai
using sentence-transformer models from huggingface sentence embedding
https://github.com/neuml/txtai

yacy:
distributed search engine circumvent censorship
provide rss feeds

searx:
meta search engine self-hosted
has third-party hosted searx websites avaliable:
https://searx.space/ total 83 online(currently)

mwmbl:
distributed crawler central search engine, can be self-hosted
written in python

video search engine:
generate summary from frames
https://github.com/AkshatSh/VideoSearchEngine

yuno:
context based search engine for anime, anime search engine with transformer and deep learning. text based search. more like a semantic search tool, or neural search tool.
Yuno is a context based search engine that indexes over 0.5 million anime reviews and other anime informations. To help you find anime with specific properties. This search engine will help people of r/AnimeSuggest who are looking for specific type of anime to watch.
This search engine was created to solve the problem of finding an object with specific properties and the object in this case is anime. But this search engine can be easily extended to any domain like books,movies,etc. Without the need of any kind of handcrafted dataset.

TypeSense:
dedicated client for every popular programminhg language
consume much fewer ram than meilisearch
need to write custom web interface via nodejs
upload data via client api

MeiliSearch:
good for small dataset
consume whoopy 900mb for my 9mb json dataset.
has intuitive web interface.
upload document via web post.
