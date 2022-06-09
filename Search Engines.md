---
created: 2022-06-08T21:57:58+08:00
modified: 2022-06-09T13:38:56+08:00
---

# Search Engines DIY

I bet there are many many alternatives. even for a relational database or graph database it can be a search engine by its nature.

how the heck can i search my own notes? slice it into little segments? standard excerpt included.

search for search engine in github.

search engines are related to spiders/crawlers.

how to utilize these search engines is a problem/challenge. use url filters, generic extractors, readbility.js, summarizers like sumy.

many specialized search engines that can search image, video and audio. one example is Jina

txtai:
semantic search tool
pip3 install txtai
using sentence-transformer models from huggingface
https://github.com/neuml/txtai

yacy:
distributed search engine circumvent censorship

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
