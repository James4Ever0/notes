---
title: LlamaIndex hackathon resource guide
created: '2024-02-07T18:41:37.098Z'
modified: '2024-02-07T18:41:45.545Z'
---

# LlamaIndex hackathon resource guide

Beginners
What is Retrieval-Augmented Generation (RAG)? What is any of this?
We have libraries in Python and TypeScript; the Python lib has more features
Installation and getting started:
Python
TypeScript
I want to customize…
LlamaHub is a collection of data connectors, agent tools and pre-written code
We have notebooks that show how to use the tools on LlamaHub
create-llama is a command-line tool that sets up a starter full-stack app for you
Installation instructions
We strongly recommend starting with this if you’re not sure where to start!
The RAG CLI is a command-line tool that will index and query files for you
Good for quickly checking if indexing documents works
Building a low-code chatbot with Streamlit (this tool is called RAGs)
What can I use?
All the vector stores we support
All the LLMs we support
All the embedding models we support
What’s the best way load and parse data?
The ingestion pipeline
How do I get full control over how my query engine works?
The query pipeline
Intermediate
We have several pre-built repos you may want to fork and modify:
SEC Insights, an advanced full-stack RAG app using multi-document agents
A full-stack demo repo using MongoDB Atlas
A (very similar) demo repo using Azure Cosmos DB (a MongoDB clone)
Create_llama_projects is a list of starter apps that can be installed with create-llama
RAG over embedded tables
Multi-document agent
Multi-modal (images)
Llamabot, a Slack bot
Gives step-by-step instructions to build a Slack bot with memory
LlamaParse, our advanced PDF parsing service
There’s a special $500 + swag prize for best use of LlamaParse!
Customizing prompts
Hybrid search
Vector search + keyword (BM25) search
Advanced
These are mostly notebooks showing how we did it
Customizing module types
Every component — retrievers, parsers, query engines, agents — can be customized.
Combining multiple data sources
e.g. Slack + docs + API
Routing across multiple sources
Shows tool use, lets the LLM decide what tool to pick
Multi-document queries
Answering a single question that needs multiple sources to answer
Examples of agents
Autonomous decision-making using LlamaIndex
Extracting structured outputs from unstructured data
e.g. Turn web pages into JSON
Multi-modal examples
Interpreting images, retrieving images
Auto-retrieval aka metadata filtering
Get the LLM to pre-filter data by tag in your database
Recursive retrieval
Treat sub-nodes differently when retrieving
Text to SQL
Query a database using an LLM
Pandas query engine
Query ingested tables using Pandas
